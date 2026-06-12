---
title: "lose with either wicd or network manager"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by theromanone on 2009-02-26
Had network manager, everything worked, but when I'm in class I of course have wireless instead of wired, and the connection would cut out and connect back every 5, 10, 15 minutes, very random. So I installed wicd, and it's amazing, but I do not know how to setup my wired connection so now I'm back to network manager. Any help on what my problem is with wicd? After I uninstalled it and installed network manager back, wired just came on automatically after a reboot.

here's my lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:6e:e9:10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:0d:f2:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=134.53.120.14 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:9e:9e:37:f7:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


and here's my ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:23:8b:0d:f2:14  
          inet addr:134.53.120.14  Bcast:134.53.120.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13985 errors:0 dropped:11175297664 overruns:0 frame:0
          TX packets:15068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9234943 (9.2 MB)  TX bytes:1645574 (1.6 MB)
          Interrupt:248 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:6e:e9:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:15308
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3169 (3.1 KB)  TX bytes:3169 (3.1 KB)


thanks!

---

### Post by theromanone on 2009-02-27
please?

---

### Post by theromanone on 2009-02-27
healthy bump.

---

### Post by DeepLake21 on 2009-02-27
Just to understand, are you looking for help to configure a wired connection in wicd?

---

### Post by theromanone on 2009-02-27
> **DeepLake21 said:**
> Just to understand, are you looking for help to configure a wired connection in wicd?

Yes.. I've searched for about 1-2 hours on this and really have no idea what's going on.

WICD settings are:::
under externam programs:
DHCP Client, Wired Link Detection, and Route Table Flushing all Automatic.

under general settings:
WPA supplicant driver - wext
wireless interface    - eth1
wired interface       - eth0

wired autoconnect setting is on "use default profile on wired autoconnect"\




** By the way I have a Realtek network card

---

### Post by DeepLake21 on 2009-02-27
For Network Manager, you can left click the networking icon on the right of the top bar and view the available wireless networks; when you right click on the same icon, it gives you options to enable wired and wireless networking; you will also see the "Edit Connection" option. Through that option, you can configure the wired/wireless settings.

On the other hand, if you don't see the list of available wireless networks, then you don't have your wireless card configured yet.

I hope this helps.

---

### Post by theromanone on 2009-02-28
Thanks, but everything is just fine with network manager other than dropping the connection every once in a while. When I used WICD, wireless seemed much faster (surprisingly) and the only problem was I did not know how to setup wired.

Usually people can't get wireless to connect, but that's fine in WICD. 

By the way, I never configured any card of any sort.. I just installed the updates when ubuntu first booted up, and installed my Broadcom driver (which is for only the wireless I believe).

---

### Post by theromanone on 2009-02-28
Just thought of something.. anyway my MAC address could help me make a new wired connection in WICD, or should I not even bother going through the trouble of reinstalling it? Thanks again!

---

### Post by imdano on 2009-02-28
I'm a little confused...You should just be able to click "Connect" on the wired entry in the GUI.  What isn't working exactly?

---

### Post by theromanone on 2009-03-01
> **imdano said:**
> I'm a little confused...You should just be able to click "Connect" on the wired entry in the GUI.  What isn't working exactly?

Basically, in WICD, when I click connect in the wired connection, it never actually connects. It just says something like "getting the ip, or trying to connect," something like that, but it never actually connects

---

### Post by imdano on 2009-03-02
Can you enable debug mode (there's an option for it in the preferences window), try to connect, then post the contents of /var/log/wicd/wicd.log here?

---

