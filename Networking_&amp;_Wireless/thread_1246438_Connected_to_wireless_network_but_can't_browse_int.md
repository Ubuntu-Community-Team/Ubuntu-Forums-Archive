---
title: "Connected to wireless network but can't browse internet"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by AprilWriter on 2009-08-21
[SIZE=3]Hello all!!  Thanks in advance for the help!!!   :P

I am running 7.04 (Feisty Fawn) on an I386 PC.  My wireless network is connected to a Linksys router (wrt54g) and a Hawking Wireless-G PCI card.  

The Network Manager found all the local wireless networks, I clicked on mine, entered the WEP key and was able to connect.  However when I go to browse the internet, Firefox is unable to browse. 

I've followed this guide step by step  and have not been able to fix my problem. I've established that there is not a problem with my driver. My router seems to be communicating with the computer.  

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Pings to the ip address of the computer (found using windows xp partition, BTW internet works fine in windows) The router address, and any internet addresses fail.

I also tried using a static manual configuration by entering my IP address, subnet, default gate way and DNS severs.  In this setting the network manager does even report a connection, and I am unable to browse.

I tried to disable my firewall using these directions:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall)
but the command was not recognized.[/SIZE] (see results section below)

[SIZE=3]I did my best to change my IPv6 to IPv4 
I did this:

*Firefox specific **In the address bar type *about:config*. Find this line *network.dns.disableIPv6* and double click on it to change the value to *true*. *[/SIZE]
[SIZE=4][B]
Here are all my results for the various tests:[/B][/SIZE]

   Result for lshw
   
  *-network:1
               description: Wireless interface
               product: RT2561/RT61 802.11g PCI
               vendor: RaLink
               physical id: 10
               bus info: pci@00:10.0
               logical name: ra1
               version: 00
               serial: 00:0e:3b:08:b4:51
               width: 32 bits
               clock: 33MHz
               capabilities: bus_master cap_list ethernet physical wireless
               configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
               resources: iomemory:febe8000-febeffff irq:11
   
  *********************************************************************
   
  results for iwconfig:
   
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  ra1       RT61 Wireless  ESSID:""  Nickname:""
            Mode:Managed  Frequency:2.437 GHz  Bit Rate=54 Mb/s   
            RTS thr:off   Fragment thr:off
            Link Quality=75/100  Signal level:-59 dBm  Noise level:-111 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  ***************************************************************************
   
  results for: ifconfig:
   
   
  eth0      Link encap:Ethernet  HWaddr 00:10:4B:64:0C:7E  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
            Interrupt:5 Base address:0xef00 
   
  eth0:avah Link encap:Ethernet  HWaddr 00:10:4B:64:0C:7E  
            inet addr:169.254.4.121  Bcast:169.254.255.255  Mask:255.255.0.0
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            Interrupt:5 Base address:0xef00 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:211 errors:0 dropped:0 overruns:0 frame:0
            TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:18646 (18.2 KiB)  TX bytes:18646 (18.2 KiB)
   
  ra1       Link encap:Ethernet  HWaddr 00:0E:3B:08:B4:51  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:97669 errors:39 dropped:0 overruns:0 frame:0
            TX packets:92475 errors:1 dropped:1 overruns:0 carrier:0
            collisions:3 txqueuelen:1000 
            RX bytes:8164708 (7.7 MiB)  TX bytes:1080 (1.0 KiB)
            Interrupt:11 
   
  ************************************************************************
   
  results for:  cat /etc/resolv.conf
   
  nameserver 68.94.156.1
  nameserver 68.94.157.1
  search [www.google.com]("http://www.google.com")
   
  **************************************************************************
   
  Atempt to disable firewall: 
   
  just2ofus@just2ofus-desktop:~$ # iptables -F
  just2ofus@just2ofus-desktop:~$ iptables -F
  WARNING: Error inserting x_tables (/lib/modules/2.6.20-15-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
  FATAL: Error inserting ip_tables (/lib/modules/2.6.20-15-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
  iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
  Perhaps iptables or your kernel needs to be upgraded.
  


[SIZE=3][B]I am at my wits end. :confused: Please help me!!!  Anwser within the forum or even better email me; AprilGWriter(at)yahoo.com   

:KSTHANK YOU SO MUCH!!!![/B][/SIZE]:KS

---

### Post by The Toxic Mite on 2009-08-21
> **AprilWriter said:**
> [SIZE=3]Hello all!!  Thanks in advance for the help!!!   :P

I am running 7.04 (Feisty Fawn)[snip][/SIZE]

Err...

I wouldn't recommend running 7.04 - it's no longer supported.

[Click here to get Ubuntu 9.04](http://www.ubuntu.com/getubuntu/download)

---

### Post by AprilWriter on 2009-08-21
Unfortunately later version won't work on my computer, it's too old. I tried to install 8.04.3 and it didn't work.  My computer is an I386  I suppose I could switch to a recent version of xbuntu...but I'd like to make this work. I've got everything going swimmingly except the internet.

So what can I do to fix the internet?

---

### Post by Iowan on 2009-08-21
You might try **sudo iptables -F**. I haven't tried flushing iptables, so hope this doesn't cause issues...  What is currently in */etc/network/interfaces*?

---

### Post by AprilWriter on 2009-08-21
I tried that once before: 

Attempt to disable firewall: 
   
  just2ofus@just2ofus-desktop:~$ # iptables -F
  just2ofus@just2ofus-desktop:~$ iptables -F
  WARNING: Error inserting x_tables (/lib/modules/2.6.20-15-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.20-15-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
  iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
  Perhaps iptables or your kernel needs to be upgraded.

I tried it again and this time nothing happened.  The command line appeared again. 

I also tried the */etc/network/interface *and it told me "permission denied"  

Strangely after this latest restart I have not been able to connect to the wireless network. God!  It seems things have gotten worse!  :confused:

---

### Post by AprilWriter on 2009-08-21
With a little bit of tweaking I got it connected to the wireless network but still no luck when it comes to browsing the internet. Ugg!

Thanks again :)

---

### Post by reddingo90 on 2009-08-22
Hi AprilWriter, I don't know if this will help but I've seen this elsewhere, please check that you have work offline unticked in Firefox. Click file, scroll down and if work offline is ticked, untick it. Adrian

---

### Post by Iowan on 2009-08-22
> **AprilWriter said:**
> I also tried the */etc/network/interface *and it told me "permission denied"  */etc/network/interfaces* cannot be executed. To view it, use ```
cat /etc/network/interfaces
``` or ```
less /etc/network/interfaces
```

---

### Post by AprilWriter on 2009-08-22
Thanks Adrian, 

I checked to make sure the "work offline" is not clicked on my Firefox browser. If only it were that simple.  :)

Iowan, 

**Here is the result for cat  */etc/network/interface.  *Thanks for correcting the code for me:  **

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I got the same exact result for ** less  **[I]**/etc/network/interface**[B].

[/B][/I]Does this help?

Thanks,

April
****

---

### Post by Iowan on 2009-08-22
> **AprilWriter said:**
> 
I got the same exact result for ** less  /etc/network/interface**Results would be the same - main difference,  **less** pauses after a pageful, and (on a "real' terminal - like CTRL-ALT-F1) it lets you scroll back. **cat** displays the entire file and exits.
How many interfaces do you have on that machine? You mentioned a wireless interface. It appears (from **ifconfig**) that you may have a wired card as well. Your */etc/network/interfaces* file could probably be cleaned up by removing the unnecessary eth#'s, dunno about the ath0, and don't see ra1. Caution would suggest making a backup copy first...
Also, please post results of **route -n** - that should show the gateway(s).

---

### Post by AprilWriter on 2009-08-22
Finally got it working!!!  I got rid of Windows XP and am running only Feisty Fawn, and what do you know, I easily got the internet working thanks to the advice of all you smart people.  Thank you so much!

Now if I can only get WINE up and going!  

THANK YOU ALL!!!!!!!!

:guitar:

---

