---
title: "Problems connecting to wireless network manually"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Achel4Ever on 2009-12-04
Hello guys,

I stupidly un-installed the network-manager! Trying to reinstall it of course doesnt work since I don't have an internet connection anymore. Now I'm trying to connect to the Wireless network manually, but I can't get it done.
Before the uninstall everything was working, so no hardware problems.
If I boot with Windows Vista, everything works perfectly.

some information which might help

```
root@Desktop-Linux:~# lshw -C network

  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:fdefc000-fdefdfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:ba:8c:db
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

```

root@Desktop-Linux:~# iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"KoenG" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated  
          Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
root@Desktop-Linux:~# iwlist wlan0 scanning

          Cell 03 - Address: 00:11:95:03:C0:8A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm 
                    Encryption key:on
                    ESSID:"KoenG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000062d3e7122
                    Extra: Last beacon: 968ms ago
                    IE: Unknown: 00054B6F656E47
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 0706455520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD0600032F010100
```


```
root@Desktop-Linux:~# iwconfig wlan0 essid "KoenG"
root@Desktop-Linux:~# iwconfig wlan0 key xxxxxxxxxx
root@Desktop-Linux:~# iwconfig wlan0 ap 00:11:95:03:C0:8A  
root@Desktop-Linux:~# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1d:60:ba:8c:db
Sending on   LPF/wlan0/00:1d:60:ba:8c:db
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

```

I tried to switch off (an later on again) WEP key in the router, took out the space in te essid (before it was "Koen G") tried the above iwconfig-commands in all possible orders, and was searching a lot of forums, but I couldn't didnt find any solution, or idea to get there until now.

I'm getting really desperate, hope somebody can help me.

Thanks in advance
Robin

---

### Post by chili555 on 2009-12-04
I suggest leaving the 'ap' line out and also use lower case letters, if any, in your WEP key, like this:```
096c7f280e
```I hope these steps will help.

---

### Post by Achel4Ever on 2009-12-05
Thanks for the reply!

My wep key exists for the moment only of numbers. Before I already changed my router settings to an unsecured network, still no success.

About the ap line: I already tried with ap set as "any". Without ap-line. All those lines above in all possible orders leaving some out writing some more, also all settings in one line I tried... 
Something else I don't understand: if I give an ap mac-address, nothing changes when I call iwconfig, it remains "Not-Associated", whatever I do. Or is this just when I'm really connected that it shows me to which ap?
Same story when I change the essid, sometimes it just disappears, then I change to sth else and it comes back again. This happens very irregular... sometimes works sometimes it doesn't 

This really drives me slowly crazy since I'm a newbie and don't have any idea any more to get forward, or how to search the problem, but I somehow believe the solution is very easy, some detail I oversee...

---

### Post by chili555 on 2009-12-05
Let's do some additional fact-finding. Get out your USB key or whatever will allow you to transfer files to a computer that connects to the internet so you can post these results. Please do:```
dmesg > dmesg.txt
```Post dmesg.txt as an attachment to your reply. Likewise, these commands:```
ps ax | grep -i netw > netw.txt
sudo cat /var/log/messages | grep wlan0 > wlan0.txt
```Please attach all three text files to your reply and let's see if we can find out what's happening...or not.

---

### Post by Achel4Ever on 2009-12-06
Problem solved :D

thanks to the commands you gave me, I found some kind of Network manager installed, probably not complete or correct, or whatever. Al least I removed it, and immediately the manual connection worked... So now I installed WICD, seems to work great.

Thanks a lot for your help!

---

