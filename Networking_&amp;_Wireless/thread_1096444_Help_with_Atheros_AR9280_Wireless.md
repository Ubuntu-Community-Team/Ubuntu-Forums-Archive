---
title: "Help with Atheros AR9280 Wireless"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by oxsyn on 2009-03-14
So, little back story.  My card didn't work out of the box.  I had to install linux-backports-modules-intrepid-generic to get it to work.  After that, it worked well.

So, now it's not working.  It stopped showing up in Network Manager.  Here's some troubleshooting material though:

**ifconfig**
> wlan0     Link encap:Ethernet  HWaddr 00:15:af:ce:c5:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-CE-C5-A2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**iwconfig**
> wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**cat /var/log/messages**
> Mar 14 16:13:13 neutron syslogd 1.5.0#2ubuntu6: restart.
Mar 14 16:16:45 neutron kernel: [ 3871.887516] type=1505 audit(1237069005.170:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=7400
Mar 14 16:16:45 neutron kernel: [ 3872.082316] type=1505 audit(1237069005.366:6): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=7405
Mar 14 16:16:45 neutron kernel: [ 3872.082562] type=1505 audit(1237069005.366:7): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=7405
Mar 14 16:32:27 neutron -- MARK --
Mar 14 16:52:27 neutron -- MARK --
Mar 14 17:12:27 neutron -- MARK --
Mar 14 17:32:27 neutron -- MARK --
Mar 14 17:52:27 neutron -- MARK --
Mar 14 18:11:55 neutron kernel: [10781.738518] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 14 18:32:27 neutron -- MARK --
Mar 14 18:52:27 neutron -- MARK --
Mar 14 19:04:19 neutron kernel: [13925.817091] r8169: eth0: link up
Mar 14 19:04:19 neutron kernel: [13925.870742] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 14 19:15:28 neutron kernel: [14595.209234] ath9k 0000:03:00.0: PCI INT A disabled
Mar 14 19:15:28 neutron kernel: [14595.209292] ath9k: Driver unloaded
Mar 14 19:15:33 neutron kernel: [14600.256178] cfg80211: Using static regulatory domain info
Mar 14 19:15:33 neutron kernel: [14600.256187] cfg80211: Regulatory domain: US
Mar 14 19:15:33 neutron kernel: [14600.256191] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 14 19:15:33 neutron kernel: [14600.256197] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256203] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256209] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256214] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256219] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256224] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Mar 14 19:15:33 neutron kernel: [14600.256229] cfg80211: Calling CRDA for country: US
Mar 14 19:15:33 neutron kernel: [14600.341096] ath9k: 0.1
Mar 14 19:15:33 neutron kernel: [14600.341157] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 14 19:15:34 neutron kernel: [14600.777979] Registered led device: ath9k-phy0:radio
Mar 14 19:15:34 neutron kernel: [14600.777992] Registered led device: ath9k-phy0:assoc
Mar 14 19:15:34 neutron kernel: [14600.778004] Registered led device: ath9k-phy0:tx
Mar 14 19:15:34 neutron kernel: [14600.778016] Registered led device: ath9k-phy0:rx
Mar 14 19:15:34 neutron kernel: [14600.778021] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xffffc20011180000, irq=17
Mar 14 19:15:38 neutron kernel: [14604.828550] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 14 19:16:14 neutron kernel: [14641.335479] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 14 19:32:27 neutron -- MARK --
Mar 14 19:52:27 neutron -- MARK --
Mar 14 20:09:25 neutron kernel: [17832.464038] CE: hpet increasing min_delta_ns to 50624 nsec
Mar 14 20:32:27 neutron -- MARK --

**cat /var/log/dmesg | grep ath9k**
> [   10.997420] ath9k: 0.1
[   10.997698] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.997882] ath9k 0000:03:00.0: setting latency timer to 64
[   11.440192] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.540334] Registered led device: ath9k-phy0:radio
[   11.540520] Registered led device: ath9k-phy0:assoc
[   11.540704] Registered led device: ath9k-phy0:tx
[   11.540887] Registered led device: ath9k-phy0:rx

**cat /var/log/dmesg | grep Atheros**
> [   11.541088] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xffffc20011180000, irq=17

**lsmod | grep ath9k**
> ath9k                 269232  0 
rfkill                 19108  2 ath9k
lbm_cw_mac80211       247744  1 ath9k
led_class              13192  2 ath9k,asus_laptop

**sudo lshw -C network**
>   *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:ce:c5:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:56:5d:16
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.11 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:98:8e:3b:35:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**sudo iwlist scan**
> wmaster0  Interface doesn't support scanning.
wlan0     No scan results

**cat /etc/network/interfaces**
> auto lo
iface lo inet loopback

Please help :)

---

### Post by oxsyn on 2009-03-15
Seriously?

---

### Post by danburyct on 2010-12-01
Did you ever find a solution to this problem?  I am having the same issue with my Atheros AR9280 on Ubuntu 10.10. It use to work on 8.04 fine.  Somewhere in the upgrades to 9.04 and then 10.10 something changed and it cannot connect.  It appears to connect at first then just does not.
I upgraded to the latest compact using these instructions 

[http://hack2live.blogspot.com/2009/09/how-to-update-atheros-ath9kko-driver-to.html](http://hack2live.blogspot.com/2009/09/how-to-update-atheros-ath9kko-driver-to.html)

  My TX-Power is set to 17 dBM  and I cannot seem to be able to change this with iwconfig  or iw.  I keep getting the error message Error for wireless request "Set Tx Power" (8B26)  

Best Regards

       Ty

---

