---
title: "VLC via LIVE CD"
date: 2010-04-04
forum: Multimedia Software
---

### Post by igorek93 on 2010-04-04
Hello.
I have this situation:
My notebooks hard died so i'm using it some times as a dvd player via ubuntu 9.10 live cd.
The problem is that every time i have to download vlc again after each restart. I'm using my phone as a modem so downloading vlc take about 10-15 minutes and thats only after i'm updating apt-get with Universe and Multiverse that takes another 10-15 minutes.
What i need is a way do copy all the file involved to a flash drive and installing them from the flash drive after live cd started.

The problem is i don't know where does it downloading all the apt-get updates and the vlc player so i can copy them.

I tried to install vlc manually from a package but it seems that it needs some dependencies and i don't understand much about it.

Any help/idea would be appreciated.

---

### Post by howefield on 2010-04-04
You could try using the Startup Disk Creator to make a bootable pen drive/memory stick Live CD. This will have the ability to save your changes, including installed applications like VLC, so next time you boot with it, VLC will still be there.

---

### Post by igorek93 on 2010-04-04
> **howefield said:**
> You could try using the Startup Disk Creator to make a bootable pen drive/memory stick Live CD. This will have the ability to save your changes, including installed applications like VLC, so next time you boot with it, VLC will still be there.

Didn't know that. Thanks.

But this raises another question:
Will i still be able to use the flash drive over other system just to transfer files (on windows)?

---

### Post by howefield on 2010-04-04
> **igorek93 said:**
> Will i still be able to use the flash drive over other system just to transfer files (on windows)?

I use separate flash drives for windows work, but I'd expect all you'd need is to have a Windows recognisable file system on a separate partition to your Ubuntu install.

I have a spare 4 gig memory stick lying around, I'll give it a go and let you know.

---

### Post by igorek93 on 2010-04-04
> **howefield said:**
> I use separate flash drives for windows work, but I'd expect all you'd need is to have a Windows recognisable file system on a separate partition to your Ubuntu install.

I have a spare 4 gig memory stick lying around, I'll give it a go and let you know.

I'll try this tonight to. Thanks for the info!

---

### Post by howefield on 2010-04-04
> **igorek93 said:**
> I'll try this tonight to. Thanks for the info!

Worked fine, didn't even need the separate partition, as Startup Disk Creator formatted the pen drive for a FAT file system, windows can see everything on it.

---

### Post by igorek93 on 2010-04-11
the flash drive created fine and beginning to load ubuntu but when it starting it up it  hang on blank screen with mouse.
Guess its some hardware problem or usb faulty configurations because the usb led indicator stops flashing.
Maybe i'll try on other usb stick.

---

### Post by gordintoronto on 2010-04-11
Have you considered using a Linux Mint LiveCD, which can play DVDs.

---

