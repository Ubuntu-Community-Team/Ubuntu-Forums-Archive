---
title: "no sound from sony laptop 8.04, 8.10, 9.04"
date: 2009-03-30
forum: Multimedia Software
---

### Post by fackinace on 2009-03-30
I guess ubuntu is not for me then back to vista as the sound works perfect in that.
Except if somebody can help me because i love ubuuntu even got it on the works machine now.

So may be that will help somebody come to my rescue
Heres some more info:-

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 15)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
AND
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
AND

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: Sony Corporation Device 81e6
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at de400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
oh and im now running 9.04
fackinace is offline   	Reply With Quote

---

### Post by MarcusA on 2009-03-30
I think I came across a message with someone that had the same laptop as yours, I believe he fixed the problem by typing "alsamixer" in the terminal and use the arrow keys if it is on 0%

And if that doesn't do anything you can always try to right click the volume button and open volume control
Could be wrong though, I'm still pretty new to ubuntu but just trying to get the ball rolling as I see you have this problem for 2 days now..

> **fackinace said:**
> I guess ubuntu is not for me then back to vista as the sound works perfect in that.

heh

---

### Post by Ubuntiac on 2009-03-30
Interesting...

I'm having a problem with no sound as well, with the exact same model of sound card, but on an HP machine. Some people seem to have managed to fix this by updating the ALSA sound driver to 1.0.19, but that hasn't worked for me so far. :(

---

### Post by fackinace on 2009-03-30
Alsamixer is fine and checked everything volume is full, i even updated to the latest alsa driver and still nothing, its really bugging me now. Would it be worth submitting a bug report??. I love ubuntu but this is no good at all ive tried everything even a usb phone just to see if i could get sound from that (Works on my HP nc6320) but doesnt even appear on the sony???.
Ive tried adding different alsa configs (option) etc in the conf and still nothing.

Will keep looking though this will not defeat me lol

In vista and xp the sound works is what i meant to say 

Cheers

Ian

---

### Post by Ubuntiac on 2009-03-30
I came across this, which is based on an HP laptop, however it's the same model sound card:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930)

Let me know if you file a bug elsewhere though and I'll add what I know to it.

---

### Post by fackinace on 2009-03-30
Will do im gonna try alsa .19 ive tried .18 and thats no good, i thought i was getting the hang of ubuntu i even got the hp mie theme working on my acer and dell notebooks i even helped in a forum and then this comes along!! lol

I'll give you a shout tomorrow to let you know how i got on bloody hate sony laptops now weve even got three sony laptops at work and none will work with a 42 inch SONY lcd!!!!

Good luck matey

Ian

---

### Post by markbuntu on 2009-03-30
These problems are very hardware specific. There are some listings for Sony in the OP and I think there are more in the links.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by fackinace on 2009-03-31
Ok well i installed to the very latest alsa drivers and still no good ive benn looking at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and it tells you to enter in terminal 

Manually Specify Module Parameters

    * First you must find which model of sound card you use, so run this command: 

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

    * You should open a file in ALSA documentation. This file is here (replace KERNEL_VERSION with your kernel's version!): 

/usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt

If you didn't have this file, for version 2.6.22, you can check out this link or you can find ALSA-Configuration.txt in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.x.x directory you created. 

Now i cant find mine and the weird thing is i have two:-

SigmaTel CXD9872RD/K
Conexnt ID 2bfa

Well i cant find any of these???

What do i do now?

---

### Post by markbuntu on 2009-03-31
I found these for the sigmatel 9872. they are for sony vaios. Give them a try

STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

---

### Post by fackinace on 2009-03-31
tried both and still nothing i founs some more info too [http://ubuntuforums.org/showthread.php?t=584178]("http://ubuntuforums.org/showthread.php?t=584178") looks like that never got answered too in full plugging in the headphones a few times doesnt do anything. Should i class this as a bug and if so where do i post the bug (i dont want to go back to vista really!!!)

---

### Post by markbuntu on 2009-03-31
Go to alsa.org, there is directions for bug reporting. You also might find some more info.

---

### Post by fackinace on 2009-04-02
Ive placed a bug on alsa-project.org hope its the right place, quick question do you think usb speakers will work?

Regards

---

### Post by markbuntu on 2009-04-02
There are problems with some logitec and Bose usb speaker sets due to some non-standard implementation of usb protocols. I have not heard of others that do not work but if you do get some make sure you can return them if they do not work for you. If they use standard usb protocols you should have no problem using them.

---

### Post by fackinace on 2009-04-03
Ive got sound working now uninstalled alsa and installed oss  few problems but the sound is now working problem is the sound icon in the taskbar throws a wobbly so unable to adjust but i dont care.. Heres the link
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Ian

---

### Post by Ubuntiac on 2009-04-03
Cool bananas.

Glad it's working for you. Replacing ALSA with OSS sounds a bit drastic for me on my system-stability-loving-wife's machine, but if it suits your situation, more power to you.

Just so you know I've just found that sound on my machine works if I install the 2.6.29 kernel by the easy steps here:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

Trouble is it borks the wireless. *sigh*

---

