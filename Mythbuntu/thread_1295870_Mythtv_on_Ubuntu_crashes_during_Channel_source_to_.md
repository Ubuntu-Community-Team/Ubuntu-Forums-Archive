---
title: "Mythtv on Ubuntu crashes during Channel source to input programming of channels"
date: 2009-10-20
forum: Mythbuntu
---

### Post by dkhajavi on 2009-10-20
I am not new to Mythbuntu but had to do a new install due to a motherboard melt down.  I am running the following:
Asus Striker II Motherboard
Full water cooling cpu, gpu's, hard disks etc...
Dual Nvidia 7800 GTs in SLI
Haupaugge PVR-150
46" Sony DVI HD Monitor
Cable company box by General Instrument
Optical audio to 5.1 Amp
775 socket P4 3.2 32bit CPU (I know, I know, saving up for a quad core)
I am on Ubuntu 9.04
Dual 1TB SATA drives
Raptor 160gig primary drive
700W silent power

Everything above minus the new motherboard and the second Nvidia to run SLI is as it was in the previous build.  I was running a full mythbuntu system.  I liked it but I was just not used to the differences between Ubuntu an Mythbuntu and wanted to go back to the Ubuntu with Myth on top option.

Everything is working minus the TV.  The card is found with this info:
~$ dmesg | grep -i ivtv
[   14.074475] ivtv:  Start initialization, version 1.4.0
[   14.074573] ivtv0: Initializing card #0
[   14.074578] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.075562] ivtv 0000:03:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   14.075576] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   14.127200] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   14.127202] ivtv0: Reopen i2c bus for IR-blaster support
[   14.161766] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   14.173931] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   14.174023] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   14.207488] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   14.207527] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   14.207566] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   14.207616] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   14.207617] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   14.207655] ivtv:  End initialization
[   23.804037] ivtv 0000:03:06.0: firmware: requesting v4l-cx2341x-enc.fw
[   23.879436] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   24.076138] ivtv0: Encoder revision: 0x02060039

I see the card in the myth backend when I set-up the capture card.  When I go to the input connections and try to 'connect source to input' and add channels on composite 1 or 2 or s-video 1 or 2 the backend immediately crashes and I get a 'Would you like to run mythfilldatabase?' pop up.  

Some notes of possible interest.  I do not get a crash when I select tuner 1 but I also only find a couple of static channels out of the 100+ I used to get.

I also tried to set-up tuner 24 and 32 and they crash differently in that one crashes on tuner 1 and the other seems to crash randomly.  At any rate I cant get any TV.

Any help would be very appreciated!!

---

