---
title: "Installing  ath5k driver"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by akisawana on 2009-02-10
My internal wireless card doesn't run with the madwifi driver.

I installed the linux-backports-modules-intrepid-generic package, and rebooted. Twice.

I ran lspci -v | less and it told me, among other things, "kernel modules: ath5k, ath_pci"

I'm dual-booting this with Windows and it works just fine on Windows.

Why is it not working?

---

### Post by x22 on 2009-02-10
try

[http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic)

"google is your friend"

---

### Post by akisawana on 2009-02-10
> **x22 said:**
> try

[http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic)

"google is your friend"

Found that package, installed it, wireless card still doesn't work.

---

### Post by akisawana on 2009-02-10
Specifically, it's a Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter.

---

### Post by dca on 2009-02-10
See if this thread helps:
 
[http://ubuntuforums.org/showthread.php?t=1026770&highlight=ar242x](http://ubuntuforums.org/showthread.php?t=1026770&highlight=ar242x)

---

### Post by akisawana on 2009-02-10
> **dca said:**
> See if this thread helps:
 
[http://ubuntuforums.org/showthread.php?t=1026770&highlight=ar242x](http://ubuntuforums.org/showthread.php?t=1026770&highlight=ar242x)

I will try that -I have an AspireOne, but it shouldn't be that different.
Thank you very much!

---

### Post by akisawana on 2009-02-10
That worked!
Now to actually *connect* to our home network. Oh, that's going to be fun.

---

### Post by J3 Remy on 2011-11-11
When I click on the link, I get an error that there are more than (2) drivers for that link.  Specifically, what driver am I looking for?

Thank you
J3

---

### Post by nothingspecial on 2011-11-11
@ J3 Remy

Please start a new thread with as much details concerning your problem as you can. :)

This thread is nearly 3 years old and as such has gone off.

Closed.

---

