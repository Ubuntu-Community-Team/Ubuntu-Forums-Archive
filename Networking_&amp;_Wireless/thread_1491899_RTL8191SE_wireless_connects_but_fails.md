---
title: "RTL8191SE wireless connects but fails"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by wtfrak on 2010-05-24
Hello there,

I have a Compaq Presario CQ42-195TX laptop with Ubuntu 10.04 (64-bit) installed on it and fully updated. It has a Realtek RTL8191SE wireless chipset which I am having trouble with - its wired connection is working perfectly.

After starting up, I am able to see and connect to wireless networks. Once connected, the wireless functions correctly for a very brief period (under 10 seconds) in which I am able to access the Internet and so forth. The connection then stops working - although it doesn't get disconnected. When I say it "stops working", I mean I can no longer access the Internet and trying to ping the router gives me a "Destination Host Unreachable" error. If I disconnect from the network I cannot reconnect, nor can I connect to any other network.- though I can still see the list of available networks.

I thought that maybe this was a 64-bit issue, but I tried the Ubuntu 10.04 32-bit live CD and experienced the same problem.

Please note that while this thread is about the RTL8191SE chipset, the RTL819xSE chipsets all use the same driver.

Below are the results of various commands while connected to the network but after the connection has stopped functioning correctly:

**lspci -nn | grep "Realtek"**
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8171] (rev 10)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
```
**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:53:a3:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5824 (5.8 KB)  TX bytes:5824 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:3e:b2:d9  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe3e:b2d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31893 (31.8 KB)  TX bytes:5305 (5.3 KB)
          Interrupt:16 Memory:ffffc90010c70000-ffffc90010c70100 

```
**iwconfig wlan0**
```
wlan0     802.11bg  ESSID:"DM7T"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:01:38:78:81:61   
          Bit Rate=11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=-54 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
**lsmod | grep "8192"**
```
r8192se_pci           486547  0 
```
**dmesg | grep "8192"**
```
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u262144
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
[    8.897073] Linux kernel driver for RTL8192 based WLAN cards
[    8.929548] Adapter(8192SE) is found - DeviceID=8171
[    9.335406] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[    9.463878] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   16.453345] ----------->rtl8192se_check_hw_scan()
[   16.454357] <-----------rtl8192se_check_hw_scan()
[   23.470127] ----------->rtl8192se_check_hw_scan()
[   23.471144] <-----------rtl8192se_check_hw_scan()
[   43.949480] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   50.938296] ----------->rtl8192se_check_hw_scan()
[   50.939308] <-----------rtl8192se_check_hw_scan()
[   50.989305] rtl8192_SetWirelessMode(), wireless_mode:2, bEnableHT = 0
[   50.991852] rtl8192_SetWirelessMode(), wireless_mode:2, bEnableHT = 0
[   73.477036] ----------->rtl8192se_check_hw_scan()
[   73.478049] <-----------rtl8192se_check_hw_scan()
[  113.350580] ----------->rtl8192se_check_hw_scan()
[  113.351592] <-----------rtl8192se_check_hw_scan()
[  173.237630] ----------->rtl8192se_check_hw_scan()
[  173.238641] <-----------rtl8192se_check_hw_scan()
[  253.087032] ----------->rtl8192se_check_hw_scan()
[  253.088044] <-----------rtl8192se_check_hw_scan()
```
**sudo lshw -C network**
```
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:3e:b2:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 ip=192.168.1.104 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:93000000-93003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:53:a3:49
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:2000(size=256) memory:91010000-91010fff(prefetchable) memory:91000000-9100ffff(prefetchable) memory:91020000-9102ffff(prefetchable)
```
**iwlist wlan0 scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:78:81:61
                    ESSID:"DM7T"
                    Protocol:IEEE802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
                    Extra: Last beacon: 6ms ago

```
**lsb_release -d**
```
Description:	Ubuntu 10.04 LTS
```
**uname -mr**
```
2.6.32-21-generic x86_64
```
**sudo /etc/init.d/networking restart**
```
 * Reconfiguring network interfaces...
   ...done.
```

---

### Post by wtfrak on 2010-05-24
I sent an e-mail to Realtek support. They responded (22 minutes later!) and told me to install the latest driver - which they'd attached to the e-mail (I couldn't download it off of their website, so I guess e-mailing them is the way to get it). I did this, and now it works. A bit obvious, really. :oops:

Old version: 0014.0115.2010
New version: 0017.0507.2010

---

### Post by hfmls on 2010-06-08
can u post here the driver?

---

### Post by rampage355 on 2010-06-09
yes is it possible for you to post the drivers?

---

### Post by rampage355 on 2010-06-09
nevermind the new drivers are up on there site now.
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by dineshbabumm on 2010-06-09
I got similar problem. My wifi gets connected but am not able to browse. Not even for the initial 10 seconds as you reported. I will see if updating the driver is the issue. Thanks for the solution.

---

### Post by rampage355 on 2010-06-09
I have not been able to try the new drivers yet. I don't know a ton about linux and I have a custom kernel and the new drivers won't install. Have not a clue how to install drivers on a custom kerenl

---

### Post by rampage355 on 2010-06-10
I was able to install the new drivers but still having the same lock up issue. Not sure if when you install the drivers the firmware gets updated or if that is a different process you need to go through. I email realtek support on how to update the firmware. I will report back when i here from them.

---

### Post by nanonils on 2010-08-07
> **rampage355 said:**
> Not sure if when you install the drivers the firmware gets updated or if that is a different process you need to go through. I email realtek support on how to update the firmware. I will report back when i here from them.

Any luck? After some trying I found your thread and although I have a CQ62 I seem to be affected by the same problem ([http://ubuntuforums.org/showthread.php?p=9689874#post9689874](http://ubuntuforums.org/showthread.php?p=9689874#post9689874)). I have just installed the driver ([http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)) after download but that doesn't change a thing.

Has anyone tried NDISwrapper? I guess the problem could be that we need a 64bit version. I'll try anyways... Faster download here: [http://wikidrivers.com/wiki/Realtek_RTL8191SE/RTL8192SE](http://wikidrivers.com/wiki/Realtek_RTL8191SE/RTL8192SE)

---

### Post by nanonils on 2010-08-08
Just to disseminate information and hopefully avoid similar frustration, this fixed it for me: [http://ubuntuforums.org/showthread.php?p=9693360#post9693360](http://ubuntuforums.org/showthread.php?p=9693360#post9693360)

---

### Post by bgman on 2010-11-19
It appeared as if downloading and installing the latest Realtek driver solved the problem for me.

However, it only took a few minutes longer for the wireless to disconnect.  I'm not sure how to proceed.

---

