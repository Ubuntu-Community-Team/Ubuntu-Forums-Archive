---
title: "No sound after upgrade to Natty"
date: 2011-05-18
forum: Multimedia Software
---

### Post by pfischer on 2011-05-18
I have an Acer Aspire 8930G with a Realtek ALC889 integrated sound card.
I got sound working in previous Ubuntu releases by adding these two lines to /etc/modprobe.d/alsa-base.conf:
[FONT=Taz]alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto[/FONT]
 
After upgrading to Natty, sound didn't work anymore. I tried some solutions spread over the internet and at some point Ubuntu stopped detecting my sound card. It shows no devices in sound preferences and lspci -v doesn't show my sound card.
Alas, I did not record my attempts to get it all working :redface: and I don't know at what point I 'lost' my sound card.

Any suggestions on how to get it all working again?

---

