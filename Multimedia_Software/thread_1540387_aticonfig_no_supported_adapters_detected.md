---
title: "aticonfig: no supported adapters detected"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Asdra on 2010-07-27
Hey all,

I have a box running Ubuntu 10.04 with an ATI Radeon 7200 video card.  I just installed a driver for it (ati-driver-installer-10-7-x86.x86_64.run) in hopes that I could get the game Stepmania to run.

I also have a guide to installing the driver which says to run /usr/bin/aticonfig --initial after it finishes installing so I can configure the driver, but I only get:

/usr/bin/aticonfig: No supported adapters detected

Tried a couple of things to fix it myself, to no avail.  Anything I can do to get this working?

Thanks!

-Asdra

---

### Post by Yellow Pasque on 2010-07-28
The proprietary ATI driver no longer supports your card, so remove it and use the default open-source driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by Asdra on 2010-08-04
Question:  does Ubuntu come with one of those open-source drivers already installed when you load it onto a computer?  The reason I got into this whole mess was because the video output from Stepmania was really choppy, and the faster the song was, the choppier it became.  That's when I tried getting a special driver for the video card - I've basically built this box out of spare parts lying around that're pretty old - and the card was an NVidia, which led to no end of trouble.  Finally found an ATI card, swapped it out.  Hence where I am now.

Also, I'm still pretty new to Linux; if anything I need to do will involve the terminal (undoubtedly will, I'm guessing), please explain what I need to do carefully, so I don't hurt this box any more than I already have by trying things on my own.  Thanks!

---

### Post by Asdra on 2010-08-13
Never mind my last question there; on further examination, it appears part of my initial problem was a dead CMOS battery, keeping the machine from properly remembering (at all) any video drivers that I would have wanted to use.  As soon as that's fixed, I'll get one of the open source drivers working.  Thanks!

---

### Post by Tekno.Statik on 2010-11-25
Well, I started a new thread specifying my graphics card as well as the message I got from Terminal:
```
aticonfig: no supported adapters detected
```
But my mother board is fairly new, plus ATI still should support my Radeon 9250 since it isn't listed *_[here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx")_*

Here's my thread for those who also received this message after trying the *aticonfig --initial -f* code.

---

### Post by Yellow Pasque on 2010-11-25
> **Tekno.Statik said:**
> But my mother board is fairly new, plus ATI still should support my Radeon 9250 since it isn't listed *_[here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx")_*
ATI drops support for a bunch of cards newer than yours, yet you think yours is still supported? Way to generate a lot of NOISE...

---

### Post by kuric on 2010-11-26
I have an ATI Mobility Radeon 9000 IGP working perfectly on Ubuntu 8.10 with ATI proprietary drivers.
When I've upgraded to Ubuntu 9, then my graphic card was no longer supported, so I had to use Radeon generic driver, instead of ATI. System usually crashed very often and this problem persisted in Ubuntu 10.

I've tried a billion solutions, here are some of the most successful:

1) Enable **Option "AGPMode" "4"** in xorg.conf.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

*"3D may hard-freeze X-server unless AGP mode is set correctly in Xorg.conf. If you have this problem, try adding Option "AGPMode" "4" to the device section of Xorg.conf"*

For those who don't have a xorg.conf file, follow these steps:
Ctrl+Alt+F1
$ sudo service gdm stop
$ sudo Xorg -configure
$ sudo service gdm start
Rename xorg.conf.new (in your home folder) to xorg.conf and copy it into /etc/X11 folder

2) Turn off **Compiz**. Go to Synaptic and remove all packages related to compiz.

3) Enable **nohz=off** option.
$ sudo gedit /boot/grub/grub.cfg and add *nohz=off* option on the first menuentry, should look something like this:
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec5f3463-a301-4f6f-aa23-3cbb44dc140d ro quiet splash nohz=off

4) Disable **3D acceleration** (poor solution). Install driconf from Synaptic. Select Preferences > Administration Tools > 3D Acceleration. Go to Debugging tab and disable 3D acceleration.

5) Uninstall applications with unstable activity like **Firefox** (due to flash player, try Google Chrome instead), **Firestarter** or **Ubuntu One**.

6) Remove **pulseaudio** and install alsa.
[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)
[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

7) Disable **Hyper Threading Technology** in Bios options. This is very effective.

---

### Post by Decatf on 2010-11-26
There have been lots of bug fixes in the driver recently. I recommend you try the most recent driver that can be obtained from the xorg-edgers ppa.
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

---

