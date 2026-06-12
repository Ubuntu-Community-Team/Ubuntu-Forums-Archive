---
title: "Natty Xorg keeping me from using older RT Kernel"
date: 2011-09-09
forum: Multimedia Software
---

### Post by thecreekninja on 2011-09-09
Hi,
I've been trying to use a RT kernel in Natty, but I get a blank screen with a mouse pointer on boot of the RT kernel in my xorg config file contains:
"Unable to submit batch buffer, expect rendering corruption......"  However, if I uninstall xserver-xorg-video-intel, which synaptic forces me to also uninstall xserver-xorg-video-all, I can boot in to the RT kernel and it works, but the Natty-generic kernel won't let me use unity.  
Is there a way to fix this, perhaps by disabling xserver-xorg-video-intel only on RT kernel boot.

The RT kernel is 2.6.31-11rt from a Lucid package.  
*The PREEMPT kernel 2.6.32 from Lucid will actually boot without uninstalling anything.  It's just the older RT kernel.  

I really want to get this working, so I can have a RT kernel.  I would use the low-latency kernel that has a PPA, but I think the new firewire stack JUJU is giving me problems, I want to continue using the old stack until the new one is solid.

---

