---
title: "Steam and video driver"
date: 2015-09-20
forum: Multimedia Software
---

### Post by jet-san on 2015-09-20
Hi there,


I have installed Ubuntu 15.04 recently and now I am trying to get all my software.
I have problem with running [Steam]("http://store.steampowered.com/about/") and I found out it might be related with graphic drivers.
The installation was fine, but when I try to run it, it does not start.
I can see Steam in the processes list in System Monitor, but I cannot see the interface to log-in and start playing.

My hardware:
[TABLE]
[TR]
[TD]*Processor:*[/TD]
[TD]*Intel Core 2 Duo E8600*[/TD]
[/TR]
[TR]
[TD]*Motherboard:*[/TD]
[TD]*Asrock G31M-S*[/TD]
[/TR]
[TR]
[TD]*Memory:*[/TD]
[TD]*4GB (2 X 2GB) Kingston PC6400 800Mhz DDR2*[/TD]
[/TR]
[TR]
[TD]*PCI-E Graphics:*[/TD]
[TD]*512MB ATI HD4850*[/TD]
[/TR]
[TR]
[TD]*Sound Card:*[/TD]
[TD]*Creative PCI Audigy SE 7.1*[/TD]
[/TR]
[TR]
[TD]*Primary Hard Drive:*[/TD]
[TD]*500GB 7200rpm SATA II*[/TD]
[/TR]
[/TABLE]

I went to [AMD website]("http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx") to download the latest driver **amd-driver-installer-14.20-x86.x86_64.run** and I tried to install.
```
sudo sh ./Downloads/amd-driver-installer-14.20-x86.x86_64.run
```
However it did not work.
```
error: Detected X Server version 'XServer 1.17.1_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib:XServer 1.17.1_64a:none:3.19.0-28-generic:)
Installation will not proceed.
```
I found an old version of that driver in my documents, so I decided to try it as well.
```
sudo sh ./Documents/amd-driver-installer-12.6-legacy-x86.x86_64.run
```
And this is what I get.
[[IMG]http://s22.postimg.org/4hzamfjy5/Screenshot_from_2015_09_20_16_12_26.png[/IMG]]("http://postimg.org/image/4hzamfjy5/")

[[IMG]http://s22.postimg.org/qsn5meh8d/Screenshot_from_2015_09_20_16_13_11.png[/IMG]]("http://postimg.org/image/qsn5meh8d/")

Any suggestions how to fix it?
Damian

---

### Post by MartyBuntu on 2015-09-20
You are unfortunately stuck with the open source drivers.
Any attempt to install newer AMD drivers will break Xorg, leaving you with an unusable machine.

The only exception is if you install the original release of 12.04. It comes with an older version of Xorg.
Once installed, you should be okay with updates as well as proprietary graphics drivers.

---

### Post by andrew257 on 2015-09-20
Hi, I'm just dropping in because I had bad problems when trying to install AMD proprietary drivers.   Does this mean that steam is currently unusable with an AMD card?  I know that the client won't run on the open source drivers.

---

### Post by QIII on 2015-09-20
andrew257 --

I have an R9 290X and Steam works fine.

Please see my response in your thread.

---

### Post by jet-san on 2015-10-05
Ok, so I need to swap my Radeon for Nvidia.
I was thinking of buying GeForce GTX 960 or GTX 970, but are not advised in this thread.
[http://www.tomshardware.co.uk/answers/id-2363986/nvidia-video-card.html](http://www.tomshardware.co.uk/answers/id-2363986/nvidia-video-card.html)
However my PSU is 460 Watt.
Does anyone know is it still up-t-date?
Should I buy GTX 750 Ti?

Thanks,
Damian

---

