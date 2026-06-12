---
title: "wlan has stopped working"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by macoklein on 2010-06-30
Hey everyone, 
I'm sorry to say this linux cliche, but I am having trouble with my wireless. 

I have a Thinkpad T400 notebook that dual boots windows 7 and Ubuntu 9.04. My wireless has worked both in windows and ubuntu for the past several months. However 2 days ago, the wireless in ubuntu stopped working. I think this may be a result of trying to set up a static eth0 connection between my laptop and an embedded board, but I dont see how messing with eth0 would stop the wlan from working.

**Symptoms: **
When I left click on the network connections icon in the tray, all it lists under "Wireless networks" is "device not ready". Needless to say, there are no networks available to connect to. Also the wireless is working fine under windows. 

**Relevant Command line outputs:**

**lspci | grep Network**
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

**cat /etc/network/interfaces **

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

#iface eth0 inet static
#address 192.168.0.10
#netmask 255.255.255.0

**ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:27:13:66:ff:18  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc600000-fc620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48578 (48.5 KB)  TX bytes:48578 (48.5 KB)

pan0      Link encap:Ethernet  HWaddr 3e:d2:de:25:86:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:ef:0f:22  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f81f8000-f81f8100 

**sudo ifconfig wlan0 up**
SIOCSIFFLAGS: Operation not permitted

This is where I think the problem lies, but I have not been able to find information on how to fix this error. 

When I restart the network connections with /etc/init.d/networking restart 
The output contains the SIOCSIFFLAGS error. 

I am stumped, any ideas would be greatly appreciated. 
Thank you very much.

---

### Post by macoklein on 2010-07-01
Bump...

---

