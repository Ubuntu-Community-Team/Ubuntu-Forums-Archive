---
title: "Problem of wireless connection  Aspire 1640Z"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by foiedecanard on 2011-04-08
Hello,


I have a new installation of Ubuntu 10.10 on my Aspire 1640Z, and since I have it, it's impossible to connect it to the web. I have a wireless connection on a SFR Neufbox (I'm french and it's a french box I guess). I've tried to be connected with a Sagem key. I have another computer with Windows XP, which is connected wireless with the same kind of key.
When I use Network Manager, there isn't any automatic connection : "no network connection" and when I click on the logo of Network Manager, I can't click neither on "<<filaire>> network" nor "wireless network".


I also used Wifi-Radar, but there isn't any connection again. I created a new network on it, with the SSIF, code WPA, MAC.. But there's no connection and when I try "connect" it writes "could not get IP  adress" (even if I'm in DHCP). 
I went to Système > Administration  > Network Tools > Périphériques > Interface ethernet (eth1)  > Configurer > Wireless and I've writen the WPA, SSIF etc. again of my box, without any result.


Here is what I have in the terminal with

> iwconfig> l0 no wireless extensions. 
eth0 no wireless extensions. 
eth1 IEE 802.11bg ESSID:"NEUF_E070 Nickname:"NEUF-E070 
Mode:Managed Channel:0 Access Point: Not-Associated 
Bit Rate: 0kb/s Tx-Power=off Sensitivity=8/0 
Retry limit:7 RTS thr : off Fragment thr : off 
Power Management : off Link Quality:0 Signal level:0 
Noise level:0 Rx invalid nwid:0 Rx invalid crypt:0 
Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon :0Thank you in advance. :D

---

### Post by grahammechanical on 2011-04-08
Bonjour

I am wondering, is this wireless device switched on? The listing from iwconfig says TX-Power=off. And the Signal level:0. Do you need to do anything in the BIOS to activate this Sagem key? I am assuming that it is a USB device.

Could you code nm-tool in a terminal and see if the device scans and finds any wireless networks in range. I do not know if any of this will help.

Regards.

---

### Post by foiedecanard on 2011-04-09
Here is what I get with the code "nm-tool"

```
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unavailable
  Default:           no
  HW Address:        00:16:6F:27:9A:A3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:16:36:44:07:F8

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```I don't know what I have to do with the key. It's a wifi key Sagem WLAN USB 2.0
When I connect it to the USB port, the light doesn't turn green. If you know how I can activate this key with the BIOS, please tell me.

Thank you

---

