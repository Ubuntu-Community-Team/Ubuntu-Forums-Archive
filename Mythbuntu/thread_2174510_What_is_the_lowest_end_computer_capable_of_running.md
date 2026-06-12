---
title: "What is the lowest end computer capable of running Mythbuntu if recording is only use"
date: 2013-09-14
forum: Mythbuntu
---

### Post by bullwinkle2 on 2013-09-14
I already have a Mythbuntu install, but my backend is used only for recording shows - there is no display of any kind attached to it.  I am wondering if I could get by with a smaller/less power hungry computer.  So I would like to get a handle on what kind of equipment is required to simply record programs.  The source is a HDHomeRun Dual (only receives over the air signals) and I only need to be able to save the programs and then view them from frontends elsewhere on the network.

 I had thought about a Raspberry Pi but I don't know if it's powerful enough, and I'm also concerned that it might not be able to handle the bandwidth if a couple of signals were being recorded while at the same time, a couple of frontends were trying to view programs.  I suspect that something with a gigabit network interface would be required.  Also, as far as I know, Mythbuntu won't run on a Raspberry Pi.  I just wonder what you guys would use in this situation.  Very low power consumption and small size (and lack of a noisy fan) would be attributes I'm seeking.

---

### Post by uteck on 2013-09-15
I read a post on the MythTV forum and the main concern there was the CPU in the Pi would bog down when doing scheduling.
Another concern is the USB bus.  Recoding shows and playing them back at the same time could saturate the USB 2.0 bus and cause things to stutter.

For your use case, you may want to look at something that has at least an Atom or a AMD APU, and either internal storage or USB3 or eSATA for external.

---

### Post by bullwinkle2 on 2013-09-15
uteck, the USB bus transfer rate was one of the things that concerned me.  I wonder if the situation would be better if you made it a point never to play back programming while something else was recording?

As for scheduling duties, those take place in the middle of the night and since we are looking at over-the-air stations, there are relative few stations that it needs to process.

Although, I do see where someone says they installed MythTV on a Raspberry Pi:  [http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=26022](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=26022) - and someone else published a PDF that supposedly shows how to do it: [http://database5.com/m/mythtv-and-raspbian-pi-e7531-pdf.pdf](http://database5.com/m/mythtv-and-raspbian-pi-e7531-pdf.pdf)

Unfortunately neither of those used Mythbuntu.  And in one use case I had in mind, being small, noiseless, and especially having low power consumption is a BIG plus.  But, I probably wouldn't use a Pi to replace my current Mythbuntu backend; which is working very well at the moment.

That's why I was specifically wondering if anyone knew of something similar that actually would run Mythbuntu.  Maybe I am dreaming, hoping for such a thing, but it never hurts to ask.

---

### Post by uteck on 2013-09-16
I think the Mythbuntu folks are focused only on x86/x86_64 hardware, so no Arm port for the Pi.  If you want to try it, you will have to use Debian and whatever verson of Myth they ported to Arm.

---

