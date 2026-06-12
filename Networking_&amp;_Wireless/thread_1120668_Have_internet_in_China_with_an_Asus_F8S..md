---
title: "Have internet in China with an Asus F8S."
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Sultan Rahi on 2009-04-09
Hello*,

I'm living in China and have a Asus F8S (laptop) with Xubuntu Jaunty (update of Ubuntu ]Feisty ). I don't have Windows.
The wifi is working but not internet (except one hour a day from a neighbour,s router I guess).

I want to be able to use internet:
1- With a modem.
2- or/and with the wifi.
3. or/and with my other computer, which has internet, via ethernet link or router (Mercury MW54R).

Nothing work. It's in Chinese and made for Windows.

Problem &#9312;: everything works for pppoeconf, but plog gives:
```
michael@michael-laptop:~$ plog
Apr  8 14:03:04 michael-laptop pppd[8556]: Remote message: [Code 9]: MAC address out of setting range
Apr  8 14:03:04 michael-laptop pppd[8556]: PAP authentication failed
Apr  8 14:03:10 michael-laptop pppd[8556]: Connection terminated.
Apr  8 14:03:10 michael-laptop pppd[8556]: Modem hangup
Apr  8 14:03:14 michael-laptop pppd[8168]: PPP session is 3787
Apr  8 14:03:14 michael-laptop pppd[8168]: Connected to 00:30:88:01:a2:12 via interface eth0
Apr  8 14:03:14 michael-laptop pppd[8168]: Using interface ppp0
Apr  8 14:03:14 michael-laptop pppd[8168]: Connect: ppp0 <--> eth0
Apr  8 14:03:14 michael-laptop pppd[8168]: Remote message: [Code 9]: MAC address out of setting range
Apr  8 14:03:14 michael-laptop pppd[8168]: PAP authentication failed
```


ifconfig gives:
```
michael@michael-laptop:~$ ifconfig ppp0
ppp0      Link encap:Protocole Point-à-Point 
          POINTOPOINT NOARP MULTICAST  MTU:1492  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
```


And:

```
michael@michael-laptop:~$ lspci | grep -i net
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```


The first eth (eth0) of the destop computer doesn't work too (I use the second one for internet) and gives:

```
~$ plog
Apr  8 14:08:07 Zeus pppd[20473]: Using interface ppp0
Apr  8 14:08:07 Zeus pppd[20473]: Connect: ppp0 <--> eth0
Apr  8 14:08:07 Zeus pppd[20473]: Remote message: [Code 9]: MAC address out of setting range
Apr  8 14:08:07 Zeus pppd[20473]: PAP authentication failed
Apr  8 14:08:07 Zeus pppd[20646]: Connection terminated.
Apr  8 14:08:07 Zeus pppd[20646]: Modem hangup
Apr  8 14:08:13 Zeus pppd[20473]: Connection terminated.
Apr  8 14:08:13 Zeus pppd[20473]: Modem hangup
Apr  8 14:08:14 Zeus pppd[6395]: Timeout waiting for PADO packets
Apr  8 14:08:14 Zeus pppd[6395]: Unable to complete PPPoE Discovery
```


```
michael@Zeus:~$ lspci | grep -i net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
01:05.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
```


Problem &#9313;:
Wifi card: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Problem &#9314;:
No idea what to do.

Help!!!

---

### Post by superprash2003 on 2009-04-09
some ISP's use MAC filtering.. from your first output.. it seems to have rejected your MAC.. you need to speak to your ISP..

---

### Post by Sultan Rahi on 2009-04-10
I will. Thank you.

The modem (&#9312;) is working. I change the MAC like that:
```

 sudo ifconfig eth0 hw ether 00:e0:e2:00:c5:21
```

I suppose I will have to do it again after a reboot, but it's o.k. for me. I will ask the school to add this address if it's possible.

Still don't know how to use the router though.

So:
&#9312; Yes.
&#9313; Maybe: I will try what they said on the Chinese forum.
&#9314; No.

---

