---
title: "Wireless gone missing after fresh Install"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by oryamoe on 2013-02-23
Hello everyone I am new to ubuntu. Installed 12.10 a couple weeks ago but was getting a system error msg regularly. something to do with the display. wireless worked great. So I looked into the 12.04 LTS. In the process i found edubuntu. Since I have two kids i chose to go with Edubuntu 12.04 LTS. I downloaded the .iso. burned it on DVD and ran it. The DVD worked fine, liked the system so Installed it. The wireless was working till this time. Once installed it asked for a reboot which I did but there was no wireless after that.
Now the wireless button (top right) shows no wireless connections, and the 'wireless networks' button is shadded so I cannot click it. it also says 'divice not managed' and 'disconnected'. The hardware button shows that wireless is on. I ran the lspci command in the terminal and got this info

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
04:00.0 Network controller: Intel Corporation WiFi Link 5100

I have a gateway nv58 laptop. I need help!

---

### Post by Hodevah on 2013-02-23
HI oryamoe:

I had similiar problems as you are experiencing now when I first install Ubuntu. 

It's too bad that you were not aware of firstly going to Software Sources>Ubuntu Software and selecting all options listed immediatly after installation and then going to do updates.

Regardless. Select to open a Terminal or do ctrl+Alt+T

You will need to put output of each of the following. 

Since you already posted information about lspci you will not need to post about that. 
Hopefully a guru will be here shortly to help you in this. Because my knowledge is still growing but I know you will be asked the following:


```
iwconfig
``````
lsusb 
``````
route -n

``````
uname -r 
``````
ifconfig -a | grep -iA9 wlan0 
``````
sudo lshw -C network
``````
 lsmod | grep -e rt2
``````
sudo lshw -class network                      
```For the last one above, put in your password that you created upon initial install. When in Terminal you are asked "password for user,"  enter your password. Do not worry, you password will not be visible.

Use 'Code' tags for all of the above. These are the "#" you will see. 


.

---

### Post by chili555 on 2013-02-23
We also want to see:```
rfkill list all
```Thanks.

---

### Post by Bucky Ball on 2013-02-23
*Thread moved to **Networking & Wireless**.*

---

### Post by oryamoe on 2013-02-27
Thanks chili555, the rfkill list all give the following info

AfCan@AfCan-NV58-Series:~$ rfkill list all 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 


@ Hodevah,

here is all the information i got from those commands. the smilies below are due to : and 0 being together.

AfCan@AfCan-NV58-Series:~$ iwconfig 
wlan0     IEEE 802.11abgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
lxcbr0    no wireless extensions. 
 
AfCan@AfCan-NV58-Series:~$ lsusb 
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
AfCan@AfCan-NV58-Series:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0 
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0 
AfCan@AfCan-NV58-Series:~$ uname -r 
3.5.0-25-generic 
AfCan@AfCan-NV58-Series:~$ ifconfig -a | grep -iA9 wlan0 
wlan0     Link encap:Ethernet  HWaddr 00:22:fa:26:b9:18   
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
AfCan@AfCan-NV58-Series:~$ sudo lshw -C network 
[sudo] password for abumuzamil:  
  *-network                
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:1f:16:9b:65:25 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:47 memory:f0500000-f050ffff 
  *-network 
       description: Wireless interface 
       product: WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:22:fa:26:b9:18 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=8.83.5.1 build 33692 ip=192.168.0.254 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:45 memory:f0600000-f0601fff 
AfCan@AfCan-NV58-Series:~$ lsmod | grep -e rt2 
AfCan@AfCan-NV58-Series:~$ sudo lshw -class network 
  *-network                
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:1f:16:9b:65:25 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:47 memory:f0500000-f050ffff 
  *-network 
       description: Wireless interface 
       product: WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:22:fa:26:b9:18 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=8.83.5.1 build 33692 ip=192.168.0.254 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:45 memory:f0600000-f0601fff 
AfCan@AfCan-NV58-Series:~$ ^C

---

### Post by oryamoe on 2013-02-27
the smiles in the  top portion are : and 0 together.

---

### Post by chili555 on 2013-02-27
> *-network
description: Wireless interface
product: WiFi Link 5100
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wlan0
version: 00
serial: 00:22:fa:26:b9:18
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=8.83.5.1 build 33692 [COLOR="Red"]ip=192.168.0.254[/COLOR] latency=0 link=no multicast=yes wireless=IEEE 802.11abgn Woweee! Where did that address come from? Did you fill in some box erroneously in Network Manager?

---

### Post by oryamoe on 2013-02-27
I have no idea where it came from. I just rechecked the Network Connections  but there are no channels listed under the wireless tab.

In the Devices-Network Tools under Network device: Wireless interface (wlan0) is selected and the IPv4 shows this 192.168.0.254 but  when i click configure i do not see any wireless channels active as stated above. I do have the image but dono how to share it with you

---

### Post by chili555 on 2013-02-27
> In the Devices-Network Tools under Network device: Wireless interface (wlan0) is selected and the IPv4 shows this 192.168.0.254 but when i click configure i do not see any wireless channels active as stated above.Remove it. NM should be blank except for Infrastructure. Please see attached.

NM ought to find and configure all Network Connections automagically.

---

### Post by oryamoe on 2013-02-27
> **chili555 said:**
> Remove it. NM should be blank except for Infrastructure. Please see attached.

NM ought to find and configure all Network Connections automagically.
Found the window you have in the image after clicking the Add button in the NM--> Network Connections but i cannot save it unless i change the ssid name.

---

### Post by oryamoe on 2013-02-27
Got to this window you have in the image after clicking  add in the NM. but I cannot save it unless i give it a ssid name.

---

### Post by chili555 on 2013-02-27
> **oryamoe said:**
> Got to this window you have in the image after clicking  add in the NM. but I cannot save it unless i give it a ssid name.Delete everything under wireless. Now are all tabs greyed out? That's what we want.

---

### Post by oryamoe on 2013-02-27
There is nothing under wireless. what do i do next.

---

### Post by chili555 on 2013-02-27
If you close that window, does the 192.xx address go away? Can you highlight it and delete it?

---

### Post by oryamoe on 2013-02-27
It is still there and I can highlight the row but cannot delete it. atleast not by pressing the del or the backspace buttons

---

### Post by chili555 on 2013-02-27
Let's dig deeper. May we see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
ls /etc/NetworkManager/system-connections/
```We may have some manual editing to do.

---

### Post by oryamoe on 2013-02-27
AfCan@AfCan-NV58-Series:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
 
auto wlan0 
iface wlan0 inet static 
  address 192.168.0.254 
  netmask 255.255.255.0 
AfCan@AfCan-NV58-Series:~$ cat /etc/NetworkManager/NetworkManager.conf[main] 
plugins=ifupdown,keyfile 
dns=dnsmasq 
 
[ifupdown] 
managed=false 
AfCan@AfCan-NV58-Series:~$ ls /etc/NetworkManager/system-connections/ 
AfCan@AfCan-NV58-Series:~$

---

### Post by chili555 on 2013-02-27
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.254
netmask 255.255.255.0 Ah, haaa! Let's try this:```
gksudo gedit /etc/network/interfaces
```Change the file to:```
auto lo
iface lo inet loopback

```Proofread, save and close gedit. Reboot and let us hear your report.

---

### Post by oryamoe on 2013-02-27
done now what. Just did a restart. here are the commands i ran again

AfCan@AfCan-NV58-Series:~$ sudo lshw -C network 
  *-network                
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:1f:16:9b:65:25 
       size: 100Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v2.19 ip=192.168.2.15 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
       resources: irq:47 memory:f0500000-f050ffff 
  *-network DISABLED 
       description: Wireless interface 
       product: WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:22:fa:26:b9:18 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=8.83.5.1 build 33692 ip=192.168.0.254 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:45 memory:f0600000-f0601fff 

AfCan@AfCan-NV58-Series:~$ cat /etc/network/interfacesauto lo 
iface lo inet loopback 
 
auto wlan0 
iface wlan0 inet static 
  address 192.168.0.254 
  netmask 255.255.255.0

---

### Post by chili555 on 2013-02-27
>  cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.254
netmask 255.255.255.0
Perhaps after you edited the file with gedit, you forgot to Save. Please retrace your steps. Please see attached.

---

### Post by joco1500 on 2013-02-27
in a word 

reinstall

---

### Post by chili555 on 2013-02-27
> **joco1500 said:**
> in a word 

reinstallAbsolutely not.

---

### Post by oryamoe on 2013-02-27
Absolutely not. I did not want to go that way. I wanted to solve the problem. And thanks to chili555 it is now solved.

Thanks alot everyone, especially chilli555

---

### Post by chili555 on 2013-02-27
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

