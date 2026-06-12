---
title: "Server - Network speed randomly degrades"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by baokeyai on 2012-11-27
Hello,
 
The short:
My network speed to the internet degrades randomly over time from 150Mbs/65Mbs to 5Mbs/5Mbs
 
If I perform a "sudo /etc/init.d/networking restart" it reverts back to it's original speed.
 
 
The long:
 
I've had this problem as far as I can remember, but I originally thought it was due to Time Warner Cable services.
 
I used to have Time Warner Wide Band 50/5 and now am on Verizon Fios 150/65.
 
I've had ubuntu version from 9.04 to now 12.04.
 
I've had 2 machines all exhibiting the same problem. First box was an AMD with Dual NICs and now I'm on a Sandy Bridge 1155 socket asus board with Dual NICs.
 
The modem hooks into one NIC where I'm using dhclient as anyone would. The second NIC is connected to my lan 8 port gig switch to other devices.
 
All of the hardware description is just to frame that I don't think the issue is hardware related. I have a feeling it must be some sort of configuration related.
 
So my ubuntu "nat"ing is all done via FireStarter.
 
When I install ubuntu-server, I pretty much start by installing Ubuntu-Desktop... why? Cause I'm too dumb/lazy to do everything from the command prompt.
 
Why do I install the ubuntu server? Back before 11, it used a different Kernel and I noticed significant latency improvement running the server kernel instead of the desktop kernel. 
 
I haven't tested doing a clean install of Ubuntu-Desktop, but if someone can give me any reason why it would solve my problem, then I guess I'll test it.
 
So after Ubuntu-Desktop, I install FireStarter and when that's ready I launch the Firestarter wizard for easy mode router. That all works perfectly and everyone in my family enjoys the internet with super low latencies and super fast bandwidth.... but only for so long.
 
After a random amount of time, the bandwidth drops from the (latency/Down/Up) 3ms/150Mbs/65Mbs to 40ms/5Mbs/5Mbs.
 
Now this can be immediately solved by running "sudo /etc/init.d/networking restart"
 
It doesn't seem to be memory as the router is showing 6Gs free and the cpu load is reporting 0.06, 0.05, 0.15
 
However, my question is what is causing this?
Has anyone else run into a similar issue like this?

---

### Post by Vermonster on 2012-11-27
Same issue here, except mine disconnects for 30 seconds and reconnects. Strange.

---

### Post by varunendra on 2012-11-29
> **baokeyai said:**
> However, my question is what is causing this?
Might be a buggy driver ? Let us see -
```
lspci -nnk | grep -iA2 net
ifconfig -a
```

---

### Post by baokeyai on 2012-11-29
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:820d]
    Kernel driver in use: r8169

---

### Post by baokeyai on 2012-11-29
eth0      Link encap:Ethernet  HWaddr f4:6d:04:98:ee:3e  
          inet addr:aaa.bbb.ccc.ddd  Bcast:aaa.bbb.ccc.255  Mask:255.255.255.0
          inet6 addr: aaaa::bbbb:cccc:dddd:eeee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:258161053 (258.1 MB)  TX bytes:93045347 (93.0 MB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr f4:6d:04:98:e4:2f  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe98:e42f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63549423 (63.5 MB)  TX bytes:195828060 (195.8 MB)
          Interrupt:18 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2836 (2.8 KB)  TX bytes:2836 (2.8 KB)

virbr0    Link encap:Ethernet  HWaddr 72:2e:aa:a8:99:91  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by baokeyai on 2012-11-30
So I got where you were going with the drivers. I've updated both of my nic drivers to the latest version. I'll poke around with this for a day or so and see if the old problem still persists.

---

### Post by baokeyai on 2012-11-30
disregard, the problem already resurfaced with minimal efforts to reproduce. So I'm going to say it's probably not the drivers.

---

### Post by varunendra on 2012-12-02
Sorry for the long delay, but I got no clues from the outputs anyway, except that you may try a few things -

1) Disable IPv6 : Easy and should have no side-effects. You can disable it by adding the following to /etc/sysctl.conf file -
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1

2) Try NOT using Network Manager. Use /etc/network/interfaces instead to see if it is some NM bug : [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html) (make sure 'mode' is set to "managed=**false**" in /etc/NetworkManager/NetworkManager.conf file if you use 'interfaces' file to manage any interface).

3) If you can make sure the Intel port (using e1000e driver) alone is working fine (modem-to-server-only connection, downloading some heavy stuff), you may try the proprietary driver from realtek for the otdher port -  [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

.

---

### Post by baokeyai on 2012-12-05
No problem about any delays, I was about to cry another plea for help. I've just modified the ipv6 settings. Confirmed I don't see any settings in ifconfig.

I've confirmed the network manager is good. On the weekend, when no one is using the internet I'll experiment with just the individual drivers.

Thanks for the suggestions.

Btw, I also removed firestarter as I realize the support for that has died a while ago and I'm explicitly on ufw now.

Of course I wouldn't be posting here if the same problems were resolved so I don't think it was necessarily firestarter.

---

### Post by baokeyai on 2012-12-06
Sadly no dice.

Got home, downloading at 5Mbs again.

Did a networking restart

and it flipped right back to 150Mbs

---

