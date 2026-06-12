---
title: "Multiple Problems!!! Please help!!! :)"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Soglad on 2007-12-01
Right, a few problems.

I can't seem to be able to hear myself play guitar through the computer AS I record. This is kind of important as other wise I'd have to play without hearing what I sound like, and that's a no-no! I can't see ANY options in my gnome-volume manager, I've tried everything on it. I have a HDA Intel chipset.

So, I thought that would be sorted if I downloaded and installed Ubuntu Studio. So I got that and installed it on a partition. When I try and load of from the GRUB loader, it's described as Ubuntu 7.10 and only loads a black screen with writing (like in terminal) and asks for Login and password, then just leaves me on the blank screen!

What's going on there? I've tried re-installing it multiple times, and I get the same every time!

Even if I get all this sorted, is there any better recording programs than Audacity!!!!!??? :(

I really want to get Windows XP back, I've had so much **** with Ubuntu on this laptop (and everything else I've put it on). But there's this weird problem....I have about 4 different Windows XP discs, and NON of them start on the boot up screen! They just over-ride it and continue loading Ubuntu. These discs work on every other pc in this house, and Ubuntu booted up on this pc, but all the Windows discs just won't load up on start up! It's BIZARRE! And yes, the boot sequence is on the DVD drive and all that!

Any help is much appreciated!!!

Thanks!

Dav.

---

### Post by Soglad on 2007-12-02
bump

---

### Post by vemon on 2007-12-03
I don't know if this is the right forum for your windows question but are you sure you've enabled CD booting from BIOS? If I recall correctly Windows bootloader asks if you want to boot from CD even if the aforementioned BIOS option is not enabled.

And to your Ubuntu Studio question:
To my knowledge Ubuntu Studio is just normal Ubuntu loaded with wider range of audio+video programs. All the programs are also available through normal Ubuntu repositories. It also has realtime kernel for low latency sound output/input. You'll probably have the same problems in US that you have in vanilla Ubuntu.

Hope you'll find peace with your installation and can conscentrate in the obvious (making music etc.) :)

---

### Post by misfitpierce on 2007-12-03
You can try force booting to other device by hiting F10-F12 upon boot. Also if you get black screen at every boot your bootsplash is messed up. Can try hittin escape upon boot and editing main partition from splash to nosplash at end. Then if that works you can edit main grub file (google) to load without splash so it does every time.

---

### Post by lian1238 on 2007-12-03
in Audacity, you can turn on Software Playthrough under Audio I/O (in Preferences). You could try. I get a bit of *static* though.

---

