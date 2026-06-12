---
title: "Problem - WIFI connectivity using iwconfig"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by muthu375 on 2010-06-05
[SIZE=3]_Environment_
OS : ubuntu 2.6.32-21-generic #32[/SIZE]
[SIZE=3]Installed as a VMWare on Windows 2003
WIFI Device: SMC Wireless Dongle

_Problem_
On Inserting a WIFI Dongle. I am able to see the new interface for the wifi interface as WLAN0 from ifconfig. Also iwconfig confirms the same.

i am able to use the iwlist to know the wifi networks.

I have my own router for testing purpose which is configured to work in DHCP mode, I am trying to connect to this wifi router

Then i issue the following set of commands to connect to wifi network.

iwlist wlan0 scan
sudo iwconfig wlan0 essid <mynetwork>
dhclient wlan0[/SIZE]
[SIZE=3]
And I get the following error.[/SIZE]

[SIZE=2][COLOR=Red][SIZE=1]There is already a pid file /var/run/dhclient.pid with pid 4798
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:13:f7:d4:21:03
Sending on   LPF/wlan0/00:13:f7:d4:21:03
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/SIZE]

[COLOR=Black]But If I am trying to connect via "Network Connections" from System/Preferences/NetworkConnections - It is getting connected and an IP is getting assigned for my ubuntu.

I checked in dmesg I get the following messages.[/COLOR]
[SIZE=1]
[ 1215.953664] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1226.936386] wlan0: no IPv6 routers present
[ 1256.773031] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 1290.329935] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 1290.359077] wlan0: direct probe responded
[ 1290.359090] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 1290.361799] wlan0: authenticated
[ 1290.361859] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 1290.370208] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 1290.370216] wlan0: associated
[ 1290.618016] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 1771.150071] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 1771.181026] wlan0: direct probe responded
[ 1771.181040] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 1771.183472] wlan0: authenticated
[ 1771.183536] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 1771.193730] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 1771.193738] wlan0: associated
[ 1771.442942] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 2219.255819] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 2219.282875] wlan0: direct probe responded
[ 2219.282947] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 2219.285640] wlan0: authenticated
[ 2219.285716] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 2219.295150] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 2219.295158] wlan0: associated
[ 2219.540934] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 3741.966469] wlan0: deauthenticating from 00:1a:2b:6a:d9:d2 by local choice (reason=3)
[ 3742.319886] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 1)
[ 3742.516843] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 2)
[ 3742.717048] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 3)
[ 3742.916354] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 timed out
[ 3758.112991] wlan0: deauthenticating from 00:16:38:f2:b2:1c by local choice (reason=3)
[ 3758.250211] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 1)
[ 3758.448130] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 2)
[ 3758.648510] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 3)
[ 3758.848602] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 timed out
[ 3841.976598] eth0: no IPv6 routers present
[ 3921.904544] eth0: no IPv6 routers present
[ 8531.252924] eth0: no IPv6 routers present
[ 9228.961873] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE]


[SIZE=3][COLOR=Black]Can anyone please help me in this regard. I am waiting for your replies eagerly, with both eyes widely open as never before.

Thanks in advance.

Regards

[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Black]Muthu[/COLOR][/SIZE]

---

### Post by Joe of loath on 2010-06-05
Is the AP encrypted or open? The dmesg output looks to me like a wpa_supplicant output.

---

### Post by chili555 on 2010-06-05
> but If I am trying to connect via "Network Connections" from System/Preferences/NetworkConnections - It is getting connected and an IP is getting assigned for my ubuntu.Network Connections is a part of Network Manager. If Network Manager is installed and running on your system, it's very difficult, and often impossible, to connect with manual methods.

You could remove NM and revert to */etc/network/interfaces*, etc., but NM takes care of all that for you.

You can very effectively connect with manual methods ***or*** NM, but probably not both.

---

### Post by muthu375 on 2010-06-05
I removed the NM vide the following command

sudo aptitude remove network-manager network-manager-gnome

Then did a restart  vide the following command

sudo /etc/init.d/networking restart

Then i tried to manually connect again, again the same result.

The AP is not encrypted and it is open.

---

### Post by chili555 on 2010-06-05
Please amend your /etc/network/interfaces to look like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid <mynetwork>
```Then restart networking:```
sudo /etc/init.d/networking restart
```

---

### Post by muthu375 on 2010-06-05
That is really wonderful, great, extraordinary...

Perfect it is now working for me, 

Thank you so much...

---

### Post by muthu375 on 2010-09-13
Hi,

  Now I need a small clarification on connecting to WIFI networks that WPA and WEP encrypted.

I was able to connect to unsecured networks using "Wireless Tools for Linux" namely iwlist and iwconfig.

Can I also connect to WEP and WPA networks using the same tools?

Thanks in advance for your replies.

---

### Post by Joe of loath on 2010-09-13
You can connect to WEP using iwconfig, but you need to use wpa_supplicant for WPA.

---

### Post by muthu375 on 2010-09-13
Thanks for your reply, instead of using wpa_supplicant for connecting to WPA networks we could use iwconfig and iwpriv in combination, is it true?

will it work in all chipsets ?

Thanks for your reply again.

one More question, when i do a scan of wireless networks I get the following o/p,

For one network I see it to be WPA Encrypted, other two are said to be Encrypted but the Type is not shown. 

Does this mean they are WEP Encrypted ? 

root@correcaminos:~# iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:23:F8:70:50:03
                    ESSID:"WLAN_5002"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-60 dBm  Noise level:-88 dBm IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 76:7C:4C:19:3E:6D
                    ESSID:"Touch2"
                    Mode:Ad-Hoc
                    Frequency=2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-88 dBm Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:24:B2:D8:11:DE
                    ESSID:"TogaInfo"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-88 dBm Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s



Thanks for your replies again

---

### Post by Joe of loath on 2010-09-13
> **muthu375 said:**
> Thanks for your reply, instead of using wpa_supplicant for connecting to WPA networks we could use iwconfig and iwpriv in combination, is it true?

will it work in all chipsets ?

Thanks for your reply again.

one More question, when i do a scan of wireless networks I get the following o/p,

<snip>

For one network I see it to be WPA Encrypted, other two are said to be Encrypted but the Type is not shown. 

Does this mean they are WEP Encrypted ? 

Thanks for your replies again

I'm not sure. However, wpa_supplicant is easy enough to use.

You are correct in that the ones stated as being encrypted, but with no information, are WEP. It's to do with authentication and encryption, where WEP has no authentication, only encryption, where WPA has both.

---

### Post by jlanza on 2010-09-17
which dongle do you have? I'm looking for one that also works natively in a virtual machine (VMWARE).

Be glad if you post the model.

---

### Post by Joe of loath on 2010-09-17
I have a 3Com 3CRUSB10075 (It's discontinued, though). It's got a Zydas/Atheros ZD1211 chipset, and works out of the box on pretty much any distribution.

---

### Post by jlanza on 2010-09-17
do you know of any other with Atheros and that is on the market?

Besides that, do PCMCIA cards work on WmWare?

Sorry for the off-topic

---

### Post by Joe of loath on 2010-09-17
I don't know about that, sorry.

---

