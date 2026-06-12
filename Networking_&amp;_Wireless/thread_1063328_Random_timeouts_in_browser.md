---
title: "Random timeouts in browser"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by letired on 2009-02-07
Alright, here's the background info:
The network is wired, but the configuration is fairly complicated due to my ISP's use of certificates etc. I'm currently relying on [this package](http://www.viciouslime.co.uk/downloads/doc_details/19-university-of-york-nas) which supplies my login details and sorts out the certificates. I can't say I'm sure what it actually does, I haven't looked at the source and probably wouldn't understand enough anyway.

I've been connecting to the network this way since October, and everything was more or less smooth until I went away for a few weeks, used a couple of other networks, and then came back and plugged the computer in back at the university. 

Problem: Now, I'm getting completely random timeouts when loading webpages, that is, sometimes the browser just stops at "Waiting for [host]...". This can happen at any point in the loading of a page if there is more than one host, for example if there's one main host for the webpage and an ad supplier, the page load could stop while loading the ads, and I end up with a timeout error. Refreshing, or clicking the link again, usually works.
This happens every 5-10 page loads, in all browsers but not on my Windows partition. I think the issue is only affecting web browsers although pidgin too has been having connection issues at times.

Well.. suggestions?

---

### Post by letired on 2009-02-08
Bumping for luck

---

### Post by superprash2003 on 2009-02-08
you could try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)  if you still face problems.. post output of ifconfig from the terminal

---

### Post by letired on 2009-02-08
Hrm. Pageloads seem to have sped up thanks to the changes you posted, but on the other hand Spotify, running under wine, didn't like it at all and gives me an error about there being a firewall. Thunderbird can't retrieve e-mails. pidgin seems to be working fine, but I'm going to switch back to my ISP's DNS servers for now.

```
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:c3:2e:df  
          inet addr:1**.**.**.12+  Bcast:1**.**.**.255  Mask:255.255.255.0
          inet6 addr: fe**::2a0:d1**:fec3:2***/*4 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2763 errors:363 dropped:0 overruns:0 frame:0
          TX packets:1151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:363 txqueuelen:1000 
          RX bytes:1344179 (1.3 MB)  TX bytes:226062 (226.0 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.234.1  Bcast:172.16.234.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.44.1  Bcast:172.16.44.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:fa:a2:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-FA-A2-05-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by superprash2003 on 2009-02-10
is thunderbird getting mails from your ISP or a local server?

---

