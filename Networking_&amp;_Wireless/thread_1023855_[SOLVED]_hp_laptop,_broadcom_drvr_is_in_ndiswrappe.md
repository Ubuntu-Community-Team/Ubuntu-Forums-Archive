---
title: "[SOLVED] hp laptop, broadcom drvr is in ndiswrapper, conflicting output reports, no w"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Lostin60's on 2008-12-28
I have an HP Pavilion zd8000 running windows Xp. This is a new install of ubuntu intrepid.  On a previous install of intrepid I installed ndiswrapper, and installed my broadcom driver, but had no wireless. Fought it for days.  Then I used a wired connection and reloaded from the net, rebooted, and boom, wireless connection. This time it didn't work. Here is some info. This is all terminal output.
lsmod | grep "wlan_module_name"   returns nothing

daniel@GLENDA:~$ sudo lshw -c network
[sudo] password for daniel: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ae:dd:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       [COLOR="Red"]product: BCM4306 802.11b/g Wireless LAN Controller[/COLOR]
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       [COLOR="Red"]configuration: driver=b43-pci-bridge latency=64 module=ssb[/COLOR]
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:14:76:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  [COLOR="Red"]daniel@GLENDA:~$ uname -mr
2.6.27-7-generic i686
[/COLOR]
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:39:a3:39:47:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


 dmesg
 16.452215] [COLOR="Red"]Broadcom 43xx driver loaded[/COLOR] [ Features: PLR, Firmware-ID: FW13 ]

[COLOR="Black"]daniel@GLENDA:~$ uname -mr
2.6.27-7-generic i686
[/COLOR]

[COLOR="Red"]Broadcom Corporation BCM4306 802.11b/g Wireless LAN
 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ 
[/COLOR]

[COLOR="Black"]eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ae:dd:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

[/COLOR]daniel@GLENDA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

daniel@GLENDA:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

[COLOR="Black"]daniel@GLENDA:~$ uname -mr
2.6.27-7-generic i686[/COLOR]
I know this post runs kind of long, but I think it has whatever is needed to figure this out.  Items in red seem to be my issues. I cant even find BCM4306 with a search.  I have looked in all the file and folders associated with ndiswrapper (I think) However my broadcom driver BCMWL5 IS in the ndiswrapper.  Also, I have nothing disabled in my network connections.  I think if I blacklist the BCM4306, I will be allright, but I am not sure.  Any and all help will be appreciated.



[COLOR="Black"][/COLOR]

---

### Post by Ayuthia on 2008-12-28
You seem to be on the right track.  You can try the following to see if it works:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```If it produces wireless sites, then it is working.  You will then need to blacklist b43 and ssb.  Hope that helps.

---

### Post by ieee488 on 2008-12-28
I am now running 8.10 on my Dell D400 laptop; it has wifi card with same chipset as yours.

Ayuthia's post [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72") worked for me. No need for ndiswrapper.

---

