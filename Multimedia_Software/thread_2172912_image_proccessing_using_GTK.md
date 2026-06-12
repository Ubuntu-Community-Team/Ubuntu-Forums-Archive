---
title: "image proccessing using GTK"
date: 2013-09-07
forum: Multimedia Software
---

### Post by devang2 on 2013-09-07
Hello,

I am beginner in field of image processing using GTK library. I am trying to convert image from RGB to YUV. I have applied standard equation for the same, but after converting it in YUV format, i dont know how to save the image in YUV format. I have read that GTK  currently support only RGB colour space. if anyone know about solution to this than please reply. thank you in advance.

---

### Post by tgalati4 on 2013-09-07
I don't think there are any GTK libraries that will do that, but *ffmpeg* might:  [http://stackoverflow.com/questions/15778774/using-ffmpeg-to-losslessly-convert-yuv-to-another-format-for-editing-in-adobe-pr](http://stackoverflow.com/questions/15778774/using-ffmpeg-to-losslessly-convert-yuv-to-another-format-for-editing-in-adobe-pr)

So you could write most of your routine in GTK and call *ffmpeg* with the appropriate switches to save back to YUV.  There do seem to be some bugs though when going from RGB to YUV, so you will have to test it extensively.

---

### Post by cathyhill on 2014-04-01
> **devang2 said:**
> Hello,

I am beginner in field of [[COLOR=#272727]image processing[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/imaging-processing/") using GTK library. I am trying to [[COLOR=#272727]convert image[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/image-converting/") from RGB to YUV. I have applied standard equation for the same, but after converting it in YUV format, i dont know how to save the image in YUV format. I have read that GTK  currently support only RGB colour space. if anyone know about solution to this than please reply. thank you in advance.

I did not find a solution yet, but I found two related posts. If you have found a solution, please share with us.:popcorn:

[http://stackoverflow.com/questions/9325861/converting-yuv-rgbimage-processing-yuv-during-onpreviewframe-in-android](http://stackoverflow.com/questions/9325861/converting-yuv-rgbimage-processing-yuv-during-onpreviewframe-in-android)
[http://stackoverflow.com/questions/9948074/convert-8-depth-single-channel-yuv-image-to-24-depth-rgb3-channels-image](http://stackoverflow.com/questions/9948074/convert-8-depth-single-channel-yuv-image-to-24-depth-rgb3-channels-image) 

But since GTK only supports 24-depth RGB, I do not think you can save image in YUV format under GTK interface.;)

---

