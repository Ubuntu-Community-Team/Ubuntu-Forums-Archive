---
title: "BCM4306 / Ubuntu 8.10 / Dell Inspiron 1150"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by jleupen on 2009-01-01
Long time computer admin, but Ubuntu noob.  

I installed a fresh copy of Ubuntu 8.10 and am unable to get the wireless working.   I have searched all over and have tried many things to no avail...  Hoping someone here can help.

Here is some information:

laptop:~$ lspci -nn |grep -i broadcom
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:08:fd:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

laptop:~$ lsmod | grep b43
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  2 b43,b44

laptop:~$ dmesg | grep -e b43 -e wlan
[    2.973653] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.658066] b43-phy0: Broadcom 4306 WLAN found
[   34.488351] input: b43-phy0 as /devices/virtual/input/input9
[   34.564079] firmware: requesting b43/ucode5.fw
[   34.715838] firmware: requesting b43/pcm5.fw
[   34.721294] firmware: requesting b43/b0g0initvals5.fw
[   34.735259] firmware: requesting b43/b0g0bsinitvals5.fw
[   34.856203] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   35.017242] Registered led device: b43-phy0::tx
[   35.020662] Registered led device: b43-phy0::rx
[   35.021137] Registered led device: b43-phy0::radio
[ 1161.369551] ADDRCONF(NETDEV_UP): wlan0: link is not ready

laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1c:f4:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
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
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:08:fd:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: f2:82:cf:33:a2:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

laptop:~$ lsb_release -d
Description:	Ubuntu 8.10

laptop:~$ uname -mr
2.6.27-9-generic i686

laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         Ignoring unknown interface eth0=eth0.

---

### Post by ieee488 on 2009-01-01
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
worked for me in Ubuntu 8.10 on Dell D400 with Dell Truemobile 1300 with Broadcom 3406 chipset.

---

### Post by jleupen on 2009-01-01
> **ieee488 said:**
> [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
worked for me in Ubuntu 8.10 on Dell D400 with Dell Truemobile 1300 with Broadcom 3406 chipset.

Thanks for the idea.  I tried it and it didn't work, though there are some different messages now.  Here is the log:

laptop:~$ dmesg | grep -e b43 -e wlan
[    3.580795] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.492009] b43-phy0: Broadcom 4306 WLAN found
[   35.527821] input: b43-phy0 as /devices/virtual/input/input9
[   35.600056] firmware: requesting b43/ucode5.fw
[   35.726762] firmware: requesting b43/pcm5.fw
[   35.747010] firmware: requesting b43/b0g0initvals5.fw
[   35.760401] firmware: requesting b43/b0g0bsinitvals5.fw
[   35.934620] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   36.087332] Registered led device: b43-phy0::tx
[   36.087674] Registered led device: b43-phy0::rx
[   36.087888] Registered led device: b43-phy0::radio
[  110.947583] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  302.853406] input: b43-phy0 as /devices/virtual/input/input10
[  303.115933] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  303.235552] Registered led device: b43-phy0::tx
[  303.235922] Registered led device: b43-phy0::rx
[  303.236189] Registered led device: b43-phy0::radio
[  303.259242] wlan0: Trigger new scan to find an IBSS to join
[  306.032215] wlan0: Trigger new scan to find an IBSS to join
[  308.808248] wlan0: Trigger new scan to find an IBSS to join
[  311.584242] wlan0: Trigger new scan to find an IBSS to join
[  312.360314] wlan0: Creating new IBSS network, BSSID 26:58:da:a7:d2:d5
[  313.860088] wlan0: no IPv6 routers present
[  314.146848] wlan0: disassociating by local choice (reason=3)
[  416.586176] wlan0: Selected IBSS BSSID 26:58:da:a7:d2:d5 based on configured SSID
[  417.794057] wlan0: disassociating by local choice (reason=3)

---

### Post by jleupen on 2009-01-01
I've read a lot of other posts about ndiswrapper.   Do I need to do something there?  

laptop:~$ ndiswrapper -l
laptop:~$

---

### Post by ieee488 on 2009-01-01
Looks to me that the card is working. It doesn't see the router.

You might want to try connecting to an open network and verify.

---

### Post by jleupen on 2009-01-01
> **ieee488 said:**
> Looks to me that the card is working. It doesn't see the router.

You might want to try connecting to an open network and verify.

Yeah, I tried that.  I modified my network to broadcast SSID and turned off all security to no avail.  Also, I can normally pick up my neighbor's SSID, which I can't see either.

Any other ideas?   Do I need to do something with ndiswrapper??

---

### Post by ieee488 on 2009-01-01
ndiswrapper is for when the native Linux driver doesn't work which doesn't appear to be the case.

have you re-booted?

---

### Post by jleupen on 2009-01-01
> **ieee488 said:**
> 
have you re-booted?

yes - several times, including just now for good measure.

I noticed that the wireless interface is Transmitting, but not Receiving??

laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:08:fd:0f  
          inet6 addr: fe80::20b:7dff:fe08:fd0f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2763 (2.7 KB)

---

### Post by jleupen on 2009-01-01
I got it!!  Went into the bios and reset the wireless adapter...

Discovered about 7 networks...

Thanks to all and Happy New Year!!

---

