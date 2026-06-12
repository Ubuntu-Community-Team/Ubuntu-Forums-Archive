---
title: "Please help. No internet after upgrading to 9.10"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by n3xtgen on 2009-12-10
I installed Ubuntu 9.04 yesterday and everything worked fine. Today I had upgraded to version 9.10 and then after the restart my internet no longer worked. It found my router when searching for a network and connected to it fine but there was no internet page's loading, even when I connect it through a network cable. The internet worked fine with 9.04 why did it just suddenly stop with the new version 9.10? I am on a IBM Thinkpad T43 and a new user to Ubuntu.

Any Help?

Thanks

---

### Post by n3xtgen on 2009-12-11
I installed Ubuntu 9.04 yesterday and everything worked fine. Today I had upgraded to version 9.10 and then after the restart my internet no longer worked. It found my router when searching for a network and connected to it fine but there was no internet page's loading, even when I connect it through a network cable. The internet worked fine with 9.04 why did it just suddenly stop with the new version 9.10? I am on a IBM Thinkpad T43 and a new user to Ubuntu.

Any Help?

Thanks

---

### Post by Iowan on 2009-12-11
Karmic's networking seems to have a few rough edges - perhaps some might be smoothed with updates... but you gotta get to internet first. Post results of **lshw -C network** and **ifconfig -a** (from a terminal).

---

### Post by n3xtgen on 2009-12-11
Thank you for the reply. Here is **lshw -C network**

>     WARNING: you should run this program as super-user.
    *-network               
         description: Ethernet interface
         product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 11
         serial: 00:16:41:54:49:e7
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5751m-v3.46a latency=0 multicast=yes
         resources: irq:16 memory:b0200000-b020ffff
    *-network
         description: Wireless interface
         product: PRO/Wireless 2200BG [Calexico2] Network Connection
         vendor: Intel Corporation
         physical id: 2
         bus info: pci@0000:0b:02.0
         logical name: eth1
         version: 05
         serial: 00:16:6f:1c:7e:53
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.100 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
         resources: irq:21 memory:b4001000-b4001fff
  


[B]ifconfig -a
[/B]>     eth0      Link encap:Ethernet  HWaddr 00:16:41:54:49:e7  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:16
   
  eth1      Link encap:Ethernet  HWaddr 00:16:6f:1c:7e:53  
            inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
            inet6 addr: fe80::216:6fff:fe1c:7e53/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:37 errors:0 dropped:0 overruns:0 frame:0
            TX packets:31 errors:0 dropped:4 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:6685 (6.6 KB)  TX bytes:4539 (4.5 KB)
            Interrupt:21 Base address:0x2000 Memory:b4001000-b4001fff
   
  irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
            NOARP  MTU:2048  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:8
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  

---

### Post by bluesscream on 2009-12-11
had a similar problem some updates ago. In lsmod my wlan driver was gone, had to load it manually.
In your case try: 
sudo modprobe ipw2200

---

### Post by zoggerman on 2009-12-11
> **n3xtgen said:**
> I installed Ubuntu 9.04 yesterday and everything worked fine. Today I had upgraded to version 9.10 and then after the restart my internet no longer worked. It found my router when searching for a network and connected to it fine but there was no internet page's loading, even when I connect it through a network cable. The internet worked fine with 9.04 why did it just suddenly stop with the new version 9.10? I am on a IBM Thinkpad T43 and a new user to Ubuntu.

Any Help?

Thanks


--if you are this new, why not just go back to what worked? That version is just not that old or out of date, etc. Keep that, then just hold out until 10.4 is released next year, try it live first, see if it still works, if it does, upgrade then. A lot of people are having a ton of networking problems with 9.10, which makes it problematic to get any fixes if you can't even get online in the first place.

---

### Post by cariboo on 2009-12-11
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by n3xtgen on 2009-12-11
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your two threads.

Sorry about that. I thought I posted one in the wrong section.

> **bluesscream said:**
> had a similar problem some updates ago. In lsmod my wlan driver was gone, had to load it manually.
In your case try: 
sudo modprobe ipw2200

**Edit**: 

I typed that code into the terminal but no luck, nothing changed. Anything else I could do? I just dont understand, it says that its connected to my wireless router but there's no internet.

Thanks

---

### Post by uncaspi on 2009-12-11
Please look in netstat -r to see if you had the default route. The one called default and with UG near the end of line. If not you have to add the default route sudo /sbin/route add default gw <ip address of the router gateway usually 192.168.0.1 or 192.168.1.1>  eth0   
which is your wired connection to start with this first.

---

### Post by uncaspi on 2009-12-11
seems that your router gateway is 19.168.2.1 from posting of sudo /sbin/ifconfig

---

### Post by n3xtgen on 2009-12-11
Yes I have a default connection. Its **eth1 **but my Genmask says: **0.0.0.0** Is it supposed to be like that?

Thanks

---

### Post by uncaspi on 2009-12-11
eth1 is your wireless card and it's more difficult to connect to wireless then wired in Ubuntu, so if you could try to plug in the wire in eth0 and run sudo dhclient eth0

---

### Post by Iowan on 2009-12-11
Just checked **route** on this machine: it has 0.0.0.0 for genmask on gateway (albeit a wired connection). The gateway address should be that of your router.

---

### Post by n3xtgen on 2009-12-11
Here is [B]netstat -r

[/B]* tried to match the columns with same color*>     Kernel IP routing table
  [COLOR=Red]Destination[/COLOR][COLOR=SandyBrown]     Gateway[/COLOR] [COLOR=YellowGreen]        Genmask[/COLOR]         [COLOR=MediumTurquoise]Flags[/COLOR] [COLOR=RoyalBlue]  MSS[/COLOR] [COLOR=RoyalBlue]Window  irtt[/COLOR] Iface
  [COLOR=Red]192.168.2.0[/COLOR] [COLOR=SandyBrown]    *[/COLOR]               [COLOR=YellowGreen]255.255.255.0[/COLOR][COLOR=MediumTurquoise]        U[/COLOR] [COLOR=RoyalBlue]        0 0          0[/COLOR] eth0
  [COLOR=Red]192.168.2.0[/COLOR] [COLOR=SandyBrown]    *[/COLOR]               [COLOR=YellowGreen]255.255.255.0[/COLOR][COLOR=MediumTurquoise]        U[/COLOR] [COLOR=RoyalBlue]        0 0          0[/COLOR] eth1
  [COLOR=Red]link-local[/COLOR]             [COLOR=SandyBrown]*[/COLOR] [COLOR=YellowGreen]              255.255.0.0[/COLOR]         [COLOR=MediumTurquoise]      U[/COLOR] [COLOR=RoyalBlue]        0 0          0[/COLOR] eth1
  [COLOR=Red]default[/COLOR][COLOR=SandyBrown]              192.168.2.1[/COLOR] [COLOR=YellowGreen]    0.0.0.0[/COLOR]  [COLOR=MediumTurquoise]        UG[/COLOR][COLOR=RoyalBlue]        0 0          0[/COLOR] eth0
  **sudo dhclient eth0**
>     Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/00:16:41:54:49:e7
  Sending on   LPF/eth0/00:16:41:54:49:e7
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPOFFER of 192.168.2.101 from 192.168.2.1
  DHCPREQUEST of 192.168.2.101 on eth0 to 255.255.255.255 port 67
  DHCPACK of 192.168.2.101 from 192.168.2.1
  bound to 192.168.2.101 -- renewal in 36179 seconds.
  Anything I can do?

---

### Post by joes7 on 2009-12-11
You must configure it manually. I had the same problem about two months ago when I had Ubuntu (now I have Xubuntu).

---

### Post by n3xtgen on 2009-12-11
How do I configure it manually? I am new to Ubuntu

---

### Post by uncaspi on 2009-12-11
Now you're wired through eth0. Is that correct? Can you ping google.com

---

### Post by n3xtgen on 2009-12-11
Yes I can. When I run the command I get the following:

**64 bytes from [www.google.com](www.google.com) (64.233.169.104): icmp_seq=1 ttl=244 time=313 ms**

And the sequence just keeps increasing by and the time changes.

---

### Post by uncaspi on 2009-12-11
Can you browse the internet? Are you satisfied with wire or shall we proceed with the wireless?

---

### Post by n3xtgen on 2009-12-11
well nothing is working. There is no internet working for me. I get the message saying that its connected but when I load a webpage it takes about 5min and I get the timed out message. I dont know whats wrong because it says im connected but no pages are loading.

---

### Post by uncaspi on 2009-12-11
Well you are connected when you can ping google.com
So it probably has to do with firefox settings.
Try Epipany browser found in <Applications> <Internet>

---

### Post by n3xtgen on 2009-12-11
Empathy browser is not listed there only firefox browser.:(

---

### Post by uncaspi on 2009-12-12
You could try to disable ipv6 in firefox or remove it and then install it again. sudo apt-get remove firefox
sudo apt-get install firefox

To disable ipv6 type about:config in browser address field.
Then proceed and move to
network.dns.disableIPv6 and set it to true

These is the only things I can think you could do. I'm not an expert in firefox settings. Sorry.
PS If this doesn't help you could install another browser

---

### Post by n3xtgen on 2009-12-12
I got firefox working by changing the IPv6:D. Now I just need to fix so I can update. Any idea on how to do that? I cant download anything when I go to the software center. I keep getting the message "Not Available In The Current Data"

Edit: I tried **sudo apt-get update** but it just hangs there at 0% and does nothing.

---

### Post by uncaspi on 2009-12-12
There is no newer versions than 9.10 and packages for upgrading shows up every week, if this helps.

---

### Post by n3xtgen on 2009-12-12
I go to software center and it says "Not Available In The Current Data" and there is no install button. Any way to fix this?

---

### Post by Nightsurfer on 2009-12-12
Any chance your router/firewall has any form of filtering enabled... may be listed as "parental control", "content filtering", etc? If so your ability to see or ping Google may not help. certainly your post shows that there is not a problem with the wired connection to your router.

---

### Post by n3xtgen on 2009-12-12
thanks for the help everyone. Im just going to go back to 9.04 where I had no problems. Will wait till version 10 comes out

---

