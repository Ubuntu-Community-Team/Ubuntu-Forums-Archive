---
title: "Wifi dead slow !!!!"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by pieroxy on 2010-06-12
I just bought a Netgear WG111v3 (wifi usb), recognized out of the bow, and installation was very fast...

The problem I am having is that the connection is very very very slow. I cannot get more than 80 kbytes/s out of my network connection. And that is very random... It took 1 minute to preview this post! (it is also that slow on my LAN)
I have another machine running windows which can easily get 1 mbytes/sec out of the very same NIC...

I am at a loss as to how to get something faster...

I tried "sudo iwconfig wlan0 rate 54M" but the connection is lost after running the command. I have to reset it to 24M for the connection to get up again.

Some debug infos:
```
pieroxy@pieroxy-linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69424 (69.4 KB)  TX bytes:69424 (69.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:f5:a6:a8  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fef5:a6a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93401597 (93.4 MB)  TX bytes:12742717 (12.7 MB)

```


```
pieroxy@pieroxy-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"palmdrive"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:2F:AC:BD   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If anyone has a clue, that'd be great.

---

### Post by rtimai on 2010-06-12
I use a Netgear WG111v3 also. This is a long-shot, but have you tried changing the adapter's physical position -- e.g. placing it about the save distance off the ground as the router? The signal is sometimes height sensitive.

It took me a while after the AT&T installer left, who didn't know how to set up Linux networking, but it turned out if I simply deleted all the network connections and restarted, they were automatically re-detected, and I only had to enter the WPA/WPA2 password (which the AT&T guy called a "Key,") and everything worked. My connection averages about 85% efficiency. I think that's normal in this setup.

---

### Post by pieroxy on 2010-06-13
My NIC stands about 1 meter from my WRT54G router so I tend to think the location is not an issue. Signal strength is 100%. I am in this setup so I can use a cable until I get the final configuration for the wifi satisfactory. Then I plan to move my PC in another room.

My windows machine on the other end is in another floor and signal strength is about 65% and yet, 7-8mbps steady out of it...

---

### Post by rtimai on 2010-06-13
pieroxy,

In case a comparison may help, I'm providing the reports from my setup below. The router is a 2Wire 8600HGV-B.


```
rtimai@rtimai-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE394"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: B0:E7:54:3D:ED:81   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rtimai@rtimai-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:78:02:74:8a  
          inet6 addr: fe80::220:78ff:fe02:748a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8959 (8.9 KB)  TX bytes:8959 (8.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:b2:44:77:e6  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:b2ff:fe44:77e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1651024 (1.6 MB)  TX bytes:356917 (356.9 KB)
```


I am curious, however, why you mentioned your NIC. The WG111v2 adapter is plugged into to a USB port, no? I have a network card too, for this machine (once) had a wired connection, but it's not being used now. Is this a significant detail?

---

### Post by pieroxy on 2010-06-14
rtimai,

Thanks for your reply. I can see from your iwconfig that your wlan0 is reporting 54Mbps, mine is only reporting 24Mbps even though it seems to run at 1Mbps...

As for my NIC, that's how I call my WG111v3 adapter. I also have a 10/100 NIC on my mobo but I always unplug the cable and "ifconfig eth0 down" before testing transfer rates ...

---

### Post by asus701user on 2010-06-14
I am having real problems as well with slow wireless connection. This affects everything, not just Firefox. With a wired connection and in update manager the download speed is around 1200kB/s whereas using wireless it is 30-40kB/s.

Ubuntu version is 10.04 and teh kernel is 2.6.32-22-generic.

I am using an Asus 701 and Ubuntu Lucid. Wireless worked fine with the original Xandros OS from Asus. Here is some output from the machine:

          sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
---------------------------------

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dlink655"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1C:F0:55:B8:3B   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-----------------------------------

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications L2 100 Mbit Ethernet Adapter (rev a0)

----------------------------------------

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:e2:66:16  
          inet6 addr: fe80::21d:60ff:fee2:6616/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32242 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:102769457 (102.7 MB)  TX bytes:2174418 (2.1 MB)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3712 (3.7 KB)  TX bytes:3712 (3.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:47:d8:59  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe47:d859/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16830 (16.8 KB)  TX bytes:9250 (9.2 KB)
--------------------------------------

sudo apt-get install --reinstall ath5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ath5
----------------------------------


[SIZE=3][FONT=Arial]I guess it is something to do with the kernel or the driver but I don't know how to load a driver or even which one, since this seems a general problem in Lucid. If I look in Hardware drivers it says 'No proprietary drivers are in use'.

Hope someone can help.


[/FONT][/SIZE]

---

### Post by dineshbabumm on 2010-06-14
I too face the same problem. Any solution friends?

---

### Post by rtimai on 2010-06-14
After some last cautions I'm going to stop trying to help. I don't know enough to provide solutions. I tried researching problems with the WG111, and find mostly help requests and no answers, particularly on the Netgear site. I did notice some common general advice, however. 

One was not to try to install Windows drivers on Linux, but to use drivers written for Linux, either Open Source or non-free -- but not Windows drivers. 

The second was not to try using NDISWRAPPER, which is I think to enable Windows drivers to run on Linux. Apparently they may work, but since Karmic, drivers written for the native system are better. I don't know if this is good advice, but I did see it repeated in several forums. I checked, and I don't have ndiswrapper installed. 

The last is don't give up looking for a solution for the WG111. It runs fine on my system without any manual configuration. I simply deleted all the network connections that the installers had set up, and restarted, and my connection was automatically set up -- all I needed to do was enter the "Key" string as the WPA/WPA2 Password. I said "installers" because the WG111 worked the same with the wireless router provided by Comcast, and now by AT&T. 

I don't know if this will help but I checked and I appear to be using the rtl8187 wireless LAN driver, and this driver seems to be provided by Canonical in the default Ubuntu installation. 

Don't know (again) if this might help, but I entered "wireless" in Synaptic Package Manager, sorted by Status, and these are the modules that were installed by default. 

bcmwl-modaliases
jockey-common
jockey-gtk
libiw30
libopenobex1
network-manager-pptp
network-manager-pptp-gnome
pcmciautils
wireless-crda
wireless-tools
wpasupplicant

OK. That's it. I got nothing more. Good luck.

---

### Post by pieroxy on 2010-06-17
Well, things changed a bit at home. I got myself to install ndiswrapper, and the first step is to disable a bunch of drivers in blacklist.conf. I restarted the computer and the USB Wifi Stick was instantly recognized... Which means I didn't disable the proper drivers. 

Now I can get my Wifi connection up to around 1.2 mbytes/s. That's a heck of a lot better than before. Still lower than my internet connection or my theoretical speed, but I can live with this a bit longer than before.

Ah, and I also tried to comment out the lines I added in my blacklist.conf, but the Wifi still goes at 1.2 mbytes/s

I think I'll wait for a little while to see if a fix comes through regular updates. Otherwise I don't see any other way than ndiswrapper. Has anyone had any success with it?

---

