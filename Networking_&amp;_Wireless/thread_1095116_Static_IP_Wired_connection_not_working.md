---
title: "Static IP Wired connection not working"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by rmburke2 on 2009-03-13
Hi,
I just installed Ubuntu as a dual boot with Mac OSX on my work computer, a mac mini.  All the networking works fine on the mac side so I know it's not a hardware issue.  Basically I've configured my connection to use a static IP address to connect to my company's network, and it worked for a while, but ever since I installed the many updates that Ubuntu advised me to install the wired connection doesn't work anymore, on the task bar it says "device is unmanaged" and won't connect.  Strangely enough, however, the wireless connection works, which is how I'm accessing the internet now.  Any ideas?

ifconfig -a #(eth0 is the one i'm trying to use)

ath0      Link encap:Ethernet  HWaddr 00:1c:b3:b2:9b:ef  
          inet addr:128.205.102.158  Bcast:128.205.102.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:b3ff:feb2:9bef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2044290 (2.0 MB)  TX bytes:458073 (458.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:cb:ae:1f:9d  
          inet addr:128.205.158.156  Bcast:128.205.158.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:feae:1f9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:874601 (874.6 KB)  TX bytes:20900 (20.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15584 (15.5 KB)  TX bytes:15584 (15.5 KB)

pan0      Link encap:Ethernet  HWaddr 6e:ab:6b:33:24:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-B3-B2-9B-EF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60629 errors:0 dropped:0 overruns:0 frame:3683
          TX packets:3100 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9781015 (9.7 MB)  TX bytes:537325 (537.3 KB)
          Interrupt:17



/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 128.205.158.156
netmask 255.255.255.0
network 128.205.158.0
broadcast 128.205.158.255
gateway 128.205.158.254

#i'm not sure on the "network" line or the "broadcast" line, that's not #something we usually have to put in to set up a computer on the network

So again, anyone know what's going on?

---

### Post by rmburke2 on 2009-03-13
*bump*

Sorry to be a dick, i can't find any solutions to this particular problem elsewhere, though.

---

### Post by zika on 2009-03-13
give us ```
cat /etc/NetworkManager/nm-system-settings.conf
```it should have a line like:```
[ifupdown]
managed=true
``` ...

---

### Post by rmburke2 on 2009-03-13
It says managed=false.  I tried changing it, but then when I did  
sudo /etc/init.d/networking restart

it came up with

 * Reconfiguring network interfaces...                                          Ignoring unknown interface ath0=ath0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

and undid what I did.  Probably just me not knowing something.
(Speaking of not knowing, how do you make a code box if you don't mind me asking?)

---

### Post by rmburke2 on 2009-03-13
Ok so this is strange.  In the drop-down menu for my network connections there's a connection "ifupdown eth0" that it says it connects to, but it has no DNS servers and won't let me change that field and save it when I edit the connection.  Something about access denied or whatnot.  The strange thing though is when logged in as root there's that connection and the original eth0 connection.  The eth0 connects to the internet and works, the ifupdown eth0 connection doesn't.  Could someone tell me what's going on?

---

### Post by aesis05401 on 2009-03-13
> **rmburke2 said:**
> 
/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 128.205.158.156
netmask 255.255.255.0
network 128.205.158.0
broadcast 128.205.158.255
gateway 128.205.158.254


I know what's going on in a general sense.  I started seeing threads like this last Fall (2008 ). 

1: Backup /etc/network/interfaces to a safe place, because we are going to blow it away.
2: Delete all lines from your interfaces file except:
auto lo
iface lo inet loopback 
3: Reboot.
4: Open Network Manager and apply all network settings through the GUI.

I don't know why this happened, but it was related to having entries in the interfaces file during one of the updates.  If you need more info search this forum and LinuxQuestions.org, there were other threads with other solutions.

---

### Post by Iowan on 2009-03-13
> **rmburke2 said:**
> 
(Speaking of not knowing, how do you make a code box if you don't mind me asking?)If you have Java/Javascript enabled, it's the # option.  Otherwise, you can manually enter it by surrounding it with [ code] [ /code] (omitting the spaces).

---

### Post by rmburke2 on 2009-03-16
Okay, so in case anybody comes across this needing help, here's what I did:

Don't use Network Manager, just do it all manually.

---

