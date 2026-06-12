---
title: "Asus Xonar D2 Bug"
date: 2010-03-22
forum: Multimedia Software
---

### Post by jhonnyas on 2010-03-22
Hello Everyone!

My old PC died and I recently bough a new one, with an ASUS Xonar D2 7.1 PCI card. So far I like it, but I ran into a bug. Since this is a problem I ll try to be brief:

BUG
-------
When I listen to music or videos or anything really, in PULSE panel, the output is set to 5.1, but i only hear sound coming out from 5 speakers not 6. One of the rear speakers, notably Rear Left, does not give out any sound.

How do I know its a bug and not a hardware error?
--------------------------------------------------------------
I swapped the channel of the rear left speaker with another, and sound does come out of the rear left speaker so its not a speaker issue.
When I switch to 4.1 speaker set in PULSE panel, the center speaker goes silent and the Rear Left speaker starts to work so its not a card issue.
When I switch back to 5.1 during the playback of the music/video all 6 speakers will work. Once the sound/video ends however and if I open another music/video, the problem reappears.

Reproduction
----------------
Disable Mobo soundcard from BIOS
Install a Clean Ubuntu 9.10
Update
start listening to music or watch a film and one of the channels will have no sound.


What I did do to try and solve the issue
-----------------------------------------------
Reinstall PulseAudio and Alsa
Install newest version of ALSA from source 1.0.22
Install newest PULSEAudio from test repo  : 0.9.21

Additional Information:
lspci:
jhon@NEXUS-SERVER:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8
01:00.1 Audio device: ATI Technologies Inc Device aa58
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
07:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
07:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
07:02.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
07:03.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
jhon@NEXUS-SERVER:~$ 

Any help/advice/suggestion would be appreciated!

---

### Post by Yellow Pasque on 2010-03-22
Maybe try pulseaudio 0.9.22 from this PPA: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by jhonnyas on 2010-03-23
Done the update, rebooted. No Joy. repeat, it did not do anything at all concerning the bug

---

### Post by jhonnyas on 2010-03-23
Update
------------

Bug is DEFINITELY in PulseAudio.

I downgraded to Ubuntu 9.04, alsa plays all channels perfectly while pulse screws up 1 channel, the one it did. I guess that means I ll stay on Ubuntu 9.04 for now. Any intel wheter you will have the option to ACTUALLY choose the output in 10.04, like you could in 9.04? Or is it gonna be 9.10 philosophy: Sticking with PulseAudio which can't be removed or switched off, and frigging annoying that the only way to remove it is to remove GNOME as well?

---

### Post by jhonnyas on 2010-03-23
UPDATE- Temporary Solution
-------------------------------------------
9.04 is not a solution as I couldn't get ALSA to support AC3 sound, it just pipes stereo through all speakers. 
Right now I've set the system to 7.1 speaker set, and using an extra jack cable which pipes side audio into rear audio. This way I get sound from all speakers but by all means this is not a permanent solution to the problem.

Any advice/help would be still appreciated!

---

