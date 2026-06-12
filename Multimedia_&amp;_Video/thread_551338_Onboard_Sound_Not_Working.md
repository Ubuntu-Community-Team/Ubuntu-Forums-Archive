---
title: "Onboard Sound Not Working"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by tlukareski on 2007-09-15
Hello - 

I have installed Ubuntu 7.04 on an old Dell Optiplex GX1 machine I had and I do not have any sound.   The volume control states that it did not find any elements and/or devices to control.  I have checked the BIOS and the onboard sound is enabled...I do not have a separate card.  (Yes, the speakers are plugged in and turned on).   Everything I have read stops at enabling at the bios or finding the drivers for the card.

The PC only has three slots, 2 PCI (already used) and one ISA, so adding another card is not possible.  Can someone please help me in getting this configured and working?  I've included some information that my help below...

Here are the results from LSPCI...
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
00:0e.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0e.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0e.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0e.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

...and lsmod |grep snd
snd_opl3_lib           11520  0 
snd_hwdep               9988  1 snd_opl3_lib
snd_cs4231_lib         26112  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         10888  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9472  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          9100  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd

---

### Post by linuxwizard on 2007-09-15
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by Crenfinkle on 2007-09-15
lspci on my machine reveals an "Audio Device:" option, so I think (and I'm definitely no expert) that you truly have absolutely no drivers installed or recognized for sound support. Have you tried upgrading to the latest alsa? There are many excellent tutorials that will walk you through this. Onboard audio has been a problem for many people, and updating to alsa 1.0.14 solves the problem for many people. Ubuntu repos are still at 1.0.13, so you will have to compile and install it yourself. Another option would be to buy a usb sound card. Some people have had to utilize this inconvenient solution to get sound working, but they say it works flawlessly.

---

### Post by dchriscoe on 2007-09-22
Here is the fix for your sound problem:

1. run terminal

2. type - sudo gedit /etc/modules

3. add to the end of the modules file:

   snd-cs4236

save file and reboot system

---

