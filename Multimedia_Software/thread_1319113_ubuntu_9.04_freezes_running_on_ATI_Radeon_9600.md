---
title: "ubuntu 9.04 freezes running on ATI Radeon 9600"
date: 2009-11-08
forum: Multimedia Software
---

### Post by exxxo45 on 2009-11-08
Hello everyone,
I've been searching all over the internet, but I couldn't get an answer to my problem. I have an older computer ( AMD Athlon 1900+; 1GB memory; ATI Radeon 9600) and I did a fresh installation of the Ubuntu 9.04. The problem is that the computer freezes upon increased graphic use, for example while playing Nexuiz or playing around with Compiz effects.
    I tried installing the **open source driver** as suggested on the website [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) , but it didn't have any effect. Then when I looked into the xorg.conf file, all the changes I saved there were gone - seems the file was automaticky regenerated.
    Does anybody know how to fix this issue please? Help would be greatly appreatiated!

Michal

---

### Post by kuric on 2010-12-01
I have an ATI Mobility Radeon 9000 IGP working perfectly on Ubuntu 8.10 with ATI proprietary drivers.
When I've upgraded to Ubuntu 9, then my graphic card was no longer supported, so I had to use Radeon generic driver, instead of ATI. System usually crashed very often and this problem persisted in Ubuntu 10.

I've tried a billion solutions, here are some of the most successful:

1) Enable **Option "AGPMode" "4"** in xorg.conf.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

"3D may hard-freeze X-server unless AGP mode is set correctly in Xorg.conf. If you have this problem, try adding Option "AGPMode" "4" to the device section of Xorg.conf"

For those who don't have a xorg.conf file, follow these steps:
Ctrl+Alt+F1
$ sudo service gdm stop
$ sudo Xorg -configure
$ sudo service gdm start
Rename xorg.conf.new (in your home folder) to xorg.conf and copy it into /etc/X11 folder

2) Turn off **Compiz**. Go to Synaptic and remove all packages related to compiz.

3) Enable **nohz=off** option.
$ sudo gedit /boot/grub/grub.cfg and add nohz=off option on the first menuentry, should look something like this:
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec5f3463-a301-4f6f-aa23-3cbb44dc140d ro quiet splash nohz=off

4) Disable **3D acceleration** (poor solution). Install driconf from Synaptic. Select Preferences > Administration Tools > 3D Acceleration. Go to Debugging tab and disable 3D acceleration.

5) Uninstall applications with unstable activity like **Firefox** (due to flash player, try Google Chrome instead), **Firestarter** or **Ubuntu One**.

6) Remove **pulseaudio** and install alsa.
[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)
[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

7) Disable **Hyper Threading Technology** in Bios options. This is very effective.

---

