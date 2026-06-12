---
title: "Need help with establishing wired connection"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by thehatching on 2011-12-25
Dear friends,

I have just started using ubuntu 10.04 on my netbook and have been suffering wired connection problems. I have gone through a lot of posts on the forum but couldn't find any solution. Now I am using wireless but the modem will be gone soon and I will only be able to use wired connection. Now I am using automatic IP but I will also be facing problems using static IP at school because I will have to use wired connection again. here is the message ifconfig returns:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:a1:46:9a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6899357 (6.8 MB)  TX bytes:1148619 (1.1 MB)

I disabled ipv6 thinking it was unnecessary but the problem is still there. I think for some reason my ubuntu does not recognize my network card.
Please help solve this problem. I desperately need the internet.

---

### Post by matt_symes on 2011-12-25
Hi

What is your card ? Open a terminal and type

```
sudo lshw -c network
```

Enter your password. It will not be echoed to the screen.

Post back results here.

Kind regards

---

### Post by thehatching on 2011-12-25
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:97000000-9703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:a1:46:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.4 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 memory:96000000-96001fff


Thank you

---

### Post by matt_symes on 2011-12-25
Hi

Have a read of this thread.

[http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html)

Kind regards

---

### Post by thehatching on 2011-12-26
Thank you very much guys,

The suggestion on the link you've given was very helpful. The problem was apparently the unrecognized ethernet driver even though it was seen by the system. I obtained the driver setup file and installed on my netbook. The setup took a while but everything works just fine now. 
What I did is simply as follows: 
1. went to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6)
2. downloaded compat-wireless-2.6.tar.bz2
3. extracted it with command tar -xjvf compat-wireless-2.6.tar.bz2
4. installed with sudo make install
5. and finally rebooted.

Thank you again.
I am marking the title [SOLVED]

---

