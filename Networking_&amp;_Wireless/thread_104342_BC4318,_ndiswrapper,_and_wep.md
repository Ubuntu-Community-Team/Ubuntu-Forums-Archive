---
title: "BC4318, ndiswrapper, and wep"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by amp_man on 2005-12-15
I've got an HP Pavilion ze2000-series laptop, with an integrated broadcom 4318 wireless card. I had this card working without encryption using ndiswrapper 1.1 (from the ubuntu repositories), but whenever I tried to set a WEP encryption key through (sudo) iwconfig or using the gnome utility, it would simply not be able to connect to the network, no packets would be exchanged. I should probably mention that I'm using the drivers from the HP website, as the asus one that everyone on the ndiswrapper wiki links to appears to either be down or the version/filename has changed. 

So, to make a long story short, after that I removed ndiswrapper-utils from apt-get and tried a few other versions of ndiswrapper, 1.7, 1.6, and 1.5, none of which worked, and now I can't get the original version to work again. I can install the windows driver just fine, and ndiswrapper -l recognizes the driver and the hardware both, but whenever I try to load the module, I get "FATAL: Module ndiswrapper not found." Any suggestions?

EDIT: okay, after reinstalling the kernel and restricted modules, I have the ndiswrapper module back up and running, but I'm still not getting any response from the card when I try to set parameters. Here's what I mean:

```
amp@amphpmobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

amp@amphpmobile:~$ sudo iwconfig wlan0 essid home
amp@amphpmobile:~$ sudo iwconfig wlan0 ap auto
amp@amphpmobile:~$ sudo iwconfig wlan0 mode ad-hoc
amp@amphpmobile:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
```

No matter what I do, I still get this same response. If I turn off my router's encrytion, I can connect to it, but iwconfig will still report off/any as the essid. Does anyone have a copy of the bc4318 driver from the asus website that I can try, or know where I can get it? Thanks

---

### Post by dbindner on 2005-12-16
According to the iwconfig documentation (somewhere) you can't set the ESSID until after you have set your WEP key.   This was my expericence.  As soon as I set the key, my access point was automatically found and the ESSID appeared.  I didn't have to set it at all.

Set your key first.  Then try to make progress on the other parameters.

---

