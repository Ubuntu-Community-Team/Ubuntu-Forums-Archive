---
title: "how can i detect whether the display driver is installed or not ??"
date: 2008-10-29
forum: Multimedia Software
---

### Post by arunharidas on 2008-10-29
how can i detect whether the display driver is installed or not ?? 

i didnt get any response when i clicked detect my display button in system > preference > screen resolution 

os id ubuntu 8.04

my motherboard is 

Asrock K8M800

AMD sempron 64 bit

---

### Post by xc3RnbFO8P on 2008-10-29
What is the output of **lspci | grep VGA** in Terminal?

---

### Post by arunharidas on 2008-10-29
i'm getting this 

01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

---

### Post by xc3RnbFO8P on 2008-10-29
Try:
> dpkg --list | grep -i s3

---

### Post by arunharidas on 2008-10-29
getting this:

> ii  libdns32                                   1:9.4.2-10                         DNS Shared Library used by BIND
ii  liblwres30                                 1:9.4.2-10                         Lightweight Resolver Library used by BIND
ii  libnss3-1d                                 3.12.0.2+1.9-0ubuntu0.8.04.1       Network Security Service libraries
ii  libsensors3                                1:2.10.5-3ubuntu1                  library to read temperature/voltage/fan sens
ii  libxfixes3                                 1:4.0.3-2                          X11 miscellaneous 'fixes' extension library
ii  xserver-xorg-video-s3                      1:0.5.0-4                          X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.9.1-7                          X.Org X server -- S3 ViRGE display driver

---

### Post by xc3RnbFO8P on 2008-10-29
It is installed:
ii xserver-xorg-video-s3 1:0.5.0-4 X.Org X server -- legacy S3 display driver
ii xserver-xorg-video-s3virge 1:1.9.1-7 X.Org X server -- S3 ViRGE display driver 

Try **gksu displayconfig-gtk**
see if your monitor is supported,
if not choose Generic
and resolution that your monitor supports.

---

### Post by arunharidas on 2008-10-29
> if not choose Generic
and resolution that your monitor supports.

explain please ... 

here 

> Location : NULL

Default screen : checked 

Graphics card > driver : NONE

video memory : automatic

Graphics card > driver > choose driver by name : openchrome 


what to do further?

---

### Post by xc3RnbFO8P on 2008-10-29
Choose your screen within the black circle.

---

### Post by suncoolsu on 2008-10-29
I have a common problem. When I select the proper screen (in My case Dell) and the resolution 1280x800, it asks for a driver. 

Can anyone tell me how to install and get drivers for dell with a max resolution of 1280 x 800 ( WXGA )

---

### Post by arunharidas on 2008-10-30
Yes i have done it ... is it enough ???

---

### Post by xc3RnbFO8P on 2008-10-30
> Yes i have done it ... is it enough ???
Can you play video, is your screen resolution OK?

---

### Post by xc3RnbFO8P on 2008-10-30
> Can anyone tell me how to install and get drivers for dell with a max resolution of 1280 x 800 ( WXGA )
Did you try **Generic 1280 x 800**?

---

### Post by arunharidas on 2008-10-30
no i cannot play video ... movie is not visible

---

### Post by xc3RnbFO8P on 2008-10-30
Read this:
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

---

### Post by xc3RnbFO8P on 2008-10-30
Delete, double post.

---

