---
title: "Internet (and Firefox) ALOT Slower on Ubuntu than Windows"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Matthileo on 2009-03-04
Hi.
I have my machine set up to duel boot Ubuntu 8.10 and Windows 7.
I've noticed that my Internet connection seems to be a lot faster in windows than in Ubuntu. Why is this, and more importantly, how can I fix it.
(The same was true when I was using Windows Vista - it beat the crap out of Ubuntu in terms of Internet speed)

I'm kind of a linux noob, so it there's more information you need let me know and I'll post it.

Thanks.

---

### Post by camberiu on 2009-03-04
Hi,

I've posted the exact same issue recently and it seems that no one has an answer for this apparently very common issue. I find it surprising that an OS that look so polished and powerful as Ubuntu has such a fundamental issue.

---

### Post by Matthileo on 2009-03-04
Update:

I guess when I'm on campus my connection is just as fast in Ubuntu as in Windows, but for some reason on my home network it's a lot slower...

---

### Post by Matthileo on 2009-03-04
bump

---

### Post by Matthileo on 2009-03-05
It's weird.
This is like the third time in a row I've asked for help on the forums and gotten none.

---

### Post by Huufarted on 2009-03-05
Perhaps your MTU is set wrong?  If you're on cable, go 1500.  Normal I think is 1492.

Just how much of a difference in speed are you talking?

---

### Post by Zimmer on 2009-03-05
Probably too many variables that will not allow a genuine comparison or resolution.

What preferences are present in each instance of the browser;
How long you have used the browser in each OS ? (Firefox may, with its dodgy site tracker save info to your HDD  and if it is starting from scratch on a new install could well slow you down, I turned this off on mine and stopped my HDD thrashing whilst browsing, and even that could be down to some other coincidence.!)
Comparison of connection .. could have been unlucky and  gotten a bad connection/peak time/line maintenence issue which is beyond your control ...
Even, perhaps, (speaking with no authority on the matter whatsoever) you have 3D effects on in Ubuntu and no Aero 3D interface whatsits running in Win 7 or  whatever..

Maybe there just are not enough Win 7 and  Ubuntu users out there to offer you  any thoughts...
It would take a lot of discreet testing of identical machines simultaneously on a known (and measured ) connection to offer a solid benchmark.

So, unless a friendly Firefox developer passes by who knows something 'special' ... or a sudden glut of Win 7 and Ubuntu users who are bowled over by Win 7's browsing performance..
you will probably not get an immediate 'answer' on an Ubuntu forum to this particular question.. sorry.. no 'answer' but I hope I have at least provided a 'reply'.

---

### Post by Matthileo on 2009-03-05
> **Zimmer said:**
> Probably too many variables that will not allow a genuine comparison or resolution.

What preferences are present in each instance of the browser;
How long you have used the browser in each OS ? (Firefox may, with its dodgy site tracker save info to your HDD  and if it is starting from scratch on a new install could well slow you down, I turned this off on mine and stopped my HDD thrashing whilst browsing, and even that could be down to some other coincidence.!)
Comparison of connection .. could have been unlucky and  gotten a bad connection/peak time/line maintenence issue which is beyond your control ...
Even, perhaps, (speaking with no authority on the matter whatsoever) you have 3D effects on in Ubuntu and no Aero 3D interface whatsits running in Win 7 or  whatever..

Maybe there just are not enough Win 7 and  Ubuntu users out there to offer you  any thoughts...
It would take a lot of discreet testing of identical machines simultaneously on a known (and measured ) connection to offer a solid benchmark.

So, unless a friendly Firefox developer passes by who knows something 'special' ... or a sudden glut of Win 7 and Ubuntu users who are bowled over by Win 7's browsing performance..
you will probably not get an immediate 'answer' on an Ubuntu forum to this particular question.. sorry.. no 'answer' but I hope I have at least provided a 'reply'.

First, the same was true when I was using Vista and Ubuntu, and I know there are significantly more users in that category than the Win7/Ubuntu category.

Second, The disparity between performance in Windows and Ubuntu only happens on my home network, but not when I access the internet from my school's wireless.

My best guess is that there is some conflict between Ubuntu and my wireless router at home. But because I am an amateur at the whole linux thing, I was hoping to find some help troubleshooting this issue here, on the forums.

Thank you though, for the reply :)

---

### Post by Matthileo on 2009-03-05
> **Huufarted said:**
> Perhaps your MTU is set wrong?  If you're on cable, go 1500.  Normal I think is 1492.

Just how much of a difference in speed are you talking?

There is a 3-6 second delay before firefox begins downloading a webpage in ubuntu. 

I'm not sure what MTU is.

---

### Post by Huufarted on 2009-03-05
> **Matthileo said:**
> There is a 3-6 second delay before firefox begins downloading a webpage in ubuntu. 

I'm not sure what MTU is.

Now THAT sounds like a routing issue.  Post us a 'netstat -rn' from Windows and from Ubuntu.  The command will be the same.  That's a (- r n) without the spaces or parentheses.

---

### Post by Matthileo on 2009-03-05
> **Huufarted said:**
> Now THAT sounds like a routing issue.  Post us a 'netstat -rn' from Windows and from Ubuntu.  The command will be the same.  That's a (- r n) without the spaces or parentheses.

For Ubuntu

```
matt@matt-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0

```

For Windows
```
C:\Users\matt> netstat -rn
===========================================================================
Interface List
 17...00 1f e1 db e6 ee ......Bluetooth Device (Personal Area Network)
 14...00 1f 3b a9 8b 93 ......Intel(R) Wireless WiFi Link 4965AGN
 12...00 1d 09 56 1c 08 ......Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller
  1...........................Software Loopback Interface 1
 10...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 13...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 15...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 16...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 18...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #3
 20...00 00 00 00 00 00 00 e0 Microsoft 6to4 Adapter
 21...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1      192.168.2.2     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.2.0    255.255.255.0         On-link       192.168.2.2    281
      192.168.2.2  255.255.255.255         On-link       192.168.2.2    281
    192.168.2.255  255.255.255.255         On-link       192.168.2.2    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link       192.168.2.2    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link       192.168.2.2    281
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 16     58 ::/0                     On-link
  1    306 ::1/128                  On-link
 16     58 2001::/32                On-link
 16    306 2001:0:4137:9e50:2c3d:4c1:3f57:fdfd/128
                                    On-link
 14    281 fe80::/64                On-link
 16    306 fe80::/64                On-link
 14    281 fe80::11e5:8d40:a98c:af9/128
                                    On-link
 16    306 fe80::2c3d:4c1:3f57:fdfd/128
                                    On-link
  1    306 ff00::/8                 On-link
 16    306 ff00::/8                 On-link
 14    281 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

```

---

### Post by Huufarted on 2009-03-05
I assume your router is 192.168.2.1 ?

Also post us 'ifconfig -a' from Ubuntu and 'ipconfig /all' from Windows, please.

---

### Post by questioning on 2009-03-05
just use firefox3.1 its awesome!

---

### Post by Matthileo on 2009-03-05
> **Huufarted said:**
> I assume your router is 192.168.2.1 ?
Yes.

> Also post us 'ifconfig -a' from Ubuntu and 'ipconfig /all' from Windows, please.

Ubuntu
```
matt@matt-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:56:1c:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9064 (9.0 KB)  TX bytes:9064 (9.0 KB)

pan0      Link encap:Ethernet  HWaddr 86:3c:d4:b0:5c:0d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:a9:8b:93  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fea9:8b93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137595 (137.5 KB)  TX bytes:17110 (17.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-A9-8B-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Windows
```
C:\Users\matt> ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : matt-laptop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Belkin

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 00-1F-E1-DB-E6-EE
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Wireless WiFi Link 4965AGN
   Physical Address. . . . . . . . . : 00-1F-3B-A9-8B-93
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11e5:8d40:a98c:af9%14(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.2(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, March 05, 2009 8:32:41 AM
   Lease Expires . . . . . . . . . . : Sunday, April 11, 2145 3:07:05 PM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 234889019
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-10-FB-49-CF-00-1D-09-56-1C-08
   DNS Servers . . . . . . . . . . . : 192.168.2.1
                                       68.87.77.130
                                       68.87.72.130
                                       68.87.75.194
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller
   Physical Address. . . . . . . . . : 00-1D-09-56-1C-08
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{076768F0-BFB2-4F08-A011-D7FC616CA594}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{C381B1CD-3A13-45D6-88EF-C47062091004}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:2c3d:4c1:3f57:fdfd(Preferred)
   Link-local IPv6 Address . . . . . : fe80::2c3d:4c1:3f57:fdfd%16(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.{593B5C61-20FA-4055-BC71-47FBE627B1E6}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Reusable Microsoft 6To4 Adapter:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.Belkin:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

```

---

### Post by Matthileo on 2009-03-05
> **questioning said:**
> just use firefox3.1 its awesome!

I'll wait for the stable release. :)

---

### Post by Brandon.Viking on 2009-03-05
Might not be the os ... it might just be wireless. Try to find any differences using Ethernet cable. Wireless is not the best medium to be using for speed and low latency.
Granted most would be faster than internet connection but ...

Only real way to tell is to do comparative analysis using some packet capture software like Wireshark..

Load a page under windows verses loading page under linux while capturing network traffic.

Compare captures to see where the delay exists.

Regards,
Brandon.

---

### Post by Matthileo on 2009-03-05
> **Brandon.Viking said:**
> Might not be the os ... it might just be wireless. Try to find any differences using Ethernet cable. Wireless is not the best medium to be using for speed and low latency.
Granted most would be faster than internet connection but ...

Only real way to tell is to do comparative analysis using some packet capture software like Wireshark..

Load a page under windows verses loading page under linux while capturing network traffic.

Compare captures to see where the delay exists.

Regards,
Brandon.

I'll try that when I have more time.
It's the week before spring break, which means...
Midterms! Yay!

I might be able to get this done tonight...otherwise it will have to wait for the weekend.

---

### Post by nidelius on 2009-03-05
Try change your DNS servers
Worked for me
see 
[http://ubuntuforums.org/showthread.php?t=1087687](http://ubuntuforums.org/showthread.php?t=1087687)

---

### Post by Huufarted on 2009-03-05
Looking a little bit deeper:


```
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:a9:8b:93  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fea9:8b93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137595 (137.5 KB)  TX bytes:17110 (17.1 KB)

```

```

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Wireless WiFi Link 4965AGN
   Physical Address. . . . . . . . . : 00-1F-3B-A9-8B-93
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11e5:8d40:a98c:af9%14(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.2(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, March 05, 2009 8:32:41 AM
   Lease Expires . . . . . . . . . . : Sunday, April 11, 2145 3:07:05 PM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 234889019
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-10-FB-49-CF-00-1D-09-56-1C-08
   DNS Servers . . . . . . . . . . . : 192.168.2.1
                                       68.87.77.130
                                       68.87.72.130
                                       68.87.75.194
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

```

I need you to give us these results:
cat /etc/resolv.conf

```

That will give us your DNS servers.  We're just wanting to see if they're the same as Windows.

I am not trying to insult your intelligence, so I apologize if it appears that way.

Also, some wireless drivers (and I don't have a list) do have known instability issues.  I wonder if this is perhaps an example of that.

---

### Post by nidelius on 2009-03-05
> **Huufarted said:**
> 
Also, some wireless drivers (and I don't have a list) do have known instability issues.  I wonder if this is perhaps an example of that.


Might actually be, I'm also running on 4965AGN. Although when using my ISPs DNS servers it's working fine for me at least.

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at f0000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number d5-6c-e9-ff-ff-e8-13-00

	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

---

### Post by Zimmer on 2009-03-05
> **Matthileo said:**
> There is a 3-6 second delay before firefox begins downloading a webpage in ubuntu. 

I'm not sure what MTU is.
Max Transmission Units, a setting in your router:check your ISP site for their recommended settings.

Also, hunted around for things I have done to speed up FF in the past.
you might want to try:

Type about:config into the firefox address bar.

Use the filter to search IPv6, and set network.dns.disableIPv6 to true

(bearing in mind that IPv6 is coming sometime soon...maybe..)

---

### Post by Matthileo on 2009-03-05
> **Huufarted said:**
> Looking a little bit deeper:


```
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:a9:8b:93  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fea9:8b93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137595 (137.5 KB)  TX bytes:17110 (17.1 KB)

```

```

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : Belkin
   Description . . . . . . . . . . . : Intel(R) Wireless WiFi Link 4965AGN
   Physical Address. . . . . . . . . : 00-1F-3B-A9-8B-93
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11e5:8d40:a98c:af9%14(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.2(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, March 05, 2009 8:32:41 AM
   Lease Expires . . . . . . . . . . : Sunday, April 11, 2145 3:07:05 PM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 234889019
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-10-FB-49-CF-00-1D-09-56-1C-08
   DNS Servers . . . . . . . . . . . : 192.168.2.1
                                       68.87.77.130
                                       68.87.72.130
                                       68.87.75.194
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

```

I need you to give us these results:
cat /etc/resolv.conf

```

That will give us your DNS servers.  We're just wanting to see if they're the same as Windows.

I am not trying to insult your intelligence, so I apologize if it appears that way.

Also, some wireless drivers (and I don't have a list) do have known instability issues.  I wonder if this is perhaps an example of that.
Thanks.

/etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.2.1
nameserver 68.87.77.130
nameserver 68.87.72.130
search Belkin

```

---

### Post by Huufarted on 2009-03-05
Everything looks proper, bud.  Your windows settings jive with your Ubuntu settings pretty well.  At this point, I'm going to point the blame at the drivers.  If that is the case, this is the end of the road for me on this thread.  I'm sorry I couldn't help you more.

Your DNS settings match between the two.  The default route on Ubuntu is the same as that in Windows (default route = gateway).  The IP addresses are the same, even.  I would try finding out which chipset your wireless uses and find better ones PERHAPS through Google.  For instance, my laptop (I'm not on it right now) uses Atheros AR5007EG.  For me to find drivers, all I'd do is search for 'AR5007EG drivers ubuntu' and go from there.  I hope you find your answer.

Good luck!

---

### Post by nidelius on 2009-03-05
> **Matthileo said:**
> Thanks.

/etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.2.1
nameserver 68.87.77.130
nameserver 68.87.72.130
search Belkin

```


try
```

sudo gedit /etc/resolv.conf

#nameserver 192.168.2.1
nameserver 68.87.77.130
nameserver 68.87.72.130

save and close

```

now surf to a website you didn't visit before since you started the computer this time, so that it's not in the cache and chech if it's working. Thats what worked for me.

---

### Post by Matthileo on 2009-03-05
> **Huufarted said:**
> Everything looks proper, bud.  Your windows settings jive with your Ubuntu settings pretty well.  At this point, I'm going to point the blame at the drivers.  If that is the case, this is the end of the road for me on this thread.  I'm sorry I couldn't help you more.

Your DNS settings match between the two.  The default route on Ubuntu is the same as that in Windows (default route = gateway).  The IP addresses are the same, even.  I would try finding out which chipset your wireless uses and find better ones PERHAPS through Google.  For instance, my laptop (I'm not on it right now) uses Atheros AR5007EG.  For me to find drivers, all I'd do is search for 'AR5007EG drivers ubuntu' and go from there.  I hope you find your answer.

Good luck!

Thanks!
I got it figured out.
After looking at the windows and ubuntu nameservers I noticed there was one on windows that wasn't listed on ubuntu.
I added it to /etc/resolvconf/resolv.conf.d/base and everything seems to be working great now.

---

### Post by Huufarted on 2009-03-05
HA!  That surprises me.  That means the first 2 DNS entries in there were failing and Windows had the third one so no problem.  I never would have thought that...  I'm glad you got it worked out!

---

### Post by odxa20 on 2012-12-11
Follow this and everything is going to be ultra fast!!! :popcorn::popcorn::popcorn:
[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/]("http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/")

---

### Post by Old_Grey_Wolf on 2012-12-11
Old thread on unsupported releases closed.

---

