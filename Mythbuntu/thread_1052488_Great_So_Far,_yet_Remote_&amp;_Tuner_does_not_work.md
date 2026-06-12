---
title: "Great So Far, yet Remote &amp; Tuner does not work."
date: 2009-01-27
forum: Mythbuntu
---

### Post by GeneralNMX on 2009-01-27
CPU: Dual P3 550MHz
Motherboard: 1997 Supermicro
RAM: 1GB SDRAM
HDD: 60GB WD IDE
Video: ATI Radeon 7000 64MB PCI (works well)
Sound: Some C-Media chipset PCI (has digital out!)
LAN: Generic 10/100
Tuner 1: Avermedia A180 HD ATSC
Tuner 2: Happauge PVR 150 w/ Remote and IR Blaster
DVD Player: Something I pulled out of an ancient Compaq
CD Player: Something I pulled out of a more ancient computer

Well I can play files off my server fine, but the HD-OTA (ATSC) Avermedia A180 HD Tuner card is not receiving any signals. I wiped out Windows XP from this machine where it was working fine with a different motherboard. Channel scanning keeps giving me "Signal Timeout" for each channel regardless of the signal/noise ratio. If I increase the timeout to something drastic like 50000, then I get "no tables". I do not have a grabber setup since the HTPC's user doesn't care what's on; he just wants a little bit of randomness. Do I need to pay for and setup ScheduleDirect just to do the channel scanning correctly? This all worked fine on Windows XP.

Additionally, the Hauppauge PVR 150 I have installed just to use its remote is not working -- the remote, not the tuner. Again, the remote was working fine in Windows XP. I haven't even tried the tuner (I have no analog input for it). I tried setting it to "custom" and pointing it directly to the Hauppauge configuration file with no go. Setup as /dev/lirc0, yet if I do "ls /dev/lirc0", that file doesn't exist. 

So I tried going to the prompt and found that lircd was running, but if I did "irw" it would cease. I checked the various logs and no error messages there. I checked dmesg | grep lirc and found something like "lircd: Happauge IR Remote driver loaded: major 61". That's my only message for lirc or lircd. I killed lircd and restarted it with lircd -d /dev/lirc0, and even though it stayed resident in memory, lirc0 still wasn't created. With or without lircd running, there was /dev/lircd. I did some googling but most of the solutions were to people who seem to be at a further point then I am. For sh--ts and giggles, I went ahead and did ln -s -T /dev/lirc0 /dev/lircd, but that didn't work either. I double-checked the configuration file and it seems accurate (it was made by Mythbuntu anyway; I changed nothing).

So, any ideas on how to troubleshoot these two problems?

Still, overall, running much smoother on lesser hardware then my hacky Windows setup.

---

### Post by w8iss on 2009-01-27
In answer to your question about having to subsrcibe to Schedules Direct to
get channel listings and all - NOPE!!! The card if working should scan and
find everything just fine without a subscription.

As to WHY your cards are not working properly, I can't say. I am having the same issue with my PVR-150 but I am also using my PVR-150 as a tuner also.
The remote worked before I switched to Mythbuntu from KnoppMyth a month ago.

James W8ISS

---

### Post by GeneralNMX on 2009-01-28
Alright, seems 9.01 Alpha 1 doesn't even properly detect my Avermedia A180 HD Tuner as "DVB". I'll try going back to 8.01.

---

### Post by GeneralNMX on 2009-01-29
OK, 8.01 didn't work, and now 8.10 doesn't detect my Avermedia A180 as DVB anymore. I figured it was a PCI slot problem so I swapped my Avermedia A180 and my Happauge 150. This fixed the remote problem and caused a PCI error on boot. I'll mess around with IRQs, but I don't know if any of this will fix the original DVB-T problem. I might have to manually setup this HD Tuner card.

---

### Post by GeneralNMX on 2009-01-30
Alright I got both cards working at once. There's no problem with them in Windows either, checked with quick fresh install. However the Avermedia HD A180 ATSC Tuner still isn't netting any signals on scan. Despite any signal strength, it always times out. And if I increase the timeout, it gives "no tables". This is for DVB-T on 8VSB.

I guess the only thing left to do is manually input the channels...unless anyone has a better idea.

---

