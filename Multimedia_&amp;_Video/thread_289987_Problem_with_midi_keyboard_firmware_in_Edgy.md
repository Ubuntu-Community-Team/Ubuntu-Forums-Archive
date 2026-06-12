---
title: "Problem with midi keyboard firmware in Edgy"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by pumaman_scotland on 2006-10-31
Hi,

I have just upgraded to Edgy, and my usb midi keyboard's firmware is no longer loaded automatically when I plug the keyboard in.

I can load the firmware manually, but obviously this is not ideal.

This is by usb list:
```
pumaman@HAL:~$ lsusb 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0763:1014 Midiman 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

and this is what is in /etc/udev/rules.d :
```
pumaman@HAL:~$ cat /etc/udev/rules.d/42-midisport-firmware.rules 
# midisport-firmware.rules - udev rules for loading firmware into MidiSport devices

# DEVPATH=="/*.0" selects interface 0 only
# (some udev versions don't work with SYSFS{bInterfaceNumber})

# MidiSport 2x2
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1001/*", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport2x2.ihx"
# MidiSport 1x1
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1010/*", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport1x1.ihx"
# KeyStation
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1014/*", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSportKS.ihx"
# MidiSport 4x4
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1020/*", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport4x4.ihx"
# MidiSport 8x8
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1031/110", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport8x8-2.10.ihx"
ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1031/121", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport8x8-2.21.ihx"
```

From the midisport-firmware-1.2 package. 

Any ideas? Nothing appears in /var/log/udev

Thanks
David

---

### Post by LevTermen on 2006-11-10
Re-,

I own a M-Audio Radium 61 MIDI keyboard. Like you might have done, I installed the firmware loader version midisport-firmware-1.2.tar.gz from this website:
[http://usb-midi-fw.sourceforge.net/]("http://usb-midi-fw.sourceforge.net/")

The device doesn't show up automatically when hotplugging for me either on Edgy, but by loading it by hand, after having apt-got fxload. I'm gonna explain what I and certainly you did to do so, for others.

Say the device can be discovered on the same address pointed by your lsusb result. The command to use for a Radium would be then:
```
fxload -I /usr/local/share/usb/maudio/MidiSportKS.ihx -D /proc/bus/usb/002/005
```
(with some little inspiration from [this tutorial]("http://ubuntuforums.org/showthread.php?t=96506"))

The bug #[27833]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/27833") has already been filed to address this issue. I'm gonna give them a note we 've met the same issue.

Cheers,
Lev Termen

---

### Post by forest_atq on 2006-11-10
Hi

As it turned out, midisport-firmware didn't quite make it in time for edgy.  You can download the package here, though:

[http://apt.alittletooquiet.net/fab/pool/main/m/midisport-firmware/midisport-firmware_1.2-0ubuntu2_all.deb](http://apt.alittletooquiet.net/fab/pool/main/m/midisport-firmware/midisport-firmware_1.2-0ubuntu2_all.deb)

Note that /usr/share/doc/midisport-firmware/README.Debian indicates that you should modify your /etc/fstab to make this device work.  From what I can tell, this actually isn't necessary.  However, I did notice that I have to restart udev in order for the device to be detected:

$ sudo /etc/init.d/udev restart

It would seem that there is some timing issue that prevents the device from being initialized properly at boot time.  I am looking into this.

Hope this helps, and I will make a note to go along with the bug as well.

-Forest

---

### Post by forest_atq on 2006-11-10
Correction: the instructions in /usr/share/doc/midisport-firmware/README.Debian are, in fact, correct.  Restarting udev shouldn't be necessary.

-Forest

---

### Post by LevTermen on 2006-11-11
Hi,

Thank you for your time. Actually this package doesn't seem to help more than  compiling and installing the source code.

I added the following in /etc/fstab as adviced on /usr/share/doc/midisport-firmware/README.Debian:
```
usbfs        /dev/bus/usb   usbfs   defaults        0   0
```

I did, in disorder to meet all possibilities, reboot my system, restart udev, replug the device... nothing helps!

I can paste here the output of any command (lsusb; dmesg; cat /proc/asound/cards) by request.

Notice that I've followed the following tutorial:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
therefore my /etc/modprobe.d/alsa-base contains the following line:
```
options snd-usb-audio index=-2
```

I suspect we should rather look at the multiple soundcards issue, shouldn't we? The facts are here:
[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard)

Cheers,
LevTermen

---

### Post by KingCharles on 2007-03-17
I am too having a problem with my M-Audio Radium69. It was working fine in Dapper, now with a fresh install won't work in Edgy.

I have [these]("http://usb-midi-fw.sourceforge.net/") drivers installed. No go automatically either.

I tried changing the udev rule file to no avail. But I did notice that by just restarting the udev deamon while having the midi keyboard just plugged in, it would work. I am not sure how the new udev works, but hopefully someone can find a way to fix it.

Having to restart the hardware detection server everytime you plug/unplug a device, is pretty much like restarting Windows XP everytime you change the computer name!!!?? :confused:

---

