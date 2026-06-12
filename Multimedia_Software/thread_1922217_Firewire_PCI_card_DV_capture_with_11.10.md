---
title: "Firewire PCI card: DV capture with 11.10?"
date: 2012-02-08
forum: Multimedia Software
---

### Post by gppixelworks on 2012-02-08
Upgraded to 11.10 and find the legacy firewire stack is no longer available.

I used this stack for DV capture via a Firewire PCI card. Prior to 11.10, I disabled juju (it wouldn't see the camera or DV deck) and the legacy stack worked fine.

I'm unable to locate the legacy stack and, thus, am stuck without DV capture firewire support. So my preference is either to:

1) Get the new juju firewire stack to function properly for DV capture/digitalizing.

or

2) Obtain and use the legacy firewire stack.

Am aware this is an on going issue. Still, any ideas?

Ubuntu sees the firewire PCI card but not the connected DV deck/camera:

[FONT="Times New Roman"]02:07.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)[/FONT]

I suppose I could use a live CD for an older version of Ubuntu for capture or dual boot. Those options seem rather silly as, surely, firewire DV camera capture should be supported in the latest kernel.

This would seem even more important (at least to those of us who cut video and wish to do so on a Linux box) as the free, Open Source Lightworks for Linux is only months away from release.

For those unfamiliar with LightWorks, it's a video editing suite that has been in use for over 20 years by professional edit houses and studios. To date it only came with specially configured hardware. A year ago the focus changed and it will now run on most hardware. For more information see their website. The Windows version is in beta. Linux and Mac versions to be released soon.

[http://www.lightworksbeta.com/](http://www.lightworksbeta.com/)

---

### Post by gppixelworks on 2012-02-12
bump

Any ideas regarding obtaining and using the legacy firewire stack in 11.10?

](*,)

Cheers!

---

### Post by gppixelworks on 2012-03-14
From my research, testing and lack of a fix to this issue, it would appear the current version of Ubuntu (11.10) simply will not connect with a DV camera or deck and capture DV video.

As such I've filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950879").

If this is a problem for you as well, feel free to [visit the bug report at Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950879") and click the 'This bug affects me' toward the top of the bug report.

*Perhaps with additional users voicing the same issue and need to get video capture operational again, we can get the priority raised for a fix.*    ](*,)

Fingers crossed!

---

