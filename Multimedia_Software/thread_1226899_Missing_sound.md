---
title: "Missing sound"
date: 2009-07-30
forum: Multimedia Software
---

### Post by HarryBhat on 2009-07-30
My friend has a Dell Studio and I recently upgraded it to Jaunty. Since then, I have not been able to get any audio output from any application.
The details of his laptop are as shown-

> karthik@karthik-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)



karthik@karthik-laptop:~$ lsusb
Bus 002 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 006: ID 05c6:6000 Qualcomm, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



karthik@karthik-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc500000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfc010000 irq 17



karthik@karthik-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel



karthik@karthik-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1



Also, when I open the volume preferences, I sometimes get the option 'Null Audio Output' (or something like that; I will add the exact words here once I get the error again).
Besides, in sound preferences, if I choose the device as 'HDA Intel STAC92xx Analog (ALSA)' , I get the error message: 
'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.'

BTW, ever since I upgraded to Jaunty, whenever I try to maximize ANY media player, I am reverted to the login screen.

I have enabled audio for all user groups too.

Could someone tell me what is happening? Was upgrading a BIG mistake? :confused:

---

### Post by MichealH on 2009-07-30
Do you have your driver??
I have dual booted Vista and Ubuntu and Sound on vista has caused mine to be low try to see If you have muted it on vista because that may be a massive problem.

---

### Post by igorzwx on 2009-07-30
"I am reverted to the login screen."

I had such strange phenomena with Ubuntu 9.04 too,
when I made noise removal with Audacity.
This problem was, however, solved in some way.
Now I have the "Brown Screen of Death" time after time.

---

### Post by HarryBhat on 2009-07-30
> **MichealH said:**
> Do you have your driver??
I have dual booted Vista and Ubuntu and Sound on vista has caused mine to be low try to see If you have muted it on vista because that may be a massive problem.

No! Sound is OK in Vista... :(

---

### Post by HarryBhat on 2009-08-01
Sorry about bumping the thread but I'm desperate for a solution :(

---

### Post by daryl314 on 2009-08-01
I have the same sound card, and I'm not getting any audio either...

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by HarryBhat on 2009-08-04
@ daryl314
Good to know I'm not the only one facing this problem ;)

@ igorzwx,
Will try soon. Thanks :)

---

### Post by MasterOfTheHat on 2009-08-04
I've got an HP DV4-1435dx, but it looks like it runs the same sound card:

```
~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

In order to get it to work, I had to edit the alsa-base.conf file. [See post here]("http://ubuntuforums.org/showthread.php?t=1128384&page=2&highlight=dv4-1435dx").

---

### Post by harry2006 on 2009-08-04
[http://ubuntuforums.org/showthread.php?t=1139700&page=2](http://ubuntuforums.org/showthread.php?t=1139700&page=2)

this should help...

---

### Post by HarryBhat on 2009-08-07
Thanks a lot all of you :)
Will try them soon...

---

### Post by desiindc on 2009-08-14
Posted my question on getting audio over HDMI there instead. Do let me know if you have any thoughts. 

[http://ubuntuforums.org/showthread.php?p=7786959#post7786959](http://ubuntuforums.org/showthread.php?p=7786959#post7786959)

---

