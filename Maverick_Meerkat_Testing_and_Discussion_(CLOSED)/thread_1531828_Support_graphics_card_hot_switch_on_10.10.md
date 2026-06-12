---
title: "Support graphics card hot switch on 10.10"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by benjamimgois on 2010-07-15
I know that vgaswitchero is already implemented on the 2.6.35 Kernel, but there are still lots of problems with this implementation. It seens that users with Intel Core I3, I5 and I7 can't switch to the offboard (RADEON or NVIDIA) graphics properly if the BIOS doesn't provide this feature. The bug in Launchpad already affects 83 people. 

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all)

The question is, will the graphics card hot switch be supported properly on Maverick ?

---

### Post by Reiger on 2010-07-15
No it won't. For starters it is not much *use* right now because it only works when you switch between X-sessions. Obviously, when you practically need a reboot (time to log-in is much less than time from log-in to desktop) to do this kind of stuff and with the fact that there's no *easy* way to do it anyway, this means that support is essentially limited to a tech-preview.

Technically the kernel can do it, realistically there's way too many issues to expect this to work smoothly with the Meerkat.

---

### Post by benjamimgois on 2010-07-15
Thanks for the reply. Some guys could make it work on a ASUSM51Ta, switching between the integrated RADEON graphics to the Dedicated Radeon graphics and even created a script with a graphical user interface for it using fedora 13 + custom kernel 2.6.34, but unfortunatly it doesn't work for every solution.

[http://asusm51ta-with-linux.blogspot.com/2010/05/07052010-fedora-13-beta-kernel-2.html](http://asusm51ta-with-linux.blogspot.com/2010/05/07052010-fedora-13-beta-kernel-2.html)

It's said to see that linux walks with so small and slow steps. If you have such kind of hardware you'll have to wait 1 year or more to make it work properly.

---

### Post by benjamimgois on 2010-07-27
Hey guys, after update to the latest kernel 2.6.35-12 the VGA switch actually works for me ! I'm writing this text throught the HDMI port of my ATI Mobility 4550. I recomend to make the test ! I still hasn't tried the FGLRX but opensource driver is working just fine.

I'll try to make a GUI for Ubuntu Control Center.

---

### Post by cecilpierce on 2010-07-27
> **benjamimgois said:**
> Hey guys, after update to the latest kernel 2.6.35-12 the VGA switch actually works for me ! I'm writing this text throught the HDMI port of my ATI Mobility 4550. I recomend to make the test ! I still hasn't tried the FGLRX but opensource driver is working just fine.

I'll try to make a GUI for Ubuntu Control Center.

How did you get 2.6.35-12 ? I just did update and still have 2.6.35-11.

---

### Post by benjamimgois on 2010-07-27
> **cecilpierce said:**
> How did you get 2.6.35-12 ? I just did update and still have 2.6.35-11.

Go to software-channel , updates and enable the option (Lucid-proposed) then you'll be able to download -12.

---

### Post by cecilpierce on 2010-07-27
All I have is Maverick in my "Software Sources" and Maverick Proposed is checked so I guess I'll have to wait, thanks 
Cecil

---

### Post by benjamimgois on 2010-07-27
yep, maybe it will be avaiable soon, here it's already working, look at my uname -a

---

### Post by cecilpierce on 2010-07-27
Strange my 11 came out a day after your 12, hmmmm!
Your using 64 bit though, mine is 32 bit.

---

### Post by benjamimgois on 2010-08-02
Hey guys, it's just to announce that on Ubuntu Control Center 0.5 Beta i have created a GUI for vga-switchero. Now it's possible to switch between GPU's with just a single click ! It works fine for me in Lucid with kernel 2.6.35-12 and Intel Core I5 + ATI Radeon Mobility 4550. If someone else could test it on other hardwares it would be great !

---

### Post by Starks on 2010-08-02
Will this work with Nvidia Optimus? Will I be able to use the binary driver?

---

### Post by xir_ on 2010-08-02
> **Starks said:**
> Will this work with Nvidia Optimus? Will I be able to use the binary driver?

my understanding was that Nvidia has no intention of supporting optimus in linux, I'm not sure if this patch will get round it, im not sure if the proprietary drivers will ever be supported properly. worth a try though.



I remember reading that the X server restart will not be necessary as on 1.9 anyone know any more about this?

---

### Post by benjamimgois on 2010-08-02
> **xir_ said:**
> my understanding was that Nvidia has no intention of supporting optimus in linux, I'm not sure if this patch will get round it, im not sure if the proprietary drivers will ever be supported properly. worth a try though.



I remember reading that the X server restart will not be necessary as on 1.9 anyone know any more about this?

xir_ i haven't heard about that on Xserver 1.9, but i would be a great feature ! No doubt, Let's hope that it happen !

---

### Post by benjamimgois on 2010-08-02
I just recorded a video showing the VGA switching process:

[http://www.youtube.com/watch?v=-S5-BVFk0G0](http://www.youtube.com/watch?v=-S5-BVFk0G0)

---

### Post by jpeddicord on 2010-08-02
The bug report cites power saving as a main reason for this. Using the NVIDIA driver my card enters a low power state when not in use -- what's different about this? Do some cards have different physical chips that need to be manually switched?

Could this let me, for example, switch between my on-board GMA and the PCIe GPU?

---

### Post by 4leite on 2010-08-03
> **jpeddicord said:**
> The bug report cites power saving as a main reason for this. Using the NVIDIA driver my card enters a low power state when not in use -- what's different about this? Do some cards have different physical chips that need to be manually switched?

Could this let me, for example, switch between my on-board GMA and the PCIe GPU?

Ideally, yes you will be able to switch to on-board GMA as opposed to PCIe, if your motherboard supports it. Also, for some (particularly later nvidia hardware) unless switcharoo (or similar) is enabled, only the onboard card works.

---

### Post by xir_ on 2010-08-03
> **benjamimgois said:**
> I just recorded a video showing the VGA switching process:

[http://www.youtube.com/watch?v=-S5-BVFk0G0](http://www.youtube.com/watch?v=-S5-BVFk0G0)

i have a similar hardware setup, but i cant get my card to switch properly, the ATI doesn't seem to power off.

do you seem the lines
```
[  950.909437] vga_switcheroo: client 1 refused switch
[  950.909443] vga_switcheroo: setting delayed switch to client 0

```

in your dmesg output?

---

### Post by benjamimgois on 2010-08-03
> **xir_ said:**
> i have a similar hardware setup, but i cant get my card to switch properly, the ATI doesn't seem to power off.

do you seem the lines
```
[  950.909437] vga_switcheroo: client 1 refused switch
[  950.909443] vga_switcheroo: setting delayed switch to client 0

```

in your dmesg output?

xir_,

Yes i see these lines, here is the output of my dmesg | grep switcheroo


[PHP]benjamim@benjamim-laptop:~$ dmesg | grep switche
[    8.163618] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    8.166132] vga_switcheroo: enabled
[ 8920.391323] vga_switcheroo: client 0 refused switch
[ 8920.391330] vga_switcheroo: setting delayed switch to client 1
[ 8931.367905] vga_switcheroo: processing delayed switch to 1
[ 8931.697342] i915: switched off[/PHP]


To confirme that Intel is OFF and ATI is in use:

[PHP]root@benjamim-laptop:/home/benjamim# cat /sys/kernel/debug/vgaswitcheroo/switch 

0: :Off:0000:00:02.0
1:+:Pwr:0000:01:00.0[/PHP]

---

### Post by firou on 2010-09-13
> **benjamimgois said:**
> Hey guys, it's just to announce that on Ubuntu Control Center 0.5 Beta i have created a GUI for vga-switchero. Now it's possible to switch between GPU's with just a single click ! It works fine for me in Lucid with kernel 2.6.35-12 and Intel Core I5 + ATI Radeon Mobility 4550. If someone else could test it on other hardwares it would be great !



):PThank you very much,I am hunting for this ,haha:D!!!  I am a Chinese student. 3Q!!!

---

### Post by Miguel on 2010-09-20
Please excuse my words, it's not really doubt and skepticism, but actually awe.

Does this really work? I mean, will I be able to set the BIOS in my Thinkpad T400 to "Switchable Graphics" once and for all? And I'll be able to switch between intel and ati? Really? Gosh, I thought this day was never going to come. I still haven't upgraded to Maverick, but the switcheroo is a good enough reason.

:popcorn:

---

### Post by moviglez on 2010-10-05
> **benjamimgois said:**
> I just recorded a video showing the VGA switching process:

[http://www.youtube.com/watch?v=-S5-BVFk0G0](http://www.youtube.com/watch?v=-S5-BVFk0G0)

=D>=D>=D>

Amazing work. Thanks :]

---

### Post by benjamimgois on 2010-10-05
> **Miguel said:**
> Please excuse my words, it's not really doubt and skepticism, but actually awe.

Does this really work? I mean, will I be able to set the BIOS in my Thinkpad T400 to "Switchable Graphics" once and for all? And I'll be able to switch between intel and ati? Really? Gosh, I thought this day was never going to come. I still haven't upgraded to Maverick, but the switcheroo is a good enough reason.

:popcorn:

Miguel, it really works ! But only with the opensource drivers. The FGLRX will not work with this solution. If you are running Lucid you will need to upgrade your kernel to 2.6.35 or higher, if you are running maverick it will works without much problem.

---

### Post by benjamimgois on 2010-10-05
> **moviglez said:**
> =D>=D>=D>

Amazing work. Thanks :]

Thanks dude ! For some strange reason, the messages on Maverick RC are inverted. When you're running the low performance graphics it's showing the High performance graphics is in use. I'll wait for the final release to see if it'll need a small fix.

---

### Post by moviglez on 2010-10-06
Yes, i see this little problem "When you're running the low performance graphics it's showing the High performance" but VGA Switching Module works prefectly for my Acer Aspire Timeline 5820TG with ubuntu 10.10. :]

Great work

---

