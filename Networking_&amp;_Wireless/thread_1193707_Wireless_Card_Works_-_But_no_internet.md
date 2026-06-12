---
title: "Wireless Card Works - But no internet"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by toasty_ghosty on 2009-06-21
Hello,

Just install Ubuntu on an older laptop I had laying around the house. Thought it would be great as a make-shift internet tablet. Everything runs nice except for the wireless card (go figure). However, the card is running quite odd. I had internet without issue until I booted up today. I receive the signal, can connect to the wireless router, yet I do not get internet. Any ideas? Heres the info on the card:

> Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
        Subsystem: Dell Device 0001
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at faffc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb


I installed the drivers via the restricted drivers pop-up in 9.04.

---

### Post by tmht on 2009-06-23
Can you ping/connect to any local machines/services?

---

### Post by toasty_ghosty on 2009-06-23
Just logged on through the laptop. I get it to work, but in a very odd way. When I start the laptop up, I open up the hardware drivers and remove the network drivers. Then reinstall them. After that everything works fine. But, after shutting down the laptop, it stops working.

---

### Post by tmht on 2009-06-23
For a permanent solution try using the NDISWRAPPER.

Also, are you using any software that would try to hi-jack your device or just the straight up network manager?

Or check out [http://ubuntuforums.org/showthread.php?t=380362](http://ubuntuforums.org/showthread.php?t=380362)

---

### Post by toasty_ghosty on 2009-06-23
Not to sound like an elitest jerk, but I rarely use the hardware driver managers as I like to do it all myself, so to be honest, I thought that driver manager was installing it through NDISWRAPPER. And about the network manager, I might try Wicd. I tend to like that better anyway and see if that helps.

Thanks for the post. I will use that. These Broadcom chips seem mediocre at best...:(

-Ghosty

---

### Post by tmht on 2009-06-23
I have a broadcom chip in my dell and it rocks for picking up wifi signal.  But it's slow and the drivers lack the features to inject and do some of the other neat pen testing stuff.

---

### Post by toasty_ghosty on 2009-06-24
Thanks. That link lead to a fix. Got an error part way through, but it seems to have worked anyway.

Thanks. 

-Ghosty

---

