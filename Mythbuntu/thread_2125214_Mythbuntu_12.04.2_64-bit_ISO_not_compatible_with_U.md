---
title: "Mythbuntu 12.04.2 64-bit ISO not compatible with USB Flash drives??"
date: 2013-03-13
forum: Mythbuntu
---

### Post by neutron68 on 2013-03-13
I tried 2 different ISO to USB programs and both produced a FAILED bootable USB Flash Drive.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Neither program produced a USB Flash drive that successfully booted into the Mythbuntu installer. 
I tried a 4GB Flash drive with unetbootin and a 1GB Flash drive with the Universal USB Installer.

I checked the MD5SUMS code to be sure the ISO was not corrupt.  The code matched.
1065b482382203d367cf7ce1c69b7c51 (for mythbuntu-12.04.2-desktop-amd64.iso)

The flash drive made with unetbootin booted to a menu of boot choices and none of them would boot the machine.  Some just sat with a blinking cursor and others just gave an error and restarted the menu.
The flash drive made with Universal USB Installer, started booting to a maroon Mythbuntu splash screen and then stopped with an error message.

Is anyone else seeing this problem?
I can take screen photos, if it will help troubleshoot.

Eric

---

### Post by neutron68 on 2013-03-13
I just got the Universal USB Installer (Pendrivelinux) to create a working bootable USB Flash drive!
I remade the USB flash drive and it worked this time.  I'm not sure why it didn't work the first time.
I wonder if I "fat-fingered" the distro choice box when I made the first one?

Bottom line: Universal USB Installer (Pendrivelinux) does work!

I'm not sure what the deal with unetbootin is.   
I made sure I had the latest version, tried it again and it failed to make a bootable Mythbuntu installer, again.
It doesn't matter what menu choice you pick.  It fails.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20130313_194234_zps8efe6b82.jpg[/IMG]

Unetbootin doesn't have a distro choice for Mythbuntu so you have to choose a generic Ubuntu.  
The settings for the generic Ubuntu choice must not be close enough to work?

Eric

---

