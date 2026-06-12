---
title: "encrypted wlan not working jaunty"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by purth on 2009-04-24
Hello

I updated to jaunty plus kde 4.2.2 yesterday and my wlan stopped working. I'm using knetworkmanager to manage my networks. It still connects fine if the network is unencrypted, but if i encrypt my wlan with wpa it doesn't even try to connect anymore. 

I have a Dell Inspiron 6400.

```
lspci
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

```
iwconfig
wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:13:02:88:5f:86
          inet6 addr: fe80::213:2ff:fe88:5f86/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:323155 (323.1 KB)  TX bytes:75450 (75.4 KB)

```

thanks in advance
purth

---

### Post by jimbob on 2009-04-24
Take a look at the release notes for Jaunty.   There is a note regarding a bug in wpa on the KDE version I think.
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by jbrid on 2009-04-24
I am also having issues connecting via WPA in Kubuntu 9.04. It seems that it won't accept my pass-phrase. 

- I click the Network Management icon
- click my SSID
- Enter the pass-phrase and it immediately says "connection failed"

I can connect to wireless routers that have security disabled. I am using the LiveCD at the moment. I can connect without issue using the Ubuntu 9.04 LiveCD. Also, I had no problems connecting to the same wireless router with 8.10 (KDE or GNOME). 

I read the bug report in the last post, but that seems to apply to a missing network management widget.

Anyone else having WPA issues with Kubuntu 9.04????

---

### Post by jimbob on 2009-04-24
Take a look at the release notes two down from the widget one.
It is about connecting with wpa2.

---

### Post by purth on 2009-04-24
I missed the new networkmanager applet in jaunty. I was still using the knetworkmanager applet from kde 3. With the networkmanager applet everything works. Although I wonder why knetworkmanager is not working anymore. 

purth

---

