---
title: "wifi connection trouble..."
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by djspank on 2006-01-05
Hi, I'm a french user of ubuntu. I'm trying to put the wifi on Ubuntu, I use a D-Link 624+. My wifi card is a broadcom, integrated with Turion, and well installed, I think :D .

I use some commands in order to find the trouble, but do you have any idea??

```

#ifconfig

wlan0     Lien encap:Ethernet  HWaddr 00:0E:9B:CD:76:A5
          inet adr:192.168.0.3  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20e:9bff:fecd:76a5/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:4449 (4.3 KiB)  TX bytes:0 (0.0 b)
          MÃ©moire:e2000000-e2001fff


#iwconfig


wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-49 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


#iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:A6:C0:66
                    ESSID:"sans-fil"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```


The wep key on my router is desactivated, i filter the connection by the MAC adress... Do anyone have any idea??

Thanks !!!

---

### Post by Zelut on 2006-01-05
The card looks configured & has been assigned an IP.  What is the problem that you're having?

---

### Post by djspank on 2006-01-05
I can't connect to my wifi network. 

Look, when i use the iwconfig command, it doesn't show any network : ESSID off/any

 and Access Point 00: ... :00

I don't understand...

---

### Post by Zelut on 2006-01-05
using the Network Tools try setting your SSID to begin with, or select one from the drop-down (if available)..

System > Admin > Networking.  Try specifying an SSID & see if that helps..

---

### Post by djspank on 2006-01-05
The ESSID is already configured with the network tools...

But there is nothing in the drop-down

---

### Post by Zelut on 2006-01-05
sudo ifup wlan0 / sudo ifdown wlan0 doesn't give you a better connection either?

---

### Post by djspank on 2006-01-05
```

#ifup wlan0
SIOCADDRT: File exists
Failed to bring up wlan0.

#ifdown wlan0
ifdown: interface wlan0 not configured

```

Not configured ?? Why ?

When i use the lspci -v | grep Ethernet it gives me that :

```

0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
        Subsystem: AMBIT Microsystem Corp.: Unknown device 0312
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at e2000000 (32-bit, non-prefetchable) [size=8K]



```

---

### Post by djspank on 2006-01-06
UP !!!!:razz:

---

### Post by Lambert on 2006-01-06
hey dj, try this from terminal

```
sudo -s
``` enter password (this just puts you as root user)
```
ifconfig wlan0 down
``` ```
ifconfig wlan0 up
``` ```
iwconifg wlan0 essid sans-fil ap 00:13:46:A6:C0:66 channel 6 commit
``` ```
dhclient wlan0
``` 

run the same iwconfig and ifconfig commands to see if you're associated and have ip address assigned. 

[FONT=monospace]now let's run through a series of pings

```
ping -c 4 127.0.0.1

ping -c 4 [/FONT]192.168.x.x

``` wher 192.168.x.x = ip assigned to device found when you run ifconfig. second line inet addr: _________

```
ping -c 4 192.168.x.x
``` where 192.168.x.x = ip addr of your router

```
ping -c 4 216.239.57.99

ping -c 4 www.ubuntulinux.com
``` 
If you were succesful with all these pings then try to surf via browser. If not post back where they started to drop.

If this doesn't work then next will be to set up static ip and try the same things.
then to exit from root type prompt

```
exit
```

In  your first post you show ip assigned but no association. That's kind of wierd, are you using dhcp or static ip assignment? Does your router have a log on it. If using dhcp I'm wondering if you associate with it long enough to receive the dhcp request and then association drops.

---

### Post by djspank on 2006-01-06
Ok, i am going to try what you say just before thanks.
I am nor using DHCP, that is why there is an IP adress assigned.

---

### Post by Lambert on 2006-01-06
quick change then. instead of the dhclient command run this

```
route -n
``` 
make sure you have lines similar to this.

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

``` 
If you don't have second line run this command

```
route add default gw 192.168.0.1 dev wlan0
```

but replace the ip I wrote with your routers ip

---

### Post by djspank on 2006-01-06
OK, First, when I use

```

iwconifg wlan0 essid sans-fil ap 00:13:46:A6:C0:66 channel 6 commit
Error : unrecognised wireless request "6"

```

then i run

```

route -n

```

the answer is
```

Destination      Gateway         Genmask            Flags  Metric Ref    Use Iface
192.168.1.0     0.0.0.0           255.255.255.0     U       0        0       0   vmnet1
172.16.59.0     0.0.0.0           255.255.255.0     UG     0        0       0   vmnet8

```

vmnet is for vmware

What should I do ?

---

### Post by Lambert on 2006-01-06
hmmm...replace channel 6 with this in the command and see what happens.

freq 2.437G

One thing I noticed in your first post was you card is showing freq 2.412 and router is on 2.437

Not familiar with vmnet but route -n shows your routing table and you need to have routes set up for the interface we're dealing with. First things first though, need to get associated with router.

Can you restart/reboot your router. Sometimes this solves similar problems to what you're having.

---

### Post by djspank on 2006-01-06
ok, I reboot my router.

Now when I use 

```

#iwlist wlan0 scan

```

it returns 

```

wlan0 no scan results

```

Arf...

I must go, it is the afternoon here, I go to work, i come back later...

Thank you for your help!!! :D

---

### Post by djspank on 2006-01-06
Up!!! :d

---

