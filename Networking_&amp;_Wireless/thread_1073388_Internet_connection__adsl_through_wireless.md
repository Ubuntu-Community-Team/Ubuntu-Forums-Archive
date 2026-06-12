---
title: "Internet connection / adsl through wireless ?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by logiccc on 2009-02-18
Hello gentlemans!
I've got a Acer Aspire 5520 with Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter  
My wifi card drivers has been fixed by madwifi-hal-0.10.5.6
Where is the problem i don't know, hope that u have a lot of data, to troubleshoot my wireless?

```
root@ubuntu:/home/ubuntu# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:3a:06:11:7e  
          inet6 addr: fe80::21f:3aff:fe06:117e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12756 (12.7 KB)  TX bytes:7380 (7.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:73:d2:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67217 (67.2 KB)  TX bytes:67217 (67.2 KB)

pan0      Link encap:Ethernet  HWaddr 5e:e5:71:d5:dc:d7  
          inet6 addr: fe80::5ce5:71ff:fed5:dcd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-06-11-7E-63-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10639 errors:0 dropped:0 overruns:0 frame:488
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:937294 (937.2 KB)  TX bytes:25521 (25.5 KB)
          Interrupt:19 


```

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:FC:17:8D:52   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:4747  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

```
 NetworkManager: <info>  Activation (ath0) starting connection 'Auto WebSTAR' 
 NetworkManager: <info>  (ath0): device state change: 3 -> 4 
 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
 NetworkManager: <info>  (ath0): device state change: 4 -> 5 
 NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto WebSTAR' requires no security.  No secrets needed. 
 NetworkManager: <info>  Config: added 'ssid' value 'WebSTAR' 
 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
 NetworkManager: <info>  Config: set interface ap_scan to 1 
 NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
 NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3 
 NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4 
 NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
 NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'WebSTAR'. 
 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
 NetworkManager: <info>  (ath0): device state change: 5 -> 7 
 NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
 NetworkManager: <info>  dhclient started with pid 11517 
 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
 dhclient: Internet Systems Consortium DHCP Client V3.1.1
 dhclient: Copyright 2004-2008 Internet Systems Consortium.
 dhclient: All rights reserved.
 dhclient: For info, please visit http://www.isc.org/sw/dhcp/
 dhclient: 
 dhclient: wifi0: unknown hardware address type 801
 NetworkManager: <info>  DHCP: device ath0 state changed normal exit -> preinit 
 dhclient: wifi0: unknown hardware address type 801
 dhclient: Listening on LPF/ath0/00:1f:3a:06:11:7e
 dhclient: Sending on   LPF/ath0/00:1f:3a:06:11:7e
 dhclient: Sending on   Socket/fallback
 dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
 dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
 dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
 dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
 dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
 NetworkManager: <info>  Device 'ath0' DHCP transaction took too long (>45s), stopping it. 
 NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 11517 
 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started... 
 NetworkManager: <info>  (ath0): device state change: 7 -> 9 
 NetworkManager: <info>  Activation (ath0) failed for access point (WebSTAR) 
 NetworkManager: <info>  Marking connection 'Auto WebSTAR' invalid. 
 NetworkManager: <info>  Activation (ath0) failed. 
 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete. 
 NetworkManager: <info>  (ath0): device state change: 9 -> 3 
 NetworkManager: <info>  (ath0): deactivating device (reason: 0). 


```

[[IMG]http://img27.imageshack.us/img27/9049/95413658nx2.th.png[/IMG]](http://img27.imageshack.us/my.php?image=95413658nx2.png)

[[IMG]http://img8.imageshack.us/img8/6571/28881603fg2.th.png[/IMG]](http://img8.imageshack.us/my.php?image=28881603fg2.png)

[[IMG]http://img23.imageshack.us/img23/279/54307154al0.th.png[/IMG]](http://img23.imageshack.us/my.php?image=54307154al0.png)

[[IMG]http://img22.imageshack.us/img22/1241/15631792zp4.th.png[/IMG]](http://img22.imageshack.us/my.php?image=15631792zp4.png)

[[IMG]http://img19.imageshack.us/img19/1028/18467239zg0.th.png[/IMG]](http://img19.imageshack.us/my.php?image=18467239zg0.png)

[[IMG]http://img18.imageshack.us/img18/5778/26149514sm2.th.png[/IMG]](http://img18.imageshack.us/my.php?image=26149514sm2.png)

[[IMG]http://img16.imageshack.us/img16/6530/92556662xd7.th.png[/IMG]](http://img16.imageshack.us/my.php?image=92556662xd7.png)

---

### Post by logiccc on 2009-02-18
[[IMG]http://img15.imageshack.us/img15/1861/36618706gq3.th.png[/IMG]](http://img15.imageshack.us/my.php?image=36618706gq3.png)

[[IMG]http://img14.imageshack.us/img14/5599/32349050qz5.th.png[/IMG]](http://img14.imageshack.us/my.php?image=32349050qz5.png)

[[IMG]http://img27.imageshack.us/img27/4697/10ub2.th.png[/IMG]](http://img27.imageshack.us/my.php?image=10ub2.png)

[[IMG]http://img8.imageshack.us/img8/7079/11tj3.th.png[/IMG]](http://img8.imageshack.us/my.php?image=11tj3.png)

[[IMG]http://img23.imageshack.us/img23/9670/12cf8.th.png[/IMG]](http://img23.imageshack.us/my.php?image=12cf8.png)

---

### Post by superprash2003 on 2009-02-18
for some reason you arent getting an ip address.. what is the ip address of your wifi router?? try setting up a static ip!!

---

### Post by logiccc on 2009-02-18
> **superprash2003 said:**
> for some reason you arent getting an ip address.. what is the ip address of your wifi router?? try setting up a static ip!!

I've used dhcp in xp, opensuse, vista and it works.
Why ubuntu need static, couse my ISP use dhcp any idea..?
If i must set a static ip, how to find my wifi's router ip address?

---

### Post by logiccc on 2009-02-19
any? ubuntu team where are u, help pls? :(

---

### Post by superprash2003 on 2009-02-19
we're talking about a local ip here not a WAN Ip... is this router yours?? do you know its model no?

---

### Post by logiccc on 2009-02-19
Scientific Atlanta
A cisco company
Model: EPC2434

---

### Post by logiccc on 2009-02-19
we're talking about a local ip here not a WAN Ip... is this router yours?? do you know its model no?

Brotha,
Do u have any suggestion what to do? 
I've said in xp, vista, openSUSE i've used a normal pppoe dhcp through wireless!
Any idea how can i modify or do i have to call my ISP?

---

### Post by logiccc on 2009-02-20
Any solutions??

---

### Post by superprash2003 on 2009-02-20
what is your cisco router's ip?

---

### Post by logiccc on 2009-02-21
```

C:\Documents and Settings\username>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : username
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Atheros AR5007EG Wireless Network Ad
apter
        Physical Address. . . . . . . . . : 00-1F-3A-06-11-7E
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.100.55
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter IPKO:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.128.136.156
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.128.136.156
        DNS Servers . . . . . . . . . . . : 80.80.160.8
                                            80.80.160.9
```

---

### Post by superprash2003 on 2009-02-21
even that output doesnt show the ip of your cisco

---

### Post by logiccc on 2009-02-21
And how do I get that IP, do I have to call my ISP service to ask them ???

---

### Post by TimDaniels on 2009-02-21
> **logiccc said:**
> And how do I get that IP, do I have to call my ISP service to ask them ???

To get the IP address that your ISP assigned to your router, you have interrogate your router.  For my Linksys router, I enter 192.168.1.1 in the url window of any browser downstream of it and enter the password for the router.  Then a window appears for the "home page" of the router's "website", and clicking on Status in the menu bar, the information page with the IP address assigned by the ISP appears.

*TimDaniels*

---

### Post by superprash2003 on 2009-02-22
as mentioned by TimDaniels usually ip address of routers are 192.168.1.1 or 192.168.0.1 .. but it could be different for a cisco router.. you could check out the manual of that router , it would definetly be mentioned there..

---

