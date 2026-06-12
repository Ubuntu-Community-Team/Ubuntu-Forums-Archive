---
title: "Can't ping anything with Linksys wrt100"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by neuralsimulation on 2009-06-24
Hi, I have a Toshiba satellite A305 laptop, running Jaunty (latest release).  I can use my wireless router at home just fine (and every other router I've ever tried), but when I take my computer over to my friend's house, who has a Linksys WRT100, I can connect to the wireless fine, but I can't ping anything. Usually. Occasionally, it works as expected. (about 1/10 of the times when I reboot). 

His windows machine, and my dual-boot Windows on my laptop can connect just fine and surf the web just fine. I can also connect to his router with a wire, which works as expected.  When it's broken, I can't ping sites, even if I enter the IP address. I can't even ping anything on the LAN. 
 
I've tried everything that I could find to fix it, except disable IPv6, because it's not possible to disable ipv6 in Jaunty (thanks!). Although it has worked mysteriously a couple of times when I thought I had disabled ipv6, only to fail again on the next reboot, I think this must be a coincidence. 

I'm at the end of my tether here and considering going back to Windows. How can we diagnose this?

---

### Post by alastair on 2009-06-24
When it's broken - open a terminal and type (and copy/paste output) :

ipconfig -a

route -n

iwconfig

and perhaps also the contents of your network file :

/etc/network/interfaces

If you are using NetworkManager - I assume you see the wlan in the drop-down list of wlan networks?
You select to connect?
Did you have to enter a wlan key/credentials?

---

### Post by neuralsimulation on 2009-06-24
> **alastair said:**
> 
If you are using NetworkManager - I assume you see the wlan in the drop-down list of wlan networks?
You select to connect?
Did you have to enter a wlan key/credentials?

Thanks for the reply. I'll the output to the commands you requested next time I'm over there, probably tomorrow.

I do have to enter credentials, and it seems to accept it and connect fine. The same credentials work in windows, and I've entered them multiple times, and also, like I said, sometimes it mysteriously works (and I'm definitely connected to the correct router in that case).

---

### Post by neuralsimulation on 2009-06-25
bash:~$ ipconfig -a
bash: ipconfig: command not found

I think you meant ifconfig, so I tried that

bash:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:32:63:f7  
          inet6 addr: fe80::21e:33ff:fe32:63f7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266539 (266.5 KB)  TX bytes:54015 (54.0 KB)
          Interrupt:250 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1955 (1.9 KB)  TX bytes:1955 (1.9 KB)

pan0      Link encap:Ethernet  HWaddr 56:d8:98:ba:f7:2b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.20.1  Bcast:172.16.20.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:26:09:89  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe26:989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12597 (12.5 KB)  TX bytes:17017 (17.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-26-09-89-39-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bash:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.20.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

bash:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ONET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:0F:68:EF   
          Bit Rate=60 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-51 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

contents of /etc/network/interfaces:
auto lo
iface lo inet loopback


Thanks in advance for the help! Please save me from windows doom!

---

### Post by neuralsimulation on 2009-06-25
I noticed this:

RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0

I'm guessing 63/116 errors is not good. I'd bet it's related to ipv6, since I've seen a post from a windows user that they had to disable ipv6 in windows for it to work with 1.0.0.4 of the router firmware. The thing is that disabling ipv6 in firefox has no effect at all, so that's kind of throwing me off the trail.

If only there was some way to test my theory without recompiling the kernel.....

Edit: oops, looks like I read that wrong. 0 errors? Ugh!

---

### Post by neuralsimulation on 2009-06-26
Any ideas? 

Did I mention I'm a software engineer? I'm not terribly familiar with low-level routing protocols, but if someone has a resource I can follow to help diagnose this, I'll throw my hat into the ring. I have eclipse installed. Desperate times....

---

### Post by neuralsimulation on 2009-06-30
Last time I bump the thread, sorry to be an attention hog. How about a bribe? I'll donate $20 to the charity of your choice if you can help me solve this.

---

### Post by IronOutsider on 2009-06-30
This could very easily be a couple of things. 

-Since I notice you got the address 192.168.1.100, you might be getting the same address as your buddy at his house. Another thing that has happened to me while using that particular address (no idea why) is I'll lose dns and won't be able to ping anything by its domain name. This would happen on my windows and linux boxes. I think it's probably a firmware issue with linksys, but getting a different address like 192.168.1.101 and above seems to fix my connection sometimes. You can also try sudo ```
sudo /etc/init.d/networking restart
``` and see if that gives you any errors.

---

### Post by neuralsimulation on 2009-07-03
> **IronOutsider said:**
> This could very easily be a couple of things. 

-Since I notice you got the address 192.168.1.100, you might be getting the same address as your buddy at his house. Another thing that has happened to me while using that particular address (no idea why) is I'll lose dns and won't be able to ping anything by its domain name. This would happen on my windows and linux boxes

Well, I tried 192.168.1.68 (subnet 255.255.255.0, gateway 192.168.1.1) The router seemed happy enough to give me the IP, but I still could not ping anything.

Other computers, including a mac, and my laptop (running windows), can connect to this router just fine, wirelessly.

Interestingly enough, when we look at the routing table on the router config page, when I'm on DHCP, I show up, but when I use a manual IP I don't show up (although Ubuntu continues to claim I'm connected to it).

Restarting the network yields this:

* Reconfiguring network interfaces...                                          
Ignoring unknown interface wlan0=wlan0.

Thanks for trying. I guess unless anyone has any more ideas, I'm just out of luck until/unless some magic update comes along to fix this.

The $20 donation is still on the table, and also my time as a software engineer is on the table, but I'm not quite sure where to begin, I need some kind of resource to jump-start the process.

---

