---
title: "Erratic Browser Behaviour: &quot;Reload, Work Offline&quot;"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Jaecyn42 on 2010-06-29
Ever since upgrading to Lucid, I've had some erratic browser behaviour.  Some pages load immediately (Google, Ubuntu Homepage).  Some pages load only load partially (loading bar gets close to full and then stops).  Other pages do not load at all.

I've found that, with pages that only load partially, I can coerce the page to finish loading through a combination of reloading the page (Reload button or clicking the address bar and hitting enter) and disabling the WiFi connection (Work Offline, Disconnect in Network Manager or toggle switch on laptop).

This behaviour is consistent in all browsers (FF, Chromium, Konqueror, Opera) and sometimes seems to affect non-browser connectivity  (when downloading packages or reloading repositories in Synaptic).

I've been keeping an eye on the forums to see if a fix crops up.  So far, nothing has worked.  Ipv6 is disabled, I have tried the wireless backports.  I have tried tinkering with different Flash Plugins (just a wild theory).  I've even tried a fresh install. I'm out of ideas.  Any suggestions?

ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:16:36:94:b7:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:e3:86:62:68  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164951812 (164.9 MB)  TX bytes:12365411 (12.3 MB)
```

lspci:

```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

Wireless driver is ath5k.

---

### Post by Sonsum on 2010-06-29
Just curious, does this happen while on ethernet?

---

### Post by Jaecyn42 on 2010-06-29
Good question. Believe it or not, I never tried connecting it via Ethernet until now.

Sure enough, problem disappears when connected via Ethernet.

---

### Post by Jaecyn42 on 2010-06-30
bump

EDIT:

To clarify, this problem is isolated to my laptop's wireless.  Problem does not persist when connected via Ethernet, nor does the problem affect my desktop.

Any ideas?

---

### Post by Jaecyn42 on 2010-06-30
Ok, Sorry for the triple post here, but I just noticed something.

I just tried running: lspci | grep Network    No results.

Upon closer inspection of the above output from lspci, I noticed that my Wireless card is listed as an Ethernet Controller.

So there is no Network Controller listed and, for some reason, the computer thinks my Wireless card is an Ethernet card.

Could this have something to do with my problem?  Or is it irrelevant?

---

### Post by Sonsum on 2010-07-02
> **Jaecyn42 said:**
> Good question. Believe it or not, I never tried connecting it via Ethernet until now.

Sure enough, problem disappears when connected via Ethernet.

Have you tried updating while on Ethernet? Maybe the problem has been fixed since the release!

---

### Post by Jaecyn42 on 2010-07-02
This problem hasn't completely prevented me from updating.  Sometimes Synaptic hangs, temporarily, but I'm still able to eventually get the updates.

So far, there hasn't been an update which fixes or mitigates this issue.

---

### Post by Jaecyn42 on 2010-07-03
*crickets chirping*

Any other suggestions?

I'll take anything.

---

### Post by Sonsum on 2010-07-04
What model is your laptop? (I'm just trying to gather helpful info)

---

### Post by Jaecyn42 on 2010-07-05
Toshiba Satellite L35-S2161

---

### Post by Jaecyn42 on 2010-07-12
Solved.

Stupidly simple solution, I can believe it took me this long to figure it out.

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Toshiba_A105-S2081](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Toshiba_A105-S2081)

Same chipset.  Just downloaded the net5211 driver from the Acer website and installed it with Ndiswrapper.  

Wifi works beautifully now.

---

