---
title: "Yet another DWL-650+ not working on breezy"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by emppu on 2006-03-12
my ubuntu 5.10 doesn't seem to be able to use my D-link DWL-650+ wireless card, I've tried Ndiswrapper, and it says everything is OK (driver and hardware present) but  nothing happens. It seems ubuntu can't use the card although it finds it and even recognizes it correctly. Texas Instruments acx 111 54M chipset. I've tried a lot of tricks, and once I got the "link" led lit up(using some guys advice I can't find anymore), but made no further progress. iwconfig gives this output:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"emppu"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
which to me seems ok, aside from it finding no AP...I tried forcing the AP address as the Mac address of the wlan card on my desktop machine that I use as a Wlan AP which forwards everything to my lan-router, and also tried forcing the bitrate to 11 as my desktop only has a 11Mbit card. This setting worked perfectly with windows, and all 4 other computers (of which one is on wlan) still work. The ethernet connection also works perfectly.

---

### Post by funkydan2 on 2006-03-12
My DWL-650+ works "perfectly" for me and I didn't need to install ndiswrapper.

As long as you don't need WPA (WEP works) I'd recommend removing all the ndiswrapper stuff and just running with the drivers that are in the kernel.  The card should come up automatically at boot and it's just a matter of setting up the network settings in either wifi-radar or the gnome-network tool.

I find that the wireless connection is hard to establish if my Access Point's ESSID is hidden, and currently I'm unable to connect wirelessly during boot-up, but it connects easily once I'm running gnome.

Daniel

---

### Post by emppu on 2006-03-12
nope, no luck there...
of course I tried that (twice actually)...
one clean install with the card inserted...installer found it, but it never worked..
one clean install without the card, no success there either...
then ndiswrapper, but still nothing...
latest try, uninstalled ndiswrapper, tried new drivers (the acx100.sourceforge,net stuff) but none of these seem to get any response out of my card..
perhaps the problem lies in the hardware on my laptop (fuijitsu-siemens amilo D, P4 2.8)? 
so still the furthest I've got was getting the link-led to light up...sadly it seems impossible to find the webpage where I read the instructions to get that done..

thx for trying

---

