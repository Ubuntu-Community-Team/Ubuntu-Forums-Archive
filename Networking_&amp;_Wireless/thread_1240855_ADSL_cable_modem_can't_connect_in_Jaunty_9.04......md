---
title: "ADSL cable modem can't connect in Jaunty 9.04..............need help"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by jamesjai on 2009-08-15
Dear friends, 

I am a new user in ubuntu. I am musing _Jaunty 9.04_.

I bought an Alcatel-Lucent ADSL cable modem. 

The modem I connected to _computer network card_ (the NIC details listed below).

I used network connection applet to connect to internet. I provide  static IP address, gateway IP and DNS server details in network connection applet.  

When I try to  connect to internet, I saw a message, the devise is not configures.

     I need help for configure my ADSL cable in Jaunty 9.04.

Please help me.

Thank you

Best regards, 

------------------------------------------------------
_My network card details as follows,_ 

root@joel-desktop:/home/joel# lshw -C Network


*-network 

description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: 00:16:ec:5b:36:fa
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s

------------------------------------------------------

---

### Post by karthick87 on 2009-08-15
Open terminal and type "sudo pppoeconf" without quotes and configure it..

---

### Post by jamesjai on 2009-08-15
Dear friend,

I used the command "sudo pppoeconf", it scanned my _eth0 and pan0 devices_ and return following error message, 

-----------------------------------------------------
NOT CONNECTED

Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond.
Please  check your network and modem cables. 
Another reason for the scan failure may also be another running pppoe process which controls the modem.
-----------------------------------------------------

I used ifconfig eth0, it read my device, _eth0 Link ecap:Ethernet HWaddr 00_:........

The same NIC I used to connect my ADSL modem in Window XP. I am using dual booting (windows xp and Ubuntu 9.04).

Please help me to solve this problem. I am long trying to connect my ubuntu to internet. First my dialup i cant connect to internet then i bought ADSL modem, still I am struggling. Badly I need internet connection in my Ubuntu.

Please help me.

Thank you

Best regards

---

### Post by superprash2003 on 2009-08-15
also post output of **ifconfig** from the terminal

---

### Post by jamesjai on 2009-08-15
Dear friends,

Please find the output of **ifconfig**,

--------------------------------------------------------------------------
root@joel-desktop:/home/joel# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1152 (1.1 KB)  TX bytes:1152 (1.1 KB)

root@joel-desktop:/home/joel# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:ec:5b:36:fa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa800 

root@joel-desktop:/home/joel# ifconfig pan0
pan0      Link encap:Ethernet  HWaddr b2:71:c5:a6:6a:ad  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
--------------------------------------------------------------------------

Please kindly help me to get my ubuntu 9.04 connected to internet. 

Thank you, 

Best regards.

---

### Post by superprash2003 on 2009-08-17
hmm..interesting , when you type ifconfig in your terminal , it only gives output of lo ?

---

### Post by jamesjai on 2009-08-19
Yes dear superprash..........could you please help me to solve this problem? I am long waited my ubuntu to connect ineternet....please advise how to solve....thank you very much for your kind support..

---

### Post by superprash2003 on 2009-08-19
post output of **lshw -C network** from the terminal , also post contents of the /etc/network/interfaces file

---

### Post by jamesjai on 2009-08-20
Dear superprash, 

Please find the details of **lshw -C Network **and **/etc/network/interfaces** file. Thanks for your kind help.


root@joel-desktop:/home/joel# lshw -C Network

*-network 

description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: 00:16:ec:5b:36:fa
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
-----------------------------------------------------------
   

auto lo


  
  iface lo inet loopback
 
iface eth0 inet dhcp
  
address 192.168.1.10
     netmask 255.255.255.0
     [FONT=&quot]gateway 192.168.1.1
---------------------------------------------------
[/FONT]     root@joel-desktop:/home/joel# lshw -C
  
  Hardware Lister (lshw) - B.02.13
  
  usage: lshw [-format] [-options ...]
  
         lshw -version
  
              -version        print program version (B.02.13)
  
  format can be
  
              -html           output hardware tree as HTML
  
              -xml            output hardware tree as XML
  
              -short          output hardware paths
  
              -businfo        output bus information
  
  
  options can be
  
              -class CLASS    only show a certain class of hardware
  
              -C CLASS        same as '-class CLASS'
  
              -c CLASS        same as '-class CLASS'
  
              -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
  
              -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
  
              -quiet          don't display status
  
              -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
  
              -numeric        output numeric IDs (for PCI, USB, etc.)

[FONT=&quot][/FONT]  -----------------------------------------------------------

---

### Post by jamesjai on 2009-08-20
Dear Prash, 

Additional information of **lshw -C Network** refer below. Please also refer my post (/etc/network/interfaces) 6 hours before. Thank you.


root@joel-desktop:/home/joel# lshw -C Network

*-network 

description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: 00:16:ec:5b:36:fa
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s



 network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: ba:12:f6:89:fa:f0
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by superprash2003 on 2009-08-24
replace the contents of the interfaces file with this

auto lo



iface lo inet loopback
auto eth0
iface eth0 inet dhcp

---

### Post by jamesjai on 2009-08-25
:guitar:  

Dear Superprash,

I am writing this reply from my Ubuntu 9.04. 
At last you help me to get my Ubuntu connected to Internet. 
I take this opportunity to say thank you very much for your kind support.

I hope this thread will be helpful for those who have ADSL cable modems.

I am expecting your kind support in near future.

Once again thank you very much.

Best regards

Cheers!

---

