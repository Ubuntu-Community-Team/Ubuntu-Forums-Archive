---
title: "New to Linux, and having some MythTv setup problems!"
date: 2009-07-25
forum: Mythbuntu
---

### Post by ChrisJames on 2009-07-25
Hello all,

About a year ago I built a Vista Media Centre for my bedroom, all was going well until last week when my disc died so I thought I would try out MythBuntu (9) with my new HDD

The installation was all really simple (which was great), but I have encountered some configuration problems, and I hope that some of the members of this forum will be able to help out.

The main problem is my DVB-T card has not been detected in Ubuntu, it is the Hauppage pvr150 (it is the MCE edition with the remote, will this make a difference, is it usable in MythTV?).  So I would appreciate some instructions to help me find out what the problem is, as I really want the TV on my media centre ^_^

Although I am computer literate, this is the first time that I have dealt with Linux (was a windows boy up until now), but the look and feel of MythTV has really drawn me in so would really like to get this working.  So a bit of patience in regards to the instructions that you may supply for Linux will be appreciated.

Also, all of my current media which I have collected over the past year is on a drive in my windows machine, is it as simple as chucking the drive into my Linux box to be able to access all of the media? or will Linux not recognise it?

The current build is:


[LIST]
[*]Antec Fusion V2 MATX MediaCenter Case - Aluminium Front Bezel with 430W PSU
[/LIST]

[LIST]
[*]Samsung SpinPoint F1 HD103UJ 1TB Hard Drive SATAII *32MB Cache* - OEM
[/LIST]

[LIST]
[*]Crucial 2GB kit (2x1GB) DDR2 667MHz/PC2-5300 Memory
[*]ASUS M3N78-EMH HDMI GeForce 8200 Socket AM2+ onboard graphics 8 channel audio mATX Motherboard
[*]AMD Athlon 64 X2 5600+ 2.9GHz Socket AM2 512KBx2 L2 Cache OEM Processor
[*]Hauppauge WinTV PVR150 MCE TV FM Tuner With Hardware Mpeg2 Encoder Composite S-video Capture Card
[/LIST]

Many Thanks,

Chris.

---

### Post by ian dobson on 2009-07-25
Hi,

Are your sure it's a Hauppage pvr150? The pvr150 is an analog mpeg card rather than DVB-T. In mythtv you need to setup an MPEG card rather than a DVB card.

Regards
Ian Dobson

---

### Post by ChrisJames on 2009-07-25
my mistake, the pvr150 was the initial card i ordered, that was replaced with my current card, it is:

Hauppauge WinTV Nova-TD 500 Dual digital DVB-T PCI TV Tuner card

is this one supported by MythTV?



Edit: it is worth noting that this isn't the diversity model, it has only one aerial input with this being split internally to achieve the dual, whereas the diversity model as 2 aerial inputs.  I have heard there were some problems with MythTv and the diversity model.

---

### Post by ian dobson on 2009-07-26
Hi,

The Hauppauge WinTV Nova-TD 500 should bw aupported "out of the box" with ubuntu/mythbuntu.

What messages do you see in our syslog (related to the nova-t)? 

Regards
Ian Dobson

---

