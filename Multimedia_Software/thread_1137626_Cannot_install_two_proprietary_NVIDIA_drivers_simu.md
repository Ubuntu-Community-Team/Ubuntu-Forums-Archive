---
title: "Cannot install two proprietary NVIDIA drivers simultaneously?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by mbc2000 on 2009-04-25
I have two NVIDIA cards (FX 5200 and MX 400) on Ubuntu 9.04.  One card requires NVIDIA driver version 173 and the other requires version 96.  I have version 173 working with one monitor, but when I try to activate version 96, version 173 is deactivated.  Is it possible to have both cards active and stretch my desktop across two monitors?

---

### Post by inobe on 2009-04-25
you will need some sort of special hardware called "sli"

[http://en.wikipedia.org/wiki/Scalable_Link_Interface](http://en.wikipedia.org/wiki/Scalable_Link_Interface)


two identical cards, both cards use one driver !

what you are describing is impossible with that hardware, also you can never enable two video drivers at the same time.

---

### Post by inobe on 2009-04-25
[IMG]http://techreport.com/r.x/sli/sli-rig1.jpg[/IMG]

---

### Post by mbc2000 on 2009-04-25
I dual-boot with Windows Server 2003 and that supports a single desktop with both cards using two different drivers.  And I had this working in the past with Kubuntu (maybe 7.04?), but I lost my xorg.conf.

---

### Post by SuperNatendo on 2009-04-27
What he is describing is setting up two video cards on the same system to stretch the desktop across both, not SLI.

SLI sets up the system to use both cards as if they were one.  This is enabled by the PCIe bus.

Dual Video Cards have been used since the 90's in home desktops, and do not require the use of SLI.  I gather that one card is AGP and the other is PCI(old) or both are PCI(old).

As for running both nvidia drivers, I am not sure how the proprietary nvidia drivers handle that.  Have you tried using the open driver?  It may work for you, but you won't be able to enable compiz effects.

---

### Post by mbc2000 on 2009-04-28
Thanks for the reply.  I'm installing on an Asus Pundit which only has two PCI slots, so both cards are PCI.  When I had this PC working with Kubuntu a couple of years ago, I was using the "nv" driver, but was hoping I could use the proprietary ones now.  Anyway, Jaunty is killing my on-board NIC when I shut down so I'm going to try some other distros to see if they like my hardware.

---

### Post by inobe on 2009-04-28
never heard of such a thing, goodluck with that.

---

### Post by markbuntu on 2009-04-28
In the past gpu drivers did not have parts that live in the kernel and now they do. I am not sure if you can get two different nvidia kernel modules to actively coexist without freaking out the kernel since the drivers would be making the same calls to the kernel and expecting different results from different kernel modules. I don't think the kernel could figure that out.

---

### Post by inobe on 2009-04-29
i suspect one card running without a driver' but not both on any platform.

---

### Post by mbc2000 on 2009-04-29
I tried Mandriva and was able to simultaneously install both proprietary drivers.  But I couldn't use both simultaneously in xorg.conf.  I was able to use the proprietary driver on my primary card (without any 3D stuff) and the "nv" driver on the other.  But then my on-board NIC died as it did in Ubuntu.  I flashed my BIOS with the latest (albeit beta) version and will try Ubuntu again, just using the "nv" driver on both cards.  That's what worked a couple of years ago on the same hardware.

---

