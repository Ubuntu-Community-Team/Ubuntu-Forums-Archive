---
title: "ALSA default audio not working 12.04"
date: 2012-04-28
forum: Mythbuntu
---

### Post by Kantalias on 2012-04-28
How can I connect the default ALSA audio to an HDMI output in Mythbuntu 12.04?

Objective: get all system audio from any application to go to HDMI on an NVidia card.

Used to work: I've been on 11.04 for about year (until yesterday) and had all audio going to the HDMI out.  I have not changed my hardware.  To get to 12.04 I installed over 11.04 keeping the partitions/home folders, etc.  

Status: I have audio in Mythtv by selecting the correct ALSA card and device.  I can use speaker-test to this same device and get sound from a console.  I cannot get this device to work as the ALSA default.  

Devices (the one I need is card 0, device 7):
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
xcb_connection_has_error() returned true
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Things that work

[LIST]
[*]Audio from Mythtv by sending the sound to "ALSA: plughw:CARD=NVidia,DEV=7"
[*]Specifying the device directly, e.g.
[/LIST]
```
$ speaker-test -Dhw:0,7 -c2
```
[LIST]
[*]Creating a superfluous device in ~/.asoundrc that points to the correct device and playing to that device
[/LIST]
 If ~/.asoundrc contains
```
pcm.!foo {
   type hw
   card 0
   device 7
}
```then this works
```
$ speaker-test -Dfoo -c2
```What doesn't work:

[LIST]
[*]Having no ~/.asoundrc file
[*]Creating an ~/.asoundrc file that sets default to the right device (this is how I've been doing things for several years and it worked on 10.10 and 11.04)
[/LIST]
```
$ cat ~/.asoundrc
pcm.!default {
   type hw
   card 0
   device 7
}
ctl.!default {
   type hw
   card 0
   device 7
}
```All SPDIF/IEC958 devices are unmuted in the mixer.  
[[IMG]http://i1075.photobucket.com/albums/w427/Kantalias/th_xfce4-mixer.jpg[/IMG]]("http://s1075.photobucket.com/albums/w427/Kantalias/?action=view&current=xfce4-mixer.jpg")


I have logged off/logged on after changes and even rebooted.


Other details:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
06:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
``````
$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfb080000 irq 17

```I don't understand what's changed that's interfering with audio on my system.  Anyone have any ideas?


Thanks!

---

### Post by Kantalias on 2012-04-28
I got it working following the first tutorial from here [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240), in the section on NVidia HDMI sound ([https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#bookmark=id.4m8gei82bie](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#bookmark=id.4m8gei82bie)).  I'd never seen the steps in the last part of that section...

---

### Post by jonnybignote on 2013-01-19
Thanks - for me it was about following the Procedure Ad (Switch default sound card)

I'm running mythbuntu and didn't even have an asound.conf file, and the required device was not primary in the system, hence programs that couldn't designate their own specific sound settings, were not getting sound.

Overall, a lot simpler than I thought - great!

---

