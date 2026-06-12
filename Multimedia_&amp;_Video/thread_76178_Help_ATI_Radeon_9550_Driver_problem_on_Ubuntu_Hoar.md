---
title: "Help: ATI Radeon 9550 Driver problem on Ubuntu Hoary."
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by mincho on 2005-10-14
hello buddies,
 i have ATI Radeon 9550 256mb DVI/TV Output and ubuntu hoary installed but i still cant install his driver can anyone help me that how can i installed the ati radeon 9550 agp driver on ubuntu hoaryhedgehog linux,
  i have all versions of driver from ati just post here the correct installation method or otherwise i am sick of ati radeon AGPs. i will goto buy a nVidia Geforce 5700 256mb.
             thanks please help me

---

### Post by mlomker on 2005-10-14
Breezy is easier because it comes with much newer drivers.  [My Hoary how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") has worked for many people.

---

### Post by SilverTab on 2005-10-14
Follow mlomker's how to and you should get your driver set up in no time...

I have the same card as you and on hoary it was working top notch...

now in breezy...the kernel doesnt recognize the card.. :(

---

### Post by xsence on 2005-10-24
[QUOTE=mincho]hello buddies,
 i have ATI Radeon 9550 256mb DVI/TV Output and ubuntu hoary installed but i still cant install his driver can anyone help me that how can i installed the ati radeon 9550 agp driver on ubuntu hoaryhedgehog linux,
  i have all versions of driver from ati just post here the correct installation method or otherwise i am sick of ati radeon AGPs. i will goto buy a nVidia Geforce 5700 256mb.
             thanks please help me[/QUOTE]

If i where you i would choose another graphicscard instead of the 5700.. because i have the leadtek a360 which has a fx 5700 and i just can't get it installed.

---

### Post by Pablo_Escobar on 2005-10-24
Hmmmmmmmm, 3 days ago on a fresh Breezy install I just dowloaded fgl-xorg-driver and fglrx-control with required dependencies, changed xorg.conf, and it works flawlessly on my Radeon 9550 (AGP 128MB - Gigabyte). When the Breezy was fresh it didn't work, but now it seems to have an added dependency which resolves the problem. 
It works great on my box (32bit OS).

---

