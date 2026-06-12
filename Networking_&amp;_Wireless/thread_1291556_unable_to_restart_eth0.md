---
title: "unable to restart eth0"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by deathrunner1 on 2009-10-14
Hello my wired ethernet port (eth0) is marked as disabled.  If this helps it is a Ethernet Controller : Intel Corporation 82562ET/EZ/GT/GZ PRO/100 VE (LOM) Ethernet Controller . Subsystem Dell Device 0181 .

I have no internet connection and my eth0 is disabled.  Any help would be greatly appreciated.

Lynn
:confused:

---

### Post by Crafty Kisses on 2009-10-14
I need a bit more information, what are the results of the following?
```
lshw -C network
iwconfig
```

---

### Post by deathrunner1 on 2009-10-15
Thanks so much for your time...here goes:

I new to the forum so I just uploaded the output of one...



and for iwconfig:

lo           no wireless connection
eth0       no wireless connection
pan0      no wireless connection
vmnet1   no wireless connection
vmnet8   no wireless connection


Thanks again you help is much appreciated!

Lynn

---

### Post by deathrunner1 on 2009-10-15
Update... I reconfigured the output file to make it easier to read.  here goes

---

### Post by deathrunner1 on 2009-10-15
Update.. I did some digging and ran
 

>sudo ip addr flush sev eth0

and when i ran:   >lshw -C network

it didn't show my network as being disabled.

....

lynn@DeathrunnerLinux:/$ sudo lshw -C network
 
  *-network            
 description: Ethernet interface
    
 product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
 
 vendor: Intel Corporation
 
 physical id: 8
  
 bus info: pci@0000:03:08.0
    
 logical name: eth0
    
 version: 03
     
 serial: 00:11:11:ad:ba:00
   
 size: 100MB/s
    
 capacity: 100MB/s
    
 width: 32 bits
    
 clock: 33MHz
   
 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   
 configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
 

 *-network
  
  description: Ethernet interface
    
  physical id: 1
   
  logical name: pan0
     
  serial: 5e:c8:a2:f7:59:7f
    
  capabilities: ethernet physical
    
  configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
.......................................................

sorry i had to hand configure the text file for some reason so it's off a little on the spacing.



next I restarted the network  with >sudo /etc/init.d/networking restart

and got this error:  

ifup: couldn't read interfaces file "/etc/networking/interfaces"

here's whats in that file:


auto lo
iface lo inet loopbackp
auto eth0
iface eth0 inet static address 192.168.1.180       
                netmask 255.255.255.0
                network 192.168.1.0        
                broadcast 192.168.1.255
                gateway 192.168.1.1

exactly as it appears.

Does it need to be changed to work?  
Any help would really be useful. I'm so new and astounded that people actually are willing to help. Hopefully when I learn more I can help others. Thanks,

Lynn

---

### Post by Iowan on 2009-10-15
> **deathrunner1 said:**
> 
ifup: couldn't read interfaces file "/etc/networking/interfaces"

here's whats in that file:


auto lo
iface lo inet [COLOR="Red"]loopbackp[/COLOR]
auto eth0
iface eth0 inet static [COLOR="Red"]address 192.168.1.180 [/COLOR]      
                netmask 255.255.255.0
                network 192.168.1.0        
                broadcast 192.168.1.255
                gateway 192.168.1.1

exactly as it appears.
I presume you're talking about */etc/network/interfaces*. A couple of things don't look normal - "loopbackp" looks like a typo slipped in, and the "address" component is usually on its own line. File should look like:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static 
      address 192.168.1.180     
      netmask 255.255.255.0
      network 192.168.1.0        
      broadcast 192.168.1.255
      gateway 192.168.1.1
```

---

### Post by deathrunner1 on 2009-10-15
Thanks Iowan!

I still need to type in the >sudo ip addr flush dev eth0     
 
every time I log on 

then after running >sudo/etc/init.d/networking restart 

I get: 

* Reconfiguring network interfaces...                                   [ OK ] 

but still no internet connection at that point.

I did some digging and found these commands

>sudo ip addr flush dev eth0 && sudo ip link set eth0 down
>sudo ip link set eth0 up
>sudo /sbin/dhclient eth0

and I get an internet connection....whew!   But honestly I would like it to work using the /etc/network/interfaces file so I can have a static IP.

Thanks so much for your time..it is well appreciated and if you can help me figure this out, I would be grateful.

Lynn

---

### Post by deathrunner1 on 2009-10-16
Ok now I run the commands after start up:

>sudo ip link set eth0 up
>sudo ip link set pan0 down
>sudo ip addr flush dev eth0


and after running 

lynn@DeathrunnerLinux:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:11:11:ad:ba:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:2b:26:43:56:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

No longer saying network disabled.

next I run:

lynn@DeathrunnerLinux:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

but still no internet connection.

so if this helps:
lynn@DeathrunnerLinux:~$ ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:11:11:ad:ba:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272 (272.0 B)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3097 (3.0 KB)  TX bytes:3097 (3.0 KB)

pan0      Link encap:Ethernet  HWaddr 62:2b:26:43:56:c3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.33.1  Bcast:172.16.33.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.135.1  Bcast:192.168.135.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

No IP address given in eh0.

Thanks for your time,

Lynn

---

### Post by deathrunner1 on 2009-10-16
Ok I went over the interfaces file and corrected it perfectly now everything works great...

I just have to look up how to run a file to execute these commands at startup now.

Thanks for all the help!

lynn
:P

---

### Post by deathrunner1 on 2009-10-16
Just want to let y'all know how great is is that people are willing to help just out the love of Linux.  It was well apprecieated...I'm up and running and completed my first networking project as I just started school for CIS Networking and I've now decided to specialize in Linux Administration.  I have a lot to learn but I'm sure I'll come through all right.


Lynn

---

