---
title: "FATAL: Module ndiswrapper not found."
date: 2005-02-10
forum: Networking &amp; Wireless
---

### Post by felixdzerzhinsky on 2005-02-10
I am trying to make my Broadcom BCM94306 802.11g wireless card work.

I've tried following the [https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper) with no joy.

It goes good for : ndiswrapper -l ....

Installed ndis drivers:

bcmwl5 hardware present


Then it goes pearshaped:

sudo modprobe ndiswrapper

Then I get:

FATAL: Module ndiswrapper not found.

What is  going wrong?

---

### Post by felixdzerzhinsky on 2005-02-10
Just checked. Would this problem be occuring because the kernel-headers are not present?

I'll have to wait till I get home to find out.

---

### Post by Mantle on 2005-02-10
[QUOTE=felixdzerzhinsky]
What is  going wrong?[/QUOTE]

You have the ndiswrapper driver, but are missing the ndiswrapper kernel module. Your options are download the linux header souce and compile it yourself or try out the hoary release which has it included (but is quite unstable). I had this problem too and it took me forever to figure out.

---

### Post by sandman85 on 2007-10-24
I've had the same problem, but found a [firm resolution]("http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/").

Oh my gosh, I just resurrected a thread that was two years dead :( oops.

---

