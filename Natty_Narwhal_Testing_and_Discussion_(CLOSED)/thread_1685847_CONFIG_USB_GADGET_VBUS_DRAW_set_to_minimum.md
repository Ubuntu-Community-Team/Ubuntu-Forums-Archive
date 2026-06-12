---
title: "CONFIG_USB_GADGET_VBUS_DRAW set to minimum?"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by loftwyr on 2011-02-11
I've been mucking about with my USB3 hard drive dock, a Vantec NexStar.  It wasn't working under Natty but had been under my previous Gentoo install.

So, I've ben mucking about with kernel settings and noticed that CONFIG_USB_GADGET_VBUS_DRAW was set to 2mA instead of the maximum 500mA.  I change it and changed a few relevant modules to be in kernel and now the dock works fine.

Is there a reason for the vbus draw to be set to the minimum?  I'm wondering if that might be my problem as I can't see why a USB drive would be affected by the relevant code being modules if they're loaded.

---

### Post by dino99 on 2011-02-11
some details might help others, please post a little howto

---

### Post by loftwyr on 2011-02-11
I'm thinking if you know how to roll your own kernel, finding that setting shouldn't need a howto.

That being said, the setting is found here:
Device Drivers                                                                                                                                                                                                                         
-> USB support                                                                                                                                                                                                                  -> USB Gadget Support
-> Maximum VBUS Power usage (2-500 mA) (enter 500)

Now back to the question, is there a reason it is set to the minimum?

---

### Post by loftwyr on 2011-02-12
IF there doesn't seem to be an answer as to why this setting is the way it is, how do I go about requesting a change?

---

### Post by mc4man on 2011-02-12
> how do I go about requesting a change? 
one way
```
ubuntu-bug linux
```

---

### Post by MacUntu on 2011-02-12
Ask your question on IRC (freenode.net) #ubuntu-kernel (usually dead during weekends).

---

### Post by loftwyr on 2011-02-14
I put the question to the irc channel and they referred me to the kernel USB devs

Their response:
> 

> I have a Vantec NexStar USB3 dock using the JMicron chipset on a NEC chipset 
> motherboard hub. The motherboard is a Asus P6X58D-E 
> 
> I am running 2.6.38-rc4 under Kubuntu
> 
> The dock is recognized but doesn't seem to work (writes not committed,etc.) 
> unless I set the default on CONFIG_USB_GADGET_VBUS_DRAW to 500 (well, that's 

The gadget Kconfig has nothing to do with the host-side drivers to
support your dock.

> the only other setting I tried).  I'm assuming that the dock is mis-reproting 
> it's needs but was wondering why the default is set to 2 in kconfig.

The default is 2 because it's the bare minimum a USB device will draw
(well, there are the ones which draw nothing). It's just a sensible
default, manufacturers should fix up the device descriptors correctly
instead of using that Kconfig entry 

> I've asked the ubuntu kernel team and they referred me to you.
> 
> Is there problem or potential problem if the default setting is changed to 
> 500?

Yes, gadget drivers are also connected to OTG or Embedded hosts. Those,
in most cases, can't source more than 1 or 2 unit loads (100 or 200mA),
so if you make it 500mA, those won't get enumerated.

Also, if you're behind a bus powered Hub, you can never get 500mA as the
HUB already consumes at least 1 unit load for itself, again your device
won't get enumerated.


So, it seems that despite needing this change for my dock, it isnt' the solution to my dock's problem.  Time to poke at Vantec.

---

