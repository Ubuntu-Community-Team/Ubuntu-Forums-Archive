---
title: "Safecom SWLMP-54108/xubuntu 8.04 problems"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by rutter on 2010-03-04
Now then,

I've just resurrected a rather aged Dell Latitude C400 which is fitted with a Safecom SWLMP 54108 wireless card. I've stuck Xubuntu 8.04 on, and wireless isn't working at all. Originally I was able to see all the wireless networks in the area (including my own) but not connect to them. After entering my WEP passphrase, network manager would think about it for a while and then ask for the passphrase again.

I then read (I think) every how-to and troubleshooting guide on the web, and have installed a windows driver using ndiswrapper. I'm pretty sure that's all gone well, but now I cannot even detect a wireless network. I've tried network manager, wcid and command line stuff and not really got anywhere. I have also trawled the web for information and not got it to work.

```

dave@craptop:~$ dmesg | grep -e ndis -e wlan
[  907.119520] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  604.781557] ndiswrapper: driver tnet1130 (Texas Instruments,12/01/2004,7.0.1.33) loaded
[  605.468570] ndiswrapper: using IRQ 5
[  908.227340] wlan0: ethernet device 00:e0:98:f6:9e:82 using NDIS driver: tnet1130, version: 0x7, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[  908.228313] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  908.229063] usbcore: registered new interface driver ndiswrapper
[  908.352209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  621.019926] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``````

dave@craptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:0a:f7:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.71 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 00
       serial: 00:e0:98:f6:9e:82
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tnet1130 driverversion=1.52+Texas Instruments,12/01/200 latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

``````

dave@craptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              There is already a pid file /var/run/dhclient.wlan0.pid with pid 7728
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:e0:98:f6:9e:82
Sending on   LPF/wlan0/00:e0:98:f6:9e:82
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:e0:98:f6:9e:82
Sending on   LPF/wlan0/00:e0:98:f6:9e:82
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Any ideas? Any other terminal contents you want to see?

---

### Post by chili555 on 2010-03-04
I want to see:```
cat /etc/network/interfaces
```More to the point, Network Manager is not going to effectively manage your network with any more than:> auto lo
iface lo inet loopbackAs well, manual configuration doesn't work well, either, as you see:> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by rutter on 2010-03-05
Currently I have entered the details for my wireless network. If I don't do this the wireless device doesn't configure at all. 

```

dave@craptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-key my_key
wireless-essid my_network

auto wlan0

```

As you have noticed though, even entering this information into the network/interfaces file doesn't get me connected.

---

### Post by chili555 on 2010-03-05
> After entering my WEP passphraseHow many characters is your passphrase? Where are you entering it? Passphrase, HEX or ASCII?

---

### Post by rutter on 2010-03-05
> **chili555 said:**
> How many characters is your passphrase? Where are you entering it? Passphrase, HEX or ASCII?

10 characters, hex. 
Initially I entered it when requested by NM, though I have later tried to configure the card by editing /etc/network/interfaces directly. Makes no odds. I can't see any wireless networks, and I can't connect to my own.

---

### Post by chili555 on 2010-03-05
> 10 characters, hex. May I assume, then, you are adding it in 'WEP 40/128-bit HEX?' If not, would you please try?

Network Manager will ordinarily not cooperate ...at all...with manual configuration. Temporarily, will you please comment out your wlan entries, thus?```
auto lo
iface lo inet loopback


#iface wlan0 inet dhcp
#wireless-key my_key
#wireless-essid my_network

#auto wlan0
```Reboot and see if NM is back at work. Try 'WEP 40/128-bit HEX' and let us know.

---

### Post by rutter on 2010-03-07
> **chili555 said:**
> Reboot and see if NM is back at work. Try 'WEP 40/128-bit HEX' and let us know.

If I comment out the manual configuration in /etc/network/interfaces the ndiswrapper driver doesn't claim the wireless card. 
```

 sudo lshw -C network
 
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:0b:f7:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.71 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32

```

It's a bit odd. If I enter a manual configuration I cannot see any wireless networks and therefore cannot connect to my network, and if I take the configuration out of /etc/network/interfaces NM doesn't show a wireless device at all.

---

### Post by chili555 on 2010-03-07
Please try:```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
```Does it work better now?

---

### Post by rutter on 2010-03-08
> **chili555 said:**
> Please try:```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
```Does it work better now?

Wireless is selectable from network manager, but no wireless networks are detected. 

Command line scan doesn't seem to find anything either.

```

 iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by chili555 on 2010-03-08
From man iwlist:> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.  By  default, the way scanning is done (the scope of the scan) is dependant on   the card and card settings.Please try:```
sudo iwlist wlan0 scan
```Please, also let us see:```
iwconfig
```Thanks.

---

### Post by rutter on 2010-03-08
```

dave@craptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

dave@craptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks for your patience, by the way.

---

### Post by chili555 on 2010-03-08
Does this command look like the card and driver are working together? ```
ndiswrapper -l
```These cards need firmware; I believe it is a .sys file. Do you remember installing it, along with the .inf? Do you have the card's original disc with the Windows driver files?

---

### Post by rutter on 2010-03-08
I have tried that, yeah. It looks OK to me, I'm fairly sure the alternative acx driver mentioned isn't messing things up as I've blacklisted it.

```

 ndiswrapper -l
tnet1130 : driver installed
    device (104C:9066) present (alternate driver: acx)

```

I don't have the original disc for the card, I downloaded a windows driver for it. The .inf file was installed from a directory containing the .sys files and some other files which were listed in .inf, so they should have installed correctly.

---

### Post by rutter on 2010-03-11
I give up. I'm putting XP back on so that I can actually take my laptop out of my house. I'd like to say that it has been an entertaining challenge, but I'd be lying.

---

