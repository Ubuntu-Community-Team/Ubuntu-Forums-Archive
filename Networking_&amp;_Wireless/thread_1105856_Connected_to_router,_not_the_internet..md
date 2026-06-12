---
title: "Connected to router, not the internet."
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by yarivm on 2009-03-25
I am running buntu 8.10 and I can connect to the wireless router but I cant connect to the internet, is there any thing I can do, do you guys need any information before you could understand what the problem is?

Here is what I did so far.

* ifconfig to check the status, eth1 appears as Ethernet (Should it be like this?)
* sudo /etc/init.d/networking restart (that was ok.)

Any more information?
The system ID my wifi card a IntelPRO Wireless 2000 or something like that.

Something is really wrong here, other computers can connect to the internet.

Note: I can access the router through firefox or other browsers, but I cannot connect out to the internet.

This problem appears to be widespread lately, is there something that happened in the update?

---

### Post by jbrevik on 2009-03-25
Are you connecting to the router via wireless or just lan?

---

### Post by yarivm on 2009-03-25
just through the wifi.

---

### Post by jbrevik on 2009-03-25
Run this and post the output:

```
iwconfig
```

---

### Post by yarivm on 2009-03-25
Here is the output:

```
yariv@BlackStar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:"commercial"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0:9A:63:D1   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-42 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:23  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:13

pan0      no wireless extensions.

yariv@BlackStar:~$
```


Please note: There is a XP system here and a Macintosh, both can access the internet through the wifi.

---

### Post by jbrevik on 2009-03-25
Might want to set the eth0 interface down. Try:
```
sudo ifconfig eth0 down
```

---

### Post by jbrevik on 2009-03-25
Are you able to ping google.com from the terminal, if so you may want to go to firefox and type in about:config in the address bar. Search for ipv6 and look for "network.dns.disableIPv6". If its set to false, right click on it and set it to true.

---

### Post by yarivm on 2009-03-25
Alright, I changed the network.dns.disableIPv6 to true.
and I brought eth0 down.

Now what  should I do, just restart firefox or the entire system?
or is there other things to do first?

Note: still no internet, and pinging google.com does not work, destination unreachable.

I have tried another wifi network and still with the same result, can connect to the router but not to the internet.

---

### Post by jbrevik on 2009-03-25
Just restart firefox. If that doesnt work, see if you can ping google.com from the terminal.
```
ping google.com
```

---

### Post by yarivm on 2009-03-25
I have restarted FireFox and and I have tried to ping google.com

Firefox still does not work, tried opera, no luck.
ping google only give me this error:

```
ping: unknown host google.com
```

---

### Post by Ferb on 2009-03-25
Do you use static ip or dynamic? 
If static then
Has the gateway been set correctly?

---

### Post by yarivm on 2009-03-25
I use a dynamic IP (DHCP is running on the router).

and the syslog is showing no error, it says it is connected and everything is ok.
but it does also say:

```
Mar 25 12:36:55 BlackStar ntpdate[12190]: can't find host ntp.ubuntu.com
Mar 25 12:36:55 BlackStar ntpdate[12190]: no servers can be used, exiting
```

---

### Post by yarivm on 2009-03-25
I have used the System Log Monitor to see what is happening, here is what it showed me.

```
Mar 25 12:42:38 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 0 
Mar 25 12:42:38 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 25 12:42:38 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 25 12:42:38 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 25 12:42:38 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Mar 25 12:42:42 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 0 
Mar 25 12:42:42 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 25 12:42:42 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 25 12:42:42 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 25 12:42:43 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Mar 25 12:42:47 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 0 
Mar 25 12:42:47 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 25 12:42:47 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 25 12:42:47 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 25 12:42:47 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Mar 25 12:42:51 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 0 
Mar 25 12:42:51 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 25 12:42:51 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 25 12:42:51 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 25 12:42:51 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  eth1: link timed out. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): device state change: 5 -> 3 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) starting connection 'Auto AutoFont' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto AutoFont' has security, and secrets exist.  No new secrets needed. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'ssid' value 'AutoFont' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 0 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'AutoFont'. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Mar 25 12:42:53 BlackStar NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Mar 25 12:42:53 BlackStar dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 25 12:42:53 BlackStar dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 25 12:42:53 BlackStar dhclient: All rights reserved.
Mar 25 12:42:53 BlackStar dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 25 12:42:53 BlackStar dhclient: 
Mar 25 12:42:54 BlackStar NetworkManager: <info>  dhclient started with pid 12544 
Mar 25 12:42:54 BlackStar NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Mar 25 12:42:54 BlackStar NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Mar 25 12:42:54 BlackStar dhclient: Listening on LPF/eth1/00:13:ce:b0:9c:84
Mar 25 12:42:54 BlackStar dhclient: Sending on   LPF/eth1/00:13:ce:b0:9c:84
Mar 25 12:42:54 BlackStar dhclient: Sending on   Socket/fallback
Mar 25 12:42:58 BlackStar dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Mar 25 12:43:03 BlackStar dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Mar 25 12:43:03 BlackStar dhclient: DHCPOFFER of 192.168.10.45 from 192.168.10.1
Mar 25 12:43:03 BlackStar dhclient: DHCPREQUEST of 192.168.10.45 on eth1 to 255.255.255.255 port 67
Mar 25 12:43:03 BlackStar dhclient: DHCPACK of 192.168.10.45 from 192.168.10.1
Mar 25 12:43:03 BlackStar NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Mar 25 12:43:03 BlackStar NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 25 12:43:03 BlackStar NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Mar 25 12:43:03 BlackStar NetworkManager: <info>    address 192.168.10.45 
Mar 25 12:43:03 BlackStar NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 25 12:43:03 BlackStar NetworkManager: <info>    gateway 192.168.10.1 
Mar 25 12:43:03 BlackStar NetworkManager: <info>    nameserver '192.168.10.1' 
Mar 25 12:43:03 BlackStar NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 25 12:43:03 BlackStar NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Mar 25 12:43:03 BlackStar NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Mar 25 12:43:03 BlackStar avahi-daemon[4665]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.10.45.
Mar 25 12:43:03 BlackStar avahi-daemon[4665]: New relevant interface eth1.IPv4 for mDNS.
Mar 25 12:43:03 BlackStar avahi-daemon[4665]: Registering new address record for 192.168.10.45 on eth1.IPv4.
Mar 25 12:43:03 BlackStar dhclient: bound to 192.168.10.45 -- renewal in 42025 seconds.
Mar 25 12:43:04 BlackStar NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Mar 25 12:43:04 BlackStar NetworkManager: <info>  Policy set 'Auto AutoFont' (eth1) as default for routing and DNS. 
Mar 25 12:43:04 BlackStar NetworkManager: <info>  Activation (eth1) successful, device activated. 
Mar 25 12:43:04 BlackStar NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 25 12:43:24 BlackStar ntpdate[12614]: can't find host ntp.ubuntu.com 
Mar 25 12:43:24 BlackStar ntpdate[12614]: no servers can be used, exiting
```

---

### Post by jbrevik on 2009-03-25
Have you tried the wired connection to the router? Can you? If so bring back up the eth0 interface
```
sudo ifconfig eth0 up
``` and test it.

Are you using any encryption for the wireless router?

---

### Post by yarivm on 2009-03-25
as the log showed, I am using a secure wireless connection, and the second router does not.

both the secured and unsecured wireless connection refuse to let me surf to the net.

I have used the ETH0 to try and access the internet, it worked.
the wifi does not work.

---

### Post by yarivm on 2009-03-25
I found the problem, it is a defective part of my entire box.
I will take it to be repaired and checked out.

I will reinstall the entire OS after I am done.
Thanks for all the help!

---

