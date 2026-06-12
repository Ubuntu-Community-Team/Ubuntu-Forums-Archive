---
title: "FF Flash issue - sound but no video?"
date: 2010-07-16
forum: Multimedia Software
---

### Post by J-C90 on 2010-07-16
I've searched all the other posts about flash issues but haven't been able to find anything related to my problem.

I'm using Ubuntu 10.04 on a Compaq 6710b laptop. I have latest flash plugin installed and have tried un-installing and re-installing, tried flash-nonfree, I have tried FLASH-AID but nothing has worked.

My problem is that on 'some' flash sites I cant view the video, I just get a grey box where the flash video should be. Youtube for example. the video appears to be playing as I can hear the sound but no actual video? Some sites with flash work ok but most do not.

Any ideas? Could it be video drivers? I am currently using the kernel drivers but I haven't noticed any other problems, compiz fusion effects are working fine. I believe this laptop uses intel graphics media accelerator x3100.

---

### Post by andrea000 on 2010-07-16
I don't think it has to do with the video drivers.I have found that installing flash from adobe's website works better you may want to try it just download the .deb for ubuntu 8.04 then double click it to install it

---

### Post by lovinglinux on 2010-07-17
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by J-C90 on 2010-07-18
**Shockwave Flash**

 File:  /usr/lib/adobe-flashplugin/libflashplayer.so
Version:    Shockwave Flash 10.1 r53

MIME Type                                 Description               Suffixes     Enabled
application/x-shockwave-flash     Shockwave Flash       swf           Yes
application/futuresplash              FutureSplash Player   spl            Yes

---

