---
title: "Cant get my soundcard working"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by Shrimpen on 2007-03-15
Hi guys, Im new to this forum but I hope someone can help me with this one..

I recently installed Ubuntu 6.10 Edgy and I really love it. I got everything working except my sound card.  When I type "lspci | egrep audio" in a terminal, I get:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)

I've looked at sound settings and my sound is not muted.

---

### Post by reclusivemonkey on 2007-03-15
Do you have two souncards; one PCI and on On-Board? If so, go to your Sound Preferences and you should be able to choose the card you have your speakers plugged into.

---

### Post by Shrimpen on 2007-03-15
> **reclusivemonkey said:**
> Do you have two souncards; one PCI and on On-Board? If so, go to your Sound Preferences and you should be able to choose the card you have your speakers plugged into.
I've tried to choose to use my Creative sound card before but that haven't solved the problem. But anyhow, I just got it working now by disabling the integrated sound card in Bios :) 


Now the only trouble is to get the surround speakers and the subwoofer to work proper.. Maybe that's not a possibility?

---

