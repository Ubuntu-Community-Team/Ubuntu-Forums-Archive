---
title: "Wireless driver installed, cannot configure network"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by buggywhip on 2009-05-27
I am a newbee to Linux.  I have installed Ubuntu 8.10 on a Dell Inspiron 1150, replacing Windows.  I am having trouble connecting to a wireless network.  The wireless card is Broadcom 1350 wlan minipci.  I have attached the correct driver.

> ~$ sudo ndiswrapper -l
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)Clicking on the NetworkManager icon shows "Wireless Networks" faded out.
System -> Administration -> Network shows all connections faded out.
What am I missing?

> ~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:62:12:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16056 (16.0 KB)  TX bytes:16056 (16.0 KB)

~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

---

### Post by superprash2003 on 2009-05-28
post output of **lshw -C network**

---

### Post by buggywhip on 2009-05-28
Thank you for responding.  I hope this helps you help me.


> ~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:62:12:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.4 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0f:9b:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:2d:80:3e:d6:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

### Post by superprash2003 on 2009-05-28
have you tried system->admin->hardware drivers?

---

### Post by buggywhip on 2009-05-29
'system->admin->hardware drivers' shows only one driver

> Broadcom B43 wireless driver
fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.I think this is where I lack of understanding.  What is the relationship between MBC43xx and the Windows driver I downloaded from Dell (bcmwl5 installed by ndiswrapper)?

Thank again for your help.  I'm checking out your blog.

---

