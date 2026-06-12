---
title: "MTP MP3 Player Requires Unreasonable Work-Around.  Alternatives Available?"
date: 2010-02-20
forum: Multimedia Software
---

### Post by bkann on 2010-02-20
Hi -

I apologize in advance if (a) this posting becomes long enough that it can be described as an epic, and/or (b) I am missing something terribly obvious here.  Even if I'm not, hopefully someone will benefit from my findings.

I have been trying for months now to get my once-working Creative Zen Xtra and Zen Sleek devices to work either with Ubuntu or a VirtualBox instance of Windows in Ubuntu.  They are both MTP (PlaysForSure) devices and they used to work perfectly and I believe they broke when I upgraded to 9.10, but I'm not certain that it was at exactly the same time.

Today I finally stumbled upon the right combination of actions to get then working again, however it's so far from the way things ought to work that I'm wondering if there is a bug or if I'm just not doing something right.

When I plug my MTP player in, Ubuntu mounts it and I can click into it.  However, it is not using the MTP protocol because the device does not find (eg., does not add to its internal database) any files I add.

In order to get it to work, I have to first unmount it at the desktop and then start Gnomad2.  Gnomad finds the device, scans the library, and then the device is usable from Ubuntu.  If I choose, I can then close Gnomad and enable the USB filter in VBox, and then (and only then) will the device be available in Windows.

Also, only after unmounting, opening Gnomad2, then closing Gnomad2, I can use Rhythmbox, Qlix, etc., to use the device.  But they are all unable to see it before doing the Gnomad2 operation.

I played around with this for several months but just today stumbled upon installing mtpfs, which I believe is what ultimately enabled me to get the devices working today, but I cannot swear to that fact.

Even so, this does not seem to be the correct behavior for the devices.  In fact, it used to be (maybe back in v2 of VBox under 8.04) that Ubuntu would play nicely with the devices by default, and I had a static USB filter in VBox that would find it and enable it in my Windows instance without any hiccups.

So my questions:
1. Is this a bug?
2. Has anyone else experienced this?
3. Why is mtpfs not installed by default with 9.10?
4. Is there a way I can get away from this multi-step process?

Thanks very much in advance for any help!

---

### Post by andrea000 on 2010-02-20
I'M not sure if this helps but what version of mtp tools
do you have you may find upgrading it will help.I am not
sure what the software sources are but i know there is one
out for 1.0.1 or if you like to compile download the source
from [here]("http://libmtp.sourceforge.net/") but there is ppa's out there for ubuntu

---

