---
title: "Wireless connection after 5-10 minutes"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by casklaverstijn on 2009-02-28
Hi,

The last weeks I have problems connecting to my wireless internet on startup. When I trie to connect it doesnt work and it asks for my pass again. Before I used ndiswrapper but when I installed the linux driver the problem was even worse. I have a wireless adapter with a Ralink rt2860 chipset. The driver is from the Deb file rt2860-source_1.8.0.0-3_all. I run Ubuntu 8.10.

I have no sources of interference like dect phones. Other computers (Ubuntu and Windows) in our house work just fine.

My wpa-supplicant log says (this repeats):
```
Trying to associate with 00:21:29:d0:f0:4e (SSID='xxxx' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:d0:f0:4e
Authentication with 00:21:29:d0:f0:4e timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 

```

/var/log/messages:
```
 ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 322
 ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
```
/varlog/syslog:
```
NetworkManager: <info>  (ra0): supplicant connection state change: 0 -> 4 
NetworkManager: <info>  (ra0): supplicant connection state change: 4 -> 0 
NetworkManager: <info>  ra0: link timed out. 

```

These messages can repeat for a long time (5-10 minutes) and then suddenly it connects just fine and stays connected from then on.

Can anybody help?

Greetings and thanks in advance, Cas.

---

### Post by l.e.g.e.n.d.a on 2009-11-27
Hello, I'm having just the same problem on my EeePC 901 with Ubuntu 9.10 netbok remix.
The logs looks like: 
```

NetworkManager: <info>  ra0: link timed out.
wpa_supplicant[1054]: Authentication with 00:00:00:00:00:00 timed out.
wpa_supplicant[1054]: Trying to associate with SSID 'MyWifi'
wpa_supplicant[1054]: Association request to the driver failed
NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating

```

Thank You for your help.

---

