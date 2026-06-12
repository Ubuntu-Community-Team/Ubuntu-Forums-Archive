---
title: "Wifi works from USB disk, fails from hard drive?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by matthew_exon on 2009-11-19
I have an EEE Box (the desktop variant of the EEE PC) and I'm trying to connect to a BT Home Hub.  This always used to be problematic under 9.04, sometimes it'd work, sometimes not.  I thought that 9.10 had fixed it, for a while it was working fine.

But now I've moved to a different house, also with a BT Home Hub, and it doesn't work.  But, weirdly, it works fine if I boot from an Ubuntu installation disk on a USB stick.  The settings are identical.  Of course I've deleted the connection settings and re-entered them several times.  No joy.

I don't want to reinstall my operating system from scratch.  Any suggestions what else I should do?

Is there any chance that different firmware is being installed somehow?  How would I check?

Where does network manager store its settings?  Maybe I could copy them over from the USB stick and see if that fixes something.

---

### Post by matthew_exon on 2009-11-20
I solved this.  I did an lsmod under both situations to see if there's a difference in the drivers, and indeed the hard drive was using ndiswrapper.  I removed ndiswrapper and used the native rt2860sta driver instead, and it works fine.

---

