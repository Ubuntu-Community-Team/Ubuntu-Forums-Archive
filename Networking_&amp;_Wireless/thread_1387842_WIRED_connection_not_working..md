---
title: "WIRED connection not working."
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by jim_naisium on 2010-01-22
I have two PCs one has Windows XP the other has Ubuntu 9.10 on it, the Windows PC has no problems getting on the Internet (I'm posting this with it) and getting an IP address from the wired router.

The wired router I have is ONLY wired it does not have wireless at all, it is currently setup to hand out IP addresses between 192.168.1.2 and 192.168.1.254.

The Ubunutu 9.10 PC worked great last night surfed all over the place for hours, then finally shut it down last night when I went to bed, shut down appeared to be normal like it always does when it shuts down, then this morning when I booted it up it gave error: "WIRED NETWORK - disconnected you are now offline".

I tried several suggestions that I found in other postings but am still getting the same error.

Anyone come up with a fix for this?

---

### Post by Iowan on 2010-01-22
**ifconfig -a** will probably confirm that the interface (eth0?) has no IP address. [This]("http://ubuntuforums.org/showthread.php?t=1156441") one may be outdated - try it if you like.

---

### Post by barrydirk on 2010-01-22
I have exactly the same problem.Got my adsl router this morning hooked up my acer 1 with UNR and it worked fine. Disconected everything to wire up the rest of the house and now it doesnt work anymore. win 7 and xp work fine I'm on my xp machine now anybody have any help that I wil understand please

---

### Post by jim_naisium on 2010-01-22
Yes Iowan, I am not getting an IP address.

---

### Post by jim_naisium on 2010-01-22
Never mind, just for grins and giggles I tried another network cable even though the link light on the switch was on, when I unplugged it from the MB's ethernet connector (NIC) the link light on the switch went out but the LINK and DATA lights on the NIC stayed on with nothing plugged into it.

I put a NIC in one of the PCI slots moved the cable over to it, booted back up, the error went away and I'm back online again.

Really pisses me off though I just bought this MB less than six months ago for $159.xx, I'm going to talk to a friend of mine who works for Intel and see if there is any way to wake the NIC up.

---

### Post by Iowan on 2010-01-22
Have you checked the BIOS settings - maybe turn it off, then back on (that probably means rebooting a few times).

---

