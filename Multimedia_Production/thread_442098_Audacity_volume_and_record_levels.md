---
title: "Audacity volume and record levels"
date: 2007-05-13
forum: Multimedia Production
---

### Post by Jeffj on 2007-05-13
I was using Audacity in Windows and I thought I would try it in Ubuntu.

If I use alsamixer on the command line I can turn microphone boost on and off.

If I right click on the speaker I get a Volume control that lets me switch between an alsa mixer and an oss mixer. This interface lacks the microphone boost but has separate record and playback controls. Change with File|Change Device.

The main difference I see is that the changing the record level does not change the height of the wave in Audacity. I'm not sure what control I need to change. Turning microphone boost on and off  does change the height of the wave but it's either really short or it gets clipped.

Also, once I've made a recording I can't hear it when I play it. I can hear other sounds like when I play a movie or turn off the mute on the microphone.

---

### Post by oxalá on 2007-06-23
same problem here.
he'p us, plz.

---

### Post by dabl on 2007-06-26
Did you guys get your Audacity recording fixed?  Jeff, it's not correct that changing the input level has no effect on the Audacity recording level -- it may not change in "realtime" but moving the slider up and down on the input mixer does change the level, visibly and audibly.

Not sure about the sound output problem -- need to check your Edit>Preferences.  Also I noticed that Firefox seems to "grab" the audio output, so Audacity can't play it.  Start your Audacity playback first.

---

### Post by oxalá on 2007-06-27
still having the same problem -- actually, my main problem is that i just can't seem to record at all.
Audacity playback is a problem, since all i want to do is record and edit narration that i would input with a mic.

---

### Post by dabl on 2007-06-28
OK, I'm the farthest thing from a Linux guru, but I'll be glad to share what works for me.

First, I'm running the Intel HDA system, which is integrated on my Intel D975XBX motherboard.  The chip is a STAC 92xx.

Second, I am using the ALSA sound system, not OSS.  So, first I'll show you what the output of lspci on my system looks like:

dabl@feisty:~$ lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

and next I'll list the packages that I have installed:

alsa-base
alsa-utils
alsa-tools
alsamixergui
alsaplayer-alsa
alsaplayer-common
alsaplayer-daemon
alsaplayer-gtk
alsaplayer-jack
alsaplayer-oss

and finally I'll post a screenshot of the settings for the input -- sorry this is kmix from Kubuntu, but it's a similar deal for the mixer in Ubuntu (right-click the speaker icon in the upper right corner, choose "open volume control").

---

### Post by fredj on 2007-06-28
If you DOUBLE CLICK on the speaker volume thingy a full alsa mixer will appear. 
Go to the Edit Menu and select preferences, this will allow you to add both the microphone VOLUME and
the microphone BOOST VOLUME. You can also add switches to the switch tab that will let you select
the record source e.g. by selecting the mix switch you will be able to record all the sound playing on your
PC or by selecting the mic switch you can choose to record the mic only.

You can also add any missing volume controls e.g. for CD or Line IN etc.

Then run Audacity, go to the EDIT menu and select preferences. Now you can choose an output and
input source. Probably the best choice here is Alsa hw:0 for both. Later if you are sending all your audio
through the Jackd server, you should select Jackd here but don't worry about that for the moment.

---

