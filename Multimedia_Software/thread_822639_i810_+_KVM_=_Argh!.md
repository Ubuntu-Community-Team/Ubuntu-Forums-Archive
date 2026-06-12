---
title: "i810 + KVM = Argh!"
date: 2008-06-08
forum: Multimedia Software
---

### Post by deathbywedgie on 2008-06-08
I've seen numerous posts regarding Intel i810 (or i8x-945) drivers, and I've gotten a little help out of them, but mostly I'm just getting a headache and needing narcotics. Before I get into the details of my issue, let me volunteer that I'm relatively new to linux in general, but I'm making progress. Just spare me the newbie and RTFM jabs, okay? lol Rest assured that I've spent *several* trying to concur this on my own before having to bug you guys for help.

Anyway, I just installed Ubuntu a few days ago. I'm running the latest and greatest (8.04). I'm running into video issues that I chalked up to my i810 video drivers (or lack of functionality thereof), but I've finally narrowed it largely down to my KVM. If I boot while connected to my KVM (doesn't matter whether I've got the Ubuntu system displaying or not), the max resolution I can get is 1280x800 ( which is useless to me on my 4:3 monitor, so the max I can use is 1024x768 ). If I boot with my monitor directly attached, all is well and I can get 1280x1024.

I've got a Dell 1907FP LCD; I'm running this on a small form factor PC (onboard video), so changing the card is out of the question. My *specific* video card is Intel 82865G.

I've run through dpkg-reconfigure xserver-xorg multiple times to no avail. I see references in other threads to selecting your video type in there, but I never even see such an option.

I've been able to make higher resolutions show up at least by adding the HorizSync (30-81) and VertRefresh (56-76) values in xorg.conf, but when I use them it leaves a large part of my monitor unusable... about 15-20% of my monitor on the right side is black and unusable. The monitor itself shows up as "Configured Monitor" and my video device simply shows up as "Configured Video Device". This is true regardless of whether I have the monitor attached through the KVM or directly when I run dpkg-reconfigure xserver-xorg.

Please help...

---

### Post by deathbywedgie on 2008-06-14
Any thoughts? Anybody? Bueller?

---

### Post by kparry on 2009-03-20
> **deathbywedgie said:**
> Any thoughts? Anybody? Bueller?
Did you ever get a reply? I am running Ubuntu 8.10 thru a KVM - I have same probelm - remvoe the KVM - all is well but no joy in the xorg.conf file...

---

