---
title: "Recommended USB Wireless Adapter for 12.04 desktop builds"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by RichardNewbie on 2013-01-15
:guitar:

I'm new here, but wanted to pass along this info ASAP for everyone who is building their own Ubuntu 12.04 desktop computer, like I did two weeks ago, and is having trouble getting the wireless connection to work.

Here is what I built (all from NewEgg), and the hardware worked fine with the Ubuntu 12.04 64-bit OS, except for the wireless: 

Box: Rosewill Challenger (Love it!!!)
Mobo: ASUS F2A55-M LK PLUS A55 FM2
CPU: AMD A6-5400K 3.6 G FM2
Mem: GSkill 4Gx2 F3-14900CL9D-8GBS
HD: WD 500 blue
PSU: Corsair CX430
DVD: Asus DRW-24B1ST
Card Reader: Transcend TS-RDP5K

I won't name the two wireless adapters I bought -- one USB, and one PCI-e -- because I don't want to look like I'm blaming the manufacturer, but... they didn't work, no matter how I tweaked the connection information in Wireless Manager. They were recognized, they were supported, they saw the wireless network in my house, but they couldn't make solid contact with it. I tried the USB first, and then I tried the PCI card, but nothing worked. :confused:

So I broke down and bought a third one -- a Panda Mini Wifi USB adapter ($15 from Amazon) -- and it worked immediately, without me having to edit any of the connections using the Wireless Manager. Plug n Play all the way. :cool: 

So based on my experience, I'm giving it a recommendation.

btw: Is there an area in this forum where people who have successfully built Ubuntu-only desktops can share their advice so others can avoid their pitfalls? It seems like there would be a great benefit to pooling people's experience in order to recommend builder systems at the $500, $1000 and $1500 price points.

---

### Post by ahallubuntu on 2013-01-15
> **RichardNewbie said:**
> I won't name the two wireless adapters I bought -- one USB, and one PCI-e -- because I don't want to look like I'm blaming the manufacturer, but... they didn't work, no matter how I tweaked the connection information in Wireless Manager. They were recognized, they were supported, they saw the wireless network in my house, but they couldn't make solid contact with it. I tried the USB first, and then I tried the PCI card, but nothing worked. :confused:

Did you post here asking about your problems?  It's quite common to need to install updated drivers to get your wireless card to work, even in Ubuntu 12.04.  Example: I have a couple of very common Realtek RTL8188/8192CU-based 802.11n USB dongles that "sort of" work in 12.04 - they show wireless networks, but they can barely connect, if at all.  But downloading/installing the latest driver from Realtek's website fixes the problem completely and gives me solid, reliable connections.

> **RichardNewbie said:**
> So I broke down and bought a third one -- a Panda Mini Wifi USB adapter ($15 from Amazon) -- and it worked immediately, without me having to edit any of the connections using the Wireless Manager. Plug n Play all the way.

Can you give a more specific model number?  Better yet, please type the command

```
sudo lsusb
```

in a terminal window and paste the results (or just the one line if you can find the one related to the Panda wireless card).  That will tell us which chipset you found worked well automatically, so that will help people who buy other cards (not just made by Panda) with the same chipset.  The chip is what's really important.

---

### Post by RichardNewbie on 2013-01-16
Here's the info from the lsusb command:

Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

Hope that sheds some light.

---

