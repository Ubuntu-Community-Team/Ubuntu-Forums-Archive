---
title: "Wireless access to windows network using PEAP"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by drjake on 2006-02-06
Hello everybody,

First of i want to say that i'm very pleased with ubuntu linux everything worked right of the start on my NEC centrino laptop.
However since i'm back at school i want to access the school network i need some extra settings. My school uses a wireless network with EAP-MSCHAP v2 and "validate a server certificate" with VeriSign Trustroot marked.
I need to supply my windows credentials to logon at the end.

Does anyone now how to set this up in linux? My wireless network card is detected and works just fine (on wlans without authencation).

In addtion at home i have a wireless network with a hexadecimal key (WPA?) is there anything special i have to setup for this?
Can i use wifi-radar for this?

Sorry for all these questions i hope you can help! 
But still i'm very pleased, i used other linux versions before but not one of them worked right out of the box!

Greetz

---

### Post by sto6ma9ch on 2006-03-06
I was just researching some methods for creating an 802.11 authentication server. I think you may need to look toward a package called "Xsupplicant" or "WPAsupplicant". In either case, try this:

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

I cannot comment as to it's reliability (still working on the server part), but you may find it useful. Let us know if that helps.

---

