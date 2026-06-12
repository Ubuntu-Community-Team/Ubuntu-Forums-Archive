---
title: "Sound has stopped working"
date: 2009-08-24
forum: Multimedia Software
---

### Post by imple on 2009-08-24
Hi,

My sound was working, but now it isn't, even though I don't remember changing any of the settings.
```

ben@ben-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...
```

How can I sort this? The computer is a hp pavillion dv5. I've read through the sound troubleshooting guide, but that hasn't sorted things out.

Is there a command to reinstall/reset the whole sound setup?

Thanks,

Ben

---

### Post by x33a on 2009-08-24
post the output of
```
lspci
lshw -C sound
```

---

### Post by imple on 2009-08-24
```
root@ben-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
root@ben-laptop:~# lshw -C sound
PCI (sysfs)  
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 module=oss_hdaudio
```

---

### Post by x33a on 2009-08-24
Your soundcard is being detected by the kernel. so, i suppose it should be working fine.

are you getting no sound from any application? try different audio/video players.

also, try system -> preferences -> multimedia systems selector.

---

### Post by imple on 2009-08-24
Thank you. I get no sound from Songbird, Totem, Flash on Firefox 3.5. Also when I open 
System->Preferences->Sound, none of the tests output any sound, even when I cycle the drop-down boxes through all the options...

---

### Post by Adyhr on 2009-08-24
If working with 9.04:

Have had the same issue. Sound was first working fine and than stopped from one day to the next.
Here what I did to fix it. It might be a bit radical but it did work:

1. use pachage manager and uninstall ALL ALSA packages. This will break your gnome and, if installed, your KDE.

2. Restart. You will have to start in recovery mode.

3. log into console. You actually need to have your computer connected through CAT5. Wireless most likely will not work. (let me know if it would work for you though. I could not get it going)

4. run apt-get install gnome (and if desired apt-get install kde)

5. reboot again.

That was all what I did. Sound is now working again.
Good luck

---

### Post by imple on 2009-08-24
There must be some diagnostics or something I can do short of reinstalling the lot! It might be quicker, but surely there's a less risky way...

---

### Post by imple on 2009-08-27
any ideas?

---

### Post by x33a on 2009-08-27
try these:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

also, please post the output of
```
id
```

---

