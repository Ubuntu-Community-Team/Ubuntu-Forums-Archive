---
title: "No IP for eth0"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by worth on 2009-06-03
I'm a newbie to ubuntu.  So when I run ifconfig for eth0 it doesn't show an IP.  There is only 1 ethernet card in this box and it is recognized when I do hardware testing.  I tried adding to /etc/network/interface the following:
auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
Then I run:
$ sudo /etc/init.d/networking restart
and I get the message "Ignoring unknown interface eth0=eth0."

Any suggestions on where to go from here?

---

### Post by theDaveTheRave on 2009-06-03
Worth

what is the output of your 
```

ifconfig

```
and
```
lshw -C network
```

that may give us some help.

Also I have a thread out there on [setting static IP]("http://ubuntuforums.org/showthread.php?t=954368"), a lot of the info in there should help you troubleshoot.

Good luck

David

---

### Post by superprash2003 on 2009-06-03
remove this line
allow-hotplug eth0

---

### Post by Iowan on 2009-06-03
If Network Manager is working correctly, you should be able to remove (or comment out) all three lines:```
#auto eth0
#allow-hotplug eth0
#iface eth0 inet dhcp
```Does DHCP server respond? (Post results of **sudo dhclient eth0**)

---

### Post by worth on 2009-06-04
Thanks for all the feedback.  I have not tried looking at the static IP link, but will soon.  Here are my results.  

```
ifconfig
```> etho                 Link encap:Ethernet  HWaddr  00:08:74:ae:19:3a
                          UP BROADCAST MULTICAST   MTU   Metric:1
                          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                          collisions:0 txqueuelen:1000
                          RX bytes:0 (0.0 B)    TX bytes:0 (0.0 B)
   
  lo                     Link  encap:Local Loopback
                          inet  addr:127.0.0.1   Mask:255.0.0.0
                          UP LOOPBACK RUNNING  MTU:16436    Metric:1
                          RX packets:0 errors:0 dropped:0 everruns:0 frame:0
                          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                          collisions:0 txqueuelen:0
                          RX bytes:0 (0.0 B)    TX bytes:0 (0.0 B)
   
  ```
lshw –C network
```> *-network
              description: ethernet interface
              product: 82540EM Gigabit Ethernet Controller
              vendor: Intel Corporation
              physical id: c
              bus info: pci@0000:01:0c.0
              logical name: eth0
              version: 02
              serial: 00:08:74:ae:19:3a
              width: 32 bits
              clock: 66MHz
              capabilities: bus_master cap_list Ethernet physical
              configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes
  *-network DISABLED
              description: ethernet interface
              physical id: 1
              logical name: pan0
              serial: 2e:6f:b4:59:6d:d3
              capabilities: ethernet physical
              configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  ```
sudo dhclient eth0
```> Internet Systems Consortium DHCP Client V3.1.1
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)
   
  Listening on LPF/eth0/00:08:74:ae:19:3a
  Sending on   LPF/eth0/00:08:74:ae:19:3a
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
  No DHCPOFFERS received.
  No working leases in persistent database  -  sleeping.


---

### Post by Iowan on 2009-06-04
> **worth said:**
> 
```
*-network DISABLED
```  Might be pointing to a driver issue.   Fortunately (or not - depending on need) I haven't had the "opportunity" to find/install different drivers.

Or is it UNCLAIMED that flags a driver problem???
Just in case... I'll point you to my [problem/fix]("http://ubuntuforums.org/showthread.php?t=1156441")

---

### Post by KalyanKK on 2009-11-14
Hi posting a solution for this problem for which i have spent a huge amt of time.

IP address is not seen in the eth0.

**To derive an IP is the action**

In the Terminal 
Step1: *sudo nano /etc/network/interfaces*
Step2: Edit the eth0
           [I]auto eth0
           iface eth0 inet dhcp[/I]
Step3: Exit the file by saving
Setp4: Run   *sudo /etc/init.d/networking restart*

Check *ifconfig* you will find the ip in INET ADDR  

If not then you will have to give a static IP Address
auto eth0
iface eth0 inet static
        address         192.168.1.2
        netmask         255.255.255.0
        broadcast       192.168.1.255
        gateway         192.168.1.254

---

