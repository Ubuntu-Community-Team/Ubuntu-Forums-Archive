---
title: "How to batch convert .jpgs to files with sRGB color profile?"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Nixie Pixel on 2010-01-01
Hello, I have a group of 4500 .jpgs which were created with a custom color profile, meaning I can't import them into a video without color problems. I understand from some multimedia folk that I need to convert this color profile to sRGB. I don't know how to do that.

I do have imagemagick, and would love to be able to use it to do this. Can anyone help me figure out how to do it?

I tried an old command I found from many years ago, convert 001.jpg -profile srgb.icm 001new.jpg, but it told me it couldn't find srgb.icm. If this is the correct command, could someone help me find that file? I have a bash script I can use to run the conversion once I get a single file working...

Thanks!

---

### Post by cor2y on 2010-01-01
You can try Imagemagick with its batch command mogrify (single images you just need convert), imagemagick can do colorprofile conversion
[http://www.imagemagick.org/Usage/formats/#color_profile](http://www.imagemagick.org/Usage/formats/#color_profile)

Or you can try Ufraw which also has a gimp plugin both are in the repos.

EDIT
Dont forget you need to have the icc profiles on system for imagemagick.
A quick net search via google should find srgb.icc or via synaptic there seems to be a few icc profiles available for installation with gimp etc

---

### Post by rduke15 on 2012-02-02
See here for useful links, including a bash script to batch convert:
[http://stackoverflow.com/questions/817727/converting-jpeg-colorspace-adobe-rgb-to-srgb-on-linux/9115755#9115755](http://stackoverflow.com/questions/817727/converting-jpeg-colorspace-adobe-rgb-to-srgb-on-linux/9115755#9115755)

---

