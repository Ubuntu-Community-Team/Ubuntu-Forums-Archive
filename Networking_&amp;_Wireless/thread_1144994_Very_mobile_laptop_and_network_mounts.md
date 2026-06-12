---
title: "Very mobile laptop and network mounts"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by pwaldo on 2009-05-01
Hi all,

I have a laptop that travels with me to work as well as being used at home.  I have a number of network CIFS mounts that I like to have available when I am at home, so I have them set to "auto" in /etc/fstab.  When I am at work, I use a Mobile Broadband card to connect to the Internet.  When at home, I typically use Ethernet.

The problem is that when I shift locations, I need proper handling of those network mounts.  Typically, I will suspend my laptop at home, come into work the next day, and resume the laptop with the Broadband card.  The problem is that I am now on a different network, and those CIFS shares are no longer available, causing most operations to hang.  I typically have to hard restart the laptop in order to gain proper functionality.

I have tried using noauto in /etc/fstab, but then I have to manually connect the CIFS shares at home.  I still have to remember to manually disconnect them before suspending at night.

I would think this is not an uncommon usage scenario.  Does anyone have any insights as to handle this seamlessly?  Thanks in advance!

---

