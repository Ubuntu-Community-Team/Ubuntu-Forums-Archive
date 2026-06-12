---
title: "Connect to a wireless network via command line"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-08-07
Hi,
Here is what I did
```

ifconfig wlan0 up
iwlist wlan0 scan
iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY

```

1. After iwconfig, I got this error
> 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:9b:ab:56:19
Sending on   LPF/wlan0/00:0e:9b:ab:56:19
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


2. I also try to see if it is to use an ascii key, so I added the &#8220;s:&#8221; prefix to my key as
```

iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY

```
But it will give error
> 
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.



Does someone know what went wrong with these two errors and how to solve them?

Thanks and regards!

---

### Post by flylehe on 2009-08-08
Can someone help please? Thanks!
Some new questions: 
3. Do I have to specify the type of the wireless network: WEP WAP etc? I am able to access several wireless networks: WEP, WAP and open without password.
4. When I connect to the open wireless network, "iwconfig wlan0" gives "Access Point: Not-Associated". 
> 
wlan0     IEEE 802.11bg  ESSID:"bell"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:2D13-1B69-557F-3574-61CF-E091-51F9-4B70-0F9E-597B-2438-7B57-3468-0C35-D704-0D3E [2]   Security mode:open
          Power Management:off
          Link Quality=48/100  Signal level:-67 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Does this mean the connection to the wireless network fail? But I still can surf on the internet.

---

### Post by superprash2003 on 2009-08-08
yes not associated means failed.. you would need to enter the key

---

