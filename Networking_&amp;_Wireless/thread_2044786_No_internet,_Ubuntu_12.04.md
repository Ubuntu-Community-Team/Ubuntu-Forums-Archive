---
title: "No internet, Ubuntu 12.04"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by calgreen on 2012-08-20
I see a lot of people seem to have the same probablem I have. I just loaded Ubuntu 12.04 lts onto my system and am having trouble accessing the internet. I have connected to my network both wired into the router and wirelessly, but when I open firefox it will not load anything. But when I load Windows 7 everything if alright. Please help!

---

### Post by sanderj on 2012-08-20
What's the output of these four commands:

> ifconfig
mtr -nrc2 8.8.8.8
host [www.google.com](www.google.com)
host [www.google.com](www.google.com) 8.8.8.8

Post the output here.

---

### Post by calgreen on 2012-08-20
CODE: ifconfig 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6376 (6.3 KB)  TX bytes:6376 (6.3 KB) 

wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:2f:66:90   
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::9e4e:36ff:fe2f:6690/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:27179 (27.1 KB)  TX bytes:11384 (11.3 KB) 

CODE: mtr -nrc2 8.8.8.8 
HOST: chumrick-Lenovo-IdeaPad-Y58 Loss%   Snt   Last   Avg  Best  Wrst StDev 
CODE: host [www.google.com](www.google.com) 
Host [www.google.com](www.google.com) not found: 5(REFUSED) 
CODE: host [www.google.com](www.google.com) 8.8.8.8 
;; connection timed out; no servers could be reached

---

### Post by sanderj on 2012-08-20
Oh. You have an IP address. That's good. The rest doesn't look good.

What's the output of

```

ip route show
sudo iptables -L

```

Post the output here.

---

### Post by calgreen on 2012-08-20
CODE: ip route show 
default via 192.168.2.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.2.0/24 dev wlan0  proto kernel  scope link  src 192.168.2.8  metric 2 

CODE: sudo iptables -L 
[sudo] password for chumrick: 
Chain INPUT (policy ACCEPT) 
target     prot opt source               destination          

Chain FORWARD (policy ACCEPT) 
target     prot opt source               destination          

Chain OUTPUT (policy ACCEPT) 
target     prot opt source               destination

---

### Post by sanderj on 2012-08-20
No firewall settings. That's good.

And default gateway. That's good too. Can you ping it?


```
ping -c5 192.168.2.1

```

---

### Post by calgreen on 2012-08-20
When I do it says 5 packets transmitted, 0 received, 100% packet loss, time 4031ms

---

### Post by sanderj on 2012-08-20
> **calgreen said:**
> When I do it says 5 packets transmitted, 0 received, 100% packet loss, time 4031ms

Very strange. Is this on your normal home LAN? Not on a Hotspot, or corporate LAN/WAN, or a phone connection?

And your computer received it's IP address automatically via DHCP?

---

### Post by calgreen on 2012-08-20
It's my home LAN and yea I think so.

---

### Post by CappyT on 2012-08-20
> **calgreen said:**
> It's my home LAN and yea I think so.

Are you sure you don't have access control on your router?
Also, (you can check from windows) 192.168.2.1 is the ip of your router? (usually if you type this address in a browser, you should see the webinterface of the router)

in windows, do this command "ipconfig /all" without quotes (") and paste here the output...

---

### Post by calgreen on 2012-08-20
ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : PCY580
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Belkin

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter #
2
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-91
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-91
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Centrino(R) Wireless-N 2200
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-90
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f0fa:105b:2a38:b5fb%15(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.8(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, August 20, 2012 1:10:40 AM
   Lease Expires . . . . . . . . . . : Thursday, September 26, 2148 7:39:55 AM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 295456310
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-17-74-48-F6-DC-0E-A1-F7-AB-DA

   DNS Servers . . . . . . . . . . . : 192.168.2.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 08-ED-B9-D7-B8-CB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Atheros AR8161/8165 PCI-E Gigabit Etherne
t Controller (NDIS 6.20)
   Physical Address. . . . . . . . . : DC-0E-A1-F7-AB-DA
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.Belkin:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:953c:428:764:52c5:3712(Prefer
red)
   Link-local IPv6 Address . . . . . : fe80::428:764:52c5:3712%18(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by CappyT on 2012-08-20
> **calgreen said:**
> ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : PCY580
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Belkin

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Centrino(R) Wireless-N 2200
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-90
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f0fa:105b:2a38:b5fb%15(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.8(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, August 20, 2012 1:10:40 AM
   Lease Expires . . . . . . . . . . : Thursday, September 26, 2148 7:39:55 AM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 295456310
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-17-74-48-F6-DC-0E-A1-F7-AB-DA

Ok, as I can see the configuration of ubuntu and windows are the same... is really strange...

boot ubuntu and connect using cable and switch off wifi... when you are connected, open terminal and type "ifconfig" without quotes... post here the results..

---

### Post by sanderj on 2012-08-20
As @CappyT says: what IP address does your Windows system get? Check with "ipconfig" (so a "P", not an "F" like in *x).

---

### Post by calgreen on 2012-08-20
INPUT: ifconfig
OUTPUT: lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3166 (3.1 KB)  TX bytes:3166 (3.1 KB) 

wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:2f:66:90   
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::9e4e:36ff:fe2f:6690/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:16779 (16.7 KB)  TX bytes:25474 (25.4 KB) 

INPUT: ipcinfig
OUTPUT: Windows IP Configuration

   Host Name . . . . . . . . . . . . : PCY580
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Belkin

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter #
2
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-91
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-91
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Centrino(R) Wireless-N 2200
   Physical Address. . . . . . . . . : 9C-4E-36-2F-66-90
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f0fa:105b:2a38:b5fb%15(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.8(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, August 20, 2012 1:10:40 AM
   Lease Expires . . . . . . . . . . : Thursday, September 26, 2148 7:39:55 AM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 295456310
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-17-74-48-F6-DC-0E-A1-F7-AB-DA

   DNS Servers . . . . . . . . . . . : 192.168.2.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 08-ED-B9-D7-B8-CB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Atheros AR8161/8165 PCI-E Gigabit Etherne
t Controller (NDIS 6.20)
   Physical Address. . . . . . . . . : DC-0E-A1-F7-AB-DA
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.Belkin:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:953c:428:764:52c5:3712(Prefer
red)
   Link-local IPv6 Address . . . . . : fe80::428:764:52c5:3712%18(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by sanderj on 2012-08-20
On Windows, can you

```
ping 192.168.2.1

```
It didn't work under Ubuntu, so I wonder about Windows

Oh, and under Windows:

```
tracert 8.8.8.8

```
Can you post the output here?

---

### Post by calgreen on 2012-08-20
So whats going on? Let me know whats going on here. Could this be a driver issue or a hardware thing?

INPUT: ping 192.168.2.1

Pinging 192.168.2.1 with 32 bytes of data:
Reply from 192.168.2.1: bytes=32 time=2ms TTL=64
Reply from 192.168.2.1: bytes=32 time=2ms TTL=64
Reply from 192.168.2.1: bytes=32 time=2ms TTL=64
Reply from 192.168.2.1: bytes=32 time=2ms TTL=64

Ping statistics for 192.168.2.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 2ms, Average = 2ms

INPUT: tracert 8.8.8.8

Tracing route to google-public-dns-a.google.com [8.8.8.8]
over a maximum of 30 hops:

  1    40 ms     1 ms     4 ms  . [192.168.2.1]
  2     2 ms     2 ms     3 ms  Wireless_Broadband_Router.home [192.168.0.1]
  3     7 ms     5 ms     8 ms  L100.LSANCA-VFTTP-121.verizon-gni.net [173.58.73
.1]
  4    14 ms    10 ms    10 ms  G0-14-3-2.LSANCA-LCR-21.verizon-gni.net [130.81.
131.46]
  5    10 ms    10 ms    14 ms  so-3-1-0-0.LAX01-BB-RTR1.verizon-gni.net [130.81
.151.236]
  6    12 ms    11 ms    10 ms  0.so-1-2-0.XL3.LAX15.ALTER.NET [152.63.10.133]
  7   108 ms     *        *     0.xe-6-1-0.XT1.NYC4.ALTER.NET [152.63.3.105]
  8    86 ms    89 ms    91 ms  TenGigE0-6-0-0.GW8.NYC4.ALTER.NET [152.63.22.41]

  9   137 ms   138 ms   139 ms  Internet-gw.customer.alter.net [152.179.72.66]
 10    86 ms    85 ms    84 ms  72.14.238.232
 11    86 ms    87 ms    86 ms  209.85.252.2
 12    86 ms    85 ms    85 ms  72.14.239.93
 13    84 ms    83 ms    84 ms  72.14.236.200
 14    88 ms    88 ms    88 ms  72.14.232.21
 15    86 ms    88 ms   123 ms  google-public-dns-a.google.com [8.8.8.8]

Trace complete.

---

### Post by Tach on 2012-08-20
I just want to add that I have the same problem. Everything looks like it's set up, but the internet won't work and pinging the gateway of the router gives 100% packet loss. Windows is fine too.

Could this be a bug introduced accidentally in 12.04?

---

### Post by sanderj on 2012-08-21
> **Tach said:**
> 
Could this be a bug introduced accidentally in 12.04?

You can test that:
First live-boot Ubuntu 11.10 (or 11.04) from CD or USB, and see if Internet works.
After that, live-boot Ubuntu 12.04 from CD or USB (so without any settings / installs / etc), and see if Internet works.

11.x works and 12.04 doesn't, I would say it's bug and you can report in on Launchpad

---

### Post by calgreen on 2012-08-21
Ive installed 11.10 and my wireless is not working in this version, and I also do not have internet while plug into the router.

---

### Post by sanderj on 2012-08-21
> **calgreen said:**
> Ive installed 11.10 and my wireless is not working in this version, and I also do not have internet while plug into the router.

To rule out your modem, you could connect your computer to another network and see what happens.

And, just checking: Ubuntu is running on bare metal, not in Virtual Machine, right?

Other than that, I'm out of ideas.

---

### Post by NikTh on 2012-08-22
Hi , 
can you please open a terminal and copy-paste from here below commands one at time. 

```
wget "http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF" -O ~/netinfo.sh 
chmod a+x netinfo.sh
./netinfo.sh
gedit netinfo.txt
```The last command will open a window . We want the results. You can attach the file netinfo.txt here or copy-paste all the results here . 
**If you copy-paste the results directly here** _PUT them inside ```
 tags  so can be readable._
[noparse][code]the results here
```[/noparse]
Thanks

---

### Post by calgreen on 2012-08-23
OK heres what happened.

INPUT: wget "http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF" -O ~/netinfo.sh 
```
--2012-08-22 21:10:42--  http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF 
Resolving ubuntuone.com (ubuntuone.com)... 
failed: Name or service not known. 
wget: unable to resolve host address `ubuntuone.com' 
```

The next two lines didnt seem to do anything. and the last line opened up the window like you said but there was no info in it, it was just a empty .txt document.

---

### Post by NikTh on 2012-08-23
Hi , 
try again ,I just test it and works fine. 
Be sure you have internet access. 
Thanks

---

### Post by sanderj on 2012-08-23
> **NikTh said:**
> Hi , 
try again ,I just test it and works fine. 
Be sure you have internet access. 
Thanks

... this whole thread is about the OP not having Internet access ... :p

So the OP should execute the wget command (or just visit [http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF](http://ubuntuone.com/73AB8BzNwtPJMHmZ0i7lpF) with a web browsing) on a working system, then copy it to the non-functional system, and there execute the other commands.

---

### Post by calgreen on 2012-08-23
Ok thanks. Copy the whole thing and execute or do I need to enter them one line at a time?

---

### Post by NikTh on 2012-08-23
> **calgreen said:**
> Ok thanks. Copy the whole thing and execute or do I need to enter them one line at a time?

Hi , 
then forget about first command (wget) . Goto the page as @sanderj suggested (with a browser on a working system) save the file and then run it on Ubuntu. 

e.g: 
If you save the file on a usb , move the file to your Desktop (in Ubuntu) and then open a terminal and execute with order

```
cd Desktop 
chmod a+x netinfo.sh
./netinfo.sh
``` 
and then look to your Desktop for the **netinfo.txt** file. _Attach the file here_. 
Thanks

---

### Post by calgreen on 2012-08-23
Finally got it. What's in this file, all mt network info?

---

### Post by NikTh on 2012-08-24
> **calgreen said:**
> Finally got it. What's in this file, all mt network info?

Hi ,
yes all your network info , except WPA, WEP keys and access point address   , those have been removed for safety. 


I am not the most experienced guy with networks in here , but I can see probably 2 problems here. 

1. I saw an extra entry in resolv.conf , it says 
```
nameserver 127.0.0.1 
search Belkin
```what is this **search Beklin **? try to remove it please. 



```
gksudo gedit /etc/resolv.conf
```remove the line **search Beklin** save the document and then run 

```
sudo /etc/init.d/networking restart 
```2. I saw that no driver loaded for Atheros Ethernet controller . Maybe we must load it by hand. Will see. 

Try the first with resolv.conf  and if you still have problem , give here the results of 

```
cat /etc/resolv.conf
```Thank you.

---

### Post by calgreen on 2012-08-24
The gedit command doesn't open anything.

Cat: /ect/resolve.conf: no such file or directory.

---

### Post by NikTh on 2012-08-24
> **calgreen said:**
> The gedit command doesn't open anything.
Hi ,
Are you using Ubuntu or another flavor ? like Xubuntu - Lubuntu etc 

Try from terminal with nano 

```
sudo nano /etc/resolv.conf
``` 
browse with arrows keys.

to save the document in nano , must click 
1.Ctrl + x 
2. Y(es) 
3. Enter

Thank you

---

### Post by calgreen on 2012-08-24
It's blank. I'm guessing there should be some text or something to edit?

---

### Post by NikTh on 2012-08-25
> **calgreen said:**
> The gedit command doesn't open anything.

Cat: /ect/resolve.conf: no such file or directory.

Hi , 
it is not **cat /[COLOR=Red]ect[/COLOR]/resovl[COLOR=Red]e[/COLOR].conf** it is **cat /etc/resolv.conf** , try to give the commands with accuracy. 

You can copy from here and paste them to your terminal. 

Thank you

---

### Post by calgreen on 2012-08-25
> **NikTh said:**
> Hi , 
it is not **cat /[COLOR=Red]ect[/COLOR]/resovl[COLOR=Red]e[/COLOR].conf** it is **cat /etc/resolv.conf** , try to give the commands with accuracy. 

You can copy from here and paste them to your terminal. 

Thank you

SMH, I'm such a newb. I would have copy and pasted but I'm using the Internet on my phone to read the forums when I'm logged into Ubuntu. I wasn't putting the extra "e" in but I was misspelling etc, which I didn't even notice. However, I finally got it. Also I am using just regular Ubuntu for your info.

---

### Post by NikTh on 2012-08-25
> **calgreen said:**
>  However, I finally got it. Also I am using just regular Ubuntu for your info.

Hi ,
I asked about what flavor of Ubuntu you use , cuz of this message 
> **calgreen said:**
> The gedit command doesn't open anything.
and I thought maybe you use another flavor and gedit is not installed. 

What about "I finally got it" ? got it what ? solved your problem ? 

Thank you.

---

### Post by calgreen on 2012-08-25
No I meant I finally got the command to work. It wouldnt work becuase I was not entering it in correctly. I did open up the file and removed the "search belkin" like you said tho. Sorry for the confusion.

---

