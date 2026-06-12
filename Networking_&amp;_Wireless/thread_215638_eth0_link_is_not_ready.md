---
title: "eth0: link is not ready"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by ubub on 2006-07-14
Hi, I've just upgraded from breezy to dapper and my wireless networking stopped working. It's a Linksys WPC11v3 PC card (in a Thinkpad T20), but maybe it isn't actually the wireless that isn't working, because the output from iwconfig looks OK (to me at least), the signal strength meter looks OK too and the access point is found. 

The only indication that anything is wrong is a single line in messages:

> Jul 14 13:39:45 localhost kernel: [  719.141936]ADDRCONF(NETDEV_UP): eth0: link is not ready


And in the Network Monitor app. there is a triangle with an "!" in.

I searched a bit about this message, but only found stuff where people had multiple ethX interfaces and the naming was getting screwed up. I don't think that applies here though, as I only had this one interface.

Since then I tried using an old wired ethernet PC card instead of the wireless one and that works fine (shows up as eth1), and networking works.

Here's the output from iwconfig:

> think:~ > sudo iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b  ESSID:"hecb57so"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.452 GHz  Access Point:00:06:25:54:24:71
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:48/92  Signal level:-52 dBm  Noise level:-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

