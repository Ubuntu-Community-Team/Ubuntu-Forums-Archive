---
title: "unable to get NIC running..."
date: 2005-02-04
forum: Networking &amp; Wireless
---

### Post by twinight on 2005-02-04
I have to apologize right away -- I'm a complete newbie when it comes to Linux for the most part, and have zero experience with ubuntu in particular until this install.

Anyways, the installation went fine which is amazing, a very pleasant surprise.  The problem came about when it was doing autodetection of network stuff.  It found my card fine, a 3com 3c905B 100BaseTX Cyclone, it just ... fails to actually work.  I'm having a hard time describing it because I'm not getting any error messaging of any sort.  Basically, at the Network Settings dialog, I hit activate, and the "Active" checkbox is checked for about 1.5 seconds, then it unchecks itself.  No errors, no messages, it just sort of shuts itself off.

This happens if I use Manual, DHCP or BOOTP, none seem to have made a difference.  I have two of this same card, and have swapped them out to make sure it wasn't the card -- no dice.

I also ran a ifconfig at the request of a friend, but the only information it gave back was for local loopback, and nothing about eth0 (the card is detected as eth0, there is no onboard lan, it's the only thing there).

I'm at a total loss... any ideas or suggestions?  I'd really appreciate it -- ubuntu seems to be working great for me so far and I'd love to keep using it, but being unable to access the internet from that pc, let alone my local lan, is a bit hindering.

Thanks so much for your time!

---

### Post by benkorkor on 2005-02-04
This might be able to fix your problem. remove all entries about your network interface except loopback in the /etc/network/interfaces file. Then go to networking in system configuration and do the network setup wizard. Hope this helps.

---

### Post by twinight on 2005-02-04
No luck there, sadly.  The wizard recognized the lack of data quickly and smoothly, and the process went fine, but the same problem happened -- was 'active' for about 1.5 seconds, then deactivated itself.

any other ideas?  :/

---

### Post by inuchan on 2005-02-05
I'm having the same problem, but mine worked two days ago on a different network.

Check, then 1.5 seconds later, unchecked.

Help?

---

### Post by kleeman on 2005-02-05
Can you find anything useful about the nic by typing "dmesg"?
Also type "sudo ifup" and see what it says....

---

### Post by buttonpusher on 2005-02-05
I had this same issue and I tried to get it to work with a different NIC, but had the same results.  Try to move the NIC to another slot to see if that don't work.  That was my solution to my problem and so far it seems to be working.

Buttonpusher 8-[

---

### Post by inuchan on 2005-02-05
My NIC is a laptop NIC (onboard, probably) and I can't move it.

---

