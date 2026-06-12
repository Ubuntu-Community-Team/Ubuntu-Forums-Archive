---
title: "WLAN got killed by automatic update?"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by t0mppa on 2009-04-07
Long story short, I had some initial trouble setting my WLAN to work, when I first installed Ubuntu 8.10 on my laptop, but after fixing that, things had worked just fine ... until today.

Today, I was working on my computer normally, when it threw a pop up at me saying something along the lines of "You have to restart your system to complete installing updates." So I figured that was probably a good idea and did that. Only to find out that now my Ubuntu cannot find my wireless adapter any more.

Not being a Linux wizard, is there any way to find out what kind of an update was installed to help figure out what went wrong? A kernel update, since it required a reboot?

Here's what happens on boot now:
kernel: [20.213116] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

The wireless adapter is:
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

And the madwifi driver (that used to work):
srcversion:     D3FD3BD11169A96DBCFF8DE
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
version:        0.9.4

iwconfig doesn't even find the adapter now.

---

### Post by coutts99 on 2009-04-07
> **t0mppa said:**
> Long story short, I had some initial trouble setting my WLAN to work, when I first installed Ubuntu 8.10 on my laptop, but after fixing that, things had worked just fine ... until today.

Today, I was working on my computer normally, when it threw a pop up at me saying something along the lines of "You have to restart your system to complete installing updates." So I figured that was probably a good idea and did that. Only to find out that now my Ubuntu cannot find my wireless adapter any more.

Not being a Linux wizard, is there any way to find out what kind of an update was installed to help figure out what went wrong? A kernel update, since it required a reboot?

Here's what happens on boot now:
kernel: [20.213116] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

The wireless adapter is:
Ethernet controller: Atheros Communications Inc. **AR242x** 802.11abg Wireless PCI Express Adapter (rev 01)

And the madwifi driver (that used to work):
srcversion:     D3FD3BD11169A96DBCFF8DE
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
version:        0.9.4

iwconfig doesn't even find the adapter now.

I've had all sorts of trouble with this card, but works fine in Jaunty (touch wood)

What kernel version are you on? Can you boot with a previous kernel to check it works again?

---

### Post by superprash2003 on 2009-04-07
while booting up , grub would give you a list of kernels which you can run.. try with the second option which would usually be the last kernel where your wireless worked..

---

### Post by t0mppa on 2009-04-08
My kernel version is: 2.6.27-11-generic and apparently it hasn't been changed, since grub only shows the recovery mode and that's for the same kernel as well. So, looks like no kernel update.

What I did notice after reading through some other posts in the forum was that when taking a look at the System / Administration / Hardware Drivers, the "Support for Atheros 802.11 wireless LAN cards" from there has disappeared. And when I was following the HOW-TO that fixed my wireless the last time, it specifically said to keep that one active. So, maybe this could be the problem?

---

### Post by t0mppa on 2009-04-08
Turns out it was as simple as grabbing a copy of the latest Madwifi-HAL package and manually compiling & installing that. Google helped me find the answers after I knew what to search for (that disappeared driver). Everything's back on track again.

---

