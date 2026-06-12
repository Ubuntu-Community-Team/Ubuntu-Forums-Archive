---
title: "Have connection but no Internet after updates on 10.04"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by Vera.ek on 2010-12-02
Hello. Please help to a new Ubuntu user. 
Running **10.04 LTS x64** on Acer Aspire 5720z as the only OS.
Everything worked just wonderful before the recent updates.
After rebooting I stopped being able to browse web or use Skype.
I have a wired connection, via splitter (Netgear 5-port 10\100 fast ethernet switch). Same cable works fine on another laptop with WinXP. 

_Here are the results of some tests I ran:_

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:52:2b:c0  
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe52:2bc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1292  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27673 (27.6 KB)  TX bytes:4117 (4.1 KB)
          Interrupt:18 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38057 (38.0 KB)  TX bytes:38057 (38.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:53:3b:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**sudo lshw -c network**
[sudo] password for vera: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:52:2b:c0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5787m-v3.22 ip=192.168.1.85 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:d8200000-d820ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:53:3b:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:d7100000-d710ffff


**ping 4.2.2.1 -c3**
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms


Network manager shows both Wired and Wireless connections. 
And says my wired connection 1 is being used.
I have tried to change MTU number from 1492 to 1500 and 1292, both in NM and by editing sudo ifconfig eth0 mtu  but it didn't seem to have any effect. 

I'd appreciate it very much if you can provide me with "how to" together with possible advices, because I'm not good with commands. 
Please help me!

---

### Post by grahammechanical on 2010-12-02
First, please tell us if your problem is with the wired (eth0) connection or with the wireless (wlan0) connection.

From the information provided I can see that eth0 is UP and RUNNING. Wlan0 is only UP. Also eth0 has an inet addr (internet address) . A Bcast (broadcast address) and a Mask address. But wlan0 does not show any of these. So, I think that you are connected to the router/modem by ethernet cable (wired connection) but not with wireless connection.

Which connection are you having problems with? Can you access the Internet? Is the modem/router connected to your ISP? What do the LEDs on the router/modem show?

If you want to connect by wireless, then we have to look in a different direction. Please confirm that the modem is connected to the ISP.

Regards.

---

### Post by Spyderkid on 2010-12-02
can you run lsusb, please?

---

### Post by Vera.ek on 2010-12-02
Yes, I have problems with the wired (eth0) connection. 
I haven't tasted the wireless, I don't use it at the moment (I'm in university accommodation, they don't allow using wireless within university network).
My splitter connected directly to ISP socket, I've tried to use direct cable without splitter - didn't work either.
The LEDs of splitter blink working, when I connect cable to PC it shows that the connection is established. 

Here are the results of lsusb:
vera@vera-laptop:~$ sudo lsusb 
[sudo] password for vera:  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 064e:a103 Suyin Corp.  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Fire_Chief on 2010-12-02
Is the wired connection getting its IP address from DHCP or did you configure it manually? It seems the system currently has a gateway configured as 192.168.1.1 (which is okay, just want to confirm that this is correct). 
Also, is there any chance the University requires a logon or authentication via web browser before you are allowed to reach the Internet (much like many hotels require for guest Internet access)?

Cheers!

---

### Post by Vera.ek on 2010-12-02
Hi. The connection has to get the IP automatically. It did so before. And it does on another computers. 
This connection does not require any logon procedures. It just starts automatically as you plug ISP cable in.

---

### Post by Fire_Chief on 2010-12-02
Ok, so let's see how far the communication is getting. Please post the results of these when run from a terminal.

```
ping 192.168.1.1 -c3
```
```
tracepath 4.2.2.1
tracepath 74.125.65.99
```The second one is for Google.com

Cheers!

---

### Post by Vera.ek on 2010-12-02
vera@vera-laptop:~$ **ping 192.168.1.1 -c3**
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=8.23 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.628 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.512 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.512/3.125/8.236/3.614 ms

ping 192.168.1.1 -c3 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. 
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=8.23 ms 
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.628 ms 
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.512 ms 
 
--- 192.168.1.1 ping statistics --- 
3 packets transmitted, 3 received, 0% packet loss, time 2000ms 
rtt min/avg/max/mdev = 0.512/3.125/8.236/3.614 ms 


vera@vera-laptop:~$ sudo **tracepath 4.2.2.1 **
 1:  vera-laptop.local (192.168.1.85)      0.124ms pmtu 1292 
 1:  192.168.1.1 (192.168.1.1)                 1.400ms !N 
 1:  192.168.1.1 (192.168.1.1)                 1.445ms !N 
     Resume: pmtu 1292 


vera@vera-laptop:~$ sudo **tracepath 74.125.65.99**
 1:  vera-laptop.local (192.168.1.85)      0.208ms pmtu 1292 
 1:  192.168.1.1 (192.168.1.1)                 9.029ms !N 
 1:  192.168.1.1 (192.168.1.1)                 1.446ms !N
     Resume: pmtu 1292

---

### Post by Vera.ek on 2010-12-04
I know everyone's very busy... but I still desperately need your help, guys!
You're the only people able to contribute into solving this problem. 
I've tried my connection under Ubuntu 10.10 trial boot, but the results were all the same. Showing connection but not going online. 
I am ready and willing to try anything you suggest! I'd really love to continue working with Ubuntu.

---

### Post by drdos2006 on 2010-12-04
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. This is part of another topic in the forum that I saved for future use, hope it helps.

Disable IPv6 in Firefox.
From the browser bar type : 
about:config
type in the filter section : network.dns
Click on disableIPv6 to change it to true. Restart Firefox.

For your operating system... 
How do I prove ipv6 has been successfully disabled ?
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

From the terminal, type :
cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.


regards

---

### Post by Fire_Chief on 2010-12-04
It seems that your workstation can talk to the gateway but not past it. That would typically be due to an authentication issue or a configuration problem beyond your computer itself.
Just to confirm, your Windows instance does not have any special settings or software that enables it to reach the Internet.
If you do ping and traceroute tests from your Windows instance, do you see the same results?

Cheers!

---

### Post by Vera.ek on 2010-12-06
Thank you for keeping helping!

Drdos, I have done what you have advised:
I have disabled ipv6 in Firefox and then in my system.
I have checked it by running cat /proc/sys/net/ipv6/conf/*/disable_ipv6 and it was 1.
Then I reboot and tried to surf net - unfortunately nothing has happened. 

Fire Chief,
I ran ping and tracert tests in my Windows pc with the same cable and here are the results (see prtsc):
[http://ubuntuforums.org/attachment.php?attachmentid=177610&stc=1&d=1291646897](http://ubuntuforums.org/attachment.php?attachmentid=177610&stc=1&d=1291646897)

there are lines in russian after ping 192.168.1.1 saying that waiting time for request is over
sent=4, received=0, lost=4.

What doest that mean?

---

### Post by pevma on 2010-12-07
I got the exact same problem.

Did anybody solve this?

---

### Post by pevma on 2010-12-07
I seemed to have resolved my issue.

what I did was to reboot the router/switch- which it didn't help in my case- then I tried a wild pitch:
changed the MAC address on my PC, after I did that everything went fine.

 
Now my situation was similar but not the same:
I had a Uduntu guest on a VMware Host running Windows 7 64bit.
I had ping by name and IP to any address - but no internet -  I was not able to browse , get to Skype ...etc.

So I changed the MAC address on the Ubuntu host manually, from the web control interface.
For VMware - Valid values for manually setting up your MAC are between 00:50:56:00:00:00 and 00:50:56:3f:ff:ff
But for a "real" physical PC behind a router - all you have to do is :

ifconfig eth0 down
ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx
ifconfig eth0 up

just MAKE SURE you don't duplicate the MAC address - there is no other PC/device in your network with the same MAC address. Or you can use the same/original MAC of your PC, just change the last 2 digits.

Hope that works for you

---

### Post by Fire_Chief on 2010-12-07
I was thinking about this yesterday and it occurred to me that there's a decent chance the network you're connecting to using a NAC environment to regulate access. Basically, it checks to see if the clients that are connecting meet certain minimum criteria before it will permit them to access the normal network (i.e. Service Pack level, AV protection installed and up to date, etc.). If they don't meet the requirements, they are sandboxed to prevent possible infection to the rest of the network. If this is the case, I'd bet that the NAC server doesn't know what to do with Ubuntu.
It's not a solution really but could be the cause. Do you know anyone else there who is successfully running Ubuntu on the network?

Cheers!

---

### Post by Vera.ek on 2010-12-08
Fire_Chief, a friend of mine runs Ubuntu 10.10 with the same provider - college network and everything works for him. 

Pevma, I have changed MAC address and it didn't help.

---

### Post by Fire_Chief on 2010-12-08
Have you tried using 10.10 to see if it works? Perhaps the LiveCD?

---

### Post by Vera.ek on 2010-12-09
Yes, I did. It was the same. 
Yesterday we've got a letter from college accommodation about the changes they're going to make. From Dec 16th we'll get a login and password system. So I hope that these changes could help me. 
If it doesn't help, the only option is earlier version or windows. So pity!

---

### Post by Vera.ek on 2010-12-13
So, here am I, browsing internet using my Ubuntu laptop.
This morning the new connection system was established - the one with the use of username and passworf to register the computer. 
And it worked.
I am affraid that the net may again recognise my system as a virus or some danger, but so far things are fine.

Thanks to all of you who have spend all this time helping me. 
And I hope that my system will go on working.

---

