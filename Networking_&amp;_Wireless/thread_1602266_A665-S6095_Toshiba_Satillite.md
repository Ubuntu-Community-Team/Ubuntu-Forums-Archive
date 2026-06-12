---
title: "A665-S6095 Toshiba Satillite"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Bynw on 2010-10-21
I all. I have a Toshiba Satillite A665-S6095 running Ubuntu 32bit version. And I am unable to connect via the built in wi-fi.

When the computer is first booted. I get a message in the GUI that the wireless device is not ready and then after a while it just doesn't find any wireless networks. Even though I know there are networks available and broadcasting their SSID's.

I am running Lucid 10.04

Any help would be great.


Thanks

---

### Post by Bynw on 2010-10-21
Here are the various specs needed for the troubleshooting of my Toshiba Laptop. It looks like a firmware issue, just need to know how to fix it.


07:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 5f)
        Subsystem: Intel Corporation Device 1301
        Flags: bus master, fast devsel, latency 0, IRQ 37
        Memory at d7300000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

bynw@whitestar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:e8:7f:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

bynw@whitestar:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

bynw@whitestar:~$ lsmod | grep iwlagn
iwlagn                107135  0 
iwlcore               106594  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
cfg80211              126528  3 iwlagn,iwlcore,mac80211


bynw@whitestar:~$ dmesg | grep iwlagn
[   19.136120] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   19.136123] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   19.136186] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.136195] iwlagn 0000:07:00.0: setting latency timer to 64
[   19.136225] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[   19.153783] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.153856] iwlagn 0000:07:00.0: irq 37 for MSI/MSI-X
[   19.352653] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   19.472230] iwlagn 0000:07:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   19.472236] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   19.473643] iwlagn 0000:07:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   19.473647] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   19.475118] iwlagn 0000:07:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   19.475122] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   19.476600] iwlagn 0000:07:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   19.476603] iwlagn 0000:07:00.0: Could not read microcode: -2
[   19.477600] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   19.478851] iwlagn 0000:07:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   19.478856] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   19.480264] iwlagn 0000:07:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   19.480270] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   19.481609] iwlagn 0000:07:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   19.481613] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   19.482981] iwlagn 0000:07:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   19.482985] iwlagn 0000:07:00.0: Could not read microcode: -2


bynw@whitestar:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down



bynw@whitestar:~$ sudo lshw -C network
[sudo] password for bynw: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:e8:7f:f3
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:6000(size=256) memory:d3104000-d3104fff(prefetchable) memory:d3100000-d3103fff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 5f
       serial: 00:23:15:72:3b:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:37 memory:d7300000-d7301fff


bynw@whitestar:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS

bynw@whitestar:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS


bynw@whitestar:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by chili555 on 2010-10-21
It is indeed a firmware issue. You can fix it as outlined here: [http://ubuntuforums.org/showpost.php?p=9986425&postcount=12](http://ubuntuforums.org/showpost.php?p=9986425&postcount=12)

---

### Post by Bynw on 2010-10-21
Awesome. That worked. Thanks.

---

### Post by Bynw on 2010-10-21
I spoke too soon. It does indeed enable me to see wireless connections. But I still cannot connect to any. I attempt to connect to my home connection disabling all security on my router. Not even mac filtering. The computer see's my router. But will not connect to it.

---

### Post by chili555 on 2010-10-21
Are there any informative messages?```
dmesg | grep wlan
sudo cat /var/log/syslog | grep wlan
```These are likely to be quite long, so please trim out the repeats and try to only post the messages that seem troublesome.

---

### Post by Bynw on 2010-10-21
Thanks again for the help.

I had to run out and when I returned I rebooted the laptop and it worked fine and connected as it should.


:)

---

### Post by chili555 on 2010-10-21
Glad it's working. Have fun!

---

### Post by Bynw on 2010-10-26
I still seem to be having some issues.

I run 10.04 LTS of Ubuntu with GNOME.

1) The Network Manager Applet vanishes from time to time if the laptop cannot get a connection. 

2) The laptop, after rebooting or coming out of hibernation, will not reconnect to my home router. This home router only uses mac filtering, no wep or other encryption is currently set on it. It takes several attempts (before the network manager vanishes completely) and or several reboots before the laptop does reestablish a wireless connection.

3) This issue repeats itself if I take the laptop to any other wireless access point. With or without a security key. Even just a fully open connection.

Thanks.

---

### Post by Bynw on 2010-10-30
Anyone able to help with the issue that I posted?
Using a laptop where it takes multiple reboots to connect via wireless is very annoying and time consuming. I should be able to connect via wireless on boot up or just after hibernation on a laptop (or any other wireless enabled computer).

I don't know where to look for errors so I can post them and then get a resolution to this issue.

Thank you again.

---

