---
title: "Internet connection problem"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by GARoss on 2010-10-16
I can connect to the internet on Win7 without issue. Boot to Ubuntu 10.10 amd64 & it works sometimes & sometimes it doesn't. 

I've attached 4 screen photos; 2 when internet is working (Working ifcomfig & Working route -n) & 2 when internet is NOT-working (NonWorking ifcomfig & NonWorking route -n).

The 1st I notice when looking @ working ifconfig is line 3 under eth0, **inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0**, is missing on NonWorking ifconfig.

If anyone has suggestions how to troubleshoot please post. Thanks

---

### Post by pricetech on 2010-10-16
Short answer is, you're not getting an IP from your DHCP server.  Try disabling and re enabling the network connection and see what happens.

---

### Post by GARoss on 2010-10-16
It was in the ON position, but, the internet wasn't working @ the time. OFF/ON did nothing.

I booted into Win7; internet was working fine, then restarted into Ubuntu & it was up as the desktop appeared.

I don't get it??? What can be checked with the terminal?

---

