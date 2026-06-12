---
title: "No auto eth0 on one Lucid box. Why? Where?"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by 19Grumpah42 on 2011-07-30
Hi everybody, so I now have 4 Ubuntu Lucid LTS installations - terrific - but the alternative Ubuntu boot on this particular PC (all made from the same Live CD) does not have any eth0 configured, so I cannot reach even my router. I can look at the eth0 properties with "Network tools" and it has no IP or MAC. I have the network notification gremlin installed but it does not appear on the top panel. {"eth0" hardware works under Win XP, hence this post}.

I'm a novice at Ubuntu, and I am at a loss. I realise that _networking is supposed to be automatic,_ no 'tool' should be needed, but [COLOR=DarkRed]what can I do when it has not configured[/COLOR]?

--Grahame

---

### Post by papibe on 2011-07-30
Could you post the result of these commands?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by 19Grumpah42 on 2011-07-31
Thanks very much for the prompt reply papibe; long may you and your cause prosper!

This is what I got .....

$ ifconfig
gep@C-2-Q:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2736 (2.7 KB)  TX bytes:2736 (2.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.114.1  Bcast:172.16.114.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.134.1  Bcast:172.16.134.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-----------------------------------------------
$ route -n
gep@C-2-Q:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.134.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.114.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1

----------------------------------------------
$ nslookup ubuntu.com
gep@C-2-Q:~$ nslookup ubuntu.com
;; connection timed out; no servers could be reached

----------------------------------------------
$ dig ubuntu.com
gep@C-2-Q:~$ dig ubuntu.com

; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

---------

My local router gateway is 192.168.0.1
My Internet IP is currently 98.235.160.147

If I could reach my router it would assign a reserved LAN IP of 192.168.0.6 to this ethernet MAC.
Regards.
***************

I used copy/paste via a shared file on a multiboot machine, so this is exactly what I got (no typos).
Look forward to your response --G

---

### Post by 19Grumpah42 on 2011-07-31
P.S. I'm certainly curious about the 172.16.....   addresses shown by *ifconfig,* I think that either they do not exist or their port is stealthed. --G

---

### Post by papibe on 2011-07-31
I don't see your ethernet interface there, just the vmnet ones (usually for VM machines).

Could your post the result of these?
```
$ sudo lshw -C network
```
Regards.

---

### Post by 19Grumpah42 on 2011-08-01
Thanks, done that .....

I don't see your ethernet interface there, just the vmnet ones (usually for VM machines).
Could your post the result of these?
Code:
---------
$ sudo lshw -C network
gep@C-2-Q:~$  sudo lshw -C network
[sudo] password for gep: 
  *-network DISABLED      
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 48:5b:39:45:1b:8a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:fe6c0000-fe6fffff ioport:bc00(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:ef:17:c9:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
gep@C-2-Q:~$ 
---------
Regards.
***************

[COLOR=Purple]*lshw*[/COLOR] and my[COLOR=Purple]* desktop*[/COLOR] seem to agree that the network is disabled. I imagine that if I could just get the network demon showing I could fix it up and enable it.

What next my captain?
--G

---

### Post by 19Grumpah42 on 2011-08-03
So I appear to have an instance of Ubuntu 10.04.1 LTS where the network daemon is not running (it is installed), so I have no network connections. Would it be possible for me to manually run the daemon - so I could configure the eth0 port - and if so what is its exact name so I can find it in "File system"? Or is it not this simple? ):P
--G

---

### Post by papibe on 2011-08-04
My guess is not a problem with the network services, but more close the hardware. Either is disabled on the BIOS, it is not properly installed (loose PCI connection), a faulty NIC, a problem of being recognized, or a missing driver.

What NIC do you have? Could you post the result of these?
```
$ lspci -nn | grep -i eth
```
Regards.

---

### Post by 19Grumpah42 on 2011-08-04
Hello thanks for the suggestion, I will check it out when I re-boot out of WinXP sometime today. Personally, in my ignorance of course, I somehow doubt that it is hardware related. I have an alternative - emergency - Ubuntu 10.04.1 LTS boot off a 4 GBy SanDisk on this machine, and that connects as expected, using the ethernet connection. Also, I normally use Win-XP on a wireless connection (I cannot get this to work under any of my Ubuntu installations, it's a Rosewill USB-WiFi) and if I switch Win-XP on this machine over to ethernet, it too works fine. The Ubuntu installation here with no eth0 has a lot of my stuff on it, so I am reluctant to reformat and re-install because I just don't have enough knowledge or confidence in doing Linux backups etc. :confused:
--G

---

### Post by 19Grumpah42 on 2011-08-05
I have just created a VM-Player instance on this PC from the same original Ubuntu Live Installation CD and it has no problem going through Win XP to eth0, so I think there is probably something wrong or missing on my main Ubuntu installation. Perhaps I could back up everything on this partition, re-install Ubuntu and then "copy back" (using a live ReDo CD) everything <* except *> those directories which may contain the problem/absent files. Can you help me with that? I just have no understanding of the Linux file system, what constitutes "system" as opposed to "user" directories. In which directory do you think the problem/absent file(s) could be?
--G

---

### Post by 19Grumpah42 on 2011-08-05
This is my actual device (clocked on the Virtual-Ubuntu) ......
grahame@ubuntu:~$ lspci -nn | grep -i eth
02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
grahame@ubuntu:~$

---

