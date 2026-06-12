---
title: "Wireless hangs (2200BG)"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by firstline on 2009-11-19
Hi all, new to Ubuntu;

I'm running 9.10 (upgraded from 9.04) to breathe new life into a Thinkpad R31. This particular machine didn't come with a wireless card. After having issues with an ACX111 based PCMCIA card, I've got it a new Intel 2200BG mini-PCI wifi card.

At the moment it's installed without antennas as they're in the post (could this be my issue?). I thought I'd test things out and see if things look promising.

It's picked up in lspci as running with ipw220 drivers.

Located around 2 metres from the AP, my wireless network is visible and it connects fine (WPA2). It'll download anything (testing it out grabbing additional packages - good speed) but after a short while, the computer hangs. Mouse won't move, screen freezes, needs a hard shutdown. The same thing happens with wireless security disabled at the AP. 

My biggest problem is that, being new to this, I really don't know where to start finding out what's wrong. I'd appreciate any suggestions. 

It's currently setup to dual boot into XP - no such problems there, admittedly haven't downloaded anything at serious speed in XP yet.

Any suggestions?

---

### Post by firstline on 2009-11-19
Any takers?

Are there any logfiles I could start going through for a start?

---

### Post by simonroyal on 2011-01-08
hi, this is a problem with the r31 and the 2200bg wireless card. i too had the same problem under ubuntu 10.10.

the machine would lock up within minutes of being on. removed the card, problem solved. i am using one in the pcmcia slot instead with no problems.

simon

---

