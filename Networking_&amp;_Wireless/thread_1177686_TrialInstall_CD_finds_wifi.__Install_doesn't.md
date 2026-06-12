---
title: "Trial/Install CD finds wifi.  Install doesn't"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by calebhoward on 2009-06-03
This is weird.

I just got a new laptop (Asus G71G), which has an Atheros AR928X Wireless Network Adapter in it.

When I booted from the trial/install CD of Kubuntu 9.04 (64bit), (Downloaded on June 1, 2009) I can scan for my wifi network from the default app icon in the lower-right taskbar widget.  It sees about 5-8 networks including mine.  

When I install clean, and do the same thing, it shows no available networks.

when I run:

lspci -v

I see that it is using the ath9k Kernel driver.

I'm a long-time Linux user, Irix and Unix before that, and a computer-savvy guy by trade, but I'm less familiar with wifi than other stuff.

Why should the CD boot find my wifi, but not the fresh install from that same CD?

All hints, and pointers appreciated.

-caleb

=========================================================

[adding info according to guidelines]

Machine: Asus G71G Laptop
Wireless Network adapter: Atheros AR928X

=========================================

lspci wireless info:
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

==========================================

ifconfig:
                                                                                               
wlan0     Link encap:Ethernet  HWaddr 00:22:43:85:e6:91
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

=================================================

iwconfig:
wlan0     IEEE 802.11bgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

=====================================================
lsmod | grep ath:
ath9k                 288568  0
mac80211              251144  1 ath9k
led_class              13064  2 ath9k,asus_laptop

======================================

modprobe -l | grep ath:
kernel/drivers/net/wireless/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath9k/ath9k.ko
kernel/drivers/md/multipath.ko
kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
volatile/ath_hal.ko
volatile/ath_pci.ko
volatile/ath_rate_amrr.ko
volatile/ath_rate_minstrel.ko
volatile/ath_rate_onoe.ko
volatile/ath_rate_sample.ko

=============================================

modprobe -l | grep wlan:
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
volatile/wlan.ko
volatile/wlan_acl.ko
volatile/wlan_ccmp.ko
volatile/wlan_scan_ap.ko
volatile/wlan_scan_sta.ko
volatile/wlan_tkip.ko
volatile/wlan_wep.ko
volatile/wlan_xauth.ko

===========================================

dmesg:                                                                                                        
...
[   11.288229] cfg80211: Calling CRDA to update world regulatory domain
...
[   11.530447] cfg80211: World regulatory domain updated:
[   11.530450]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.530452]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.530455]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.530456]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.530458]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.530460]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.569648] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.569708] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.611896] ath9k: 0.1
[   11.611941] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.611950] ath9k 0000:07:00.0: setting latency timer to 64
[   12.038787] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.086221] Registered led device: ath9k-phy0:radio
[   12.086255] Registered led device: ath9k-phy0:assoc
[   12.086290] Registered led device: ath9k-phy0:tx
[   12.086322] Registered led device: ath9k-phy0:rx
[   12.086727] phy0: Atheros 9280: mem=0xffffc20010160000, irq=17
[   12.192157] lp: driver loaded but no devices found
....
[   12.263796] Adding 12699340k swap on /dev/sdb5.  Priority:-1 extents:1 across:12699340k
[   12.379248] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04711/0xa00000
[   12.453413] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   12.802318] EXT3 FS on sdb1, internal journal
[   13.821385] type=1505 audit(1244096946.150:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2358
[   13.821477] type=1505 audit(1244096946.150:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2358
[   13.821521] type=1505 audit(1244096946.154:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2358
[   13.821557] type=1505 audit(1244096946.154:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2358
[   13.918241] type=1505 audit(1244096946.249:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2363
[   13.918379] type=1505 audit(1244096946.249:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2363
[   13.963785] type=1505 audit(1244096946.294:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2367
[   16.004642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.004644] Bluetooth: BNEP filters: protocol multicast
[   16.018104] Bridge firewalling registered
[   16.998812] ppdev: user-space parallel port driver
[   20.669435] r8169: eth0: link up
[   20.669449] r8169: eth0: link up
[   21.176453] ADDRCONF(NETDEV_UP): wlan0: link is not ready


===================================================

sudo lshw -C network:

*-network                                                                                                                  
       description: Wireless interface                                                                                       
       product: AR928X Wireless Network Adapter (PCI-Express)                                                                
       vendor: Atheros Communications Inc.                                                                                   
       physical id: 0                                                                                                        
       bus info: pci@0000:07:00.0                                                                                            
       logical name: wmaster0                                                                                                
       version: 01                                                                                                           
       serial: 00:22:43:85:e6:91
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:5f:a3:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.1.107 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:8d:b9:ac:c6:c6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

==========================================================

iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

======================================================

lsb_release -d:

Description:    Ubuntu 9.04

==================================================

uname -mr:
2.6.28-11-generic x86_64

==================================================

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...Ignoring unknown interface eth0=eth0.
                                                                                                                      [ OK ]

===================================================

OK.  That's everything the guidelines ask for.  It seems overly thorough to me, but there you are.

(actually, I had to crop the output of lsmod and dmesg severly because otherwise, the forum posting interface complained that I was trying to upload 28 pictures.  There were actually no pictures in my post)

Help?

Thanks!

-caleb

---

### Post by chili555 on 2009-06-04
Please note here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 

Especially note this:> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.As long as you have a working ethernet connection, which you do:> duplex=full ip=10.0.1.107 latency=0 link=yesNetwork Manager is designed to disallow a wireless connection. Please disconnect the wire and restart networking:```
sudo /etc/init.d/networking restart
```Any improvement in your wireless behavior?

---

### Post by calebhoward on 2009-06-04
> **chili555 said:**
> Please note here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 

Especially note this:As long as you have a working ethernet connection, which you do:Network Manager is designed to disallow a wireless connection. Please disconnect the wire and restart networking:```
sudo /etc/init.d/networking restart
```Any improvement in your wireless behavior?

Sadly, no.

At boot, on a more-or-less virginal install (I have installed a new NVidia driver), there is a network icon on the bottom toolbar.  It is just the same as you see booting from the live disk.  When I choose "Manage Connections" from it's menu options, it brings up a window called: "Network Management - KDE Control Module".  I then select the "Wireless" tab, and press the "Add" button which brings up a window called "Add network connection - KDE Control Module".  On this window is a button that says "Scan".  Pressing this brings up a window with a graphic representation showing available access points.  When I boot from the live CD, this display shows me several local wireless networks.  When I boot from HD after having installed from that very same live CD, it shows me nothing.  This is true whether I have an ethernet cable plugged into eth0 or not.

I am grateful for your attention and assistance in this.  I have seen your expertise on other threads I've come accross, and you clearly are one who can help.  I'm pretty comfortable with diagnostic procedures, and have worked as a tech support person in the past.  Any and all detailed advice you can offer will be gratefully received.  If you can point me at any online step-by-step rigorous diagnostic procedures - with and/or without GUIs, I would appreciate that as well.  I love GUIs, but I also appreciate gaining an underlying understanding of the config files involved.

Thanks again!

-caleb

---

### Post by chili555 on 2009-06-05
Thank you for your very kind comments. The appreciation of my 'clients' is what keeps me going. Since you are a long time linux user, I will try to go fast. First, in order to manage your network interfaces (eth0 and wlan0, in your case), they must *not* be set up to be manually configured. Please do:```
sudo nano /etc/network/interfaces
```If there is anything further in the file than this:```
auto lo
iface lo inet loopback
```Please remove the excess wording, unless it's commented out. Proofread, save and close.

Next, scanning should be done as root, or in Ubuntu-speak, as sudo. Please do:```
sudo iwlist wlan0 scan
```Are there any scan results?

Last, let's see if we can see what's happening under the hood:```
dmesg | grep wlan0
sudo cat /var/log/messages | grep -i network
```Frankly, in all the data you have posted above, I don't see anything alarming. This may be my favorite issue: everything looks perfect, except it doesn't work!

---

### Post by calebhoward on 2009-06-06
> **chili555 said:**
> Thank you for your very kind comments. The appreciation of my 'clients' is what keeps me going. Since you are a long time linux user, I will try to go fast. First, in order to manage your network interfaces (eth0 and wlan0, in your case), they must *not* be set up to be manually configured. Please do:```
sudo nano /etc/network/interfaces
```If there is anything further in the file than this:```
auto lo
iface lo inet loopback
```Please remove the excess wording, unless it's commented out. Proofread, save and close.

Next, scanning should be done as root, or in Ubuntu-speak, as sudo. Please do:```
sudo iwlist wlan0 scan
```Are there any scan results?

Last, let's see if we can see what's happening under the hood:```
dmesg | grep wlan0
sudo cat /var/log/messages | grep -i network
```Frankly, in all the data you have posted above, I don't see anything alarming. This may be my favorite issue: everything looks perfect, except it doesn't work!


Well, you certainly have the full appreciation of this client.  ;-)

$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


$ sudo iwlist wlan0 scan
wlan0     No scan results

$ dmesg | grep wlan0
[   21.679494] ADDRCONF(NETDEV_UP): wlan0: link is not ready

$ sudo cat /var/log/messages | grep -i network
Jun  3 00:59:55 Laptop kernel: [   13.376723] type=1505 audit(1244015994.905:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2370
Jun  3 23:29:07 Laptop kernel: [   13.821521] type=1505 audit(1244096946.154:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2358
Jun  4 19:18:43 Laptop kernel: [   14.324899] type=1505 audit(1244168322.644:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2383
Jun  4 19:52:33 Laptop kernel: [   13.722848] type=1505 audit(1244170352.044:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2360
Jun  4 23:10:56 Laptop kernel: [   13.364329] type=1505 audit(1244182254.884:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2429
Jun  5 00:59:06 Laptop kernel: [   14.580484] type=1505 audit(1244188744.921:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2403
Jun  5 19:21:40 Laptop kernel: [   14.079338] type=1505 audit(1244254899.425:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2412
Jun  5 19:42:57 Laptop kernel: [ 1292.607245] type=1505 audit(1244256177.272:11): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=5112

I'll look for you on AOL (AIM) tomorrow morning at 9:30 my time, 12:30 pm your time.

Thanks!

-caleb

P.S.  I'm glad this is a pleasant challenge.  I like learning stuff, and I know it will work in the end.  I find it particularly interesting that it runs from the live CD.  Could the NVidia driver be causing it?  What else is different between booting from Cd and HD?  Thhis laptop also has some sort of weird firmware quasi-OS that - from powered off - lets me quick boot to an environment with email, skype, a music player, and a web browser.  I disabled it's access to the wireless interface, on the off chance that it might have a ghostly grip on the resources when I boot to linux.  The system is also dual-boot with (gak) vista.The wireless works fine on the windows side, and in the quick-boot interface, and from the live CD - just not kubuntu from HD.  Fun stuff!

---

### Post by calebhoward on 2009-06-06
Let me here say this and no one deny:  chili555 rocks!

weird problem solved!

NetworkManager was the fault.  wicd was the solution.

My beefy new laptop is now fully operational!

Yay!

---

### Post by chili555 on 2009-06-07
Thank you for your kind comments, sir! Just a few more details for the benefit of the searchers. Network Manager saw no networks. Disabling it with:```
sudo /etc/init.d/NetworkManager stop
```and then starting the interface manually and scanning:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```and we ***did*** see your network! You installed Wicd from apt-get and saw your network and connected.

Thanks again for your compliment.

---

### Post by kachemak on 2009-06-09
I too am having the same problem on my new G71G. The wireless works fine when I boot from the Ubuntu 9.04 live CD, but not after installed on the system. I also tried installing a few other distros just to test and the wireless worked fine with them all. It just doesn't work with a clean Ubuntu install. I'm not much of a techie, but I'll follow this thread and give it a try in the next couple days. Thanks.

---

