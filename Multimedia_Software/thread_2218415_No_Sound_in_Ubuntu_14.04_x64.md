---
title: "No Sound in Ubuntu 14.04 x64"
date: 2014-04-20
forum: Multimedia Software
---

### Post by terrykiwi83 on 2014-04-20
Unusual problem really. I get the sound indicator and sound when it comes to the login screen. However, once I click enter to login I get no indicator or sound at all.

I have already tried this troubleshooting guide to no avail > [SoundTroubleShootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

Output showing devices

> 
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT2020 Alt Analog [VT2020 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Terminating processes: 2123.
Unloading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-usb-audio snd-usbmidi-lib snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-rawmidi snd-seq-device snd-timer).
Loading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Support status summary of 'AOC-PC':


You have 76 packages (3.7%) supported until January 2015 (9m)
You have 50 packages (2.4%) supported until April 2017 (3y)
You have 1879 packages (91.5%) supported until April 2019 (5y)


You have 6 packages (0.3%) that can not/no-longer be downloaded
You have 42 packages (2.0%) that are unsupported


Run with --show-unsupported, --show-supported or --show-all to see more details
  *-multimedia            
       description: Audio device
       product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:48 memory:f7f10000-f7f13fff
terry@AOC-PC:~$ 


Any help would be appreciated as without sound I can't enjoy the OS :(

Edit:

I ran the below command and the indicator popped back up, but no sound.

> 
[COLOR=#000000]sudo /sbin/alsa force-reload
[/COLOR]

---

### Post by terrykiwi83 on 2014-04-20
Here is my alsainfo.

[QUOTE]
[http://www.alsa-project.org/db/?f=cc4df65edff1414784bdfe98a2729c7b59265092](http://www.alsa-project.org/db/?f=cc4df65edff1414784bdfe98a2729c7b59265092)
[QUOTE]

---

### Post by vetulani on 2014-07-19
IT says solved in the title, how did you fix this?
I'm having the same issue! :(

---

### Post by sre2kor on 2014-10-18
> **vetulani said:**
> IT says solved in the title, how did you fix this?
I'm having the same issue! :(

alsactl -F restore 
It worked for me

---

