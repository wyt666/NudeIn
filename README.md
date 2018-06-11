<img src="https://github.com/hon-key/HKAttributedTextView/raw/master/logo.png" width = "100%" />

# NudeIn

NudeIn 是一个基于 UITextView ，书写风格类似于 masonry 的 iOS 端富文本控件，它采用优雅的声明式(链式)方法定义富文本控件，和编程式的不同，它所需的代码量相当短，且非常直观易用。

## Usage

NudeIn 的用法非常简单明了，这里给出一个非常简单的例子，相信你会被这样的用法惊艳到，一旦用起来就会爱不释手:

1、引入控件
```Objective-C
#import "NudeIn.h"
```

2、声明控件为你的成员变量

```objc
@property (nonatomic,strong) NudeIn *attrLabel;
```

3、Do it yourself
```objc
_attrLabel = [NudeIn make:^(NUDTextMaker *make) {
    make.text(@"this is a ").font(14).color([UIColor blackColor]).attach();
    make.text(@"BlueLink").font(17).color([UIColor blueColor]).link(self,@selector(linkHandler:)).attach();
    make.text(@", and this is a ").font(14).color([UIColor blackColor]).attach();
    make.text(@"RedLink").font(17).color([UIColor redColor]).link(self,@selector(linkHandler:)).attach();
}];

```

3、对声明了 **`link`** 属性的部分定义回调
```objc

- (void)linkHandler:(NUDAction *)action {
    
    if ([action isKindOfClass:[NUDLinkAction class]]) {
        
        NUDLinkAction *linkAction = (NUDLinkAction *)action;
        
        UIAlertController *alertController = [UIAlertController alertControllerWithTitle:linkAction.string message:nil preferredStyle:UIAlertControllerStyleAlert];
    
        [alertController addAction:[UIAlertAction actionWithTitle:@"OK" style:UIAlertActionStyleDefault handler:^(UIAlertAction * _Nonnull action) {
        }]];
        
        [self presentViewController:alertController animated:YES completion:nil];
        
    }
    
}

```

结果会是这样：

<img src="https://github.com/hon-key/HKAttributedTextView/raw/master/Screenshots/1.png" width = "50%" />

点击带有 **`link`** 属性的部分，将产生回调：

<img src="https://github.com/hon-key/HKAttributedTextView/raw/master/Screenshots/2.png" width = "50%" />


## Documents

* ### [Text](#usage)

    - [**font**](#usage) **`通过大小声明字体，统一使用系统字体`**

    - [**fontName**](#usage) **`通过字体名以及大小声明字体`**

    - [**fontRes**](#usage) **`通过 UIFont 声明字体`**

    - [**fontStyle**](#usage) **`声明字体的风格，如 Bold、Light 等`**

    - [**bold**](#usage) **`声明字体为 Bold 风格，如果有的话`**

    - [**color**](#usage) **`声明文字的前景色`**

    - [**mark**](#usage) **`声明文字的底色`**

    - [**hollow**](#usage) **`声明文字为镂空`**
    
    - [**solid**](#usage) **`声明文字为实心`**

    - [**link**](#usage) **`声明文字为链接文字`**

    - [**_**](#usage) **`声明文字带下划线`**

    - [**deprecated**](#usage) **`声明文字带删除线`**

    - [**skew**](#usage) **`声明文字为斜体`**

    - [**kern**](#usage) **`声明文字的紧凑程度`**

    - [**ln**](#usage) **`声明文字换行`**
    
    - [**ligature**](#usage) **`声明文字为连体字`**
    
    - [**letterpress**](#usage) **`声明文字为印刷风格（凸起效果），该属性占用内存较高，谨慎使用`**
    
    - [**veritical**](#usage) **`声明文字的垂直偏移`**
    
    - [**stretch**](#usage) **`声明文字的水平拉伸程度（产生变形）`**
    
    - [**reverse**](#usage) **`声明文字逆序书写`**
    
    - [**shadow**](#usage) **`声明文字带默认阴影`**
    
    - [**shadowDirection**](#usage) **`声明文字带阴影，并且设定阴影为八个基本方向`**
    
    - [**shadowOffset**](#usage) **`声明文字带阴影，并且完全自定义阴影的方向`**
    
    - [**shadowBlur**](#usage) **`声明文字带阴影，并自定义阴影的模糊程度`**
    
    - [**shadowColor**](#usage) **`声明文字带阴影，并自定义阴影颜色`**
    
    - [**shadowRes**](#usage) **`通过 NSShadow 声明并自定义阴影`**
    
    - [**lineSpacing**](#usage) **`声明文字的行距`**
    
    - [**lineHeight**](#usage) **`声明文字的行高，（最小行高，最大行高，行高倍数）`**
    
    - [**paraSpacing**](#usage) **`声明文字每个自然段对其他自然段拉开的点距，（与前自然段拉开的点距，与后自然段拉开的点距）`**
    
    - [**paraSpacing**](#usage) **`声明文字每个自然段对其他自然段拉开的点距，（与前自然段拉开的点距，与后自然段拉开的点距）`**
    
    - [**aligment**](#usage) **`声明文字的对齐方式，参数为 NUDAlignment`**
    
    - [**indent**](#usage) **`声明文字的缩进，（前缩进，后缩进）`**
    
    - [**fl_headIndent**](#usage) **`声明文字的首行前缩进，该属性会在首行覆盖 indent 的前缩进属性`**
    
    - [**linebreak**](#usage) **`声明文字的断行方式，参数为 NUDLineBreakMode`**
    
   
    
* ### [textTemplate](#usage)

* ### [Image](#usage)

    - [**origin**](#usage) **`声明图像的偏移，锚点为左下角`**
    
    - [**size**](#usage) **`声明图像的大小`**
    
    - [**ln**](#usage) **`声明图像换行`**
    
* ### [imageTemplate](#usage)

## Installation

```
pod 'NudeIn' '~> 1.2.1-beta'
```
最新 pod 版本：`1.2.1-beta`

目前该版本属于不稳定版本，有一些属性是在1.2.1-beta之后添加的，有可能不包含一部分功能

最低 iOS 版本： `8.0`

## License

NudeIn is released under the MIT license. See [LICENSE](https://github.com/hon-key/HKAttributedTextView/raw/master/LICENSE) for details.
