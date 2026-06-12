---
title: "Atheros AR928X network card disabled on Asus laptop"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by The Dragon Master on 2009-11-22
Hi

My Atheros AR928X network card is permanently disconnected. It used to give me a workjing wifi many (about 9) months ago. When it stopped working I tried upgrading to Jaunty (I can't remember what Ubuntu flavour I had before that though, probably what ever was cutting edge 12 months ago) and after failling to get wifi working in Jaunty I upgraded to Karmic last week. Still no joy, so I tried dropping Network Manager and currently have wicd installed, wicd reports "no wireless networks found" but I am posting from a second laptop running XP via a wireless connection so lack of signal is not the problem. The clues (for those with enough coffee beans behind them to understand them)....

Machine: Asus X59SR series laptop

david@wert:~$ lspci -nn|grep Wireless
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

david@wert:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:ef:da:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

david@wert:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
david@wert:~$ lsmod |grep wlan
wlan                  226448  1 ath_pci

david@wert:~$ dmesg|grep module
[    0.886131] brd: module loaded
[    0.886571] loop: module loaded
[   24.624541] ath_hal: module license 'Proprietary' taints kernel.

david@wert:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:23:54:ef:da:51
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:19 memory:fddfcc00-fddfcc7f ioport:cc00(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:43:51:b2:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdff0000-fdffffff

david@wert:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

david@wert:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

david@wert:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

david@wert:~$ uname -mr
2.6.31-14-generic i686

david@wert:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces..


So what do you Ubuntu Guru's recon? Time I ditch Karmic and go buy Vista? ;)

---

### Post by The Dragon Master on 2009-11-22
aRRRHHHGGG!!!! I just found this thread	](*,)

[http://vip.asus.com/forum/view.aspx?board_id=3&model=X59SR&id=20090525161556002&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=X59SR&id=20090525161556002&page=1&SLanguage=en-us)

So there's an on / off switch at the side of the laptopj. Well, it's not actually solved the problem, but what's changed?

1) ifconfig hasn't, still no mention of wlan0
2) iwconfig wlan0 now shows "Tx-Power=0 dBm" 
3) same "ath_hal: module licence 'Propriety' taints kernel" message from dmesg
4) lshw still shows "*-network DISABLED" for the wireless
5) iwlist output unchanged

Hmmm. A disapointing lack of progress after turning the device on and rebooting.

any ideas dudes?

---

### Post by The Dragon Master on 2009-11-22
For the record, there is nothing obvious related in 

System | Administration | Hardware Drivers

so I'll try the procedure described here [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by The Dragon Master on 2009-11-22
> **The Dragon Master said:**
> 
so I'll try the procedure described here [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Nice!!! So lshw no longfer show the "DISABLED" thing and we get

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:22:43:51:b2:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
:P

However, wicd still doesn't see any wireless networks though and there's no sign of life in System | Administration | Network Tools  

it ain't over yet! :?

---

### Post by The Dragon Master on 2009-11-22
> **The Dragon Master said:**
> 
it ain't over yet! :?

It is now!!! :guitar:

thanks to Ayuthia's tips on this thread [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-1308533.html&ei=uaQJS_m8O4Oj4QbLzrDPCw&usg=AFQjCNFRYvzDIBAteAiWMTzeFj1RoKcV4g&sig2=GTx_3wr0bw9mIkLaYzyZ3Q](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-1308533.html&ei=uaQJS_m8O4Oj4QbLzrDPCw&usg=AFQjCNFRYvzDIBAteAiWMTzeFj1RoKcV4g&sig2=GTx_3wr0bw9mIkLaYzyZ3Q)

"modprobe wl" was giving a fatal error and I didn't have any of the dkms stuff, so I just installed bcmwl-kernel-source and dkms, rebooted. Then an "iwlist scan" showed the local livebox was being detected and wicd was able to connect to it once I had enterred my WPA 1/2 passphrase.

whola whola whola!! ):P

---

