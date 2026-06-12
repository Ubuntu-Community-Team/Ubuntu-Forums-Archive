---
title: "How to merge boot repair in an ubuntu dvd?"
date: 2019-05-04
forum: Multimedia Software
---

### Post by gipsyshadow on 2019-05-04
I hope this is the best area to post my request in.
My goal is to create a DVD with ubuntu 18.04.2lts and boot repair ready-to-use, I mean I won't have to download it via internet connection within the live session; is it possible?
I've got ubuntu iso and it's very easy to burn it in a dvd but how to merge boot repair? It's not necessary for me to have it within desktop applications list (like gparted, eg), I just need it'll be present within the dvd without internet connection.

I know hot to get [boot repair](https://help.ubuntu.com/community/Boot-Repair) via an internet connection:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```
but here my knowledge stops. Can you help me?

---

### Post by Rubi1200 on 2019-05-04
There are a few guides out there on how to do this:
[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)
[https://linuxconfig.org/how-to-create-a-persistent-ubuntu-usb-stick-using-mkusb-tool](https://linuxconfig.org/how-to-create-a-persistent-ubuntu-usb-stick-using-mkusb-tool)

Search for other links if these ones do not suit your needs.

---

### Post by oldfred on 2019-05-04
You still use DVD to install?
I have not used DVDs for installing for years. And my one system with a DVD is only used to backup most critical data to a DVD.
I historically burned many coasters, actually used some as coasters as otherwise worthless.
So I use flash drive or now mostly install from one hard drive to another on same system.

If you use flash drive and persistence, then you can save some data that you download.
Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Never tried this, I normally do a full install to larger flash drive and just have a data partition on flash drive:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Tweaks to improve USB flash drive performance for Installer with persistence, but similar for full install.
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

---

### Post by yancek on 2019-05-04
In the past, this was a fairly simple process with an installed system with added software.  You could use software such as remastersys, systemback and pinguy builder to create an iso from the installed system.  I haven't used any of them for several years so don't know if they will work with the current 18.04.  Using a usb with perisitence or a full install will be easier.

---

### Post by gipsyshadow on 2019-05-05
I think I misled you and it was my fault. I said DVD but I'm interested in the one-iso file ubuntu+bootrepair. Of course I use flashdrive to install linux and other ooss but I'd like to have an optical support too for emergencies, I mean for the most critical scenario I could image: far from of my home, no flashdrive (or not enough for my purposes), no internet connection, a pc/laptop with booting issues to fix. So my goal is an iso indeed.

I'm very newbie and I started reading the contents of your links. As far as I could understand from [this](https://www.pendrivelinux.com/what-is-persistent-linux/) I'm not interested in a persistent installation because I don't want to use a dedicated flasdrive only for this job, it'd be a waste for my goal. I think sw as systemback and pinguy builder could help me but I've to ask you a question about them. As far as I saw those ssww create an iso image of the system, right? Are they able to create an iso image of a system relying to RAM -and not to the disk- as a live ubuntu session is? If yes I'll run an ubuntu live, I'll download and install boot repair via those posted commands, I'll download and install systemback or pinguy and finally get the iso image of all that which is my goal.

---

