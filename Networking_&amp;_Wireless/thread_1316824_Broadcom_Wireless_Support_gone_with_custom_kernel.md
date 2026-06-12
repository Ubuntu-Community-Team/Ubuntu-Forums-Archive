---
title: "Broadcom Wireless Support gone with custom kernel"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by landersohn on 2009-11-06
I hope I can get some help: I am running Januty 64bit on an HP Pavillion dv5t laptop with Broadcom 43xx wireless network card.

I tried to build a custom kernel (using the Jaunty git repository as well as the 2.6.31 sources from kernel.org). As far as I can tell everything built fine.
I used the config-2.6.28-16-generic file which ships with Jaunty and the only change I made was to select the Core2 processor instead of "X86 generic".

When I booted the custom kernel it did not recognize the Broadcom card and I don't have wireless. The Braodcom hardware driver does not show up under System-Administration-Hardware drivers as it does under the kernel that shipped with Jaunty (note: other hardware drivers do).

It also appears as if under the normal Jaunty kernel a module "wl" is loaded (I modprobe'd it). When I try to load this under the custom kernel it does not exist. I don't think I have turned it off in the config file, though.

I am at a complete loss as to why the broadcom support disappeared with my custom kernel. Does anybody have any ideas?

---

### Post by landersohn on 2009-11-06
Fixed it. I found some good posts out there

---

