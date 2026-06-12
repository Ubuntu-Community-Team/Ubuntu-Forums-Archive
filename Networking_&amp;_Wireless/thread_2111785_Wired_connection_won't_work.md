---
title: "Wired connection won't work"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by CommuneOfLoon on 2013-02-02
I'm trying to connect to a new wired internet connection I got at my house. My desktop, running Ubuntu 12.04, won't connect via the ethernet, though when I had the computer at work it would. The connection is good, as I tried the ethernet in the laptop I'm writing this on and it worked. I tried adding 
auto eth0 iface eth0 inet dhcpto the interfaces gedit doc and then restarting networking via the terminal (as per the directions here: [http://askubuntu.com/questions/161482/wired-connection-not-working-ubuntu-12-04](http://askubuntu.com/questions/161482/wired-connection-not-working-ubuntu-12-04)), but I get the following:

stop: Unknown instance
networking stop/waiting

Any assistance would be greatly appreciated. Thanks.

---

### Post by Bucky Ball on 2013-02-02
*Thread moved to **Networking & Wireless**.*

---

### Post by Hadaka on 2013-02-02
Hi, if you are just running your desktop as a stand alone, not a server
the /etc/network/interfaces file should just look like this in 12.04
```
auto lo
iface lo inet loopback
 
```
if you plug bback in your laptop to the ethernet cabe and do
```
cat /etc/network/interfaces 
```
it also will not have the extra lines you added, I would suggest
removing those added lines.
please post
```
ifconfig 
```
thanks

---

### Post by Bucky Ball on 2013-02-03
And also post the output of:
```

sudo lshw -C network
```

thanks.

---

### Post by CommuneOfLoon on 2013-02-03
I have removed the two lines I added to the gedit networking file; as well, the two lines you said should be there are, Hadaka.

Here is the output from the two commands (sorry about the lack of formatting):
```

Version:1.0 StartHTML:0000000167 EndHTML:0000003451 StartFragment:0000000457 EndFragment:0000003435    	 	 	 	 	 	   :~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 1c:6f:65:4b:0e:1f   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:41 Base address:0xe000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:16 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)  
 

 :~$ sudo lshw -C network  
 [sudo] password:  
   *-network                
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 02  
        serial: 1c:6f:65:4b:0e:1f  
        size: 10Mbit/s  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
        resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
```

---

### Post by CommuneOfLoon on 2013-02-07
Anything?

---

### Post by mörgæs on 2013-02-07
> **CommuneOfLoon said:**
> sorry about the lack of formatting

If you use CODE tags there's no need to be sorry.

---

### Post by CommuneOfLoon on 2013-02-08
> **mörgæs said:**
> If you use CODE tags there's no need to be sorry.

Perhaps you could explain how to do that or post a link explaining it?

Any help with my  issue?

---

### Post by JJSkoli on 2013-02-08
Can you please post the output of
```

cat /etc/network/interfaces

```
Thank you

---

### Post by Bucky Ball on 2013-02-08
> **CommuneOfLoon said:**
> Perhaps you could explain how to do that or post a link explaining it?

Any help with my  issue?

[code] at the beginning of the text and the same thing at the other end but add [/

You can also create a quick reply and click 'Go Advanced', select the code then click the # icon.

---

### Post by Bucky Ball on 2013-02-08
[/code] at the end of the code ...

---

### Post by CommuneOfLoon on 2013-02-16
> **JJSkoli said:**
> Can you please post the output of
```

cat /etc/network/interfaces

```Thank you


```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by CommuneOfLoon on 2013-02-21
I still have been unable to resolve this. Any help would be appreciated.

---

### Post by chili555 on 2013-02-21
Please plug in the ethernet and try to connect. Then immediately run and post:```
cat /var/log/syslog | grep -e eth -e etwork | tail -n20
dmesg | grep r8168
```Thanks.

---

### Post by CommuneOfLoon on 2013-02-28
I have no idea why, but the wired connection is now working. I plugged in an ethernet from the router LAN port and my desktop immediately connected to the wired connection. The USB wireless device is unplugged, and I even restarted the comp, still connected. Perhaps it's a result of being plugged into the router, or perhaps there was a serendipitous update that helped, not sure. 

Thanks to those of you who took the time to try and help me out :)

---

