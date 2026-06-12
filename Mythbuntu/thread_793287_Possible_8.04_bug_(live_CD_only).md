---
title: "Possible 8.04 bug (live CD only)"
date: 2008-05-13
forum: Mythbuntu
---

### Post by poke4christ on 2008-05-13
Last night I installed mythbuntu on a new box and I encountered problem with the live CD.  Anytime I rebooted, it froze and I was forced to do a hard reset.  This was only when rebooting from the live cd and not from my installed system.

---

### Post by ozybushwalker on 2008-05-15
I observed the same thing. On booting the Mythbuntu 8.04 live CD I see
> 
ISOLINUX 3.53 Debian 2007-12-11
Loading...

and then the system hangs: the keyboard doesn't respond. In particular, typing the <Num Lock> key doesn't toggle the Num Lock LED. This happens with both an IDE CD drive and a USB CD drive.

The same CD successfully boots on three other systems. 

The Mythbuntu 7.10 Live CD and FreeBSD boot CDs successfully boot on the system where the Mythbuntu 8.04 live CD hangs. This system has a mini-ITX motherboard with VIA C3 800MHz Samuel CPU.

I got around this problem by moving the hard drive to another system, installing there, then moving the hard drive back. I still have other problems and strongly suspect the installation didn't work correctly.

---

