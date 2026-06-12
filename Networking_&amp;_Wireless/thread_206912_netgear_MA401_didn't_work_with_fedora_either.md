---
title: "netgear MA401 didn't work with fedora either"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by ZimShady on 2006-06-30
I have tried pretty much everything in getting this notebook card to work. I have no idea why it isnt working, but I do know that it didn't work in Fedora Core 5. I have tried DHCP, but it won't get a DHCP address from the router. I have tried static, but that doesnt seem to work either. Whats wierd is this card worked fine in windows, so I know its the operating system.

---

### Post by timefortea on 2006-07-01
I have been having a lot of pain with this card as well. It is connecting to the AP ok but refuses to work with DHCP or a static IP. Last night though, *it started working* and I used it for a while, downloading updates and extra packages. When I booted this morning, it refused to work again. What I did before it started working, was change the interface in /etc/iftab from eth1 to wlan0. It is still configured like this but of course no longer works as before...

My output from iwconfig:

wlan0     IEEE 802.11b  ESSID:"HOUSE"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:3F:EC:20
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:restricted
          Power Management:off
          Link Quality=28/92  Signal level=-69 dBm  Noise level=-138 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:30:AB:17:11:45
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

dmesg:

[17180496.880000] pcmcia: registering new device pcmcia0.0
[17180497.092000] eth1: Hardware identity 800c:0000:0001:0000
[17180497.092000] eth1: Station identity  001f:0006:0001:0003
[17180497.092000] eth1: Firmware determined as Intersil 1.3.6
[17180497.092000] eth1: Ad-hoc demo mode supported
[17180497.092000] eth1: IEEE standard IBSS ad-hoc mode supported
[17180497.092000] eth1: WEP supported, 104-bit key
[17180497.092000] eth1: MAC address 00:30:AB:17:11:45
[17180497.092000] eth1: Station name "Prism  I"
[17180497.092000] eth1: ready
[17180497.092000] eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[17180497.504000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

When I run /etc/networking restart it just loops trying DHCP then says it got no offers. I wonder is something missing somewhere, some driver that it needs?
BTW the AP is working fine with another wireless laptop, and it used to work with this laptop when it had Windies on it.

Any ideas anyone? I am pulling my hair out with this issue.
Thanks.

Chris.

---

### Post by nexus_6 on 2006-08-10
I'm having just the same trouble here, the card worked for a while and then suddenly stopped to do so, looping DHCP requests and so on :(
i have always experienced problems with netgear products and cannot suggest them for anyone :mad:

---

