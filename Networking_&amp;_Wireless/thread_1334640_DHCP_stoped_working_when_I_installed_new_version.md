---
title: "DHCP stoped working when I installed new version"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by richpri on 2009-11-22
I just installed UBUNTU 9.04 on my desktop.
It was previously running 8.4 and the network
was working fine.  But now I cannot get DHCP
to work except if I power cycle my Linksys
router and then execute a sudo dhclient
command.  This work around is annoying.

My Linksys BEFSR41 router is running its
default configuration and my other pc
is still working fine while connected to it.

I tried the fix to /etc/dhcp3/dhclient.conf
recommended in the "DHCP quit working" thread
but the symptoms did not change.

I would be thankful for any suggestions.

Other information:

rich@rich-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:da:34  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe8a:da34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3524086 (3.5 MB)  TX bytes:264007 (264.0 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233180 (233.1 KB)  TX bytes:233180 (233.1 KB)

pan0      Link encap:Ethernet  HWaddr b2:a8:b5:5e:03:04  
          inet6 addr: fe80::b0a8:b5ff:fe5e:304/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:17175 (17.1 KB)

pan0:avahi Link encap:Ethernet  HWaddr b2:a8:b5:5e:03:04  
          inet addr:169.254.3.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

rich@rich-desktop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 pan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 pan0
rich@rich-desktop:~$

---

### Post by Iowan on 2009-11-22
I presume the information you provided was after the router reboot?  Check contents of */etc/network/interfaces* to see if anything got put/left in there during upgrade (should have only definition for "lo". Also, make sure "Auto eth0" is set to "Connect automatically".

---

### Post by richpri on 2009-11-23
Yes it was after router reboot?  Do you want a before shot?

The /etc/network/interfaces file looks ok.

Where do I check that "Auto eth0" is set to "Connect automatically"?

---

### Post by Iowan on 2009-11-23
May as well include the "before" shot...
> **richpri said:**
> Where do I check that "Auto eth0" is set to "Connect automatically"?
Right-click NM-applet icon, choose **Edit Connections...**
Highlight **Auto eth0**, click the **Edit** button.
Just below **Connection name:** is a checkbox to **Connect automatically** that should be checked.

---

### Post by richpri on 2009-11-23
I just solved problem [I think] by uninstalling and reinstalling the Network Manager.  I will see if the problem reoccurs when I reboot later.

---

### Post by richpri on 2009-11-23
After I rebooted I was back to no connection .  Thats when I made my big mistake. I uninstalled network manager again and now I cannot reinstall it because I am not connected to the network.

I tried to configure eth0 staticly but I get the message 
SIOCADDRT: No such process
failed to bring up ETH0
when I try to start it.

Is there a way to use the distro disk to reinstall network manager?

---

### Post by richpri on 2009-11-25
Solved problem of configuring static connection. 
This got me back in, but when i shut down and restarted the PC
I could not connect until i rebooted the Linksys.
I am beginning to suspect som basic incompatability 
with Linksys was created by the 9.04 upgrade!!!

---

### Post by richpri on 2009-11-26
I tried to upgrade the firmware on the Linksys and I fried the router.
I purchased a new DYNEX DX-E402 and everything works fine now.
Dhcp works with the Dynex but I never got it to work with the Linksys.
I guess I would advise the cheeper Dynex to anyone setting up a home LAN.

---

