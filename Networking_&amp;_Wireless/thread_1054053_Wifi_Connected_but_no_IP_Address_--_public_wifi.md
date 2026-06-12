---
title: "Wifi Connected but no IP Address -- public wifi"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by wincen on 2009-01-29
I'm getting a problem obtaining an IP Address from a major city's public library wifi connection.  Network Manager says it's connected, but no ip address is obtained.  I dual boot, so I rebooted into windows and it works fine in windows.

Once connected you're forced to agree to their terms of use via browser and then you're off.  Like I said, with Ubuntu I cannot even obtain an IP Address even though Network Manager says it's connected.  In Windows it will connect and obviously get a lease.

I also tried doing it via command line:
```

iwconfig wlan0 essid TheirSSID
dhclient

```
No offers, it times out and gives up.

I use Ubuntu 8.10 with ndiswrappers and have generally had no wifi issues since using using ndiswrappers; wifi has been working fine at home and all public places except this library.  Any ideas?

---

### Post by x22 on 2009-01-29
here's the script I use:

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0 

you may have to set channel, crypt key
etc.

---

### Post by sysadmn62 on 2009-01-29
Under Ubuntu, what does ifconfig -a say when Network Manager thinks you are connected?  Also, what is the output of "netstat -rn"?

Next time you're logged in using windows, open a command window and check the address range the library uses - both before and after you click-thru the T&C web page.

---

### Post by robere.it on 2009-01-29
I have the exact same trouble with my wireless card when I go to my university. I can join the network, but dhclient cannot get an ip address. When using wpa_supplicant and dhclient on the command line, I get authorized and join the network but no dhcp offers made, and the program times out.

Help would be nice.

---

### Post by wincen on 2009-01-29
X22, nice script.  If anyone out there is wondering how to connect to wifi using the command line his steps are way more thorough than mine.  Unfortunately I was doing something similar to begin with so nothing changed.

Also since this is a public library there is no encryption, it's an open network.

The error message is send_packet: Message too long.  Ignore the DHCPDISCOVER on eth0, on this particular attempted I didn't specify my wifi when using dhclient.
```
SIOCSIFADDR: No buffer space available
Listening on LPF/pan0/3a:df:67:16:f1:16
Sending on   LPF/pan0/3a:df:67:16:f1:16
Listening on LPF/wlan0/00:1d:92:c4:43:d3
Sending on   LPF/wlan0/00:1d:92:c4:43:d3
Listening on LPF/eth0/00:40:45:2c:43:f1
Sending on   LPF/eth0/00:40:45:2c:43:f1
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Message too long

```

sysadmn62, I'll have to try ifconfig -a later.  But off the top of my head when I type ifconfig the IP Address so not listed at all.  Nothing whatsoever.

netstat -rn results from windows after clicking through
```

Route Table
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 40 45 2c 43 f1 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
0x10004 ...00 1d 92 c4 43 d3 ...... 802.11g Mini Card Wireless Adapter - Packet
Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0        10.12.0.1     10.12.0.142       30
        10.12.0.0      255.255.0.0      10.12.0.142     10.12.0.142       30
      10.12.0.142  255.255.255.255        127.0.0.1       127.0.0.1       30
   10.255.255.255  255.255.255.255      10.12.0.142     10.12.0.142       30
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0      10.12.0.142     10.12.0.142       30
  255.255.255.255  255.255.255.255      10.12.0.142               2       1
  255.255.255.255  255.255.255.255      10.12.0.142     10.12.0.142       1
Default Gateway:         10.12.0.1
===========================================================================
Persistent Routes:
  None

```

I can't check and see what it's like before I click accept because it remembers me now.  It probably records my mac address and just let me through.

---

