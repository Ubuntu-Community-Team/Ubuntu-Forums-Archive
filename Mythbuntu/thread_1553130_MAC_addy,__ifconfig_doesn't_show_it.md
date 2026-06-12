---
title: "MAC addy,  ifconfig doesn't show it"
date: 2010-08-14
forum: Mythbuntu
---

### Post by wilma92010 on 2010-08-14
Hi!

I have a Mythbuntu system that I use to transcode videos that is identical to one connected to my TV (which is the only one with the TV related hardware).   I use ffmpeg and it is setup to do mp4 encoding (h.whateveritis) and works great.

I decided to swap in a new motherboard, hoping that it would work without having to re-install, but no big deal if it didn't -- I'd just re-install Mythbuntu and so forth.

The only thing that failed was the networking.   It doesn't recognize the built-in NIC, and from looking at the networking setup, I am assuming that it cannot find the device with the old MAC addy.  So, I deleted the network interface instance with the old MAC addy and tried to install a new one, but it is clearly not PnP or whatever, it accepts the entry without the MAC address, but doesn't connect.   So, my plan is to enter the correct MAC address and perhaps this will work.  

So, how do I find the MAC address, when ifconfig shows only the loopback device?   I've looked at the BIOS but don't see it.

Is there a Mythbuntu (or other) method/utility for determining the new MAC address?  

Thanks,

Wilma

Please accept my apologies if this is considered off-topic here.

---

### Post by ian dobson on 2010-08-14
Hi,

First of all what network card is it (lspci should show it).

ifconfig lists all eth devices known to the system.

It sounds as if the ethernet card (maybe onboard) is not being detected my mythbuntu. 

Regards
Ian Dobson

---

### Post by wilma92010 on 2010-08-14
Thanks, Ian.

lspca (didn't know/forgot this command) did not show an eth card, so I checked the bios again and it was disabled. I missed this the first time I looked!.  

Re-enabled it and works great.

Wilma

---

