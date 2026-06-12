---
title: "PPPoE connection problems"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by cguy on 2009-01-23
Since I can't set up a PPPoE connection with Network Manager, I always set it up manually. (pppoeconf)

However, for the last couple of days the connection won't work properly anymore. It does start at boot time, but I can't directly surf the Internet. I must start the terminal, then type
sudo poff dsl-provider
then
sudo pon dsl-provider
Basically I have to reload the modules.

pppoeconf stops at "Looking for PPPoE Access Concentrator on eth1...". I have an onboard ethernet (pan0) and an ethernet card (eth1)


What's wrong here?
I remember I have had the same problem on an older Ubuntu release, but never tried to solve it. (now I use Intrepid)

---

### Post by superprash2003 on 2009-01-23
post output of ifconfig from the terminal at bootup

---

### Post by cguy on 2009-01-23
> eth1      Link encap:Ethernet  HWaddr 00:40:f4:cb:bc:5e  
          inet6 addr: fe80::240:f4ff:fecb:bc5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1408860 (1.4 MB)  TX bytes:2571 (2.5 KB)
          Interrupt:18 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16966 (16.9 KB)  TX bytes:16966 (16.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.121.188.38  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:337 (337.0 B)  TX bytes:349 (349.0 B)


And after poff+pon:
> eth1      Link encap:Ethernet  HWaddr 00:40:f4:cb:bc:5e  
          inet6 addr: 2002:5679:bcdf:5:240:f4ff:fecb:bc5e/64 Scope:Global
          inet6 addr: fec0::5:240:f4ff:fecb:bc5e/64 Scope:Site
          inet6 addr: fe80::240:f4ff:fecb:bc5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3374612 (3.3 MB)  TX bytes:185242 (185.2 KB)
          Interrupt:18 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16966 (16.9 KB)  TX bytes:16966 (16.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.121.188.227  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:537787 (537.7 KB)  TX bytes:167245 (167.2 KB)


---

### Post by superprash2003 on 2009-02-06
do you use IPV6?

---

### Post by prox-e on 2009-02-22
I find myself having similar problems with my internet connection on my laptop as well . I am running Ubuntu 8.04 and I am struggling to finish getting all my updates because I can't keep my internet connection stable.

It seems to randomly disconnect itself. Another thing I have noticed is that the speed as well is very very very very slow  ..... feel like I am on a dial-up 56k modem ......while my other machines are rocking my 4mb line like it should be rocked.

I couldn't get my wireless to work and have lost a lot of hope for the moment but would just like to have a stable connection so I can actually work on my machine. I actually can't install updates because I can not connect for a long enough period.


> eth0      Link encap:Ethernet  HWaddr 00:16:d3:57:77:01  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe57:7701/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185027 errors:15294 dropped:0 overruns:0 frame:17507
          TX packets:166715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230911004 (220.2 MB)  TX bytes:20691854 (19.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132580 (129.4 KB)  TX bytes:132580 (129.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:a6:33:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-A6-33-1F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



I don't know if what I just quoted is any help.

---

### Post by bgates on 2009-02-22
If you are not using IPv6 then turning it off helps a lot.  I have to do that after installing (before getting all the updates :) ).  My download speed increases by about 4x after it is gone.

Here is a thread on the ways to do it:  [http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

---

### Post by deepclutch on 2009-02-22
what's the content of /etc/ppp/peers/dsl-provider says?It looks to me that your lan card was change manually(PCI one?)
for udev to work ,
look at /etc/udev/rules.d/ -and network link -check for it.normally if you have only one lan card ,eth0 must be the default.

---

### Post by prox-e on 2009-02-22
ok how do I find out if I am using this IPv6 ?
and where do I get the information form to put in the brackets?

Sorry very n00b at this.

---

### Post by prox-e on 2009-02-22
> **deepclutch said:**
> what's the content of /etc/ppp/peers/dsl-provider says?It looks to me that your lan card was change manually(PCI one?)
for udev to work ,
look at /etc/udev/rules.d/ -and network link -check for it.normally if you have only one lan card ,eth0 must be the default.

> dsl-provider:

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so
nic-wlan0
user "lie13@wadsl"
usepeerdns


I don't know what i'm looking for in that second directory you have specified

---

### Post by deepclutch on 2009-02-22
>  plugin rp-pppoe.so
Mine says:
```
 plugin rp-pppoe.so eth1
```
edit using "gksudo gedit /etc/ppp/peers/dsl-provider" .then try. pon dsl-provider

---

### Post by prox-e on 2009-02-22
ok I did that and it loaded the plugin but is still won't connect.

I made mine the same as yours and it rejected it completely...... so I changed the eth1 to eth0

---

### Post by prox-e on 2009-02-22
ok been clicking connect for 20 min and it connected but I was stuck in a repeat mode and clicking it again disconnected it before I realized it was connected.

I've also changes my LAN cable in case that was a problem
I tried to follow the IPv6 disabling but non of the files it says I need to edit are non existent so it wouldn't let change anything there.
only think i got to work was ~# ip a | grep inet6     
which gave me .....

> inet6 ::1/128 scope host
inet6 fe80::216:d3ff:fe57:7701/64 scope link

---

### Post by prox-e on 2009-02-22
[http://ubuntuforums.org/archive/index.php/t-87798.html]("http://ubuntuforums.org/archive/index.php/t-87798.html")

I'm trying to follow some of the things that are suggested on this page but a lot of it doesn't seem to be doing for me what it is others, do these file excite or do I have to create then ?

---

### Post by prox-e on 2009-02-22
OK I can't connect at all anymore ...... when I open the GUI network manager and  try check my PPPOE connection to activate it, it checks and tried to connect but fail every time now.

Have I set something up wrong from the beginning maybe? I followed as close to the process I would in  my winxp machines.

---

### Post by bgates on 2009-02-22
Apologies, it is probably a little confusing because that thread goes so far back in the past.  It should work only doing this:

[http://ubuntuforums.org/showpost.php?p=2631546&postcount=116](http://ubuntuforums.org/showpost.php?p=2631546&postcount=116)

Then after you reboot and do ifconfig, this line should be gone:

inet6 addr: fe80::216:d3ff:fe57:7701/64 Scope:Link

From the eth0 interface.

---

### Post by alexandari on 2009-02-22
> **prox-e said:**
> OK I can't connect at all anymore ...... when I open the GUI network manager and  try check my PPPOE connection to activate it, it checks and tried to connect but fail every time now.

Have I set something up wrong from the beginning maybe? I followed as close to the process I would in  my winxp machines.

I was having the same problem so I just used the sudo pppoeconf  (I`m using a router now)

---

### Post by prox-e on 2009-02-22
Ok  I have done all that and it is still refusing to connect.

Everything is doing what you say it should but I still have no connection. Is it maybe not something a lot more simple I could have missed. The password and user are correct I have double checked those and have been connected with them earlier today.

I have to use the PPPOE system as I have multiple account running through my router, and I can't afford to offer free internet to people connecting to my router.

---

### Post by prox-e on 2009-02-22
I ran the pppoeconf and went thought the process it has and at the end it says something else is using the modem. This leads me back to the thought that there is hardware conflicting with each other. I did try install ndisswrapper and I think another driver a while back trying to get that to work but it was more fail than this ethernet cable attempt.

Is there by any chance maybe it has something to do with it, if so how would I go about stopping my wireless drivers and hardware .....with out disabling in the bios because I use the wireless in my WinXP ....as this laptop has a dual booting system.

---

