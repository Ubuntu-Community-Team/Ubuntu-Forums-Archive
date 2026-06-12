---
title: "MythTV lost all network connectivity"
date: 2009-06-13
forum: Mythbuntu
---

### Post by korgman on 2009-06-13
Not sure how it happened, but my onboard network adaptor on my Asus M3N78 Pro MOBO went to hell. I cannot get a link light. The rest of the MythTV box seems to be working, and I really don't want to get a replacement MOBO just because I lost net connection. I also don't have a spare net card lying around that I could throw in.

I have a wireless G network. Is there an inexpensive USB wireless G adapater that will work pretty easy with a Mythbuntu box? All I really need it for is updates and SchedulesDirect.

Its late and I will try to figure out whay happened to the ASUS net port tomorrow. BTW, anyone got any cmd line things I could run to check the HW? (And yes, the Cat5 cable and router port are ok. I took the Cat5 cable out of myth, plugged it into a laptop, got a link light, got the LT on the net, and all was good)

Matt

---

### Post by ian dobson on 2009-06-13
Hi,

Here's a bit of commnd line magic:-

lspci       - Lists all devices on pci bus
dmesg|more  - Lists all the kernel messages
ifconfig    - Lists the status of your network cards

First do a lspci to see if the network card is there. Then a ifconfig to see if the network card is configured. And if your got the time do a dmesg to dump the kernel messages looking for errors/warnings about your network card.

What motherboard is it? Have you changed anything between working/not working (software update/bios update)?

Regards
Ian Dobson

---

