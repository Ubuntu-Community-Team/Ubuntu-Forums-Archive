---
title: "No sound in fresh install of Mythbuntu 14.04.1 64-bit"
date: 2014-08-19
forum: Mythbuntu
---

### Post by patslap on 2014-08-19
I've just installed Mythbuntu 14.04, and there is no sound being played through TV speakers.

When I plug in headphones to the TV or to the headphone socket on the motherboard, I still hear no sound.

I have Ubuntu 14.04 installed on another drive in this PC, using same hardware (apart from hard drive), and sound plays with no problems in Ubuntu. 

I've checked alsamixer and volumes for all outputs are set to maximum, and nothing is muted.

I am sending video and sound to TV via HDMI cable attached to HDMI out on my GPU. I know that in Ubuntu I had to select HDMI in order to send sound to TV via HDMI cable, but I can't see a way to do this in Mythbuntu with XFCE. 

My motherboard is an MSI 990FXA-GD65
GPU is MSI GeForce GTX 650 N650-1GD5/OCV1

How can I get sound to output through my TV via HDMI cable? 

Many thanks

---

### Post by patslap on 2014-08-19
Solved: I installed and ran pavucontrol. Then in the 'configuration' tab I selected the HDMI output which didn't say 'unplugged' next to it. 

It appears that pavucontrol is aware of three HMDI ports (only one physical one on my GPU though), and that Mythbuntu had defaulted to use one of the two listed as 'unplugged'.

---

