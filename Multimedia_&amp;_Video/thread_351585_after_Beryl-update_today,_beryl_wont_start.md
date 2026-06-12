---
title: "after Beryl-update today, beryl wont start"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by NoMo on 2007-02-02
hi,

beryl was running very smooth on my machine till this morning when i got beryl updated :

now it tells me :

> Checking for non power of two texture support   : failed

>  Support for non power of two textures missing

i am running edgy eft wit an ATI850xt with the the build-essential xorg-driver-fglrx  installed 


i found this:

> 
compiz outputs this:

compiz: Support for non power of two textures missing

The driver has to support either the GL_{NV,EXT,ARB}_texture_rectangle or the GL_ARB_texture_non_power_of_two extension. The open source ATi driver, x11-drivers/xf86-video-ati, does not support these extensions. If you are using an ATi card, try using the proprietary fglrx drivers, x11-drivers/ati-drivers. This info may only relate to r300 and newer cards. 

does that mean that since they updated beryl i cant use the build-essential xorg-driver-fglrx for my card anymore ???

HELP plz

iam a bloody noob to all this, first week in linux..   :confused:  :confused:  :confused:

if the issue above is  the case that i have to install a other driver, please tell my the steps to do so.....

---

### Post by jd65pl on 2007-02-02
If you are a 'noob' then you probably shouldn't be trying to run temperamental beta software. If you insist on using it then try re-installing beryl see [this link]("https://help.ubuntu.com/community/BerylOnEdgy") for a how to

---

### Post by NoMo on 2007-02-02
i did

> sudo apt-get remove beryl

then 

>  sudo apt-get autoremove

then restarted the x-server 

then 

>  sudo apt-get install beryl beryl-manager

restarted  but no matter 
still got the error ??

any idea

---

