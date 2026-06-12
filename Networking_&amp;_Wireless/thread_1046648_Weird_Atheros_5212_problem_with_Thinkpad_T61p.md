---
title: "Weird Atheros 5212 problem with Thinkpad T61p"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by letriste on 2009-01-21
Hi, I got my new Thinkpad T61p just two weeks ago, installed Intrepid, got the wireless working and everything was just fine.

But when i tried to connect at my school, I couldn't for some reason neither i nor the network support could understand. The card found the network all right. And when i got home, it still worked. Next day, it was dead. The GNOME Network Manager didn't list any wireless networks, and the wireless light below the screen is not on. Still not working a week later...

Here I've listed the output of some commands. To me (GNU/Linux noo-hoob!!) it looks here like I AM connected, but sadly I'm not. I checked...

```

 $ lspci -nn | grep 'Atheros'
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212 802.11abg NIC [168c:1014] (rev 01)

 $ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:51:CE:3B   
          Bit Rate:54 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=53/70  Signal level=-44 dBm  Noise level=-97 dBm
          Rx invalid nwid:59257  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:02:72:59:E0:40
                    ESSID:"Bikeriders"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:39:2C:53:2A
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-73 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:66:51:CE:3B
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

[COLOR="Red"].
. and on it goes with more networks
.[/COLOR]

pan0      Interface doesn't support scanning.


```

---

### Post by pytheas22 on 2009-01-21
In the output above, it looks like you're connected to a network named 'linksys'.  Did you connect on purpose?  If not, Network Manager must have connected you automatically.

Do you have an IP address as well on ath0 (use the command 'ifconfig' to check)?  If not, try typing:
```

sudo dhclient ath0
```

to request one.  If you have an IP, can you browse the web using the connection to linksys?

You can also clearly see your networks using 'iwlist scan', so I'm a bit puzzled as to why NM won't list them.  Not to insult you, but are you sure you are *left*-clicking on the NM applet in order to see available networks, not right-clicking?  Also, what is the output of:
```

cat /etc/network/interfaces
```

---

### Post by letriste on 2009-01-22
> **pytheas22 said:**
> In the output above, it looks like you're connected to a network named 'linksys'.  Did you connect on purpose?

Not to insult you, but are you sure you are *left*-clicking on the NM applet in order to see available networks, not right-clicking?

Actually, i *did* connect to linksys manually. Heheh, <blush>because i wasn't left-clicking the icon it didn't list the networks</blush>. It was bugging the hell out of me. But then I found out, and it was working for a while. this was before the problem i described above. But now :( nope....

ifconfig shows no ip for ath0, but after running dhclient it does. Still no networks in NM (left-click). And the driver is enabled and so is wireless on right-click. I'm online through eth0, and unplugging the cable leaves me offline with no options otherwise...

```
 $ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by pytheas22 on 2009-01-22
hmmm, that's weird.  You could try reinstalling Network Manager by typing:
```

sudo apt-get remove --purge network-manager
sudo apt-get install network-manager-gnome
```

(If you lose your Internet connection in the middle of this process, just type 'sudo dhclient eth0' to connect on the wired interface manually.)

After doing that and rebooting, are you able to see networks?  If not, please unplug the ethernet cable, connect again to 'linksys' manually, then post the output of:
```

ifconfig
sudo dhclient ath0
ifconfig
wget google.com
ping -c 5 google.com
ping -c 5 74.125.45.100
```

---

### Post by letriste on 2009-01-22
Hmm... the reinstall did not do the trick...

Throughout the commands below, the cable was disconnected. Network Manager and Firefox claimed to be disconnected th whole time... This is really weird, cause it looks like i'm connected.........

```
 $ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:66:51:CE:3B
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-43 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:21:29:81:70:CB
                    ESSID:"DIRIK"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:19:5B:E1:0B:F2
                    ESSID:"Corleone"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:18:39:2C:53:2A
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-68 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:1C:F0:61:37:2B
                    ESSID:"HjemmeDlink"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd070050f202000100
          Cell 06 - Address: 00:1C:B3:AD:32:86
                    ESSID:"JHS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101010003a4000027a4000042435e0062322f00
          Cell 07 - Address: 00:0F:CB:FC:C3:EA
                    ESSID:"JackLie"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101030003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010020ff7f

pan0      Interface doesn't support scanning.

 $ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:22:69:12:30:c6  
          inet6 addr: fe80::222:69ff:fe12:30c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:622 (622.0 B)  TX bytes:300 (300.0 B)

eth0      Link encap:Ethernet  HWaddr 00:21:86:5a:56:38  
          inet6 addr: fe80::221:86ff:fe5a:5638/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2256797 (2.2 MB)  TX bytes:147630 (147.6 KB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-12-30-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14999 errors:0 dropped:0 overruns:0 frame:3966
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1575508 (1.5 MB)  TX bytes:1625 (1.6 KB)
          Interrupt:17 

 $ sudo dhclient ath0

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:22:69:12:30:c6
Sending on   LPF/ath0/00:22:69:12:30:c6
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.109 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.109 from 192.168.1.1
bound to 192.168.1.109 -- renewal in 35980 seconds.

 $ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:22:69:12:30:c6  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe12:30c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1226 (1.2 KB)  TX bytes:3584 (3.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:21:86:5a:56:38  
          inet6 addr: fe80::221:86ff:fe5a:5638/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2256797 (2.2 MB)  TX bytes:147630 (147.6 KB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-12-30-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19635 errors:0 dropped:0 overruns:0 frame:5083
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2066580 (2.0 MB)  TX bytes:5359 (5.3 KB)
          Interrupt:17 

 $ wget google.com
--2009-01-22 23:28:46--  http://google.com/
Resolving google.com... 74.125.45.100, 209.85.171.100, 72.14.205.100
Connecting to google.com|74.125.45.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2009-01-22 23:28:46--  http://www.google.com/
Resolving www.google.com... 74.125.43.103, 74.125.43.104, 74.125.43.99, ...
Connecting to www.google.com|74.125.43.103|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.no/ [following]
--2009-01-22 23:28:46--  http://www.google.no/
Resolving www.google.no... 74.125.43.104, 74.125.43.99, 74.125.43.147, ...
Reusing existing connection to www.google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 6,154       --.-K/s   in 0.05s   

2009-01-22 23:28:46 (120 KB/s) - `index.html' saved [6154]

 $ ping -c 5 google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=1 ttl=238 time=137 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=238 time=139 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=3 ttl=238 time=149 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=4 ttl=238 time=153 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=5 ttl=238 time=143 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4013ms
rtt min/avg/max/mdev = 137.837/144.674/153.146/5.818 ms

 $ ping -c 5 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=237 time=145 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=237 time=146 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=237 time=154 ms
64 bytes from 74.125.45.100: icmp_seq=4 ttl=237 time=144 ms
64 bytes from 74.125.45.100: icmp_seq=5 ttl=237 time=146 ms

--- 74.125.45.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 144.863/147.530/154.429/3.537 ms

```

whew, that's a long one. did an *iwlist scan* too there.

I checked the hardware drivers now BTW, and it seems i have two atheros drivers installed one generic 802.11 and one for 5xxxx cards (not in use), but i don't think that's the problem, since it wasn't like that before, and i installed madwifi tools yesterday without finding them. Guess that's where they ended up...

---

### Post by pytheas22 on 2009-01-22
Yes, you were definitely connected after you typed 'dhclient ath0' because you were able to wget google.com successfully and ping with no packet loss.  Network Manager may not be smart enough to detect that you've connected manually, however, and Firefox may still have been in offline mode.  If you disable offline mode (under File menu in Firefox), could you browse.

I'm still puzzled as to why NM won't list any networks, however.  Does it show the wired interface at all?  Or do you just see 'wired network' when you left-click on it?
> 
I checked the hardware drivers now BTW, and it seems i have two atheros drivers installed one generic 802.11 and one for 5xxxx cards (not in use), but i don't think that's the problem, since it wasn't like that before, and i installed madwifi tools yesterday without finding them. Guess that's where they ended up...

Yes, your card is currently using the ath_pci driver, but it could probably also use ath5k (the one for 5xxxx cards).  If you want to try switching between drivers to see if it makes a difference, run:

```
sudo modprobe -r ath_pci ath5k
sudo modprobe ath5k
```

You should then see a wireless interface named 'wlan0' (instead of 'ath0') when you type 'sudo iwlist scan'.  Maybe Network Manager will behave properly when ath5k is being used?

If this doesn't work, you can type 'sudo modprobe ath_pci' to get ath_pci back, or just reboot and it should default back to ath_pci.

---

### Post by letriste on 2009-01-23
> **pytheas22 said:**
> Yes, you were definitely connected after you typed 'dhclient ath0' because you were able to wget google.com successfully and ping with no packet loss.  Network Manager may not be smart enough to detect that you've connected manually, however, and Firefox may still have been in offline mode.  If you disable offline mode (under File menu in Firefox), could you browse.

I'm still puzzled as to why NM won't list any networks, however.  Does it show the wired interface at all?  Or do you just see 'wired network' when you left-click on it?


Yes, your card is currently using the ath_pci driver, but it could probably also use ath5k (the one for 5xxxx cards).  If you want to try switching between drivers to see if it makes a difference, run:

```
sudo modprobe -r ath_pci ath5k
sudo modprobe ath5k
```

You should then see a wireless interface named 'wlan0' (instead of 'ath0') when you type 'sudo iwlist scan'.  Maybe Network Manager will behave properly when ath5k is being used?

If this doesn't work, you can type 'sudo modprobe ath_pci' to get ath_pci back, or just reboot and it should default back to ath_pci.

It worked the same as last time. when i *sudo dhclient wlan0*, i can wget all right. and when i turn off offline mode in firefox, it works too. i'm actually using it now with no cable connected. For some reason Network Manager does not agree...

Left-clicking NM reads:
{
**Wired network**
<O> auto ath0
**Wireless networks**
------------------------
VPN
}


Forgot to mention this. I didn't really connect manually besides the dhclient line.... the networks were all just there.

I'm glad it works now *thanks*, but it bugs me that NM is so stubborn. It shows offline when i'm clearly online.

---

### Post by pytheas22 on 2009-01-23
Yes, it must be frustrating not to have Network Manager working.  It will also be difficult to connect by hand to WPA-protected networks, so unless you plan on only using linksys, you might want to consider installing [wicd]("http://wicd.sourceforge.net") to replace NM.  You can install wicd by running these commands:

```
echo 'deb http://apt.wicd.net intrepid extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

wicd will replace Network Manager, but will hopefully work (if it doesn't seem to see networks at first, go into 'Preferences' and make sure it's set to use the correct interface--ath0 or wlan0).

---

### Post by letriste on 2009-01-24
> **pytheas22 said:**
> Yes, it must be frustrating not to have Network Manager working.  It will also be difficult to connect by hand to WPA-protected networks, so unless you plan on only using linksys, you might want to consider installing [wicd]("http://wicd.sourceforge.net") to replace NM.  You can install wicd by running these commands:

```
echo 'deb http://apt.wicd.net intrepid extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

wicd will replace Network Manager, but will hopefully work (if it doesn't seem to see networks at first, go into 'Preferences' and make sure it's set to use the correct interface--ath0 or wlan0).

Yeah, I was pondering on installing KNetwork Manager. Should I uninstall NM first? Is wicd in any way superior to KNM?

---

### Post by pytheas22 on 2009-01-24
I've never used KNetworkManager, but you could give it a try.  It would probably work as well as wicd.

When you install wicd, the package manager will automatically remove Network Manager.  I'm not sure if the installer for KNetworkManager will do the same, but if not, you could remove Network Manager yourself by typing:
```

sudo apt-get remove network-manager
```

It would probably not hurt to get NM uninstalled, whatever you do.

---

### Post by letriste on 2009-01-28
wicd worked out of the box, so to speak. i like it. thanks!!

---

