---
title: "wireless problem"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by bradstaley123 on 2009-02-10
Hi,

About two days ago I took my laptop to work and connected to the wireless using network manager, but when I got home the network manager would not work.. it detected the wireless network, but could not authenticate.  I tried my XP partition which connected w/o a problem.

The next day I went to my college, and connected w/ the network manager on ubuntu 8.10 there as well, so I downloaded WICD just to try something new, to see if the network manager was the problem.  It wasn't...  

Any ideas at why I can connect anywhere but my own house?  It was random, it has worked perfectly until 2 days ago

---

### Post by RPMurph on 2009-02-10
I am having a similar problem.  My wireless worked great last week... a little burp here and there but overall good.  I tried connecting at home last night and it wouldn't connect.  I disabled the password requirement for the network, but it didn't make any difference.  Now I'm at school and I can't connect to the public wireless network.  I booted up Vista and it connects just fine.

I'm using a HP Pavillon dv6000 with an atheros wireless network card.  I'll post up the configuration in a minute.

---

### Post by bradstaley123 on 2009-02-10
I'm using an acer5610z with an atheros wireless card.

---

### Post by RPMurph on 2009-02-10
Just booted up on ubuntu, and it connected right off.

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

wlan0     IEEE 802.11g  ESSID:"TowsonUguest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:20:4B:C4:90   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1642  Invalid misc:21974   Missed beacon:0

---

### Post by superprash2003 on 2009-02-10
what authentication is used in your home network??WPA? does it keep asking for the authentication password over and over again?

---

### Post by bradstaley123 on 2009-02-10
with the network manage it asked for it after it wouldn't connect, but not the same case w/ WICD

---

### Post by bradstaley123 on 2009-02-10
I'm embarrest to say I fixed the problem.. and it was obvious..  *hangs head*  It needed a WEP hex key and I had it listed as a WAP.. I'm not sure as to how it got put to that setting but it did.  Thanks for the help guys

---

