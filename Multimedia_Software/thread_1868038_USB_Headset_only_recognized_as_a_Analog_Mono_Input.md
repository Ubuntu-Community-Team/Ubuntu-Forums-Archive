---
title: "USB Headset only recognized as a Analog Mono Input device, no Output"
date: 2011-10-23
forum: Multimedia Software
---

### Post by naxfen on 2011-10-23
Hi,

Since about 24h ago, my USB Headset stopped working normally in Linux. I'm on Ubuntu 11.10, with latest updates (and in contrast to others, my sound problem doesn't seem to be related to updates...)

Only possible cause that I can see is that I unplugged and re-plugged my USB Headset in two different USB ports... Tried switching it back, and then a ton of other combinations, to no avail. 

The hardware: Logitech USB Headset G35. Worked without any problems on 10.10, 11.04, and 11.10 until 24h ago. I dual boot on Windows 7, and works great in Windows.
My internal analog sound card (on the motherboard) works without a problem.

So when I open System Settings -> Sound Settings, with my USB Headset plugged in, it looks like this: 
Hardware tab:
[INDENT]Logitech G35 Headset
1 Input
Analog Mono Input
(and in Profile, its Analog Mono Input or Off)[/INDENT]
Input tab:
[INDENT]Logitech G35 Headset Analog Mono[/INDENT]
And the Headset does appear under the Output Tab
(I also have a Internal Audio device, and a GF110 High Def Audio Controller (HDMI) device)

But, strangely, the volume button on the headset still controls the master volume.
And in alsamixer (in terminal), the USB headset is detected, and has a Speaker volume (not muted, set to 86), plus bass plus trebble plus Mic

I cannot launch gnome-alsamixer, which I've read might help my situation, since it is currently broken (do a Google search of "gnome-alsamixer crash", ex.: [https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/850943](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/850943) )
I tried alsamixer-gui (another suggestion), but there I only see 2 volumes, and I think it's for my internal analog sound card.

I tried following this guide to provide some good valid info in addition to my ramblings: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) but 1- gnome-alsamixer is broken and 2- some of the repositories added are non-valid...

So anyway, here's some log:
command:
```
aplay -l
```
output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech G35 Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

tried ```
lspci -v
```, but don't see the Headset in there, probably because it's usb and external

after running:
command:
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh; chmod +x ./alsa-info.sh; ./alsa-info.sh
```
I get this report:
[http://www.alsa-project.org/db/?f=2b9b395792dea886f2dfb3fd733b8238322b0001](http://www.alsa-project.org/db/?f=2b9b395792dea886f2dfb3fd733b8238322b0001)

command:
```
sudo lshw -C sound
```
output:
```
  *-multimedia            
       description: Audio device
       product: GF110 High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:faffc000-faffffff
  *-multimedia
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:fbff4000-fbff7fff
```

And finally, I've done a lot of google research around my problem, haven't found someone else with exactly my problem, but a few similar things... One of the suggestions was to disable PulseAudio, but I'm not sure if it's wise, and how do to that exactly.

I was unsure if the best practice was to write here first, or enter a bug in LaunchPad first... But anyway, felt less scary here. If you didn't understand that up until now, I'm kind of out of my technical comfort zone here. :-s

Thanks for any help that you can provide, this has been driving crazy for more than a day! :)

---

### Post by warnellg on 2011-10-30
I'm having a very similar problem.  Any luck yet?

---

### Post by naxfen on 2011-10-30
**warnellg**: no... actually I was logging in to...:

*bump*

:|

---

### Post by naxfen on 2011-11-14
re bump!

Actually, something else might be of note:
```
lsusb
```
```
Bus 001 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 005 Device 005: ID 046d:c216 Logitech, Inc. Dual Action Gamepad

```
See the strange thing here? My mouse appears "as a mouse", my Gamepad as a gamepad. While my headset appears only as "Logitech, Inc.".
Dunno. seems strange.

In fact, I've got also an issue with a Webcam I just bought (USB, of course), it is not detected by Cheese or Skype, and it also only appear as the manufacturer when running lsusb... But that's another bug.

Again, I'm stomped.
**edit:** bug entered: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/890496](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/890496)

---

### Post by Dimath on 2012-11-11
Edit:
Nevermind, didn't realized that it's last year thread. Sorry about that.

---

