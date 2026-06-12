---
title: "Natty Narwhal Wireless Disconnects"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by aschweig on 2011-05-08
Hi!

I recently upgraded from Maverick Meerkat to (classic) Natty Narwhal Ubuntu Linux.  I am running on a Toshiba Satellite A665 (Intel i7).  I use a wireless internet connection.  Under  Maverick, I had no issues.  Under the update, I am finding that occasionally things stop working:  The indicator Applet looks fine, but from a terminal, I find that I am no longer able to ping my own router (less than 10 feet away.)  This behavior occurs after working fine for a few hours.  I am unsure if anything in particular triggers it (I will report back if I determine a particular cause).  I have a few other computers (2 running Windows, and the other Maverick Meerkat) -- and they are unaffected.  

Turning wireless off and on resolves the issue for me on Natty.  Rebooting also works.

Here's some hopefully relevant technical details about my system:

```

~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


```

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
16:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)
16:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 20)
16:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 20)
16:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 20)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)

```

Here's a failed ping attempt:

```

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable
From 192.168.1.6 icmp_seq=6 Destination Host Unreachable
From 192.168.1.6 icmp_seq=7 Destination Host Unreachable

```

After turning off and turning on:

```

wlan0     Link encap:Ethernet  HWaddr 00:26:4d:e3:3d:d2  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:4dff:fee3:3dd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124113920 (124.1 MB)  TX bytes:13066213 (13.0 MB)
          Interrupt:17 Memory:ffffc90012090000-ffffc90012090100 

```

---

### Post by aschweig on 2011-05-08
I just had my wireless connection drop again -- just a few hours since my last post and last disconnect.  Also, I am running natty-proposed, all the latest updates.  (I switched to natty-proposed because of exactly this issue.  Incidentally, I was listening to Rhythmbox for the duration.)

Here's the symptoms:

```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable

```

```

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"XXXXX"  Nickname:"rtl8XXXXXXXX"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:62:72:65:BA   
          Bit Rate=52 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=89/100  Signal level=-54 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

wlan0     Link encap:Ethernet  HWaddr 00:26:4d:e3:3d:d2  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:4dff:fee3:3dd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171901318 (171.9 MB)  TX bytes:18845691 (18.8 MB)
          Interrupt:17 Memory:ffffc90012090000-ffffc90012090100 

```


```

# uname --all
Linux a665 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by aschweig on 2011-05-10
... I am still getting the disconnects.  I have tried to ping the natty box when it is in the "destination host unreachable" state from other computers on the LAN, and have found that it is unpingable.  Today, I was unable to bring the wireless down and up from the tray icon -- it was unresponsive.  

More details:

```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:4e:38:ec
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:7000(size=256) memory:d3104000-d3104fff memory:d3100000-d3103fff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:4d:e3:3d:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:d7300000-d7303fff

```

---

### Post by aschweig on 2011-05-10
Poking around -- looks like others have issues with this driver as well:

powertop causes kernel panic (me too!):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585938]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585938")

more problems:
[http://ubuntuforums.org/showthread.php?t=1635892]("http://ubuntuforums.org/showthread.php?t=1635892")

The second link mentions specifically turning off hardware WEP.  (I do use WEP -- so maybe that is the cause.  I am trying that now.)

---

### Post by williejones on 2011-05-10
> wlan0     802.11bgn  ESSID:"XXXXX"  Nickname:"rtl8XXXXXXXX"           Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:62:72:65:BA              Bit Rate=52 Mb/s              Retry:on   RTS thr:off   Fragment thr:off           **[COLOR=black]Power Management period:0us[/COLOR]**  mode:All packets received           Link Quality=89/100  Signal level=-54 dBm  Noise level=-114 dBm           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:Try changing the power mode to see if it helps:
```
sudo iwconfig wlan0 power off

```Quote and code tags not working

---

### Post by aschweig on 2011-05-11
williejones -- does the "Power Management period:0us" indicate a problem? 

So far, I have not had a disconnect since running the fix for non-hardware WEP:
```

rmmod r8192se_pci
modprobe r8192se_pci hwwep=0
```

Next reboot, I will try 
```
sudo iwconfig wlan0 power off
```
and report back.


Update:  Just now had a disconnect.  Now trying the iwconfig suggestion.

---

### Post by aschweig on 2011-05-13
I see that there is further discussion along these lines at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008)

I am trying putting the config changes in

```

/etc/pm/power.d/wireless

```

---

### Post by aschweig on 2011-05-14
Setting up config files for the changes above did not resolve the issue I am having.

I am thinking about buying a usb wireless card to tide me over until the proper drivers/fixes arrive.

These sound vaguely familiar.

[http://markmail.org/message/rcwur3cf4l3h3fdu](http://markmail.org/message/rcwur3cf4l3h3fdu)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/726058](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/726058)

Thinking about trying out wicd as well -- any experience using this with natty?

Also see: 
[http://ubuntuforums.org/archive/index.php/t-1644053.html](http://ubuntuforums.org/archive/index.php/t-1644053.html)
[http://askubuntu.com/questions/26395/wireless-keeps-disabling-or-stays-disconnected-realtek-rtl8191sevb](http://askubuntu.com/questions/26395/wireless-keeps-disabling-or-stays-disconnected-realtek-rtl8191sevb)

---

### Post by aschweig on 2011-05-15
Trying the driver from RealTek now:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)



(Some inspired by [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all) )

---

### Post by aschweig on 2011-05-16
Looks like compiling and using the RealTek driver has resolved my issues.

---

### Post by ETecoli on 2011-06-16
I'm having similar symptoms and it's driving me up the wall... Wireless is constantly dropping in Natty, in Windows 7 it appears ok...

specs: Lenovo Thinkpad x220

result from lshw -C network:

```
*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:60:d3:67
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:d2500000-d251ffff memory:d252b000-d252bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:c2:01:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-8-generic-pae firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:d2400000-d2403fff
```

iwconfig: 

```
wlan0     IEEE 802.11bgn  ESSID:"nyu"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 9C:4E:20:C8:B8:30   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

from lsmod, the driver I'm using is: rtl8192ce.. I think this is the latest driver.


Any tips for things to try?

---

### Post by aschweig on 2011-06-16
Try the steps in the thread above.  Based on my experience, consider downloading, compiling, and installing the realtek linux drivers (from the realtek website) first.  The readme they supply with the driver is accurate.  Don't forget step 1.

---

### Post by ETecoli on 2011-06-17
> **aschweig said:**
> Try the steps in the thread above.  Based on my experience, consider downloading, compiling, and installing the realtek linux drivers (from the realtek website) first.  The readme they supply with the driver is accurate.  Don't forget step 1.

Do you know any good tutorial on this process?

---

