---
title: "Installing Netgear WG111 v2 Wireless Dongle"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by mikebeecham on 2010-01-26
Hi there,

I've got a Netgear WG111 v2 Wireless Dongle which, when inserted into my ubuntu machine, is recognised when I type LSUSB.

However, I cannot get this to work (in fact I do not know how to check).

Can anyone help get this wireless dongle working please?

Thanks




Mike

---

### Post by The Toxic Mite on 2010-01-26
Hey!

We need some more information; can you post the outputs of the following commands please?

```

lsusb
dmesg

```

Thanks :)

-TTM-

---

### Post by lambengolmor on 2010-01-26
I tried for years to make that thing work... I managed to gain something acceptable with ndiswrapper... Although it was a lot easyer to buy a 20€ linux-compatible dongle... I don't know if things have changed since then...

---

### Post by mayorhigh on 2010-01-27
i read a good review for that adapter and was thinking of buying it. im trying to make sure it will wrk with ubuntu without the need for ndiswrapper tho and read that it works with the rtl8187 driver. have u tried that 1 yet?

---

### Post by lambengolmor on 2010-01-27
I haven't tried it still and I don't have it either for something like a week... If you can wait that long I'll try and see what I get (although there may be someone else out there that have already tried it).

---

### Post by Chris-Chicken on 2010-01-27
Hi there, I too am having issues with this damned dongle....

Using Karmic NBR on an HP mini (1030NR)

Karmic recognises the WG111v2, and uses its native driver, rtl8187.

The dongle's light lights, and the network connection widget displays a list of available networks. I am able to connect to the network, but can download nothing, the connection just times out.

Does anyone have any ideas on getting this to work?

I've tried using Ndiswrapper, but, so far, haven't been able to get a driver to load. I've disabled other drivers using blacklist. 

When installing in the terminal (or the GUI) Ndiswrapper only copies the .inf file to its directory, and not the .sys file. Ndiswrapper then reports that the driver is installed, but doesn't detect the hardware, though it is there when the lsusb command is entered.

Any help at this stage would be marvelous!

Thanks.

---

### Post by lambengolmor on 2010-01-27
Hmmmmmm... Using the rtl8187 can you surf the web? I mean, can you connect to some site and have just a download error (how could that be possible anyway? O.o) or you can't connect to anything in the first place? If that's the case it could be a bug of the network manager, and could (MAYBE!) solved by installing wicd from the package manager (it asks you if you're sure to remove networkmanager, I did and was happy about it, but don't know if it has some inconvenience on particular usages... You can always turn back to networkmanager if you feel it was better)

---

### Post by Chris-Chicken on 2010-01-27
Well, I can connect to the network -(Network manager reports a connection, and displays the mac address, ips etc.) however, I am unable to download any information. Firefox reports "connecting to www.website.com", but times out.... I can't even access the router's control page.

I can use Network manager to connect with my internal broadcom card, so I don't think it's the problem, but I'll give it a try :)

---

### Post by Swagman on 2010-01-27
Are you sure your configuring it correctly ?

I have the same one...

[img]http://farm3.static.flickr.com/2293/2201741164_31258b3279.jpg[/img]

And in both Ubuntu and Mandriva it just  works.. No faffing about required

[img]http://farm3.static.flickr.com/2314/2201002195_869049901a_o.png[/img]


[Edit]

Ok.. I just plugged it in this minute to test it with 9:10

here's the results. (disconnected the wired connection first)

[**Pic ONE**](http://www.upload3r.com/serve/270110/1264606899.jpeg)

[** Pic TWO**](http://www.upload3r.com/serve/270110/1264607002.jpeg)

[** Pic THREE**]( http://www.upload3r.com/serve/270110/1264607078.jpeg)

[ **Pic FOUR**](http://www.upload3r.com/serve/270110/1264607197.jpeg)

There ya go

I also uploaded all those pix using it's  connection (That warmed it up!!)

---

### Post by Chris-Chicken on 2010-01-27
Lambengoimor: I installed Wicd - it didn't change anything, but does have more options than the network manager. :)

Swagman: Well.... as you say, it 'just works' for me too, only nothing will download....apart from that - the dongle is recognised, and can connect to the access point.

Did you configure using Ndiswrapper?

---

### Post by Swagman on 2010-01-27
No.

Just plugged it in and it went !!

---

### Post by bkratz on 2010-01-27
You might want to post the outputs of:

sudo lshw -C network
sudo iwlist scan
ifconfig

---

### Post by lambengolmor on 2010-01-27
Are you trying to connect to an encrypted network? If yes, can you turn down the encryption and see if that way it works? (My card -not the wg111- can't connect to wpa networks without wicd so that could be the problem for having the network "connected" but not working)

---

### Post by Chris-Chicken on 2010-01-27
Thanks bkratz.

Incidentally, I now have both the dongle and my internal card running, as wlan0 and eth1 respectively. Previously I had blacklisted one or the other, but with no discernible difference.

Here's some terminal output:


sudo lshw -C network

```
 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:83:0d:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:33:7b:51:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```


sudo iwlist scan


```
lo        Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E4:27:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001271c7181
                    Extra: Last beacon: 1204ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD1A00037F0301000000000FB5E4274C020FB5E4274C64002C011F08

cwis2phar@Sylvan-Manko:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:E4:27:4C
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:24:B2:AD:26:44
                    ESSID:"AETH"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: Unknown: DD890050F204104A00011010440001011041000100103B00010310470010E2C32A30C3208B483398E04036D3D08C102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1C:DF:C0:3F:E6
                    ESSID:"WLAN"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E4:27:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001290e8548
                    Extra: Last beacon: 1340ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD1A00037F0301000000000FB5E4274C020FB5E4274C64002C011F08
          Cell 02 - Address: 00:24:B2:AD:26:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"AETH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b446ad1e9
                    Extra: Last beacon: 2044ms ago
                    IE: Unknown: 000441455448
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 070A415500010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A00011010440001011041000100103B00010310470010E2C32A30C3208B483398E04036D3D08C102100074E4554474541521023000844473833344776351024000844473833344776351042000A313233343536373839301054000800060050F20400011011001644473833344776352028576972656C65737320415029100800020086
          Cell 03 - Address: 00:19:DB:0B:18:D9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a53f5a06c1
                    Extra: Last beacon: 2028ms ago
                    IE: Unknown: 00024E50
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:1C:DF:C0:3F:E6
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c2739492e
                    Extra: Last beacon: 1920ms ago
                    IE: Unknown: 0004574C414E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00


```

and ifconfig


```
eth1      Link encap:Ethernet  HWaddr 00:23:4e:83:0d:74  
          inet6 addr: fe80::223:4eff:fe83:d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20091 errors:0 dropped:0 overruns:0 frame:17743
          TX packets:15462 errors:139 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25138114 (25.1 MB)  TX bytes:2251161 (2.2 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:938 (938.0 B)  TX bytes:938 (938.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:33:7b:51:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2318 (2.3 KB)  TX bytes:22522 (22.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-33-7B-51-4D-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


Thanks. :)






also, I tried sudo dhclient wlan0



which gave:

```
There is already a pid file /var/run/dhclient.pid with pid 2962
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:33:7b:51:4d
Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Swagman on 2010-01-27
ok.. First one..


```

susan@susans-desktop:~$ sudo lshw -C network
[sudo] password for susan: 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: 00:18:4d:65:50:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.14 multicast=yes wireless=IEEE 802.11bg
susan@susans-desktop:~$ 
```

And scond one..

```


susan@susans-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan3     Scan completed :
          Cell 01 - Address: 00:18:4D:68:00:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"UbuntuNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e064f3d155
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 00095562756E74754E4554
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C

susan@susans-desktop:~$ 
```

And last but by no means least

```

susan@susans-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:c8:9f:52  
          inet6 addr: fe80::211:9ff:fec8:9f52/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36736837 (36.7 MB)  TX bytes:18478375 (18.4 MB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90507 (90.5 KB)  TX bytes:90507 (90.5 KB)

wlan3     Link encap:Ethernet  HWaddr 00:18:4d:65:50:93  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe65:5093/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168670 (168.6 KB)  TX bytes:186072 (186.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-65-50-93-36-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

susan@susans-desktop:~$
```

Hope that helps.... *Someone*

---

### Post by bkratz on 2010-01-27
> **Chris-Chicken said:**
> 

Incidentally, I now have both the dongle and my internal card running, as wlan0 and eth1 respectively. Previously I had blacklisted one or the other, but with no discernible difference.

Here's some terminal output:


Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.




Is the internal one actually working it shows data? I don't know how to turn off one of two but for the no DHCP offers you might look at this thread.

[http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)

---

### Post by Chris-Chicken on 2010-01-27
Well, thanks for the link. I tried commenting out the "rfc3442" lines as suggested in the other thread, but to no avail. I still get the same output for the dhclient command. :(

My internal card connects without any issues, and there's no security on the access point.......if others can use this dongle out of the box, then it must be something simple! I just don't have the knowledge :(

Thanks Swagman.... the only difference I note is that your "lshw -C network" output gives the device an ip address, where mine doesn't......

Any help or suggestions at this point would be very appreciated. :)

---

### Post by Swagman on 2010-01-28
Bump!

---

### Post by Chris-Chicken on 2010-01-29
Bump Bump!!

So - Not being able to solve the DHCP issues, I've tried installing windows drivers using Ndiswrapper. This makes no difference! The same DHCP problem remains..... but my other wireless card works fine.

Is there anyone out there who could make some suggestions on what might be the problem, or where to look?

---

### Post by Chris-Chicken on 2010-01-29
Okay!

Next problem?

I think I've killed the dongle!

Now when I plug it in, there is no light, and it's not detected by Wicd, network manager or iwconfig. :O

It does show up as connected under lsusb, so perhaps I've managed to switch it off somewhere?

I've removed the windows drivers, uninstalled Ndiswrapper, thinking that the native driver would pick back up...... I've made sure that the RTL8187 driver is no longer blacklisted....

I've run Karmic from a live usb, and the dongle works there, just with the same DHCP issues.


Any ideas?

I'm out of depth :o(

---

### Post by Swagman on 2010-01-29
Is there anyway to manually edit lshw -C network?

Perhaps copying in the ip addy in my list ?
Not that it should make any difference as there's 254 it could use!!

btw.. I'm running a NetGear Wireless Router on BT internet

---

### Post by papa15 on 2010-07-06
I bought the wireless dongle for about $10 from TigerDirect.  It arrived, I plugged it in (with a wired connection established) and the computer detected the wireless network.  I entered the WPA password and the connection was established.  Easier than with Windows XP.

---

