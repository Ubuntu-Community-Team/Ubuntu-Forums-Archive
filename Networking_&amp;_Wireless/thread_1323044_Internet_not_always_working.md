---
title: "Internet not always working"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by arizonagirl11 on 2009-11-11
Hi everyone. I as wondering if you can help me. I just installed ubuntu 9.10. my Windows 7 is about to expire, and i really do not want to buy it, since I really dislike Microsoft. Anyway, I am having a lot of trouble with the Internet. Sometimes, the Internet works, sometimes, it does not. It seems to be luck if the Internet works. The Internet worked fine on that same machine under Windows 7. This computer has Ubuntu 8.04, and is also working properly. However, the other machine in which I installed Ubuntu 9.10, I just cannot get internet working. I am fairly new to the scene, and I do not know what to do. i do not wanna go back to Windows. 

Any help would be greatly appretiated! Thanks!
Kimmy

---

### Post by kestrel1 on 2009-11-11
Is this wired or wireless?

---

### Post by arizonagirl11 on 2009-11-11
It is a wired connection.

---

### Post by kestrel1 on 2009-11-11
Do you connect via a router?
Can you post the output from ```
lspci
```

---

### Post by oldgeekster on 2009-11-11
> **arizonagirl11 said:**
> Hi everyone. I as wondering if you can help me. I just installed ubuntu 9.10. my Windows 7 is about to expire, and i really do not want to buy it, since I really dislike Microsoft. Anyway, I am having a lot of trouble with the Internet. Sometimes, the Internet works, sometimes, it does not. It seems to be luck if the Internet works. The Internet worked fine on that same machine under Windows 7. This computer has Ubuntu 8.04, and is also working properly. However, the other machine in which I installed Ubuntu 9.10, I just cannot get internet working. I am fairly new to the scene, and I do not know what to do. i do not wanna go back to Windows. 

Any help would be greatly appretiated! Thanks!
KimmyPardon me for jumping in here, but in your situation it would make sense to install Ubuntu 9.04 on the machine in question rather than 9.1 which was only released a couple of weeks ago and has some reported difficulty in the networking arena.  I have my older notebook on the newer version and seem to be having very good luck compared to many, but even with that my DNS lookups are horribly slow compared to the Jaunty (9.04) version.  You can always upgrade to Karmic later on after things settle down and bugs are squashed. ;)

Just my own personal opinion - worth less than two cents. :rolleyes:

---

### Post by kestrel1 on 2009-11-11
> **oldgeekster said:**
> Pardon me for jumping in here, but in your situation it would make sense to install Ubuntu 9.04 on the machine in question rather than 9.1 which was only released a couple of weeks ago and has some reported difficulty in the networking arena.  I have my older notebook on the newer version and seem to be having very good luck compared to many, but even with that my DNS lookups are horribly slow compared to the Jaunty (9.04) version.  You can always upgrade to Karmic later on after things settle down and bugs are squashed. ;)

Just my own personal opinion - worth less than two cents. :rolleyes:

Valid point. I am using 9.10 myself, but have had few problems so far :-)
Maybe, coz I am on older hardware.

---

### Post by arizonagirl11 on 2009-11-11
Yes, I do connect via a router. This is the information that you requested, or at least, i hope it is :o) 

  	 	 	 	 	 	  00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)  
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)  
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)  
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)  
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)  
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)  
 00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)  
 00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)  
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)  
 01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)  
 02:01.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)  
 02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder  
 02:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)  
 

Yes, if this can't be figured out, i just may go to 9.04. 9.10 looks pretty neat, and I would love for it to work :(

---

### Post by kestrel1 on 2009-11-11
Can you post the results of ```
ifconfig
```
both, when you get an internet connection & also when you do not have a connection.

---

### Post by arizonagirl11 on 2009-11-11
I just rebooted the computer, and the Internet is working now. However, it will probably stop working if I reboot it again. This is the information from ifconfig, with the internet working. When it does not working, it is more or less the same, except under eth0, there is no inet addr. 

  	 	 	 	 	 	  eth0      Link encap:Ethernet  HWaddr 00:1a:92:47:c3:a1   
           inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::21a:92ff:fe47:c3a1/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1  
           RX packets:14 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:34 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:1939 (1.9 KB)  TX bytes:4782 (4.7 KB)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:82 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:82 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0

---

### Post by kestrel1 on 2009-11-11
If you right click on the network icon on the top right task bar you should be able to go to Edit Connections. Select the eth0 connection & click Edit. Make sure that MTU is set to automatic, IPv4 setting is on Automatic (DHCP) & that IPv6 is set to Ignore.
Are you certain that you ethernet lead is secure in the socket & not damaged in any way. It seems to suggest that you are not picking up your IP address via DHCP when you have no connection, which normally suggests faulty connection, cable or router.
When you have no connection can you try pinging the router ```
ping -b 192.168.0.1
```
Do you get a reply or not, I suspect not.

---

### Post by arizonagirl11 on 2009-11-11
the computer ran an update on itself, and after rebooting, I still had internet access. So hopefully, it's fixed! I'll let you know :OD

---

### Post by kestrel1 on 2009-11-11
Yes there have been a fair few updates since the original release. Ensure that you are fully up to date before you lose connection again :-)
You can check to see what updates have been installed with this command ```
dpkg -l
```
You may see something that relates to the network.

---

### Post by arizonagirl11 on 2009-11-11
there is so much stuff on it, it doesn't even all fit in the window when I scroll up. I really hope this update fixes the Internet. Thank you so much for your help :D

---

