---
title: "Sharing internet over bluetooth with Lucid"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by anquetil.n on 2010-05-25
Hi,

I have been looking for a solution to an apparently simple problem, but could not find anything for Lucid.
All solution I found imply modifying files that apparently don't exist anymore (/etc/default/bluetooth, /etc/bluetooth/hid.conf, ...)

So:
I have an old laptop running Xubuntu (lucid). Internet card is dead but it has a bluetooth adapter in the USB port.

I also have another laptop with internet, wireless, and bluetooth on board.

How can I configure both so that the first access the internet trough the second?

- Internet works on the second (of course!)
- Bluetooth work on both, I can pair them and send file from one to the other (although I cannot browse them, but it seems to be an unrelated problem)
- I have blueman on both and tried to configure it to do what I want but it did not work (old computer has a bnep0 interface, but no address for it)
- Old laptop sees "Network access point" and "group network" as bluetooth services of new laptop (although I did uncheck "group network" in the local services setting on new laptop)
- as I said I looked on the web but only found solutions that appear to be designed for older versions of Ubuntu because they refer to non existing files on my two laptops.


hummmm,
that's about it I believe.
If you could provide some help...

thx

nicolas

---

### Post by Teracis on 2010-05-26
I also am working on a solution which requires the editing of /etc/default/bluetooth Which does not exist anymore. Where can I find the equivalent?

EDIT: This may work, testing now. Last post by Mevos says to just create the file (/etc/default/bluetooth) with the appropriate lines and the program will use it.
[http://ubuntuforums.org/showthread.php?t=1316959](http://ubuntuforums.org/showthread.php?t=1316959)

EDIT2: This didn't work for my keyboard, might still work for you though.

---

### Post by simple_2k3 on 2010-05-26
In Karmic there was a little box that you could check when pairing the devices that said "connection to the internet through this device" or something to that effect.  It has since disappeared in Lucid and I haven't been able to find it.

---

### Post by anquetil.n on 2010-05-28
OK, I succeed yesterday night.

From what I recall, this is what I did:
- on the new laptop (gateway) I used blueman-manager to configure the local service "Network Access Point (NAP)" (i.e. I tick the selection box)
- on the old laptop (client) I used blueman-services (because it is Xubuntu, I have to call it from the command line) to configure  the local service "Group Network"
- then I connect the two laptops together using blueman (from the old laptop) and selecting the NAP service of the new laptop

At this point, the new laptop had an interface configured (pan1 if I remember well, but bnep0 was involved too ....?) with an internet address (192.168.20.1 if I remember well)
However, the old laptop had a bnep0 interface with no address so I added it manually:
- sudo ifconfig bnep0 192.168.20.2 up

At this point the two are able to communicate: "ping 192.168.20.1" from old laptop and "ping 192.168.20.2" from new laptop both work
So the rest is "normal network setup as far as I can tell.

Specifically, I manually set up a gateway on old laptop:
- sudo route add gw 192.168.20.1 bnep0
(or something similar)
- create the file /etc/resolv.conf on old laptop (it did not exist yet) and put the same DNS has found in this file on new laptop
- added the new laptop name in /etc/hosts because it was complaining it could not find it

and voila, more or less.
Synaptic did not work at this point, but "apt-get install" did so I am not sure what's going on, but it is enough to fulfil my needs.

As I did many attempts, I am not sure if this is enough or not.
For example, I did some editing of /etc/bluetooth/network.conf (on both computers) but as I remember, it was only to un-comment things that were defaults anyway (like "Interface=bnep0")

good luck everybody

---

