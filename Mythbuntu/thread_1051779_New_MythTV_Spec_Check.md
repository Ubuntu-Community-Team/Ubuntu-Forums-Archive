---
title: "New MythTV Spec Check"
date: 2009-01-27
forum: Mythbuntu
---

### Post by lisnalinchy on 2009-01-27
Hi All,

This is my first delve into MythTV and I am hoping that, with your help, I get this right first time. I have looked at a number of the other posts regarding machine builds and come up with a build that should work - just wanting you to run your expert eyes over it and see what you think and any changes you would make.

The general idea is that I am looking for an ultra quiet and energy efficient machine that will record UK freeview (DVB-T), play mp3s, ripped DVDs (iso's probably) and stream audio and video out to other units around the house.  Maximum load (as far as I can tell) would be two digital TV stations being recorded/viewed and two dvd movies being played at the same time (one locally and one remotely).  This unit will be both frontend and backend.

Considered spec:
MB:   ASUS M3N78-AM with GForce 8200 onboard uATX
CPU:  AMD Athlon X2 5050e (2.6GHz)
Mem:  2Gb (PC2-8500)
HD:   1TB WD10EACS Caviar Green x 1 (for now)
Case: Antec NSK2480-UK Desktop media centre case (380W PSU)
Tuner:Hauppauge Nova-T 500 (dual digital tuner)

Additional frontend unit: ZyXEL DMA-1000 UPnP media player

At the moment I have traditional TVs (not HD) though I will consider an upgrade to an HD TV in the future.  I will also be running all connections over a Gigabit ethernet.

There are a couple of questions though:

Would it be better to have a dedicated PCI-E graphics/network/sound card?

What would it take to boost this to run HD?

Many thanks

---

### Post by tgm4883 on 2009-01-27
Your machine should run recorded HD just fine.  If you want Blu-ray HD, then you might need to use VDPAU, which I don't think has been backported officially to 0.21 yet.

IIRC, The 8xxx series of nvidia cards support VDPAU, but since yours in onboard i'm not sure.

---

### Post by stevanbt on 2009-01-27
Hi,
You might want to check out the noise from your hard drive - I've settled for Spinpoint drives in my Myth PC... whisper quiet :).

I agree with the previous reply you should be ok for HD, I've just upgraded from nova-t 500 to nova-s plus.  BBC HD playback is good (75% load on AMD 4200+).

Thanks, Steve.

---

### Post by lisnalinchy on 2009-01-29
Many thanks for the replies :)  Sets my mind at rest :)

I have been toying with two different boards - the one specified above and this one: [Asus M3A78-CM]("http://www.asus.com/products.aspx?modelmenu=2&model=2341&l1=3&l2=149&l3=736&l4=0") which has an Integrated ATI RV610 which supports an RGB output.

Any idea how well this ATI chipset is supported?  or would it be better to go with a separate graphics card such as an NVidia [GeForce 8400GS]("http://www.asus.com/products.aspx?modelmenu=2&model=2094&l1=2&l2=6&l3=551&l4=0")?

What is the composite video output on these cards like?

Many thanks

---

