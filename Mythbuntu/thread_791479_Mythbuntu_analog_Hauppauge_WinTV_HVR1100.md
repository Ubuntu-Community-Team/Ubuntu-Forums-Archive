---
title: "Mythbuntu analog Hauppauge WinTV HVR1100?"
date: 2008-05-12
forum: Mythbuntu
---

### Post by bergqvistjl on 2008-05-12
Hi, im thinking of using mythbuntu with this TV card: Hauppauge WinTV HVR1100. Ive been on linuxtv and i think it works. What i want to know is does mythbuntu accept analog tv signals from hybrid tuners, or will it default to the digital signal? Im in the UK so the digital signal will be freeview.

---

### Post by db260179 on 2008-05-12
If you have the HVR-1100 you should have no problems (so i've been told), but i was unfortunate to have the HVR-1110 - i had to manually find the channels, then import back into mythtv - what a pain!. I gave up in the end and bought a Asus My cinema Hybrid.

You have to set the card up as two seperate cards in mythtv.

Analog will be /dev/video0
and DVB-T will be /dev/dvb/frontend0

> **bergqvistjl said:**
> Hi, im thinking of using mythbuntu with this TV card: Hauppauge WinTV HVR1100. Ive been on linuxtv and i think it works. What i want to know is does mythbuntu accept analog tv signals from hybrid tuners, or will it default to the digital signal? Im in the UK so the digital signal will be freeview.

---

