---
title: "hauppauge hvr 900"
date: 2010-01-11
forum: Multimedia Software
---

### Post by user34 on 2010-01-11
Hello,

I can not get my usb dvb-t sick working. It is a hauppauge WinTV-HVR 900 hybrid TV stick.
The number on the backside is: M/R: 65018/BC20

Some time ago I read somewhere that this model was supposed to work with ubuntu 9.10.
But I still have trouble setting it up. Does anyone know if there is a way to make it work?

Thanks

---

### Post by HappyFeet on 2010-01-11
From [here]("http://www.hauppauge.com/site/support/linux.html"):

"Linux support for the WinTV-HVR-900 series will be in the upcoming kernel 2.6.26 release. **Work is under way for the WinTV-HVR-900H**."

---

### Post by user34 on 2010-01-11
> **HappyFeet said:**
> From [here]("http://www.hauppauge.com/site/support/linux.html"):

"Linux support for the WinTV-HVR-900 series will be in the upcoming kernel 2.6.26 release. **Work is under way for the WinTV-HVR-900H**."

Hi,

I already tried the official homepage. I do not know if my stick is a 900 or 900H. That is why I posted the number.
I also entered that number at hauppauge and it redirected me to the section for the regular 900 series, NOT 900H - although it is sensible that the H stands for hybrid.
So I am still not sure which model I have.

---

### Post by HappyFeet on 2010-01-11
> **user34 said:**
> Hi,

I already tried the official homepage. I do not know if my stick is a 900 or 900H. That is why I posted the number.
I also entered that number at hauppauge and it redirected me to the section for the regular 900 series, NOT 900H - although it is sensible that the H stands for hybrid.
So I am still not sure which model I have.

I'm pretty sure the H stands for hybrid.

---

### Post by user34 on 2010-01-12
> **HappyFeet said:**
> I'm pretty sure the H stands for hybrid.

Hi,

I got it working now after installing and deinstalling dozens of packages. But I am not sure if that all was necessary. The device was not properly recongnised by kaffeine and no source was displayed. But when I switched to the options today there was device tab. The device entry there is 'Micronas DRX3973D DVB-T'. There I could select the source and after applying these changes I was able to scan for channels and it has been working fine since then.
So I don't think I have a 900H even if the name of the stick is HVR 900 Hybrid.

---

