---
title: "can't get USB dongle to work"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by youWho on 2013-01-20
Hello all,

Sorry if I'm asking something that has been answered, but even after *much* searching it's not clear to me what exactly to do.

I have a Huawei E303 USB dongle. I'm using Ubuntu Studio Precise (12.4), which means that I'm sort of using Xubuntu, because it uses xfce. I have 2 partitions with systems installed though; I also have Ubuntu Studio Natty (but that's Gnome based).

I know that the stick is not locked because I was able to use it with a SIM that I bought in Berlin from a company called "fyve"; at the moment I'm in Vienna, and have tried a couple of SIMs and neither have worked, though both work fine with Wondows 7 (dual boot). The SIM I have at the moment is from a company called "bob", if this has any relevance.

The really frustrating part is that even to try something means carefully noting what to do and then rebooting, rebooting again back into Windoze to search, etc. a SLOW process.

I'm also certain that the device is being mode switched when I plug it in under Precise, though not when I plug it in under Natty; indeed I never got usb_modeswitch to switch the mode in Natty but could use the stick by booting into Precise and letting that do the mode switching, then rebooting into Natty (I didn't have apps I use installed in Precise yet).

Any help would be really appreciated.

---

### Post by youWho on 2013-02-22
This is quasi-solved. I mean it's now working after I reinstalled the OS from scratch. It seemed I had installed somethiing that stopped the network-manager applet from creating or perhaps recognizing a connection.

I should say that I reinstalled the system twice(!) because after the first time I happened to boot with the dongle plugged in one day and from that moment on it wouldn't work (again)!! No form of restarting with/without it plugged in would get it to work anymore. I simply decided that it was less time spent to reinstall again (since I had only just done that) than to try to fix it.

I'm sort of reluctant to mark this as [SOLVED} since it seems the problem remains; just that I found a workaround. If I learn more about what happened and why, I'll post that info.

In the process I upgraded from Precise to Quantal too BTW. It was working after the reinstall of Precise too though.

---

