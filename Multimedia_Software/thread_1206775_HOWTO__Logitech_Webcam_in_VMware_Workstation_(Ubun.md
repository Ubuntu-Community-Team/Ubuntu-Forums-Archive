---
title: "HOWTO:  Logitech Webcam in VMware Workstation (Ubuntu 9.04 Host, Windows XP Guest)"
date: 2009-07-07
forum: Multimedia Software
---

### Post by nxmehta on 2009-07-07
Honestly, getting webcams to work in VMware is like one of the most annoying things I've ever attempted.  However I finally got this to work, and I've yet to see a good guide about this posted, so I thought I'd post something to help out.

These instructions are for Ubuntu Desktop 9.04, VMware Workstation 6.5.2 build-156735 (the latest at the time of this posting), and a Windows XP guest.

[SIZE="4"]**Step 1: Disable the webcam in Ubuntu**[/SIZE]

First we need to make sure that the webcam cannot be accessed by Ubuntu.  If the webcam can somehow be used in Ubuntu then VMware will not be able to gain control over the device which will obviously cause problems.  Of course, this means you won't be able to use things like Ekiga, Skype, etc.  Personally I don't care about that since I can use Skype in my VMware install if I want.  I for sure have to use it with my Polycom PVX software, which is why I'm attempting to do this in the first place.

We need to disable the following kernel modules related to the webcam: uvcvideo (for video) and snd-usb-audio (for audio).

Create a file called /etc/modprobe.d/blacklist.local and add the following lines:

```
blacklist uvcvideo
blacklist snd-usb-audio
```

Restart Ubuntu to make sure these modules are disabled.

[SIZE="4"]**Step 2: Make sure VMware can get access to your soundcard**[/SIZE]

In Linux there are three different soundsystems: ALSA, OSS, and PulseAudio.  Ubuntu uses ALSA and Pulseaudio.  ALSA is the standard soundsystem which is supported natively in the kernel.  VMware, because they're lazy or whatever, I dunno, supports OSS.  So we need to make sure OSS is installed and that VMware is able to use it.  The following lines should help accomplish that.  They install the oss layer and make sure that VMware is able to access the oss libraries.  I'm assuming that you've installed VMware and that since you're using Workstation your binary is /usr/bin/vmware.  If you using Server or something like that then change these lines accordingly:

```
sudo apt-get install alsa-oss
echo '#!/bin/bash' > ~/vmware
echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> ~/vmware
sudo mv /usr/bin/vmware /usr/bin/vmware.orig
sudo mv ~/vmware /usr/bin/vmware
sudo chmod 755 /usr/bin/vmware
sudo chmod +s /usr/lib/libaoss.so.*
```

If you do not perform this step then there is a good chance that when you fire up your Windows VM you will get this error message:

```
Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.
```

Anyways, after you do this, start your VM and verify that you get sound.  You may need to set the sound card to use /dev/audio instead of /dev/dsp (VM settings -> Sound Card -> Use physical sound card /dev/audio).

[SIZE="4"]**Step 3: Setup the webcam in VMware**[/SIZE]

First, make sure USB 2.0 support is enabled in VMware (VM settings -> USB Controller -> Enable high-speed support for USB 2.0 devices) and that "Automatically connect new USB devices is unchecked".  Automatic connections can probably be checked, but I just like to uncheck it to make sure the webcam gets plugged in at the right time.  I should mention that, surprisingly, in these newer versions of VMware USB 2.0 support is implemented properly and you can have it **enabled** and still use a webcam.  Previously you had to disable USB 2.0 support to get a webcam to work.  Therefore, if you have a version of VMware Workstation older than 6.5.2 build-156735 I can't promise that USB 2.0 will work properly (it might, but I don't know at what version they fixed USB 2.0 isochronous transfers).

**PLEASE NOTE- there is a reason that this guide is for VMware and not VirtualBox.  VirtualBox does not implement USB 2.0 isochronous transfers, while VMware does.  Until this bug is fixed ([http://www.virtualbox.org/ticket/242](http://www.virtualbox.org/ticket/242)) you will not be able to use a webcam in VirtualBox with USB 2.0 support enabled.  I believe it can still work if you turn of USB 2.0 support however.  I haven't tried it recently though.**

Anyways, fire up VMware and install the latest Logitech webcam drivers (they have new drivers that install their own "Vid" software, annoying).  You may have to reboot Windows to continue the install.  When you get to the point where you need to connect the webcam, plug it in and tell VMware to connect it to the running VM (right click the icon in the bottom right corner of VMware and select connect).

You should be able to finish the webcam software install and see at the end that your webcam is working!  (I hope).

Hope that someone out there found this useful.

---

### Post by Alfiegerner on 2009-07-26
Thank you, I appreciated these tips.

---

### Post by pros on 2010-02-24
Still valid! Thanks a lot...

Karmic and Vmware 7.01

Create a file called /etc/modprobe.d/blacklist.local and add the following lines:
```
blacklist uvcvideo
blacklist snd-usb-audio
```
reboot and install logitech driver in vmware.

---

### Post by Murdoch99 on 2010-06-13
NXMEHTA 

YOU STAR !!! Have been trying to get this working for quite some time and your explanations have worked a treat. I kept getting crashes and my PC kept hanging etc. Just to confirm for everyone else heres my setup: 

Ubuntu ver: 10.04 (Lucid Lynx)
Windows VM ver : Windows xp 32-bit
webcam type: Logitech Pro 5000

I did as you mentioned and where it said "Automatically connect new USB devices" i actually CHECKED it and it has worked fine. 

As I intend to use all of my windows based apps within my XP VM, I uninstalled 'Ekiga' and 'GUVCVIEW' apps in Ubuntu to make sure there was no confusion. 

Thanks again and enjoy everyone 
Murdoch99

---

### Post by my_tomcat on 2010-07-16
Thanks nxmehta

Your post saved my day :-)

Writing this for all others using VMware 7.0/ 7.1 with OpenSuSE 11.2 or 11.3 and a Logitech webcam c905 (I assume all logitech models which use the ucv driver layer, so to say these models from Logitech and its competitors which do work with UNIX like OSes out of the box should behave the same) 

My problem was:
- VMware 7.0 or 7.1 hosted on a OpenSuSE 11.2 or 11.3 x64 box (both show the same behavior) 
- Windows XP, Windows 7 x86 as guest OS. 
- Logitech C905 Webcam

- Host and guest have been just installed with default settings
- Newest available Logitech webcam drivers and application have also been installed on the guest systems using default settings

First time I connected the webcam to the guests it worked quite fine.
But after this, depending on the host OS, just reconnecting the plug or rebooting either the guest or host was enough change to crash or freeze my guest OS or / and my host OS the next time I started any software which should grab the picture from the cam whithin the guest OS (like the Logitech video app, msn, skype,..!). But only using the cam in the host worked quite fine (cheese, amsn, .. did a quite fine job with the cam).
There were no changes to this behaviour neither I selected the"use USB 2.0" or "automatic connect" or "show all devices" Option within the VMware USB option menue. Also "using USB 2.0" is mandatory for my webcam, as it can offer 2 MB pictures, so  USB 1.1 is actually far too slow to handle this.

Following your advice, everything works quite fine. Of course from now on the webcam can only connect to either the host or the guest, depending on the existence of the blacklist file until to the next reboot of the host. But this is a very comfortable "walk around".


Keywords for search engine robots:
Linux OpenSuSE 11.2 OpenSuSE 11.3 VMware 7.0 VMware 7.1 Windows XP Windows 7 host guest crash stürzt ab friert ein freeze bluescreen Logitech webcam C905 connect anschließen USB msn skype yahoo messenger cheese

---

### Post by DanBender on 2011-05-17
I'm trying to deal with this on Mythbuntu 10.10 and am not understanding what is happening in Step 2 after the install alsa-oss. It seems to be creating/adding to certain files or folders (home/username/vmware maybe, and /usr/bin/vmware.orig). My home folder doesn't have a /vmware directory (it does, however, have /.vmware), and there isn't a /usr/bin/vmware.orig file (no vmware.orig anywhere on the system; however, there are a number of other vmware-somethings in that folder).

I'm using vmware ver. 3.1.4 build-385536. Do I still need to do that step exactly as posted, or do I need to change some things in filenames?

Thanks for the help
-Dan

EDIT: Oh, I guess mine is player, not workstation. EDIT2: Evidently Step 2 does not need to be completed in full anymore.

---

### Post by daka on 2011-06-21
Anyone have this webcam logitech 905 ...working on Ubuntu 10.04?

If so please pass on the process

Many thanks

---

