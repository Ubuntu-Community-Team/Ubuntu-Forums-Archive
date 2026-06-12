---
title: "VPN to Wired Network - How?"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by shenoy007 on 2009-02-04
Hi Experts,

My office network is based on Windows (Hub based) and using Windows Server 2003. But Some machines OS is Ubuntu 8.10 (Including My Machine!). We have total 15 machines and 5 of them Using Windows OS and others are based on different Ubuntu Versions (8.04, 8.10, 7.10).

**The Main Problem is:** 
After installation of Ubuntu 8.10 in my machine, the connection shows **VPN Network**. In all other systems in my office shows **Wired Network**. Due to this problem i can't access server and no others can access shared folders in my computer. But i can access Internet. I tried to convert into Wired Netrwork but failed. 

I have permission to change all things. I am the **root** user. But when try to edit network connection, the VPN Tab appears as disabled.


Please help me!

With Thanks & Regards,
Prasanth Shenoy

---

### Post by callan79 on 2009-02-05
> **shenoy007 said:**
> After installation of Ubuntu 8.10 in my machine, the connection shows **VPN Network**. In all other systems in my office shows **Wired Network**. Due to this problem i can't access server and no others can access shared folders in my computer. But i can access Internet. I tried to convert into Wired Netrwork but failed.

Hi Prasanth,

You can't 'convert' as such.

If I left-click on Network Manager on my computer (Ubuntu 8.10), I see this:

Wired Network
  Auto (eth0)
-------------
VPN Connections > 


So "Wired Network" is just a category, and "Auto (eth0)" is the name of my connection.

Do you have anything underneath "Wired Connection" ?

If not, it probably means that your network card has not been detected by Ubuntu.

Is your computer old, or new?

Can you post output of:

```
lspci
```

and

```
ifconfig
```

Thanks
Callan

---

### Post by shenoy007 on 2009-02-05
Thanks Callan,

But when I left-click on Network Manager on my computer (Ubuntu 8.10), I see this:

Wired Network
Auto (eth0)
-------------
VPN Connections >  

and only the VPN Connections> appears enabled. Others are disabled.

///////////////////////////////////////////////////////////////////////

The result of your code is:



00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


AND




eth0      Link encap:Ethernet  HWaddr 00:1c:c0:10:6a:a9  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe10:6aa9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299435463 (299.4 MB)  TX bytes:8636910 (8.6 MB)
          Interrupt:222 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1434824 (1.4 MB)  TX bytes:1434824 (1.4 MB)



Waiting for your reply,

With Thanks & Regards,
Prasanth Shenoy

---

### Post by callan79 on 2009-02-06
> **shenoy007 said:**
> 

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:10:6a:a9  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0




Hi Prasanth,

Well it looks like your network is up, as you have an IP Address etc.

Next, I'd make sure you're logged in as a user that can create network connections (check via system >> administration >> users & groups).

Also, perhaps you could take a screenshot of what your network manager looks like, it seems like Auto (eth0) should be enabled, as the ifconfig command shows that it's up.

To take a screenshot, use the tools on Applications >> Accessories.

Cheers
Callan

---

### Post by superprash2003 on 2009-02-06
what is your server ip address?? the windows server's ip.. should be of the form 192.168.1.x .. are you able to ping that?

---

### Post by shenoy007 on 2009-02-07
Thanks Callan,

Actually i didn't get the idea you shared. But here i posted some images which will helps you.

[IMG]http://prasanthshenoyp.googlepages.com/SC-1.jpg/SC-1-full;init:.jpg[/IMG]


[IMG]http://prasanthshenoyp.googlepages.com/SC2.jpg/SC2-full;init:.jpg[/IMG]

Also, I am the full powered root user, i can edit, delete, create all items. [Gruop, User].

Please write back if any clarification needed.

With lots of thanks,
Prasanth Shenoy

---

### Post by callan79 on 2009-02-07
> **shenoy007 said:**
> 
[IMG]http://prasanthshenoyp.googlepages.com/SC2.jpg/SC2-full;init:.jpg[/IMG]

Also, I am the full powered root user, i can edit, delete, create all items. [Gruop, User].



Hi Prasanth,

Okay, so your network is up and running, you have an Auto (eth0) connection which is connected, and you can access the Internet.

I'm not sure if I mis-read something, but what exactly is the actual problem?

Cheers
Callan

---

### Post by din on 2009-02-08
install network-manager-openvpn

---

### Post by shenoy007 on 2009-02-09
Thanks Callan,

My problem is solved after a long automatic updation. I can now enter into others shared folders, which was my actual problem. I don't no how was it solved? I think it was due to some missing packages. 

Also thanks to din and superprash.

But after the reboot the system takes more time to boot and at the time of booting the following line displayed.

NFS Connections         [failed]

this shows two times.

I reboot my computer and same thing happened.

If u have any idea on this plz share.

With Thanks & Regards,
Prasanth Shenoy

---

