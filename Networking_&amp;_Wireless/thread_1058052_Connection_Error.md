---
title: "Connection Error"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Adyghe on 2009-02-02
my internet connection is lost every time i wanna connect this message appears to me (the network driver have been disconnected) and i checked with my ISP if there is a problem with my connection but nothing was wrong and the password was right also.. my ubuntu is up to date and yesterday i was connecting normally now i have to use windows to connect to internet


an ideas for this problem !!!!

---

### Post by halovivek on 2009-02-02
Welcome to ubuntu forums
please type this in terminal and post the output
sudo lshw -C network

route

ifconfig

iwconfig

---

### Post by Adyghe on 2009-02-02
here is the output

firas@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface

       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY

       vendor: Sundance Technology Inc / IC Plus Corp
       
physical id: 2
       
bus info: pci@0000:02:02.0

       logical name: eth0

       version: 31

       serial: 00:e0:4c:08:29:10

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz
 
      capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full latency=32 link=yes maxlatency=10 mingnt=10 module=sundance multicast=yes port=MII speed=100MB/s
 
 *-network DISABLED
 
      description: Ethernet interface

       physical id: 1
    
   logical name: pan0
     
  serial: 76:a4:f5:cb:17:93
     
  capabilities: ethernet physical
  
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


firas@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

firas@ubuntu:~$ ifconfig
eth0   
   Link encap:Ethernet  HWaddr 00:e0:4c:08:29:10 
 
          inet6 addr: fe80::2e0:4cff:fe08:2910/64 Scope:Link
  
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 
         RX packets:14 errors:0 dropped:0 overruns:0 frame:0
    
      TX packets:20 errors:0 dropped:0 overruns:0 carrier:9
        
  collisions:0 txqueuelen:1000 
        
  RX bytes:840 (840.0 B)  TX bytes:1308 (1.3 KB)
   
       Interrupt:17 Base address:0xbc00 

lo       
 Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
  
        inet6 addr: ::1/128 Scope:Host
  
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
        RX packets:32 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
   
       collisions:0 txqueuelen:0 
      
    RX bytes:2432 (2.4 KB)  TX bytes:2432 (2.4 KB)

firas@ubuntu:~$ iwconfig
lo   
     no wireless extensions.

eth0  
    no wireless extensions.

pan0    
  no wireless extensions.

firas@ubuntu:~$ 


hope it will solve the problem

---

### Post by mgmechanics on 2009-02-02
I had the same problem. I use a build-in Dell 5530 in my DELL E4300 - laptop. Yesterday i got automaticly the new kernel 2.6.27-11 via internet. After reboot it was impossible to reconnect to the internet.

1) First Aid: After switching on your laptop you probably see wich operating systems / kernel versions are available. The newest kernel is the first option, the third option is the kernel you used bevor. Just choose this (the 3rd) option at startup and test your internet connection.

2) on my machine, the new kernel connected my modem no longer as
 - /dev/ttyACM0
 - /dev/ttyACM1
 - /dev/ttyACM2
but as 
 - /dev/ttyUSB0
...
 - /dev/ttyUSB10

where i can use it as  - /dev/ttyUSB4 with wvdial

There is a fine Gnome-App for viewing your system-logs - you can see what happens.

edit:
strange enough: umtsmon works only with

umtsmon -s/dev/ttyUSB2,/dev/ttyUSB2

and adding an [Device] - section like

[Device]
ATPortName=/dev/ttyUSB2
PPPPortName=/dev/ttyUSB2

did not have the desired effect.

---

### Post by halovivek on 2009-02-02
> **Adyghe said:**
> here is the output



Do you use manual ip configuration or auto?

---

