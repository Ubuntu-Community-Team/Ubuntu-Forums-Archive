---
title: "Intel 855GM/852GM Graphics S-Video Out Setup"
date: 2008-05-12
forum: Multimedia Software
---

### Post by DSP8000 on 2008-05-12
Hi guys, 

I'm using Ubuntu Hardy and I'm having hard time configuring dual screen or extended desktop with my laptop. It is my work laptop, mainly used for basic purposes and it has Intel 855GM/852GME Graphic chipset. I've used Ubuntu in the past starting from v6. I'm dual booting with XP Pro and on XP I can easily set up extended desktop so I can watch some movies on my TV. This is done thru s-video. Can someone walk me thru doing this on Ubuntu.I did some reading on this forums but seems like there's no clear answer or easy setup for this. I really like Ubuntu and want to get this sorted out. It is one of the few things that keeps me dual booting.

Any help is greatly appreciated.
Cheers

DSP8000

---

### Post by DSP8000 on 2008-05-26
Hi,

any news on this issue. I'd really like to use vlc under ubuntu for watching movies thru s-video out on my TV.

Anyone ?

DSP8000

---

### Post by mailsub2000 on 2010-11-24
Hi,
 not the solution but some help from me.
From internet search I made conclusion that i810 drivers should work for intel 852. 
and so started in that dorection.
First of all I tried verious verions of ubuntu but no luck.
Then I found one blog about fedora core4 and s-video out.
I installed FC4 and used suggestion from [http://oasis.dit.upm.es/~jantonio/personal/aspire1410/](http://oasis.dit.upm.es/~jantonio/personal/aspire1410/)

Section "Device"
        Identifier "Videocard0"
        Driver "i810"
        VendorName "Videocard vendor"
        BoardName "Intel 852"
        Option "MonitorLayout" "LFP,TV"
        VideoRam 32768
EndSection

and could see tv out.
and it was clear that s-video works with i810 drivers.
but as fc4 was too old I switched to puppy 4.3.1[since lightweight]
Initially it did not work and after lot of trial and errors 
found that puppy internally has symbolic link i810 -> actual 
intel driver.
but in same directory I found renamed i810 files for i810_driver.so
and I switched to this file and voila! could see tv out from
s-video.
I spend so much time in this, that I am not interested in trying out
on ubuntu now.
But I guess if you can use correct file of i810 driver you might be able to see
tv-out in ubuntu as well.
best of luck!

---

