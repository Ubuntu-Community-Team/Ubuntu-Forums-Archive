---
title: "Audio volume question"
date: 2009-06-17
forum: Multimedia Software
---

### Post by xilefone on 2009-06-17
Hello,
 
I have a Toshiba Satellite L305D laptop that's set up to dual boot to Ubuntu and Windows. While in Windows, the maximum sound volume is much louder than the maximum volume under Ubuntu. Is there a way to increase the maximum audio volume under Ubuntu? 
 
Thanks,
 
Xilefone.

---

### Post by raboofje on 2009-06-17
> **xilefone said:**
> I have a Toshiba Satellite L305D laptop that's set up to dual boot to Ubuntu and Windows. While in Windows, the maximum sound volume is much louder than the maximum volume under Ubuntu. Is there a way to increase the maximum audio volume under Ubuntu? 

I noticed this on my girlfriend's acer aspire 5735Z, too. Didn't see anything obvious, would be interesting to know what's going on.

---

### Post by raboofje on 2009-06-22
What soundcard does that laptop contain (lspci might give hints)?

Mine carried an Intel HDA card, and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) has some good info on it. More specifically, I fixed my volume issue by configuring 'model=acer' in my /etc/modprobe.d/alsa-conf . For a mapping between laptop models and suitable settings, see also [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) .

---

### Post by LKjell on 2009-06-22
Hi check all slider are maxed out. When you do a clean install the volume of each slider are set to 75% to protect the speakers.

---

