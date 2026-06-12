---
title: "Newbie:  Wireless networking from Ubuntu??"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by OldMac on 2006-01-03
Hi guys,

x86 system with both XP Home and newly installed Ubuntu 5.10.

Sees all of my hardware, and uses it appropriately, EXCEPT my WiFi card.

NIC is a D-Link DWL 520+ (22Mbps).

Router/modem combo is a D-Link DSL 604+

I am posting this from the same machine booted into XP, and my iBook can see the router/modem/internet as well via its Airport card. So I know the hardware is all working as it should be.

Device Manager in Ubuntu can see the NIC and reports all the appropriate bits & pieces. I've set all options to what they should be in order to see the router/modem and the internet beyond.

However, nothing running under Ubuntu can see the internet. I can't even log into the router's HTML based config page. PING-ing the router also fails (100% packet loss).

Evidently the NIC is not talking to Ubuntu. The access-point MAC is returned as a string of zero's.

I'm assuming the system is missing a driver layer...

I'm hoping not to have to play with ndiswrapper...

Am I too hopeful? =)

I can conceivably plug the machine into the router with CAT-5 cable but it will be a pain (it's a bit isolated from the router).

Is there anything else obvious I'm overlooking or is it simply that Ubuntu needs some drivers installed for this particular NIC? And will I have to fart around with ndiswrapper to install them? And last but not least, if I download ndiswrapper on another machine (or this one under Windows) dump it and the drivers onto a USB flash drive and then boot Ubuntu.... can I install ndiswrapper and the NIC drivers from there?

Cheers,
Chris

---

### Post by OldMac on 2006-01-03
UPDATE TO THE ABOVE...

Did an "apt-get install ndiswrapper-utils" which seemed to install okay.

Downloaded and installed the appropriate Windows-XP drivers for my wireless network card.

Ndiswrapper reported a successful nistallation of the driver, and running it with the -l argument gave a report of both driver and hardware installed ok.

"iwconfig" still reports an accesspoint address of 00:00:00, etc...

I still can't ping my router

I still can't see the internet

Identical settings (DHCP) on the wired/cat-5 connection are working fine.

What am I missing / overlooking??

Thanks,
Chris

---

### Post by funkydan2 on 2006-01-03
What sort of encryption does your network have?

I use a 650+, which works fine with my WEP enabled accesspoint.

Did you put in all the necessary info (essid, WEP key) into the gnome network-manager?

Can you post your /etc/network/interfaces file here (but you can replace your WEP key and essid with x's if you like).

Unless you NEED WPA security, the included driver in the kernel should do fine.

---

