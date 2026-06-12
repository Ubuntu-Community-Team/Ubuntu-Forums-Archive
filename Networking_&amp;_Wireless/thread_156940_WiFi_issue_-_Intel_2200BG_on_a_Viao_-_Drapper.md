---
title: "WiFi issue - Intel 2200BG on a Viao - Drapper"
date: 2006-04-08
forum: Networking &amp; Wireless
---

### Post by MetalSkin on 2006-04-08
G'day all,

First time I'm posting here so if I'm posting to the wrong area please let me know.

I've got a VGN-A49GP Sony Viao laptop with a Intel 2200BG Wifi onboard.  got drapper installed okay but having problems getting the WiFi to work.

The details on the hardware is (via sudo lspci -v):
```
0000:01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
Subsystem: Intel Corporation: Unknown device 2753
Flags: bus master, medium devsel, latency 64, IRQ 201
Memory at fe9fd000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [dc] Power Management version 2

0000:01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Subsystem: sony Corporation: Unknown device 81cb
Flags; bus master, 66 MHz, medium devsel, latency 64, IRQ 209
I/O ports at 9800 [size=256]
```

Now i've spent all day (6+ hours) trying to get it to work and have learnt quite a bit :D.  Been following the guide on the wiki here (and others):

[https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29](https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29)

The final installation instructions talks about changing /etc/network/interfaces to use /etc/init.d/wpasupplicant start for pre-up, but there are notes in the wiki entry that say this is redunant as apparently it's now automatic.

I have noticed that there is no /etc/init.d/wpasupplicant to call anyway. However If I do:
```
sido wpa_supplicant -ieth0 -c/etc/wpa_suppilcant/wpa_supplicant.conf -Dwext -w
```

I get eth0 associated with the access point as iwconfig shows:
```
eth0      IEEE 802.11g  ESSID:"Sol_g"
            Mode:Managed Frequency:2.457 GHz  Access point: 00:11:50:63:16:F4
            Bit Rate=54 Mb/s   Tx-Power=20 dBm    Sensitivity=8/0
            Retry limit:7       RTS thr:off       Fragment thr:off
            Power Management:off
            Link Quality=89/100  Signal level=-20 dBm  Noise level=-75 dBm
```

If I try and ping the switch I get a 'Network is unreachable", if i try and put it up it says that it's already configured. If I bring it down and up again then the DHCP part fails.

The wiki entry talks about changing the /etc/default/wpasupplicant to enable it automatically and so forth, but comments added have said that this isn't required anymore and the file doesn't exist.

The wiki goes on to talk about enabling DHCP via writing a custom script but But comments in the wiki entry say that its not needed, as its depreciated...

Does anyone know how I should continue?

I'll only install breazy if I have to but I would like to get dapper working.  I only installed dapper to try out Xgl (but that's another story, dont even talk to me about ATI!), but as its generaly okay I would like to stick with it (and maybe get Xgl working too or at least 3D acceleration).

Thanks in advance for any assistance.

:edit: opps just realised this is a breezy section, sorry guys.  can a mod please move this to the appropriate area?

---

### Post by MetalSkin on 2006-04-08
Dont worry, got it sorted out.  figured out my problems this morning.

Seems to be the issue of trying to do it manualy compared to letting the network manager sort it all out for you.  Disabled all my manual fiddling, did an upgrade and rebooted.  lo and behold astounding things happened, my wifi was working!

Very impressed with the dapper nw-applet btw.  actualy the whole networking solution is very nice.  

so it works fine on a Sony Vaio VGN-A49GP!

---

