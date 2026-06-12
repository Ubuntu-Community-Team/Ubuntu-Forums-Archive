---
title: "HP USB Graphics Adapter"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Merciless on 2012-05-08
Sadly, I have poulsbo, and resolution isn't all that great (1024 X 768). 

To help solve that problem, I got a HP USB Graphics Adapter.  However when I plug it in all I get is a green screen.  How do I tell Ubuntu 12.04 that it is a video out and to use it?


Details:

USB info: 17e9:01d7 Newnham Research 

~$ lsb_release -a
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

[68389.026027] udlfb: DisplayLink HP USB Graphics Adap - serial #
[68389.026051] udlfb: vid_17e9&pid_01d7&rev_0101 driver's dlfb_data struct at f166e800
[68389.026067] udlfb: console enable=1
[68389.026078] udlfb: fb_defio enable=1
[68389.026089] udlfb: shadow enable=1
[68389.026418] udlfb: vendor descriptor length:22 data:22 5f 01 0020 05 00 01 03 04 02
[68389.026437] udlfb: DL chip limited to 2080000 pixel modes
[68389.026818] udlfb: allocated 4 65024 byte urbs
[68389.108494] udlfb: 1280x1024 valid mode
[68389.108502] udlfb: 720x400 valid mode
[68389.108509] udlfb: 640x480 valid mode
[68389.108513] udlfb: 640x480 valid mode
[68389.108518] udlfb: 800x600 valid mode
[68389.108523] udlfb: 800x600 valid mode
[68389.108528] udlfb: 832x624 valid mode
[68389.108533] udlfb: 1024x768 valid mode
[68389.108538] udlfb: 1024x768 valid mode
[68389.108543] udlfb: 1024x768 valid mode
[68389.108548] udlfb: 1280x1024 valid mode
[68389.108553] udlfb: 1280x1024 valid mode
[68389.108557] udlfb: 1280x960 valid mode
[68389.108563] udlfb: 1280x1024 valid mode
[68389.108569] udlfb: Reallocating framebuffer. Addresses will change!
[68389.110892] udlfb: 1024x768 valid mode
[68389.110899] udlfb: set_par mode 1024x768
[68389.119757] udlfb: DisplayLink USB device /dev/fb1 attached. 1024x768 resolution. Using 3072K framebuffer memory

---

### Post by Merciless on 2012-05-11
*bump*

I have some time this weekend to work on this, any suggestions or hints would be helpful.

---

