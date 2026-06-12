---
title: "linksys wmp54g with rt61 chipset doesn't work"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by shoffman11 on 2006-07-12
I've been trying for the last three days to get my Linksys WMP54g wireless pci card to work in Ubuntu 6.06.  I've read the how-to on the forum and the wiki and neither work for me.  I'm using the default Ubuntu 2.6.15-26-k7 kernel.

I think the driver works fine because the card does show up in ifconfig:
> ra0       Link encap:Ethernet  HWaddr 00:16:B6:58:3F:71
          inet6 addr: fe80::216:b6ff:fe58:3f71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000
          RX bytes:515609 (503.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:177
iwconfig shows this:> ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:6  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/70  Signal level:-39 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I read the readme that comes with the Ralinktech driver and configured /etc/Wireless/RT61STA/rt61sta.dat as follows for my network:> [Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
SSID=1337h4x0rz0rz
NetworkType=Infra
Channel=0
AuthMode=WPA2PSK
EncrypType=AES
DefaultKeyID=1
Key1Type=0
Key1Str=10_CHAR_WEP_KEY
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=############# MY WPA2 PSK KEY ########################
...

I tried the card in Windows and it works fine, so I'm having software issues.  I'm going to try turning off all security on my wireless router (wrt54gl) and see if I can connect then.

Can anybody give me some info about what I should be doing differently?

---

### Post by fabiand on 2006-07-13
Did you try to configure this network via the network-administration tool?

---

### Post by shoffman11 on 2006-07-13
Thanks for the reply.  Yes, I did try to connect with the network administration tool in System->Network, but I still cannot connect.  I've tried to connect with all security disabled on the router and I still cannot connect :(.  My network shows up in the list when i run *iwlist ra0 scan*.

Any other advice?

---

### Post by mikepee on 2007-12-12
I'm having a similar problem but have narrowed mine down to a misread by the adapter of the network settings.

On my laptop with the iwlist [apdapter] scan command I get

```
                    Address: 00:15:2B:92:AC:10
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    Extra: Last beacon: 2764ms ago

```

but on the desktop running the wmp54g I get:

```
                    Address: 00:15:2B:92:AC:10
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal Level=-62 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s  
                    Extra: tsf=0000003263f87935

```

Two things to note here:
One card, the one that works lists the encryption correctly, as off.  Also the ESSID, which is hidden, is listed as "" not hidden as well as the Protocol us listed, I assume it's a feature of the intel hardware.  I believe the LT has an Inter Wireless Pro 2200BG.

The other fact is I'm at a hospital trying to connect to there network, they could give a crap about Linux and they're not reconfiguring their network for me.  So it's up to us to solve this.  I have a friend bringing by a D-Link card but I fear the D-Link card uses the same damn driver which would be the same damn problem. 

Every time I try to connect with the connection manager it demands put in a key, for which there is none.  I tried a full manual connection command with no luck.

That would be as follows:

```
sudo iwconfig wlan0 essid "hfhguest" key off ap 00:15:2B:92:AC:10
```

No luck.

I hope someone out there is smarter than I am.

Mike

---

### Post by charwhee on 2007-12-12
There are some good how-to's on this forum for dealing with the RaLink RT61. This chip cannot be configured using network manager, and the rt61pci driver provided in Ubuntu will not work, but Ralink does have a linux driver that works, so you have to (a) disable the existing driver (b) download the rt61 driver and (c) configure it.

---

### Post by charwhee on 2007-12-12
You can tell that you're on the right track because your RT61 will show up as ra0 or ra1, NOT wlan0.

---

