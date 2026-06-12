---
title: "Myth does not tune DVB S or T...VLC does!"
date: 2011-06-01
forum: Mythbuntu
---

### Post by dibuntux on 2011-06-01
Ok people, we have some serious tuning problem going on with tuning DVB in myth, either satellite or terrestrial. 
On some channels, I get the dreaded "partial lock" error. It is not a hardware or driver problem: just changing to VLC (or Kaffeine) the same channels do lock and display perfectly.

I get this error on some DVB-S channels and on some DVB-T channels. So different cards and different drivers.

What can we do to solve this? TIA to all

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI
dibuntux is online now Report Post Edit/Delete Message

---

### Post by klc5555 on 2011-06-01
My own setup is DVB-C, but in my case I tended get partial lock errors on three particular channels on two brands of tuner in mythtv because the signal was too strong. On the specific tuners affected (Hauppauge 1600 with new drivers and AverMedia A180), I had to split the input again to attenuate the signal to the point where mythtv could lock on all stations, including the fatal three.

---

### Post by dibuntux on 2011-06-01
Interesting! In my case, the signal is average at 72-75%, whereas other channels have up to 95% and no problem with partial lock.

And still is a myth problem, since VLC does tune them ok.

thanks!

Any other ideas? Anyone? TIA

---

