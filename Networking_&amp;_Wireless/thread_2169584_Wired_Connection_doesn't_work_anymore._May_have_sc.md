---
title: "Wired Connection doesn't work anymore. May have screwed something up, please Help!"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by Jeremy_Stewart on 2013-08-22
I'm a linux novice, but I'm finding Ubuntu to be great and able to do everything I need to be able to do. I was playing around with some different installs, including trying to walk through an install tutorial for Arch Linux, during which I wasn't able to get the network driver working correctly from the Live CD (command-line). Now I've booted Ubuntu back up from my HD (which I've had installed for days and it's been working fine) and the network connection is totally kaput. 

I restarted my router. I even took the ethernet cable out of my desktop (the computer with the problem) and plugged it into my Macbook to double check that it wasn't a problem with the cable or the router. Everything worked fine there. I've plugged it back into my Ubuntu machine, tried rebooting, playing with settings on the network devices, nothing's fixing it. Can someone help me figure out this issue?

Thanks!

---

### Post by papibe on 2013-08-22
Hi Jeremy_Stewart. Welcome to the forum ):P

Could you open a terminal, run these commands and post back its results?
```
sudo lshw -C network

lspci -nnk | grep -iA2 eth

ifconfig

route -n

nslookup ubuntu.com
```
Regards.

---

### Post by Jeremy_Stewart on 2013-08-22
Hi papibe, thanks for the help!
Below is what I've got:



jeremy@jeremy:~$ sudo lshw -C network
[sudo] password for jeremy: 
 *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:0b:b8:88:bf
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=1.1-1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:f3100000-f311ffff memory:f3124000-f3124fff ioport:2100(size=32)



jeremy@jeremy:~$ lspci -nnk | grep -iA2 eth
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:281e]
    Kernel driver in use: e1000e


jeremy@jeremy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:0b:b8:88:bf  
          inet6 addr: fe80::21e:bff:feb8:88bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27348 (27.3 KB)  TX bytes:53081 (53.0 KB)
          Interrupt:19 Memory:f3100000-f3120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16690 (16.6 KB)  TX bytes:16690 (16.6 KB)



jeremy@jeremy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface



jeremy@jeremy:~$ nslookup ubuntu.com
;; connection timed out; no servers could be reached

---

### Post by papibe on 2013-08-22
Thanks.

I see that at least the proper driver is loaded (e1000e), but you are getting an IP address. It may be a problem with some config files.

Could you run these other commands and post its output back?
```
lsmod | grep e1000e

apt-cache policy network-manager

cat /etc/network/interfaces

cat /etc/NetworkManager/NetworkManager.conf
```
Regards.

---

### Post by Jeremy_Stewart on 2013-08-22
Thanks! I just installed a Nvidia 8400GS video card. Although that was installed and working for a couple days before this just happened today. I also tried to clean install Ubuntu from a minimum install CD, and that couldn't connect to the internet either. I'm not sure how that would be connected to this.

Thanks again!

::




jeremy@jeremy:~$ lsmod | grep e1000e
e1000e                198832  0 
jeremy@jeremy:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.9.8.0-0ubuntu6
  Candidate: 0.9.8.0-0ubuntu6
  Version table:
 *** 0.9.8.0-0ubuntu6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status
jeremy@jeremy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#NetworkManager#auto eth0
#NetworkManager#iface eth0 inet dhcp
jeremy@jeremy:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:1E:0B:B8:88:BF,

[ifupdown]
managed=false
jeremy@jeremy:~$

---

### Post by papibe on 2013-08-22
That all looks OK.

Open 'Network Connections', go to the Wired tab and select your Wired connection. Then press Edit. Make sure that:
The checkbox 'Connect automatically' is check.
The checkbox 'Available to all users' is check.
In the IPv4 tab, the Method is 'Automatic (DHCP)'.
If that is all check, and you don't have your network back, please post the result of this 2 commands: 
```
sudo service network-managet stop

sudo service network-manager start

grep -i dhclient /var/log/syslog | tail -n15
```
Regards.

---

### Post by Jeremy_Stewart on 2013-08-22
Still didn't work. The network icon on the toolbar just runs incessantly  and occasionally a popup notification will say "Disconnected - you are  now offline"

jeremy@jeremy:~$ sudo service network-manager stop
[sudo] password for jeremy: 
network-manager stop/waiting
jeremy@jeremy:~$ sudo service network-manager start
network-manager start/running, process 4743
jeremy@jeremy:~$ grep -i dhclient /var/log/syslog | tail -n15
Aug 22 20:49:16 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x15c04403)
Aug 22 20:49:24 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0x15c04403)
Aug 22 20:49:38 jeremy NetworkManager[4743]: <info> dhclient started with pid 4750
Aug 22 20:49:38 jeremy dhclient: Internet Systems Consortium DHCP Client 4.2.4
Aug 22 20:49:38 jeremy dhclient: Copyright 2004-2012 Internet Systems Consortium.
Aug 22 20:49:38 jeremy dhclient: All rights reserved.
Aug 22 20:49:38 jeremy dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 22 20:49:38 jeremy dhclient: 
Aug 22 20:49:38 jeremy dhclient: Listening on LPF/eth0/00:1e:0b:b8:88:bf
Aug 22 20:49:38 jeremy dhclient: Sending on   LPF/eth0/00:1e:0b:b8:88:bf
Aug 22 20:49:38 jeremy dhclient: Sending on   Socket/fallback
Aug 22 20:49:38 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x4330c8fc)
Aug 22 20:49:41 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 (xid=0x4330c8fc)
Aug 22 20:49:46 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0x4330c8fc)
Aug 22 20:49:55 jeremy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0x4330c8fc)
jeremy@jeremy:~$ 


If  I clean install, should it come back? I have no reservations about just  clean installing, but the last time I tried, it wouldn't connect to  download the needed files.


Thanks again for your help. System problems aside, you're winning me over to the Ubuntu community.

---

### Post by papibe on 2013-08-22
It looks like your machine is doing everything ok, but no DHCP server responses to your machine request.

A few ideas:
[LIST]
[*]I would take a look a the router settings to make sure DHCP is set properly.
[*]I double check that your ethernet cable is working properly.
[/LIST]
Let us know how it goes.
Regards.

---

### Post by chili555 on 2013-08-22
@papibe--

The driver *e1000e* is troublesome right now. Many, including me,  have solved their problems by compiling and installing a later version. I'm using 2.3.2. [http://sourceforge.net/projects/e1000/files/e1000e%20stable/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/)

I know it compiles beautifully on 13.04 but I suggest you verify his version first. I have 12.04 and 12.10 around somewhere if you'd like me to test.

I hope I am not stepping on toes.

---

### Post by papibe on 2013-08-22
Hi chili555.

Thanks for the heads up :D

I wasn't aware of that since I'm using it myself on my 12.04 desktop without noticeable problems.

What would be the signs of a faulty driver? The dhclient fail? 

@Jeremy_Stewart, What version of Ubuntu are you using?

Regards.

---

### Post by Jeremy_Stewart on 2013-08-23
I'm on 13.04.

---

### Post by Jeremy_Stewart on 2013-08-23
Alright so I figured it out, not sure why this happened so maybe someone can try to help me understand it:

I backed up my relevant files, tried to boot from an Ubuntu min. install disk. It failed to connect to the network. It said that my network must not be configured for DHCP or there is a problem with the network hardware. I shut everything off and removed my recently installed graphics card (Nvidia 8400GS) and tried to boot from the same Ubuntu install disk. It instantly connected to the network and was able to download all needed files for a clean install.

My thinking is that when I tried to run the installer for Arch (with the video card installed), it changed some driver settings or installed the wrong drivers. (That was the first "install" attempt I made since installing the video card). Does this make sense? What else could it be?

When I put the graphics card in, I did lose access to the integrated sound in/outs on the motherboard. Ubuntu wasn't indicating any possible sound connections (not even a dummy input was listed as I saw mentioned on some troubleshooting forums).

Any thoughts or advice for getting the video card back in my machine while avoiding the networking and sound problems?

Thanks for your help guys!

---

### Post by chili555 on 2013-08-23
> **papibe said:**
> Hi chili555.

Thanks for the heads up :D

I wasn't aware of that since I'm using it myself on my 12.04 desktop without noticeable problems.

What would be the signs of a faulty driver? The dhclient fail? 

@Jeremy_Stewart, What version of Ubuntu are you using?

Regards.Looks like it healed itself!

The symptom is not just that it won't get an address by DHCP, but also static! Everything looks fine but it just doesn't work.

Are you able to help young Jeremy further?

---

### Post by Jeremy_Stewart on 2013-08-25
It is working again, but I still haven't reinstalled the video card, which seemed to be the culprit. Any thoughts on how this created this interaction? How can I avoid it if I want to reinstall it?

---

