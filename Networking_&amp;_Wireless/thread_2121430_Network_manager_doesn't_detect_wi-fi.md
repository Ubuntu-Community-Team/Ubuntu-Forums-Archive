---
title: "Network manager doesn't detect wi-fi"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by Victorfancelli on 2013-03-01
Hi 

It's a long time i'm using Ubuntu, but still a beginner. So, after searching without results, now it's my first post in this Forum!

I have an ASUS EEE 1001px with Ubuntu 12.04. I tried to update to 12.10 but everything crashes, so I re-installed 12.04: now Network manager doesn't detect any Wi-fi. I'm sure that there is a Wi-fi, and I'm sure it's not a problem with Wi-fi button (in my computer FN+F2). Indeed there's something strange: before, when I type FN+F2 I activate the Wi-fi Network in Network manager (I mean I check or uncheck the second option of the network manager applet). Now nothing happens.
 

 I installed the Broadcom STA drivers: "This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware".


 And I can show you the results of some commands (i put in blue what i type) I saw frequently in other posts: I hope this will be usefull.  

 

 Thank you in advance!



```
[COLOR=#0000ff]victor@perceval:~$ lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: AR2427 802.11bg Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:25:49:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:7f:2f:70
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=8.13.2.11 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
[COLOR=#0000cd]victor@perceval:~$ ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 20:cf:30:7f:2f:70  
          inet addr:8.13.2.11  Bcast:8.13.3.255  Mask:255.255.252.0
          inet6 addr: fec0::b:553c:6d69:e69f:b862/64 Scope:Site
          inet6 addr: 2002:80d:24a:b:553c:6d69:e69f:b862/64 Scope:Global
          inet6 addr: fec0::b:22cf:30ff:fe7f:2f70/64 Scope:Site
          inet6 addr: 2002:80d:24a:b:22cf:30ff:fe7f:2f70/64 Scope:Global
          inet6 addr: fe80::22cf:30ff:fe7f:2f70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:642148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247142 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:879755824 (879.7 MB)  TX bytes:27070321 (27.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:347886 (347.8 KB)  TX bytes:347886 (347.8 KB)

[COLOR=#0000cd]victor@perceval:~$ lspci[/COLOR]
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR2427 802.11bg Wireless Network Adapter (PCI-Express) (rev 01)
victor@perceval:~$ iwconfig wlano
wlano     No such device

[COLOR=#0000ff]victor@perceval:~$ iwlist scan[/COLOR]
wlan0     Failed to read scan data : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

### Post by El Tito on 2013-03-01
Hello.
I suppose you have tried, with no luck: 
```
sudo ifconfig wlan0 up
```
Have you read the following link and still doesn't work?[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"]
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx[/URL]

---

### Post by Hadaka on 2013-03-01
Hi, you dont have a broadcom card, lets 
remove that driver and see if the athk9 driver
that is for your card can be activated. please
copy and paste the following commands into
a termninal..ctrl/alt/t

```
sudo apt-get remove --purge bcmwl-kernel-source
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
 sudo modprobe -rfv ath9k 
sudo modprobe -v ath9k 
```
thanks

---

### Post by Victorfancelli on 2013-03-02
HI
Thank you for your answers and your help:
 
EL TITO: Yes I tried here the answers:
```
[COLOR=#0000ff]victor@perceval:~$ sudo ifconfig wlan0 up[/COLOR]
[COLOR=#0000ff]victor@perceval:~$ lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR2427 802.11bg Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:25:49:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:7f:2f:70
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=8.13.2.11 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

HADAKA:
This is the result: I wrote your commands, and after this rebooted for see if there's any diference. I think that's the reason for the purge "error". Now in the applet apperas the wired connection and the wifi but in the second it says "the device is not managed" Any idea?
```
[COLOR=#0000ff]victor@perceval:~$ sudo apt-get remove --purge bcmwl-kernel-source[/COLOR]
[sudo] password for victor: 
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11: El recurs no es troba disponible temporalment)
E: No s'ha pogut bloquejar el directori d'administració (/var/lib/dpkg/), hi ha cap altre procés utilitzant-lo?
[COLOR=#0000ff]victor@perceval:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[/COLOR]options ath9k nohwcrypt=1
[COLOR=#0000ff]victor@perceval:~$ sudo modprobe -rfv ath9k[/COLOR]
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-25-generic/kernel/net/wireless/cfg80211.ko
[COLOR=#0000ff]victor@perceval:~$ sudo modprobe -v ath9k[/COLOR]
insmod /lib/modules/3.5.0-25-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1

```
The problem is the driver, isn't?

---

### Post by Hadaka on 2013-03-02
Hi, please post the output of..

```
rfkill list all
```

thanks

---

### Post by Victorfancelli on 2013-03-02
Hi Hadaka;

here is the output:
```
victor@perceval:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by Hadaka on 2013-03-02
Hi,please do..

```
sudo modprobe ath9k 
```

and post the output of..

```
cat /etc/network/interfaces  
```
thanks.

---

### Post by Victorfancelli on 2013-03-03
Hi,
here is the output:

```
victor@perceval:~$ sudo modprobe ath9k
[sudo] password for victor: 
victor@perceval:~$ cat /etc/network/interfaces
auto lo br0
iface lo inet loopback
 
# wireless wlan0
allow-hotplug wlan0
iface wlan0 inet manual
 
# eth0 connected to the ISP router
allow-hotplug eth0
iface eth1 inet manual
```

Thanks!

---

### Post by Hadaka on 2013-03-03
Ah ha ! there is the problem !

*If your computer is a stand alone unit, not a server
and not part of a bridged network. Then changes need 
to be made to /etc/network/interfaces. it currently looks
like this....
```

victor@perceval:~$ cat /etc/network/interfaces
 auto lo br0
 iface lo inet loopback
   # wireless wlan0 allow-hotplug wlan0 iface wlan0 inet manual 
  # eth0 connected to the ISP router allow-hotplug eth0 iface eth1 inet manual 
```
 it should only look like this...for a stand alone computer

```
auto lo
iface lo inet loopback
 
```
so..again *if it is a single unit,stand alone please do this..
```
sudo gedit /etc/network/interfaces
```
remove all the extra lines and make it look like the sample i  sent you.
2 lines only. proof read, save and close. then
boot. your wireless should start working.

---

### Post by Victorfancelli on 2013-03-04
Hadaka, thanks for your help,

We have solved the problem, but just in part. I don't know why, every time I restart the computer I must write this (otherwise the wi-fi options doesn't appear in the applet). 
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
 sudo modprobe -rfv ath9k
  sudo modprobe -v ath9k
```
Is there a option to automatize this?

And maybe it's a different problem, but can I use my laptot as router for my smartphone? I used hostapd (before the big crash) and probably the problem was this (sorry for don't advice, I thought I refix all the things I changed!). I mean for using it I must change /etc/network/interfaces: must I find a solution without change this "file" or there's a way to change it without a wi-fi crash?

Thank you so much!

---

### Post by Hadaka on 2013-03-04
Hi, this will make it load the driver when you boot.

```
sudo su
 echo ath9k >> /etc/modules
exit
```

you will have to modify that file again to use hostpd
I have no experience with hostpd so i cant off any
ideas. If you get stuck, please open a new thread
and ask for help.
*If you are satisfied with how it is now
please use thread tools and mark this solved
thanks.

---

### Post by Hadaka on 2013-03-04
This is what your /etc/newtork/interfaces
looked like and NOT working..
--------------------------------------------------------------

victor@perceval:~$ cat /etc/network/interface
 auto lo br0 
iface lo inet loopback   
# wireless wlan0 
allow-hotplug wlan0 
iface wlan0 inet manual   
# eth0 connected to the ISP router 
allow-hotplug eth0 
iface eth1 inet manual
----------------------------------------------

you may have a typo or something simple that can be
eaisly corrected, I am sorry I cant't help you, as
I have no experience with hostapd...perhaps someone
else would care to chime in.
thanks again.

---

