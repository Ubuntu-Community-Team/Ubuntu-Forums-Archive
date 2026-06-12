---
title: "Acer Veriton 281G Wireless Not Working"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by Jeffbuntu on 2012-06-05
Greetings everyone - I'm hoping that someone can help me with this one because it's driving me crazy.  I recently bought an Acer Veriton 'nettop'.  This box comes loaded with linpus linux.  I have now dual booted it with 12.04.  Unfortunately under Ubuntu the wireless isn't working at all.

I did a search to see if anyone else has come across this issue but didn't see it listed.  Here's my output:

1) Hardware - Acer Veriton 281G

2) Wireless Brand/Chipset

jeff@jeff-Veriton-N281G:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8193
02:00.1 Network controller: Realtek Semiconductor Co., Ltd. Device 8193 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

jeff@jeff-Veriton-N281G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:0c08 Toshiba Corp. 
Bus 001 Device 004: ID 090c:037b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Silicon Motion Camera
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 002 Device 002: ID 0461:0010 Primax Electronics, Ltd 
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

jeff@jeff-Veriton-N281G:~$ lspci -nn | grep Realtek
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8193]
02:00.1 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8193] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

3) Check interrface

jeff@jeff-Veriton-N281G:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d0:27:88:ab:6b:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11776 (11.7 KB)  TX bytes:11776 (11.7 KB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:cd:5d:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 74:de:2b:cd:0c:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


jeff@jeff-Veriton-N281G:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          
wlan0     IEEE 802.11an  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          
eth0      no wireless extensions.

Yep I have tried setting power management to on ;)

4) Check for modules

jeff@jeff-Veriton-N281G:~$ lsmod | grep wifi
rtlwifi                95804  1 rtl8192de
mac80211              436455  1 rtlwifi
cfg80211              178679  2 rtlwifi,mac80211

5) Kernel boot messages

jeff@jeff-Veriton-N281G:~$ dmesg | grep wifi
[   13.723000] rtl8192de: Loading firmware file rtlwifi/rtl8192defw.bin
[   15.994785] rtlwifi: wireless switch is on
[   16.071229] rtlwifi: wireless switch is on

6) Network Configuration

jeff@jeff-Veriton-N281G:~$ sudo lshw -C network
[sudo] password for jeff: 
  *-network:0             
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:de:2b:cd:5d:df
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11an
       resources: irq:18 ioport:d800(size=256) memory:feafc000-feafffff
  *-network:1
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: wlan1
       version: 01
       serial: 74:de:2b:cd:0c:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:d400(size=256) memory:feaf8000-feafbfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:ab:6b:a7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff

7) Scan for networks

jeff@jeff-Veriton-N281G:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan1     No scan results

wlan0     No scan results

eth0      Interface doesn't support scanning.

8 ) Ubuntu Version

jeff@jeff-Veriton-N281G:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS

9) Kernel/architecture (including 32 vs. 64 bit)

jeff@jeff-Veriton-N281G:~$ uname -mr
3.2.0-24-generic-pae i686

10) Restarting the network

jeff@jeff-Veriton-N281G:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 


Thanks in advance for any assistance.

---

### Post by Jeffbuntu on 2012-06-06
Hmmm I did some more poking around.  There appears to be different bin files in /lib/firmware/rtlwifi bewtween the linpus installation and the ubuntu installation.

Could it be that these missing files in Ubuntu are what's causing the wireless to not work?

---

### Post by Jeffbuntu on 2012-06-06
One other thought I just had.  Would it be worth trying out another Distro to see if it is simply a lack of support for the hardware in Ubuntu?  Perhaps something like mepis or suse? 

Anyone?

---

### Post by chili555 on 2012-06-06
> **Jeffbuntu said:**
> One other thought I just had.  Would it be worth trying out another Distro to see if it is simply a lack of support for the hardware in Ubuntu?  Perhaps something like mepis or suse? 

Anyone?The hardware is supported in Ubuntu. What do you make of this?> *-network:0
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 00
serial: [COLOR="Red"]74:de:2b:cd:5d:df[/COLOR]
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11an
resources: irq:18 ioport:d800(size=256) memory:feafc000-feafffff
*-network:1
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0.1
bus info: pci@0000:02:00.1
logical name: wlan1
version: 01
serial: [COLOR="Red"]74:de:2b:cd:0c:0f[/COLOR]
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:19 ioport:d400(size=256) memory:feaf8000-feafbfffDo you really have *two separate wireless cards* there? What do these tell us?```
rfkill list all
dmesg | grep 8192
```Thanks.

EDIT: modinfo says: > description:    Realtek 8192DE 802.11n Dual Mac PCI wirelessI suppose it's a dual-band N device. I love a mystery!

---

### Post by Jeffbuntu on 2012-06-06
This is what I get

jeff@jeff-Veriton-N281G:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

jeff@jeff-Veriton-N281G:~$ dmesg | grep 8192
[    0.228192] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.981160] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   13.487982] rtl8192de 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.488000] rtl8192de 0000:02:00.0: setting latency timer to 64
[   13.503624] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   13.505396] rtl8192de: rtl8192ce: FW Power Save off (module option)
[   13.514868] rtl8192de: Driver for Realtek RTL8192DE WLAN interface
[   13.514879] rtl8192de: Loading firmware file rtlwifi/rtl8192defw.bin
[   15.421513] rtl8192de 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.421530] rtl8192de 0000:02:00.1: setting latency timer to 64
[   15.429521] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   15.438831] rtl8192de: rtl8192ce: FW Power Save off (module option)


What does Unkown CUT! mean? 

thanks

Jeff

---

### Post by chili555 on 2012-06-06
> [ 15.429521] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[ 15.438831] rtl8192de: rtl8192ce: FW Power Save off (module option)


What does Unkown CUT! mean?I don't know and I doubt it's significant. Googling the phrase yields a few hits; none are bugs or complaints about the device not working. Your question will appear as a hit soon! 

Frankly, all your readings look solid. You have a driver; you have firmware; you have two, count them, two wireless interfaces. Does it scan?```
sudo iwlist wlan0 scan
```Any errors, warnings, etc. are significant; please post them.

What exactly doesn't work?> Unfortunately under Ubuntu the wireless isn't working at all.

---

### Post by Jeffbuntu on 2012-06-06
No scan 

jeff@jeff-Veriton-N281G:~$ sudo iwlist wlan0 scan
[sudo] password for jeff: 
wlan0     No scan results

But no error messages either.  My work laptop also running 12:04 connects perfectly.  For some reason at least under Ubuntu I'm just not able to connect to the wireless network.  It's not seeing any access points and I'm surrounded by at least 6.

What makes little sense is that if I reboot to Linpus it connects to my home network immediately.

---

### Post by chili555 on 2012-06-06
> sudo iwlist wlan0 scanAny change with wlan1? What is Network Manager doing all this time?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```I assume you are testing with the ethernet cable *de*tached.

---

### Post by Jeffbuntu on 2012-06-06
Disconnecting cable each time I try something new.

jeff@jeff-Veriton-N281G:/$ sudo iwlist wlan0 scan
[sudo] password for jeff: 
wlan0     No scan results

jeff@jeff-Veriton-N281G:/$ sudo iwlist wlan1 scan
wlan1     No scan results

jeff@jeff-Veriton-N281G:/$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jun  6 10:49:56 jeff-Veriton-N281G NetworkManager[560]: <info>   gateway 192.168.0.1
Jun  6 10:49:56 jeff-Veriton-N281G NetworkManager[560]: <info>   nameserver '192.168.0.1'
Jun  6 10:49:56 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  6 10:49:56 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> DNS: starting dnsmasq...
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) successful, device activated.
Jun  6 10:49:57 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  6 10:50:16 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  6 10:50:16 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  6 10:50:16 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  6 10:50:16 jeff-Veriton-N281G NetworkManager[560]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  6 10:51:59 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  6 10:52:03 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Jun  6 10:52:03 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Jun  6 10:52:03 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2150
Jun  6 10:52:03 jeff-Veriton-N281G NetworkManager[560]: <info> DNS: starting dnsmasq...
Jun  6 10:52:03 jeff-Veriton-N281G NetworkManager[560]: <info> (eth0): writing resolv.conf to /sbin/resolvconf

---

### Post by chili555 on 2012-06-06
Ugh! All we see are entries related to ethernet. Let's dig deeper:```
sudo cat /var/log/syslog | grep wlan | tail -n20
```

---

### Post by Jeffbuntu on 2012-06-06
jeff@jeff-Veriton-N281G:/$ sudo cat /var/log/syslog | grep wlan | tail -n20
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.1/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): using nl80211 for WiFi device control
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192de' ifindex: 3)
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): now managed
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  6 10:26:17 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): bringing up device.
Jun  6 10:26:18 jeff-Veriton-N281G kernel: [   20.529549] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): preparing device.
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  6 10:26:19 jeff-Veriton-N281G kernel: [   20.556318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan1): supplicant interface state: starting -> ready
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 10:26:19 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan1): supplicant interface state: ready -> inactive
Jun  6 10:26:21 jeff-Veriton-N281G NetworkManager[560]: <info> (wlan0): supplicant interface state: ready -> inactive

Am I reading this correctly and the interfaces are bouncing up/down?

---

### Post by chili555 on 2012-06-06
> Am I reading this correctly and the interfaces are bouncing up/down?Yes. I suspect it's because Network manager sees the same thing we mere mortal humans see:> jeff@jeff-Veriton-N281G:/$ sudo iwlist wlan0 scan
[sudo] password for jeff:
wlan0 No scan results

jeff@jeff-Veriton-N281G:/$ sudo iwlist wlan1 scan
wlan1 No scan resultsThat is, NM can't see anyone to connect to, so it doesn't proceed further.

I am very interested in this:> What makes little sense is that if I reboot to Linpus it connects to my home network immediately.Can you please do so and take a look at the corresponding readings over there; especially:```
iwconfig
sudo iwlist wlan0 scan
sudo iwlist wlan1 scan
dmesg | grep 8192
```It would be most helpful if you could copy over those readings here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then post the link here. We don't need the full scan result; just that one or the other or both get scan results. Are they different??

Off to the Big City with Mrs. Chili in a few minutes...

---

### Post by Jeffbuntu on 2012-06-06
> **chili555 said:**
> Yes. I suspect it's because Network manager sees the same thing we mere mortal humans see:That is, NM can't see anyone to connect to, so it doesn't proceed further.

I am very interested in this:Can you please do so and take a look at the corresponding readings over there; especially:```
iwconfig
sudo iwlist wlan0 scan
sudo iwlist wlan1 scan
dmesg | grep 8192
```It would be most helpful if you could copy over those readings here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then post the link here. We don't need the full scan result; just that one or the other or both get scan results. Are they different??

Off to the Big City with Mrs. Chili in a few minutes...

Results will be posted asap - thanks for all your help Chili.  Hope you have a good time in the city.

---

### Post by Jeffbuntu on 2012-06-06
> **chili555 said:**
> Yes. I suspect it's because Network manager sees the same thing we mere mortal humans see:That is, NM can't see anyone to connect to, so it doesn't proceed further.

I am very interested in this:Can you please do so and take a look at the corresponding readings over there; especially:```
iwconfig
sudo iwlist wlan0 scan
sudo iwlist wlan1 scan
dmesg | grep 8192
```It would be most helpful if you could copy over those readings here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then post the link here. We don't need the full scan result; just that one or the other or both get scan results. Are they different??

Off to the Big City with Mrs. Chili in a few minutes...

Results from Linpus
[user@localhost ~]$ lsb_release -d
Description:    allin1X-Lite1.4-110929v1

[user@localhost ~]$ uname -mr
3.0.0-lp.2 i686

[user@localhost ~]$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11an  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: on
          
wlan1     IEEE 802.11bgn  ESSID:"Kalahari"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:70:84:04   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

[user@localhost ~]$ sudo iwlist wlan0 scan
wlan0     No scan results

[user@localhost ~]$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:11:95:70:84:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key: on
                    ESSID:"Kalahari"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013de19bb0a
                    Extra: Last beacon: 11ms ago
                    IE: Unknown: 00084B616C6168617269
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 02 - Address: C4:3D:C7:A8:04:4B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key: on
                    ESSID:"2ghunter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000620433fa7
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 0008326768756E746572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC7A8044B1021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103


[user@localhost ~]$ dmesg | grep 8192
[user@localhost ~]$ 
[user@localhost ~]$ dmesg | grep 8192
[user@localhost ~]$ 

the last command yielded no results.

---

### Post by chili555 on 2012-06-06
> [user@localhost ~]$ dmesg | grep 8192
[user@localhost ~]$
[user@localhost ~]$ dmesg | grep 8192
[user@localhost ~]$Nothing in dmesg about rtl8192de? Nothing?!? What driver is it using, we wonder.```
sudo lshw -C network
```It will report *driver=*whatever. Fascinating!

---

### Post by Jeffbuntu on 2012-06-06
In Linpus

[user@localhost ~]$ sudo lshw -C network
sudo: lshw: command not found
[user@localhost ~]$

---

### Post by chili555 on 2012-06-06
Can you please pastebin these from Linpus?```
dmesg
lsmod
```This just gets more interesting by the minute!

---

### Post by Jeffbuntu on 2012-06-06
> **chili555 said:**
> Can you please pastebin these from Linpus?```
dmesg
lsmod
```This just gets more interesting by the minute!

Not sure what you mean by pastebin

but here's the output

[user@localhost ~]$ dmesg
-storage: usb_stor_clear_halt: result = 0
[ 2613.866853] usb-storage: Attempting to get CSW (2nd try)...
[ 2613.866857] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2613.866972] usb-storage: Status code 0; transferred 13/13
[ 2613.866976] usb-storage: -- transfer complete
[ 2613.866980] usb-storage: Bulk status result = 0
[ 2613.866985] usb-storage: Bulk Status S 0x53425355 T 0x189f R 72 Stat 0x0
[ 2613.866990] usb-storage: -- Result from auto-sense is 0
[ 2613.866994] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2613.867000] usb-storage: Not Ready: Medium not present - tray closed
[ 2613.867020] usb-storage: scsi cmd done, result=0x2
[ 2613.867028] usb-storage: *** thread sleeping.
[ 2613.867068] usb-storage: queuecommand_lck called
[ 2613.867080] usb-storage: *** thread awakened.
[ 2613.867086] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2613.867091] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2613.867111] usb-storage: Bulk Command S 0x43425355 T 0x18a0 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2613.867118] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2613.867230] usb-storage: Status code 0; transferred 31/31
[ 2613.867235] usb-storage: -- transfer complete
[ 2613.867241] usb-storage: Bulk command transfer result=0
[ 2613.867248] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2613.867605] usb-storage: Status code 0; transferred 8/8
[ 2613.867611] usb-storage: -- transfer complete
[ 2613.867617] usb-storage: Bulk data transfer result 0x0
[ 2613.867622] usb-storage: Attempting to get CSW...
[ 2613.867628] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2613.868228] usb-storage: Status code 0; transferred 13/13
[ 2613.868232] usb-storage: -- transfer complete
[ 2613.868236] usb-storage: Bulk status result = 0
[ 2613.868241] usb-storage: Bulk Status S 0x53425355 T 0x18a0 R 0 Stat 0x0
[ 2613.868246] usb-storage: scsi cmd done, result=0x0
[ 2613.868253] usb-storage: *** thread sleeping.
[ 2613.868294] usb-storage: queuecommand_lck called
[ 2613.868307] usb-storage: *** thread awakened.
[ 2613.868312] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2613.868316] usb-storage:  1e 00 00 00 00 00
[ 2613.868328] usb-storage: Bulk Command S 0x43425355 T 0x18a1 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2613.868333] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2613.868474] usb-storage: Status code 0; transferred 31/31
[ 2613.868478] usb-storage: -- transfer complete
[ 2613.868481] usb-storage: Bulk command transfer result=0
[ 2613.868485] usb-storage: Attempting to get CSW...
[ 2613.868489] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2613.869490] usb-storage: Status code 0; transferred 13/13
[ 2613.869497] usb-storage: -- transfer complete
[ 2613.869502] usb-storage: Bulk status result = 0
[ 2613.869509] usb-storage: Bulk Status S 0x53425355 T 0x18a1 R 0 Stat 0x0
[ 2613.869516] usb-storage: scsi cmd done, result=0x0
[ 2613.869525] usb-storage: *** thread sleeping.
[ 2615.845934] usb-storage: queuecommand_lck called
[ 2615.845952] usb-storage: *** thread awakened.
[ 2615.845959] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2615.845965] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2615.845986] usb-storage: Bulk Command S 0x43425355 T 0x18a2 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2615.845993] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.846123] usb-storage: Status code 0; transferred 31/31
[ 2615.846129] usb-storage: -- transfer complete
[ 2615.846134] usb-storage: Bulk command transfer result=0
[ 2615.846141] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2615.846482] usb-storage: Status code 0; transferred 8/8
[ 2615.846488] usb-storage: -- transfer complete
[ 2615.846494] usb-storage: Bulk data transfer result 0x0
[ 2615.846499] usb-storage: Attempting to get CSW...
[ 2615.846505] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.847497] usb-storage: Status code 0; transferred 13/13
[ 2615.847505] usb-storage: -- transfer complete
[ 2615.847510] usb-storage: Bulk status result = 0
[ 2615.847517] usb-storage: Bulk Status S 0x53425355 T 0x18a2 R 0 Stat 0x0
[ 2615.847525] usb-storage: scsi cmd done, result=0x0
[ 2615.847538] usb-storage: *** thread sleeping.
[ 2615.847597] usb-storage: queuecommand_lck called
[ 2615.847612] usb-storage: *** thread awakened.
[ 2615.847619] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2615.847623] usb-storage:  00 00 00 00 00 00
[ 2615.847639] usb-storage: Bulk Command S 0x43425355 T 0x18a3 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2615.847646] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.847823] usb-storage: Status code 0; transferred 31/31
[ 2615.847828] usb-storage: -- transfer complete
[ 2615.847833] usb-storage: Bulk command transfer result=0
[ 2615.847838] usb-storage: Attempting to get CSW...
[ 2615.847843] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.849121] usb-storage: Status code 0; transferred 13/13
[ 2615.849129] usb-storage: -- transfer complete
[ 2615.849135] usb-storage: Bulk status result = 0
[ 2615.849142] usb-storage: Bulk Status S 0x53425355 T 0x18a3 R 0 Stat 0x1
[ 2615.849148] usb-storage: -- transport indicates command failure
[ 2615.849153] usb-storage: Issuing auto-REQUEST_SENSE
[ 2615.849163] usb-storage: Bulk Command S 0x43425355 T 0x18a4 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2615.849170] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.849229] usb-storage: Status code 0; transferred 31/31
[ 2615.849234] usb-storage: -- transfer complete
[ 2615.849240] usb-storage: Bulk command transfer result=0
[ 2615.849246] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2615.850251] usb-storage: Status code -121; transferred 24/96
[ 2615.850258] usb-storage: -- short read transfer
[ 2615.850265] usb-storage: Bulk data transfer result 0x1
[ 2615.850270] usb-storage: Attempting to get CSW...
[ 2615.850277] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.850483] usb-storage: Status code -32; transferred 0/13
[ 2615.850490] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2615.850499] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2615.850607] usb-storage: usb_stor_clear_halt: result = 0
[ 2615.850614] usb-storage: Attempting to get CSW (2nd try)...
[ 2615.850620] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.850729] usb-storage: Status code 0; transferred 13/13
[ 2615.850735] usb-storage: -- transfer complete
[ 2615.850740] usb-storage: Bulk status result = 0
[ 2615.850748] usb-storage: Bulk Status S 0x53425355 T 0x18a4 R 72 Stat 0x0
[ 2615.850755] usb-storage: -- Result from auto-sense is 0
[ 2615.850762] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2615.850771] usb-storage: Not Ready: Medium not present - tray closed
[ 2615.850781] usb-storage: scsi cmd done, result=0x2
[ 2615.850793] usb-storage: *** thread sleeping.
[ 2615.850899] usb-storage: queuecommand_lck called
[ 2615.850916] usb-storage: *** thread awakened.
[ 2615.850922] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2615.850927] usb-storage:  1e 00 00 00 00 00
[ 2615.850942] usb-storage: Bulk Command S 0x43425355 T 0x18a5 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2615.850949] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.851383] usb-storage: Status code 0; transferred 31/31
[ 2615.851389] usb-storage: -- transfer complete
[ 2615.851395] usb-storage: Bulk command transfer result=0
[ 2615.851400] usb-storage: Attempting to get CSW...
[ 2615.851406] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.851737] usb-storage: Status code 0; transferred 13/13
[ 2615.851742] usb-storage: -- transfer complete
[ 2615.851747] usb-storage: Bulk status result = 0
[ 2615.851753] usb-storage: Bulk Status S 0x53425355 T 0x18a5 R 0 Stat 0x0
[ 2615.851761] usb-storage: scsi cmd done, result=0x0
[ 2615.851771] usb-storage: *** thread sleeping.
[ 2615.851872] usb-storage: queuecommand_lck called
[ 2615.851889] usb-storage: *** thread awakened.
[ 2615.851897] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2615.851902] usb-storage:  00 00 00 00 00 00
[ 2615.851918] usb-storage: Bulk Command S 0x43425355 T 0x9e8 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2615.851925] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.852113] usb-storage: Status code 0; transferred 31/31
[ 2615.852120] usb-storage: -- transfer complete
[ 2615.852125] usb-storage: Bulk command transfer result=0
[ 2615.852130] usb-storage: Attempting to get CSW...
[ 2615.852136] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.852230] usb-storage: Status code 0; transferred 13/13
[ 2615.852236] usb-storage: -- transfer complete
[ 2615.852241] usb-storage: Bulk status result = 0
[ 2615.852248] usb-storage: Bulk Status S 0x53425355 T 0x9e8 R 0 Stat 0x0
[ 2615.852255] usb-storage: scsi cmd done, result=0x0
[ 2615.852265] usb-storage: *** thread sleeping.
[ 2615.852338] usb-storage: queuecommand_lck called
[ 2615.852355] usb-storage: *** thread awakened.
[ 2615.852362] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2615.852367] usb-storage:  00 00 00 00 00 00
[ 2615.852383] usb-storage: Bulk Command S 0x43425355 T 0x9e9 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2615.852390] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2615.852482] usb-storage: Status code 0; transferred 31/31
[ 2615.852488] usb-storage: -- transfer complete
[ 2615.852493] usb-storage: Bulk command transfer result=0
[ 2615.852498] usb-storage: Attempting to get CSW...
[ 2615.852504] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2615.852605] usb-storage: Status code 0; transferred 13/13
[ 2615.852611] usb-storage: -- transfer complete
[ 2615.852616] usb-storage: Bulk status result = 0
[ 2615.852622] usb-storage: Bulk Status S 0x53425355 T 0x9e9 R 0 Stat 0x0
[ 2615.852629] usb-storage: scsi cmd done, result=0x0
[ 2615.852639] usb-storage: *** thread sleeping.
[ 2617.845633] usb-storage: queuecommand_lck called
[ 2617.845657] usb-storage: *** thread awakened.
[ 2617.845664] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2617.845668] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2617.845685] usb-storage: Bulk Command S 0x43425355 T 0x18a6 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2617.845691] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.845862] usb-storage: Status code 0; transferred 31/31
[ 2617.845868] usb-storage: -- transfer complete
[ 2617.845873] usb-storage: Bulk command transfer result=0
[ 2617.845880] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2617.846228] usb-storage: Status code 0; transferred 8/8
[ 2617.846235] usb-storage: -- transfer complete
[ 2617.846241] usb-storage: Bulk data transfer result 0x0
[ 2617.846246] usb-storage: Attempting to get CSW...
[ 2617.846252] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.847130] usb-storage: Status code 0; transferred 13/13
[ 2617.847137] usb-storage: -- transfer complete
[ 2617.847142] usb-storage: Bulk status result = 0
[ 2617.847150] usb-storage: Bulk Status S 0x53425355 T 0x18a6 R 0 Stat 0x0
[ 2617.847159] usb-storage: scsi cmd done, result=0x0
[ 2617.847174] usb-storage: *** thread sleeping.
[ 2617.847272] usb-storage: queuecommand_lck called
[ 2617.847291] usb-storage: *** thread awakened.
[ 2617.847299] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2617.847304] usb-storage:  00 00 00 00 00 00
[ 2617.847320] usb-storage: Bulk Command S 0x43425355 T 0x18a7 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2617.847328] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.847488] usb-storage: Status code 0; transferred 31/31
[ 2617.847494] usb-storage: -- transfer complete
[ 2617.847499] usb-storage: Bulk command transfer result=0
[ 2617.847504] usb-storage: Attempting to get CSW...
[ 2617.847509] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.848755] usb-storage: Status code 0; transferred 13/13
[ 2617.848761] usb-storage: -- transfer complete
[ 2617.848765] usb-storage: Bulk status result = 0
[ 2617.848771] usb-storage: Bulk Status S 0x53425355 T 0x18a7 R 0 Stat 0x1
[ 2617.848776] usb-storage: -- transport indicates command failure
[ 2617.848780] usb-storage: Issuing auto-REQUEST_SENSE
[ 2617.848788] usb-storage: Bulk Command S 0x43425355 T 0x18a8 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2617.848794] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.848851] usb-storage: Status code 0; transferred 31/31
[ 2617.848855] usb-storage: -- transfer complete
[ 2617.848858] usb-storage: Bulk command transfer result=0
[ 2617.848864] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2617.850487] usb-storage: Status code -121; transferred 24/96
[ 2617.850491] usb-storage: -- short read transfer
[ 2617.850495] usb-storage: Bulk data transfer result 0x1
[ 2617.850499] usb-storage: Attempting to get CSW...
[ 2617.850503] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.850727] usb-storage: Status code -32; transferred 0/13
[ 2617.850732] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2617.850739] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2617.850852] usb-storage: usb_stor_clear_halt: result = 0
[ 2617.850856] usb-storage: Attempting to get CSW (2nd try)...
[ 2617.850860] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.850975] usb-storage: Status code 0; transferred 13/13
[ 2617.850979] usb-storage: -- transfer complete
[ 2617.850982] usb-storage: Bulk status result = 0
[ 2617.850987] usb-storage: Bulk Status S 0x53425355 T 0x18a8 R 72 Stat 0x0
[ 2617.850992] usb-storage: -- Result from auto-sense is 0
[ 2617.850997] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2617.851018] usb-storage: Not Ready: Medium not present - tray closed
[ 2617.851027] usb-storage: scsi cmd done, result=0x2
[ 2617.851039] usb-storage: *** thread sleeping.
[ 2617.851203] usb-storage: queuecommand_lck called
[ 2617.851220] usb-storage: *** thread awakened.
[ 2617.851227] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2617.851233] usb-storage:  1e 00 00 00 00 00
[ 2617.851253] usb-storage: Bulk Command S 0x43425355 T 0x18a9 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2617.851260] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.851365] usb-storage: Status code 0; transferred 31/31
[ 2617.851370] usb-storage: -- transfer complete
[ 2617.851376] usb-storage: Bulk command transfer result=0
[ 2617.851381] usb-storage: Attempting to get CSW...
[ 2617.851387] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.851999] usb-storage: Status code 0; transferred 13/13
[ 2617.852016] usb-storage: -- transfer complete
[ 2617.852022] usb-storage: Bulk status result = 0
[ 2617.852028] usb-storage: Bulk Status S 0x53425355 T 0x18a9 R 0 Stat 0x0
[ 2617.852034] usb-storage: scsi cmd done, result=0x0
[ 2617.852043] usb-storage: *** thread sleeping.
[ 2617.852140] usb-storage: queuecommand_lck called
[ 2617.852159] usb-storage: *** thread awakened.
[ 2617.852166] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2617.852170] usb-storage:  00 00 00 00 00 00
[ 2617.852186] usb-storage: Bulk Command S 0x43425355 T 0x9ea L 0 F 0 Trg 0 LUN 0 CL 6
[ 2617.852192] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.852373] usb-storage: Status code 0; transferred 31/31
[ 2617.852379] usb-storage: -- transfer complete
[ 2617.852385] usb-storage: Bulk command transfer result=0
[ 2617.852390] usb-storage: Attempting to get CSW...
[ 2617.852396] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.852491] usb-storage: Status code 0; transferred 13/13
[ 2617.852497] usb-storage: -- transfer complete
[ 2617.852502] usb-storage: Bulk status result = 0
[ 2617.852508] usb-storage: Bulk Status S 0x53425355 T 0x9ea R 0 Stat 0x0
[ 2617.852514] usb-storage: scsi cmd done, result=0x0
[ 2617.852523] usb-storage: *** thread sleeping.
[ 2617.852598] usb-storage: queuecommand_lck called
[ 2617.852613] usb-storage: *** thread awakened.
[ 2617.852619] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2617.852624] usb-storage:  00 00 00 00 00 00
[ 2617.852639] usb-storage: Bulk Command S 0x43425355 T 0x9eb L 0 F 0 Trg 0 LUN 0 CL 6
[ 2617.852645] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2617.852731] usb-storage: Status code 0; transferred 31/31
[ 2617.852736] usb-storage: -- transfer complete
[ 2617.852742] usb-storage: Bulk command transfer result=0
[ 2617.852747] usb-storage: Attempting to get CSW...
[ 2617.852753] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2617.852861] usb-storage: Status code 0; transferred 13/13
[ 2617.852867] usb-storage: -- transfer complete
[ 2617.852872] usb-storage: Bulk status result = 0
[ 2617.852879] usb-storage: Bulk Status S 0x53425355 T 0x9eb R 0 Stat 0x0
[ 2617.852886] usb-storage: scsi cmd done, result=0x0
[ 2617.852896] usb-storage: *** thread sleeping.
[ 2619.845073] usb-storage: queuecommand_lck called
[ 2619.845095] usb-storage: *** thread awakened.
[ 2619.845101] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2619.845105] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2619.845122] usb-storage: Bulk Command S 0x43425355 T 0x18aa L 8 F 128 Trg 0 LUN 0 CL 10
[ 2619.845127] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.845235] usb-storage: Status code 0; transferred 31/31
[ 2619.845239] usb-storage: -- transfer complete
[ 2619.845243] usb-storage: Bulk command transfer result=0
[ 2619.845248] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2619.845728] usb-storage: Status code 0; transferred 8/8
[ 2619.845732] usb-storage: -- transfer complete
[ 2619.845735] usb-storage: Bulk data transfer result 0x0
[ 2619.845739] usb-storage: Attempting to get CSW...
[ 2619.845743] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.846733] usb-storage: Status code 0; transferred 13/13
[ 2619.846737] usb-storage: -- transfer complete
[ 2619.846741] usb-storage: Bulk status result = 0
[ 2619.846746] usb-storage: Bulk Status S 0x53425355 T 0x18aa R 0 Stat 0x0
[ 2619.846751] usb-storage: scsi cmd done, result=0x0
[ 2619.846759] usb-storage: *** thread sleeping.
[ 2619.846797] usb-storage: queuecommand_lck called
[ 2619.846809] usb-storage: *** thread awakened.
[ 2619.846814] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2619.846818] usb-storage:  00 00 00 00 00 00
[ 2619.846829] usb-storage: Bulk Command S 0x43425355 T 0x18ab L 0 F 0 Trg 0 LUN 0 CL 6
[ 2619.846834] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.846976] usb-storage: Status code 0; transferred 31/31
[ 2619.846980] usb-storage: -- transfer complete
[ 2619.846984] usb-storage: Bulk command transfer result=0
[ 2619.846988] usb-storage: Attempting to get CSW...
[ 2619.846992] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.847856] usb-storage: Status code 0; transferred 13/13
[ 2619.847861] usb-storage: -- transfer complete
[ 2619.847865] usb-storage: Bulk status result = 0
[ 2619.847870] usb-storage: Bulk Status S 0x53425355 T 0x18ab R 0 Stat 0x1
[ 2619.847874] usb-storage: -- transport indicates command failure
[ 2619.847878] usb-storage: Issuing auto-REQUEST_SENSE
[ 2619.847885] usb-storage: Bulk Command S 0x43425355 T 0x18ac L 96 F 128 Trg 0 LUN 0 CL 6
[ 2619.847890] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.847976] usb-storage: Status code 0; transferred 31/31
[ 2619.847980] usb-storage: -- transfer complete
[ 2619.847983] usb-storage: Bulk command transfer result=0
[ 2619.847989] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2619.849485] usb-storage: Status code -121; transferred 24/96
[ 2619.849489] usb-storage: -- short read transfer
[ 2619.849493] usb-storage: Bulk data transfer result 0x1
[ 2619.849497] usb-storage: Attempting to get CSW...
[ 2619.849501] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.849735] usb-storage: Status code -32; transferred 0/13
[ 2619.849741] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2619.849749] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2619.849857] usb-storage: usb_stor_clear_halt: result = 0
[ 2619.849864] usb-storage: Attempting to get CSW (2nd try)...
[ 2619.849870] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.849980] usb-storage: Status code 0; transferred 13/13
[ 2619.849986] usb-storage: -- transfer complete
[ 2619.849991] usb-storage: Bulk status result = 0
[ 2619.849999] usb-storage: Bulk Status S 0x53425355 T 0x18ac R 72 Stat 0x0
[ 2619.850021] usb-storage: -- Result from auto-sense is 0
[ 2619.850029] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2619.850038] usb-storage: Not Ready: Medium not present - tray closed
[ 2619.850047] usb-storage: scsi cmd done, result=0x2
[ 2619.850059] usb-storage: *** thread sleeping.
[ 2619.850134] usb-storage: queuecommand_lck called
[ 2619.850147] usb-storage: *** thread awakened.
[ 2619.850153] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2619.850158] usb-storage:  1e 00 00 00 00 00
[ 2619.850173] usb-storage: Bulk Command S 0x43425355 T 0x18ad L 0 F 0 Trg 0 LUN 0 CL 6
[ 2619.850180] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.850232] usb-storage: Status code 0; transferred 31/31
[ 2619.850237] usb-storage: -- transfer complete
[ 2619.850242] usb-storage: Bulk command transfer result=0
[ 2619.850246] usb-storage: Attempting to get CSW...
[ 2619.850252] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.851244] usb-storage: Status code 0; transferred 13/13
[ 2619.851250] usb-storage: -- transfer complete
[ 2619.851256] usb-storage: Bulk status result = 0
[ 2619.851266] usb-storage: Bulk Status S 0x53425355 T 0x18ad R 0 Stat 0x0
[ 2619.851274] usb-storage: scsi cmd done, result=0x0
[ 2619.851284] usb-storage: *** thread sleeping.
[ 2619.851381] usb-storage: queuecommand_lck called
[ 2619.851397] usb-storage: *** thread awakened.
[ 2619.851404] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2619.851409] usb-storage:  00 00 00 00 00 00
[ 2619.851425] usb-storage: Bulk Command S 0x43425355 T 0x9ec L 0 F 0 Trg 0 LUN 0 CL 6
[ 2619.851432] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.851611] usb-storage: Status code 0; transferred 31/31
[ 2619.851616] usb-storage: -- transfer complete
[ 2619.851620] usb-storage: Bulk command transfer result=0
[ 2619.851624] usb-storage: Attempting to get CSW...
[ 2619.851628] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.851731] usb-storage: Status code 0; transferred 13/13
[ 2619.851735] usb-storage: -- transfer complete
[ 2619.851739] usb-storage: Bulk status result = 0
[ 2619.851744] usb-storage: Bulk Status S 0x53425355 T 0x9ec R 0 Stat 0x0
[ 2619.851749] usb-storage: scsi cmd done, result=0x0
[ 2619.851756] usb-storage: *** thread sleeping.
[ 2619.851829] usb-storage: queuecommand_lck called
[ 2619.851842] usb-storage: *** thread awakened.
[ 2619.851849] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2619.851854] usb-storage:  00 00 00 00 00 00
[ 2619.851871] usb-storage: Bulk Command S 0x43425355 T 0x9ed L 0 F 0 Trg 0 LUN 0 CL 6
[ 2619.851878] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2619.851978] usb-storage: Status code 0; transferred 31/31
[ 2619.851984] usb-storage: -- transfer complete
[ 2619.851989] usb-storage: Bulk command transfer result=0
[ 2619.851993] usb-storage: Attempting to get CSW...
[ 2619.851999] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2619.852109] usb-storage: Status code 0; transferred 13/13
[ 2619.852115] usb-storage: -- transfer complete
[ 2619.852120] usb-storage: Bulk status result = 0
[ 2619.852127] usb-storage: Bulk Status S 0x53425355 T 0x9ed R 0 Stat 0x0
[ 2619.852134] usb-storage: scsi cmd done, result=0x0
[ 2619.852143] usb-storage: *** thread sleeping.
[ 2621.845127] usb-storage: queuecommand_lck called
[ 2621.845147] usb-storage: *** thread awakened.
[ 2621.845155] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2621.845161] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2621.845184] usb-storage: Bulk Command S 0x43425355 T 0x18ae L 8 F 128 Trg 0 LUN 0 CL 10
[ 2621.845192] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.845363] usb-storage: Status code 0; transferred 31/31
[ 2621.845369] usb-storage: -- transfer complete
[ 2621.845374] usb-storage: Bulk command transfer result=0
[ 2621.845382] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2621.845610] usb-storage: Status code 0; transferred 8/8
[ 2621.845616] usb-storage: -- transfer complete
[ 2621.845621] usb-storage: Bulk data transfer result 0x0
[ 2621.845627] usb-storage: Attempting to get CSW...
[ 2621.845633] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.846645] usb-storage: Status code 0; transferred 13/13
[ 2621.846654] usb-storage: -- transfer complete
[ 2621.846660] usb-storage: Bulk status result = 0
[ 2621.846667] usb-storage: Bulk Status S 0x53425355 T 0x18ae R 0 Stat 0x0
[ 2621.846678] usb-storage: scsi cmd done, result=0x0
[ 2621.846696] usb-storage: *** thread sleeping.
[ 2621.846800] usb-storage: queuecommand_lck called
[ 2621.846815] usb-storage: *** thread awakened.
[ 2621.846822] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2621.846826] usb-storage:  00 00 00 00 00 00
[ 2621.846842] usb-storage: Bulk Command S 0x43425355 T 0x18af L 0 F 0 Trg 0 LUN 0 CL 6
[ 2621.846848] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.846996] usb-storage: Status code 0; transferred 31/31
[ 2621.847031] usb-storage: -- transfer complete
[ 2621.847037] usb-storage: Bulk command transfer result=0
[ 2621.847042] usb-storage: Attempting to get CSW...
[ 2621.847049] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.848135] usb-storage: Status code 0; transferred 13/13
[ 2621.848143] usb-storage: -- transfer complete
[ 2621.848149] usb-storage: Bulk status result = 0
[ 2621.848156] usb-storage: Bulk Status S 0x53425355 T 0x18af R 0 Stat 0x1
[ 2621.848162] usb-storage: -- transport indicates command failure
[ 2621.848168] usb-storage: Issuing auto-REQUEST_SENSE
[ 2621.848178] usb-storage: Bulk Command S 0x43425355 T 0x18b0 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2621.848186] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.848232] usb-storage: Status code 0; transferred 31/31
[ 2621.848238] usb-storage: -- transfer complete
[ 2621.848242] usb-storage: Bulk command transfer result=0
[ 2621.848249] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2621.849387] usb-storage: Status code -121; transferred 24/96
[ 2621.849395] usb-storage: -- short read transfer
[ 2621.849401] usb-storage: Bulk data transfer result 0x1
[ 2621.849406] usb-storage: Attempting to get CSW...
[ 2621.849412] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.849609] usb-storage: Status code -32; transferred 0/13
[ 2621.849614] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2621.849621] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2621.849729] usb-storage: usb_stor_clear_halt: result = 0
[ 2621.849733] usb-storage: Attempting to get CSW (2nd try)...
[ 2621.849738] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.849852] usb-storage: Status code 0; transferred 13/13
[ 2621.849856] usb-storage: -- transfer complete
[ 2621.849860] usb-storage: Bulk status result = 0
[ 2621.849865] usb-storage: Bulk Status S 0x53425355 T 0x18b0 R 72 Stat 0x0
[ 2621.849871] usb-storage: -- Result from auto-sense is 0
[ 2621.849876] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2621.849885] usb-storage: Not Ready: Medium not present - tray closed
[ 2621.849894] usb-storage: scsi cmd done, result=0x2
[ 2621.849903] usb-storage: *** thread sleeping.
[ 2621.849992] usb-storage: queuecommand_lck called
[ 2621.850012] usb-storage: *** thread awakened.
[ 2621.850020] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2621.850024] usb-storage:  1e 00 00 00 00 00
[ 2621.850040] usb-storage: Bulk Command S 0x43425355 T 0x18b1 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2621.850046] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.850105] usb-storage: Status code 0; transferred 31/31
[ 2621.850110] usb-storage: -- transfer complete
[ 2621.850115] usb-storage: Bulk command transfer result=0
[ 2621.850119] usb-storage: Attempting to get CSW...
[ 2621.850125] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.850611] usb-storage: Status code 0; transferred 13/13
[ 2621.850620] usb-storage: -- transfer complete
[ 2621.850626] usb-storage: Bulk status result = 0
[ 2621.850633] usb-storage: Bulk Status S 0x53425355 T 0x18b1 R 0 Stat 0x0
[ 2621.850641] usb-storage: scsi cmd done, result=0x0
[ 2621.850651] usb-storage: *** thread sleeping.
[ 2621.850759] usb-storage: queuecommand_lck called
[ 2621.850778] usb-storage: *** thread awakened.
[ 2621.850786] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2621.850794] usb-storage:  00 00 00 00 00 00
[ 2621.850811] usb-storage: Bulk Command S 0x43425355 T 0x9ee L 0 F 0 Trg 0 LUN 0 CL 6
[ 2621.850819] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.850988] usb-storage: Status code 0; transferred 31/31
[ 2621.850994] usb-storage: -- transfer complete
[ 2621.850998] usb-storage: Bulk command transfer result=0
[ 2621.851019] usb-storage: Attempting to get CSW...
[ 2621.851025] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.851109] usb-storage: Status code 0; transferred 13/13
[ 2621.851114] usb-storage: -- transfer complete
[ 2621.851119] usb-storage: Bulk status result = 0
[ 2621.851126] usb-storage: Bulk Status S 0x53425355 T 0x9ee R 0 Stat 0x0
[ 2621.851133] usb-storage: scsi cmd done, result=0x0
[ 2621.851144] usb-storage: *** thread sleeping.
[ 2621.851604] usb-storage: queuecommand_lck called
[ 2621.851624] usb-storage: *** thread awakened.
[ 2621.851630] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2621.851635] usb-storage:  00 00 00 00 00 00
[ 2621.851651] usb-storage: Bulk Command S 0x43425355 T 0x9ef L 0 F 0 Trg 0 LUN 0 CL 6
[ 2621.851658] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2621.851752] usb-storage: Status code 0; transferred 31/31
[ 2621.851757] usb-storage: -- transfer complete
[ 2621.851762] usb-storage: Bulk command transfer result=0
[ 2621.851767] usb-storage: Attempting to get CSW...
[ 2621.851772] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2621.851856] usb-storage: Status code 0; transferred 13/13
[ 2621.851865] usb-storage: -- transfer complete
[ 2621.851870] usb-storage: Bulk status result = 0
[ 2621.851877] usb-storage: Bulk Status S 0x53425355 T 0x9ef R 0 Stat 0x0
[ 2621.851884] usb-storage: scsi cmd done, result=0x0
[ 2621.851896] usb-storage: *** thread sleeping.
[ 2623.845079] usb-storage: queuecommand_lck called
[ 2623.845101] usb-storage: *** thread awakened.
[ 2623.845107] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2623.845111] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2623.845128] usb-storage: Bulk Command S 0x43425355 T 0x18b2 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2623.845133] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.845237] usb-storage: Status code 0; transferred 31/31
[ 2623.845241] usb-storage: -- transfer complete
[ 2623.845245] usb-storage: Bulk command transfer result=0
[ 2623.845250] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2623.845605] usb-storage: Status code 0; transferred 8/8
[ 2623.845609] usb-storage: -- transfer complete
[ 2623.845613] usb-storage: Bulk data transfer result 0x0
[ 2623.845616] usb-storage: Attempting to get CSW...
[ 2623.845620] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.846240] usb-storage: Status code 0; transferred 13/13
[ 2623.846249] usb-storage: -- transfer complete
[ 2623.846255] usb-storage: Bulk status result = 0
[ 2623.846262] usb-storage: Bulk Status S 0x53425355 T 0x18b2 R 0 Stat 0x0
[ 2623.846269] usb-storage: scsi cmd done, result=0x0
[ 2623.846280] usb-storage: *** thread sleeping.
[ 2623.846324] usb-storage: queuecommand_lck called
[ 2623.846349] usb-storage: *** thread awakened.
[ 2623.846356] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2623.846361] usb-storage:  00 00 00 00 00 00
[ 2623.846377] usb-storage: Bulk Command S 0x43425355 T 0x18b3 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2623.846385] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.846484] usb-storage: Status code 0; transferred 31/31
[ 2623.846489] usb-storage: -- transfer complete
[ 2623.846494] usb-storage: Bulk command transfer result=0
[ 2623.846498] usb-storage: Attempting to get CSW...
[ 2623.846504] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.847484] usb-storage: Status code 0; transferred 13/13
[ 2623.847489] usb-storage: -- transfer complete
[ 2623.847493] usb-storage: Bulk status result = 0
[ 2623.847498] usb-storage: Bulk Status S 0x53425355 T 0x18b3 R 0 Stat 0x1
[ 2623.847502] usb-storage: -- transport indicates command failure
[ 2623.847506] usb-storage: Issuing auto-REQUEST_SENSE
[ 2623.847513] usb-storage: Bulk Command S 0x43425355 T 0x18b4 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2623.847518] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.847603] usb-storage: Status code 0; transferred 31/31
[ 2623.847607] usb-storage: -- transfer complete
[ 2623.847611] usb-storage: Bulk command transfer result=0
[ 2623.847616] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2623.849247] usb-storage: Status code -121; transferred 24/96
[ 2623.849252] usb-storage: -- short read transfer
[ 2623.849256] usb-storage: Bulk data transfer result 0x1
[ 2623.849260] usb-storage: Attempting to get CSW...
[ 2623.849264] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.849480] usb-storage: Status code -32; transferred 0/13
[ 2623.849485] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2623.849491] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2623.849604] usb-storage: usb_stor_clear_halt: result = 0
[ 2623.849608] usb-storage: Attempting to get CSW (2nd try)...
[ 2623.849613] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.849728] usb-storage: Status code 0; transferred 13/13
[ 2623.849732] usb-storage: -- transfer complete
[ 2623.849735] usb-storage: Bulk status result = 0
[ 2623.849741] usb-storage: Bulk Status S 0x53425355 T 0x18b4 R 72 Stat 0x0
[ 2623.849746] usb-storage: -- Result from auto-sense is 0
[ 2623.849751] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2623.849758] usb-storage: Not Ready: Medium not present - tray closed
[ 2623.849764] usb-storage: scsi cmd done, result=0x2
[ 2623.849773] usb-storage: *** thread sleeping.
[ 2623.849842] usb-storage: queuecommand_lck called
[ 2623.849856] usb-storage: *** thread awakened.
[ 2623.849861] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2623.849865] usb-storage:  1e 00 00 00 00 00
[ 2623.849884] usb-storage: Bulk Command S 0x43425355 T 0x18b5 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2623.849891] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.849988] usb-storage: Status code 0; transferred 31/31
[ 2623.849993] usb-storage: -- transfer complete
[ 2623.849998] usb-storage: Bulk command transfer result=0
[ 2623.850020] usb-storage: Attempting to get CSW...
[ 2623.850026] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.850621] usb-storage: Status code 0; transferred 13/13
[ 2623.850627] usb-storage: -- transfer complete
[ 2623.850633] usb-storage: Bulk status result = 0
[ 2623.850640] usb-storage: Bulk Status S 0x53425355 T 0x18b5 R 0 Stat 0x0
[ 2623.850647] usb-storage: scsi cmd done, result=0x0
[ 2623.850659] usb-storage: *** thread sleeping.
[ 2623.850763] usb-storage: queuecommand_lck called
[ 2623.850780] usb-storage: *** thread awakened.
[ 2623.850787] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2623.850792] usb-storage:  00 00 00 00 00 00
[ 2623.850809] usb-storage: Bulk Command S 0x43425355 T 0x9f0 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2623.850816] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.851016] usb-storage: Status code 0; transferred 31/31
[ 2623.851025] usb-storage: -- transfer complete
[ 2623.851031] usb-storage: Bulk command transfer result=0
[ 2623.851036] usb-storage: Attempting to get CSW...
[ 2623.851042] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.851112] usb-storage: Status code 0; transferred 13/13
[ 2623.851117] usb-storage: -- transfer complete
[ 2623.851122] usb-storage: Bulk status result = 0
[ 2623.851128] usb-storage: Bulk Status S 0x53425355 T 0x9f0 R 0 Stat 0x0
[ 2623.851135] usb-storage: scsi cmd done, result=0x0
[ 2623.851144] usb-storage: *** thread sleeping.
[ 2623.851212] usb-storage: queuecommand_lck called
[ 2623.851224] usb-storage: *** thread awakened.
[ 2623.851230] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2623.851235] usb-storage:  00 00 00 00 00 00
[ 2623.851250] usb-storage: Bulk Command S 0x43425355 T 0x9f1 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2623.851256] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2623.851358] usb-storage: Status code 0; transferred 31/31
[ 2623.851364] usb-storage: -- transfer complete
[ 2623.851373] usb-storage: Bulk command transfer result=0
[ 2623.851379] usb-storage: Attempting to get CSW...
[ 2623.851385] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2623.851481] usb-storage: Status code 0; transferred 13/13
[ 2623.851490] usb-storage: -- transfer complete
[ 2623.851495] usb-storage: Bulk status result = 0
[ 2623.851502] usb-storage: Bulk Status S 0x53425355 T 0x9f1 R 0 Stat 0x0
[ 2623.851509] usb-storage: scsi cmd done, result=0x0
[ 2623.851518] usb-storage: *** thread sleeping.
[ 2625.845671] usb-storage: queuecommand_lck called
[ 2625.845692] usb-storage: *** thread awakened.
[ 2625.845698] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2625.845702] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2625.845719] usb-storage: Bulk Command S 0x43425355 T 0x18b6 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2625.845725] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.845863] usb-storage: Status code 0; transferred 31/31
[ 2625.845867] usb-storage: -- transfer complete
[ 2625.845871] usb-storage: Bulk command transfer result=0
[ 2625.845876] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2625.846361] usb-storage: Status code 0; transferred 8/8
[ 2625.846371] usb-storage: -- transfer complete
[ 2625.846376] usb-storage: Bulk data transfer result 0x0
[ 2625.846380] usb-storage: Attempting to get CSW...
[ 2625.846386] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.846734] usb-storage: Status code 0; transferred 13/13
[ 2625.846738] usb-storage: -- transfer complete
[ 2625.846742] usb-storage: Bulk status result = 0
[ 2625.846747] usb-storage: Bulk Status S 0x53425355 T 0x18b6 R 0 Stat 0x0
[ 2625.846752] usb-storage: scsi cmd done, result=0x0
[ 2625.846760] usb-storage: *** thread sleeping.
[ 2625.846797] usb-storage: queuecommand_lck called
[ 2625.846809] usb-storage: *** thread awakened.
[ 2625.846814] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2625.846817] usb-storage:  00 00 00 00 00 00
[ 2625.846829] usb-storage: Bulk Command S 0x43425355 T 0x18b7 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2625.846834] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.846980] usb-storage: Status code 0; transferred 31/31
[ 2625.846984] usb-storage: -- transfer complete
[ 2625.846987] usb-storage: Bulk command transfer result=0
[ 2625.846991] usb-storage: Attempting to get CSW...
[ 2625.846995] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.847871] usb-storage: Status code 0; transferred 13/13
[ 2625.847876] usb-storage: -- transfer complete
[ 2625.847880] usb-storage: Bulk status result = 0
[ 2625.847885] usb-storage: Bulk Status S 0x53425355 T 0x18b7 R 0 Stat 0x1
[ 2625.847890] usb-storage: -- transport indicates command failure
[ 2625.847894] usb-storage: Issuing auto-REQUEST_SENSE
[ 2625.847901] usb-storage: Bulk Command S 0x43425355 T 0x18b8 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2625.847906] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.847980] usb-storage: Status code 0; transferred 31/31
[ 2625.847984] usb-storage: -- transfer complete
[ 2625.847987] usb-storage: Bulk command transfer result=0
[ 2625.847992] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2625.849115] usb-storage: Status code -121; transferred 24/96
[ 2625.849119] usb-storage: -- short read transfer
[ 2625.849123] usb-storage: Bulk data transfer result 0x1
[ 2625.849127] usb-storage: Attempting to get CSW...
[ 2625.849132] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.849357] usb-storage: Status code -32; transferred 0/13
[ 2625.849361] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2625.849368] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2625.849480] usb-storage: usb_stor_clear_halt: result = 0
[ 2625.849484] usb-storage: Attempting to get CSW (2nd try)...
[ 2625.849489] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.849604] usb-storage: Status code 0; transferred 13/13
[ 2625.849608] usb-storage: -- transfer complete
[ 2625.849612] usb-storage: Bulk status result = 0
[ 2625.849617] usb-storage: Bulk Status S 0x53425355 T 0x18b8 R 72 Stat 0x0
[ 2625.849622] usb-storage: -- Result from auto-sense is 0
[ 2625.849627] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2625.849634] usb-storage: Not Ready: Medium not present - tray closed
[ 2625.849640] usb-storage: scsi cmd done, result=0x2
[ 2625.849649] usb-storage: *** thread sleeping.
[ 2625.849715] usb-storage: queuecommand_lck called
[ 2625.849731] usb-storage: *** thread awakened.
[ 2625.849736] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2625.849739] usb-storage:  1e 00 00 00 00 00
[ 2625.849751] usb-storage: Bulk Command S 0x43425355 T 0x18b9 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2625.849756] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.849856] usb-storage: Status code 0; transferred 31/31
[ 2625.849860] usb-storage: -- transfer complete
[ 2625.849864] usb-storage: Bulk command transfer result=0
[ 2625.849867] usb-storage: Attempting to get CSW...
[ 2625.849871] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.850489] usb-storage: Status code 0; transferred 13/13
[ 2625.850495] usb-storage: -- transfer complete
[ 2625.850499] usb-storage: Bulk status result = 0
[ 2625.850505] usb-storage: Bulk Status S 0x53425355 T 0x18b9 R 0 Stat 0x0
[ 2625.850509] usb-storage: scsi cmd done, result=0x0
[ 2625.850516] usb-storage: *** thread sleeping.
[ 2625.850601] usb-storage: queuecommand_lck called
[ 2625.850617] usb-storage: *** thread awakened.
[ 2625.850624] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2625.850629] usb-storage:  00 00 00 00 00 00
[ 2625.850645] usb-storage: Bulk Command S 0x43425355 T 0x9f2 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2625.850652] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.850740] usb-storage: Status code 0; transferred 31/31
[ 2625.850746] usb-storage: -- transfer complete
[ 2625.850751] usb-storage: Bulk command transfer result=0
[ 2625.850757] usb-storage: Attempting to get CSW...
[ 2625.850763] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.850866] usb-storage: Status code 0; transferred 13/13
[ 2625.850872] usb-storage: -- transfer complete
[ 2625.850877] usb-storage: Bulk status result = 0
[ 2625.850884] usb-storage: Bulk Status S 0x53425355 T 0x9f2 R 0 Stat 0x0
[ 2625.850891] usb-storage: scsi cmd done, result=0x0
[ 2625.850901] usb-storage: *** thread sleeping.
[ 2625.850971] usb-storage: queuecommand_lck called
[ 2625.850984] usb-storage: *** thread awakened.
[ 2625.850989] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2625.850994] usb-storage:  00 00 00 00 00 00
[ 2625.851024] usb-storage: Bulk Command S 0x43425355 T 0x9f3 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2625.851030] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.851122] usb-storage: Status code 0; transferred 31/31
[ 2625.851127] usb-storage: -- transfer complete
[ 2625.851131] usb-storage: Bulk command transfer result=0
[ 2625.851136] usb-storage: Attempting to get CSW...
[ 2625.851142] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.851231] usb-storage: Status code 0; transferred 13/13
[ 2625.851240] usb-storage: -- transfer complete
[ 2625.851245] usb-storage: Bulk status result = 0
[ 2625.851252] usb-storage: Bulk Status S 0x53425355 T 0x9f3 R 0 Stat 0x0
[ 2625.851259] usb-storage: scsi cmd done, result=0x0
[ 2625.851269] usb-storage: *** thread sleeping.
[ 2625.859082] usb-storage: queuecommand_lck called
[ 2625.859104] usb-storage: *** thread awakened.
[ 2625.859110] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2625.859114] usb-storage:  00 00 00 00 00 00
[ 2625.859126] usb-storage: Bulk Command S 0x43425355 T 0x9f4 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2625.859132] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2625.859236] usb-storage: Status code 0; transferred 31/31
[ 2625.859240] usb-storage: -- transfer complete
[ 2625.859244] usb-storage: Bulk command transfer result=0
[ 2625.859248] usb-storage: Attempting to get CSW...
[ 2625.859252] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2625.859358] usb-storage: Status code 0; transferred 13/13
[ 2625.859362] usb-storage: -- transfer complete
[ 2625.859366] usb-storage: Bulk status result = 0
[ 2625.859371] usb-storage: Bulk Status S 0x53425355 T 0x9f4 R 0 Stat 0x0
[ 2625.859376] usb-storage: scsi cmd done, result=0x0
[ 2625.859384] usb-storage: *** thread sleeping.
[ 2627.845424] usb-storage: queuecommand_lck called
[ 2627.845447] usb-storage: *** thread awakened.
[ 2627.845453] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2627.845457] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2627.845474] usb-storage: Bulk Command S 0x43425355 T 0x18ba L 8 F 128 Trg 0 LUN 0 CL 10
[ 2627.845479] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.845615] usb-storage: Status code 0; transferred 31/31
[ 2627.845619] usb-storage: -- transfer complete
[ 2627.845623] usb-storage: Bulk command transfer result=0
[ 2627.845628] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2627.845982] usb-storage: Status code 0; transferred 8/8
[ 2627.845986] usb-storage: -- transfer complete
[ 2627.845990] usb-storage: Bulk data transfer result 0x0
[ 2627.845994] usb-storage: Attempting to get CSW...
[ 2627.845998] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.846370] usb-storage: Status code 0; transferred 13/13
[ 2627.846376] usb-storage: -- transfer complete
[ 2627.846381] usb-storage: Bulk status result = 0
[ 2627.846388] usb-storage: Bulk Status S 0x53425355 T 0x18ba R 0 Stat 0x0
[ 2627.846395] usb-storage: scsi cmd done, result=0x0
[ 2627.846407] usb-storage: *** thread sleeping.
[ 2627.846467] usb-storage: queuecommand_lck called
[ 2627.846482] usb-storage: *** thread awakened.
[ 2627.846488] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2627.846493] usb-storage:  00 00 00 00 00 00
[ 2627.846508] usb-storage: Bulk Command S 0x43425355 T 0x18bb L 0 F 0 Trg 0 LUN 0 CL 6
[ 2627.846515] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.846620] usb-storage: Status code 0; transferred 31/31
[ 2627.846625] usb-storage: -- transfer complete
[ 2627.846631] usb-storage: Bulk command transfer result=0
[ 2627.846636] usb-storage: Attempting to get CSW...
[ 2627.846641] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.847758] usb-storage: Status code 0; transferred 13/13
[ 2627.847765] usb-storage: -- transfer complete
[ 2627.847770] usb-storage: Bulk status result = 0
[ 2627.847777] usb-storage: Bulk Status S 0x53425355 T 0x18bb R 0 Stat 0x1
[ 2627.847784] usb-storage: -- transport indicates command failure
[ 2627.847790] usb-storage: Issuing auto-REQUEST_SENSE
[ 2627.847800] usb-storage: Bulk Command S 0x43425355 T 0x18bc L 96 F 128 Trg 0 LUN 0 CL 6
[ 2627.847808] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.847859] usb-storage: Status code 0; transferred 31/31
[ 2627.847863] usb-storage: -- transfer complete
[ 2627.847867] usb-storage: Bulk command transfer result=0
[ 2627.847872] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2627.849366] usb-storage: Status code -121; transferred 24/96
[ 2627.849371] usb-storage: -- short read transfer
[ 2627.849375] usb-storage: Bulk data transfer result 0x1
[ 2627.849378] usb-storage: Attempting to get CSW...
[ 2627.849383] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.849608] usb-storage: Status code -32; transferred 0/13
[ 2627.849612] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2627.849618] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2627.849732] usb-storage: usb_stor_clear_halt: result = 0
[ 2627.849736] usb-storage: Attempting to get CSW (2nd try)...
[ 2627.849740] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.849855] usb-storage: Status code 0; transferred 13/13
[ 2627.849859] usb-storage: -- transfer complete
[ 2627.849863] usb-storage: Bulk status result = 0
[ 2627.849868] usb-storage: Bulk Status S 0x53425355 T 0x18bc R 72 Stat 0x0
[ 2627.849873] usb-storage: -- Result from auto-sense is 0
[ 2627.849877] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2627.849884] usb-storage: Not Ready: Medium not present - tray closed
[ 2627.849891] usb-storage: scsi cmd done, result=0x2
[ 2627.849900] usb-storage: *** thread sleeping.
[ 2627.849969] usb-storage: queuecommand_lck called
[ 2627.849984] usb-storage: *** thread awakened.
[ 2627.849989] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2627.849992] usb-storage:  1e 00 00 00 00 00
[ 2627.850019] usb-storage: Bulk Command S 0x43425355 T 0x18bd L 0 F 0 Trg 0 LUN 0 CL 6
[ 2627.850026] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.850109] usb-storage: Status code 0; transferred 31/31
[ 2627.850114] usb-storage: -- transfer complete
[ 2627.850119] usb-storage: Bulk command transfer result=0
[ 2627.850123] usb-storage: Attempting to get CSW...
[ 2627.850129] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.850609] usb-storage: Status code 0; transferred 13/13
[ 2627.850618] usb-storage: -- transfer complete
[ 2627.850624] usb-storage: Bulk status result = 0
[ 2627.850630] usb-storage: Bulk Status S 0x53425355 T 0x18bd R 0 Stat 0x0
[ 2627.850638] usb-storage: scsi cmd done, result=0x0
[ 2627.850648] usb-storage: *** thread sleeping.
[ 2627.850754] usb-storage: queuecommand_lck called
[ 2627.850771] usb-storage: *** thread awakened.
[ 2627.850778] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2627.850783] usb-storage:  00 00 00 00 00 00
[ 2627.850803] usb-storage: Bulk Command S 0x43425355 T 0x9f5 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2627.850811] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.850986] usb-storage: Status code 0; transferred 31/31
[ 2627.850995] usb-storage: -- transfer complete
[ 2627.851000] usb-storage: Bulk command transfer result=0
[ 2627.851013] usb-storage: Attempting to get CSW...
[ 2627.851020] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.851111] usb-storage: Status code 0; transferred 13/13
[ 2627.851120] usb-storage: -- transfer complete
[ 2627.851125] usb-storage: Bulk status result = 0
[ 2627.851132] usb-storage: Bulk Status S 0x53425355 T 0x9f5 R 0 Stat 0x0
[ 2627.851138] usb-storage: scsi cmd done, result=0x0
[ 2627.851146] usb-storage: *** thread sleeping.
[ 2627.851296] usb-storage: queuecommand_lck called
[ 2627.851312] usb-storage: *** thread awakened.
[ 2627.851318] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2627.851323] usb-storage:  00 00 00 00 00 00
[ 2627.851343] usb-storage: Bulk Command S 0x43425355 T 0x9f6 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2627.851351] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2627.851490] usb-storage: Status code 0; transferred 31/31
[ 2627.851495] usb-storage: -- transfer complete
[ 2627.851504] usb-storage: Bulk command transfer result=0
[ 2627.851509] usb-storage: Attempting to get CSW...
[ 2627.851515] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2627.851615] usb-storage: Status code 0; transferred 13/13
[ 2627.851620] usb-storage: -- transfer complete
[ 2627.851629] usb-storage: Bulk status result = 0
[ 2627.851636] usb-storage: Bulk Status S 0x53425355 T 0x9f6 R 0 Stat 0x0
[ 2627.851642] usb-storage: scsi cmd done, result=0x0
[ 2627.851652] usb-storage: *** thread sleeping.
[ 2629.845209] usb-storage: queuecommand_lck called
[ 2629.845233] usb-storage: *** thread awakened.
[ 2629.845242] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2629.845248] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2629.845272] usb-storage: Bulk Command S 0x43425355 T 0x18be L 8 F 128 Trg 0 LUN 0 CL 10
[ 2629.845280] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.845369] usb-storage: Status code 0; transferred 31/31
[ 2629.845375] usb-storage: -- transfer complete
[ 2629.845381] usb-storage: Bulk command transfer result=0
[ 2629.845388] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2629.845861] usb-storage: Status code 0; transferred 8/8
[ 2629.845866] usb-storage: -- transfer complete
[ 2629.845872] usb-storage: Bulk data transfer result 0x0
[ 2629.845877] usb-storage: Attempting to get CSW...
[ 2629.845883] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.846371] usb-storage: Status code 0; transferred 13/13
[ 2629.846377] usb-storage: -- transfer complete
[ 2629.846382] usb-storage: Bulk status result = 0
[ 2629.846389] usb-storage: Bulk Status S 0x53425355 T 0x18be R 0 Stat 0x0
[ 2629.846397] usb-storage: scsi cmd done, result=0x0
[ 2629.846408] usb-storage: *** thread sleeping.
[ 2629.846462] usb-storage: queuecommand_lck called
[ 2629.846477] usb-storage: *** thread awakened.
[ 2629.846483] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2629.846488] usb-storage:  00 00 00 00 00 00
[ 2629.846505] usb-storage: Bulk Command S 0x43425355 T 0x18bf L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.846512] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.846615] usb-storage: Status code 0; transferred 31/31
[ 2629.846620] usb-storage: -- transfer complete
[ 2629.846626] usb-storage: Bulk command transfer result=0
[ 2629.846631] usb-storage: Attempting to get CSW...
[ 2629.846637] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.847621] usb-storage: Status code 0; transferred 13/13
[ 2629.847627] usb-storage: -- transfer complete
[ 2629.847632] usb-storage: Bulk status result = 0
[ 2629.847638] usb-storage: Bulk Status S 0x53425355 T 0x18bf R 0 Stat 0x1
[ 2629.847644] usb-storage: -- transport indicates command failure
[ 2629.847650] usb-storage: Issuing auto-REQUEST_SENSE
[ 2629.847658] usb-storage: Bulk Command S 0x43425355 T 0x18c0 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2629.847665] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.847739] usb-storage: Status code 0; transferred 31/31
[ 2629.847744] usb-storage: -- transfer complete
[ 2629.847749] usb-storage: Bulk command transfer result=0
[ 2629.847755] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2629.848876] usb-storage: Status code -121; transferred 24/96
[ 2629.848882] usb-storage: -- short read transfer
[ 2629.848888] usb-storage: Bulk data transfer result 0x1
[ 2629.848893] usb-storage: Attempting to get CSW...
[ 2629.848899] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.849119] usb-storage: Status code -32; transferred 0/13
[ 2629.849126] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2629.849135] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2629.849239] usb-storage: usb_stor_clear_halt: result = 0
[ 2629.849244] usb-storage: Attempting to get CSW (2nd try)...
[ 2629.849250] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.849363] usb-storage: Status code 0; transferred 13/13
[ 2629.849369] usb-storage: -- transfer complete
[ 2629.849374] usb-storage: Bulk status result = 0
[ 2629.849381] usb-storage: Bulk Status S 0x53425355 T 0x18c0 R 72 Stat 0x0
[ 2629.849388] usb-storage: -- Result from auto-sense is 0
[ 2629.849395] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2629.849405] usb-storage: Not Ready: Medium not present - tray closed
[ 2629.849414] usb-storage: scsi cmd done, result=0x2
[ 2629.849427] usb-storage: *** thread sleeping.
[ 2629.849512] usb-storage: queuecommand_lck called
[ 2629.849527] usb-storage: *** thread awakened.
[ 2629.849534] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2629.849540] usb-storage:  1e 00 00 00 00 00
[ 2629.849556] usb-storage: Bulk Command S 0x43425355 T 0x18c1 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.849562] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.849612] usb-storage: Status code 0; transferred 31/31
[ 2629.849617] usb-storage: -- transfer complete
[ 2629.849622] usb-storage: Bulk command transfer result=0
[ 2629.849627] usb-storage: Attempting to get CSW...
[ 2629.849632] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.850387] usb-storage: Status code 0; transferred 13/13
[ 2629.850392] usb-storage: -- transfer complete
[ 2629.850397] usb-storage: Bulk status result = 0
[ 2629.850404] usb-storage: Bulk Status S 0x53425355 T 0x18c1 R 0 Stat 0x0
[ 2629.850410] usb-storage: scsi cmd done, result=0x0
[ 2629.850422] usb-storage: *** thread sleeping.
[ 2629.850527] usb-storage: queuecommand_lck called
[ 2629.850543] usb-storage: *** thread awakened.
[ 2629.850550] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2629.850554] usb-storage:  00 00 00 00 00 00
[ 2629.850570] usb-storage: Bulk Command S 0x43425355 T 0x9f7 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.850577] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.850746] usb-storage: Status code 0; transferred 31/31
[ 2629.850752] usb-storage: -- transfer complete
[ 2629.850757] usb-storage: Bulk command transfer result=0
[ 2629.850762] usb-storage: Attempting to get CSW...
[ 2629.850767] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.850861] usb-storage: Status code 0; transferred 13/13
[ 2629.850866] usb-storage: -- transfer complete
[ 2629.850871] usb-storage: Bulk status result = 0
[ 2629.850877] usb-storage: Bulk Status S 0x53425355 T 0x9f7 R 0 Stat 0x0
[ 2629.850884] usb-storage: scsi cmd done, result=0x0
[ 2629.850895] usb-storage: *** thread sleeping.
[ 2629.851026] usb-storage: queuecommand_lck called
[ 2629.851041] usb-storage: *** thread awakened.
[ 2629.851048] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2629.851052] usb-storage:  00 00 00 00 00 00
[ 2629.851068] usb-storage: Bulk Command S 0x43425355 T 0x9f8 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.851074] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.851267] usb-storage: Status code 0; transferred 31/31
[ 2629.851272] usb-storage: -- transfer complete
[ 2629.851277] usb-storage: Bulk command transfer result=0
[ 2629.851281] usb-storage: Attempting to get CSW...
[ 2629.851287] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.851368] usb-storage: Status code 0; transferred 13/13
[ 2629.851374] usb-storage: -- transfer complete
[ 2629.851379] usb-storage: Bulk status result = 0
[ 2629.851386] usb-storage: Bulk Status S 0x53425355 T 0x9f8 R 0 Stat 0x0
[ 2629.851394] usb-storage: scsi cmd done, result=0x0
[ 2629.851406] usb-storage: *** thread sleeping.
[ 2629.858209] usb-storage: queuecommand_lck called
[ 2629.858233] usb-storage: *** thread awakened.
[ 2629.858242] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2629.858247] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2629.858269] usb-storage: Bulk Command S 0x43425355 T 0x18c2 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2629.858276] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.858384] usb-storage: Status code 0; transferred 31/31
[ 2629.858389] usb-storage: -- transfer complete
[ 2629.858394] usb-storage: Bulk command transfer result=0
[ 2629.858401] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2629.858906] usb-storage: Status code 0; transferred 8/8
[ 2629.858912] usb-storage: -- transfer complete
[ 2629.858919] usb-storage: Bulk data transfer result 0x0
[ 2629.858922] usb-storage: Attempting to get CSW...
[ 2629.858927] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.859367] usb-storage: Status code 0; transferred 13/13
[ 2629.859374] usb-storage: -- transfer complete
[ 2629.859379] usb-storage: Bulk status result = 0
[ 2629.859387] usb-storage: Bulk Status S 0x53425355 T 0x18c2 R 0 Stat 0x0
[ 2629.859395] usb-storage: scsi cmd done, result=0x0
[ 2629.859410] usb-storage: *** thread sleeping.
[ 2629.859496] usb-storage: queuecommand_lck called
[ 2629.859512] usb-storage: *** thread awakened.
[ 2629.859520] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2629.859525] usb-storage:  00 00 00 00 00 00
[ 2629.859541] usb-storage: Bulk Command S 0x43425355 T 0x18c3 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.859549] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.859614] usb-storage: Status code 0; transferred 31/31
[ 2629.859619] usb-storage: -- transfer complete
[ 2629.859624] usb-storage: Bulk command transfer result=0
[ 2629.859629] usb-storage: Attempting to get CSW...
[ 2629.859635] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.861127] usb-storage: Status code 0; transferred 13/13
[ 2629.861134] usb-storage: -- transfer complete
[ 2629.861140] usb-storage: Bulk status result = 0
[ 2629.861148] usb-storage: Bulk Status S 0x53425355 T 0x18c3 R 0 Stat 0x1
[ 2629.861154] usb-storage: -- transport indicates command failure
[ 2629.861160] usb-storage: Issuing auto-REQUEST_SENSE
[ 2629.861170] usb-storage: Bulk Command S 0x43425355 T 0x18c4 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2629.861178] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.861236] usb-storage: Status code 0; transferred 31/31
[ 2629.861242] usb-storage: -- transfer complete
[ 2629.861247] usb-storage: Bulk command transfer result=0
[ 2629.861255] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2629.862876] usb-storage: Status code -121; transferred 24/96
[ 2629.862883] usb-storage: -- short read transfer
[ 2629.862889] usb-storage: Bulk data transfer result 0x1
[ 2629.862894] usb-storage: Attempting to get CSW...
[ 2629.862900] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.863116] usb-storage: Status code -32; transferred 0/13
[ 2629.863123] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2629.863133] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2629.863241] usb-storage: usb_stor_clear_halt: result = 0
[ 2629.863247] usb-storage: Attempting to get CSW (2nd try)...
[ 2629.863253] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.863363] usb-storage: Status code 0; transferred 13/13
[ 2629.863369] usb-storage: -- transfer complete
[ 2629.863375] usb-storage: Bulk status result = 0
[ 2629.863382] usb-storage: Bulk Status S 0x53425355 T 0x18c4 R 72 Stat 0x0
[ 2629.863389] usb-storage: -- Result from auto-sense is 0
[ 2629.863396] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2629.863406] usb-storage: Not Ready: Medium not present - tray closed
[ 2629.863415] usb-storage: scsi cmd done, result=0x2
[ 2629.863427] usb-storage: *** thread sleeping.
[ 2629.863509] usb-storage: queuecommand_lck called
[ 2629.863524] usb-storage: *** thread awakened.
[ 2629.863531] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2629.863536] usb-storage:  00 00 00 00 00 00
[ 2629.863553] usb-storage: Bulk Command S 0x43425355 T 0x18c5 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.863560] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.863612] usb-storage: Status code 0; transferred 31/31
[ 2629.863617] usb-storage: -- transfer complete
[ 2629.863623] usb-storage: Bulk command transfer result=0
[ 2629.863628] usb-storage: Attempting to get CSW...
[ 2629.863634] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.864616] usb-storage: Status code 0; transferred 13/13
[ 2629.864623] usb-storage: -- transfer complete
[ 2629.864628] usb-storage: Bulk status result = 0
[ 2629.864635] usb-storage: Bulk Status S 0x53425355 T 0x18c5 R 0 Stat 0x1
[ 2629.864641] usb-storage: -- transport indicates command failure
[ 2629.864646] usb-storage: Issuing auto-REQUEST_SENSE
[ 2629.864656] usb-storage: Bulk Command S 0x43425355 T 0x18c6 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2629.864664] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.864736] usb-storage: Status code 0; transferred 31/31
[ 2629.864741] usb-storage: -- transfer complete
[ 2629.864747] usb-storage: Bulk command transfer result=0
[ 2629.864754] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2629.865995] usb-storage: Status code -121; transferred 24/96
[ 2629.866012] usb-storage: -- short read transfer
[ 2629.866018] usb-storage: Bulk data transfer result 0x1
[ 2629.866023] usb-storage: Attempting to get CSW...
[ 2629.866029] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.866245] usb-storage: Status code -32; transferred 0/13
[ 2629.866251] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2629.866260] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2629.866367] usb-storage: usb_stor_clear_halt: result = 0
[ 2629.866373] usb-storage: Attempting to get CSW (2nd try)...
[ 2629.866380] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.866551] usb-storage: Status code 0; transferred 13/13
[ 2629.866557] usb-storage: -- transfer complete
[ 2629.866561] usb-storage: Bulk status result = 0
[ 2629.866568] usb-storage: Bulk Status S 0x53425355 T 0x18c6 R 72 Stat 0x0
[ 2629.866574] usb-storage: -- Result from auto-sense is 0
[ 2629.866581] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2629.866590] usb-storage: Not Ready: Medium not present - tray closed
[ 2629.866599] usb-storage: scsi cmd done, result=0x2
[ 2629.866611] usb-storage: *** thread sleeping.
[ 2629.866678] usb-storage: queuecommand_lck called
[ 2629.866693] usb-storage: *** thread awakened.
[ 2629.866699] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2629.866705] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2629.866725] usb-storage: Bulk Command S 0x43425355 T 0x18c7 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2629.866733] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.867195] usb-storage: Status code 0; transferred 31/31
[ 2629.867202] usb-storage: -- transfer complete
[ 2629.867208] usb-storage: Bulk command transfer result=0
[ 2629.867215] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2629.867376] usb-storage: Status code 0; transferred 8/8
[ 2629.867382] usb-storage: -- transfer complete
[ 2629.867387] usb-storage: Bulk data transfer result 0x0
[ 2629.867392] usb-storage: Attempting to get CSW...
[ 2629.867398] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.867989] usb-storage: Status code 0; transferred 13/13
[ 2629.867995] usb-storage: -- transfer complete
[ 2629.868000] usb-storage: Bulk status result = 0
[ 2629.868021] usb-storage: Bulk Status S 0x53425355 T 0x18c7 R 0 Stat 0x0
[ 2629.868029] usb-storage: scsi cmd done, result=0x0
[ 2629.868040] usb-storage: *** thread sleeping.
[ 2629.868109] usb-storage: queuecommand_lck called
[ 2629.868124] usb-storage: *** thread awakened.
[ 2629.868131] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2629.868136] usb-storage:  1e 00 00 00 00 00
[ 2629.868152] usb-storage: Bulk Command S 0x43425355 T 0x18c8 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2629.868160] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2629.868243] usb-storage: Status code 0; transferred 31/31
[ 2629.868249] usb-storage: -- transfer complete
[ 2629.868254] usb-storage: Bulk command transfer result=0
[ 2629.868259] usb-storage: Attempting to get CSW...
[ 2629.868265] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2629.869138] usb-storage: Status code 0; transferred 13/13
[ 2629.869145] usb-storage: -- transfer complete
[ 2629.869151] usb-storage: Bulk status result = 0
[ 2629.869158] usb-storage: Bulk Status S 0x53425355 T 0x18c8 R 0 Stat 0x0
[ 2629.869166] usb-storage: scsi cmd done, result=0x0
[ 2629.869180] usb-storage: *** thread sleeping.
[ 2631.845585] usb-storage: queuecommand_lck called
[ 2631.845607] usb-storage: *** thread awakened.
[ 2631.845613] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2631.845617] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2631.845634] usb-storage: Bulk Command S 0x43425355 T 0x18c9 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2631.845639] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.845742] usb-storage: Status code 0; transferred 31/31
[ 2631.845746] usb-storage: -- transfer complete
[ 2631.845750] usb-storage: Bulk command transfer result=0
[ 2631.845755] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2631.846263] usb-storage: Status code 0; transferred 8/8
[ 2631.846269] usb-storage: -- transfer complete
[ 2631.846274] usb-storage: Bulk data transfer result 0x0
[ 2631.846280] usb-storage: Attempting to get CSW...
[ 2631.846286] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.847239] usb-storage: Status code 0; transferred 13/13
[ 2631.847243] usb-storage: -- transfer complete
[ 2631.847247] usb-storage: Bulk status result = 0
[ 2631.847252] usb-storage: Bulk Status S 0x53425355 T 0x18c9 R 0 Stat 0x0
[ 2631.847258] usb-storage: scsi cmd done, result=0x0
[ 2631.847266] usb-storage: *** thread sleeping.
[ 2631.847305] usb-storage: queuecommand_lck called
[ 2631.847317] usb-storage: *** thread awakened.
[ 2631.847322] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2631.847325] usb-storage:  00 00 00 00 00 00
[ 2631.847337] usb-storage: Bulk Command S 0x43425355 T 0x18ca L 0 F 0 Trg 0 LUN 0 CL 6
[ 2631.847342] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.847483] usb-storage: Status code 0; transferred 31/31
[ 2631.847487] usb-storage: -- transfer complete
[ 2631.847491] usb-storage: Bulk command transfer result=0
[ 2631.847495] usb-storage: Attempting to get CSW...
[ 2631.847499] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.848363] usb-storage: Status code 0; transferred 13/13
[ 2631.848373] usb-storage: -- transfer complete
[ 2631.848378] usb-storage: Bulk status result = 0
[ 2631.848385] usb-storage: Bulk Status S 0x53425355 T 0x18ca R 0 Stat 0x1
[ 2631.848392] usb-storage: -- transport indicates command failure
[ 2631.848398] usb-storage: Issuing auto-REQUEST_SENSE
[ 2631.848407] usb-storage: Bulk Command S 0x43425355 T 0x18cb L 96 F 128 Trg 0 LUN 0 CL 6
[ 2631.848414] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.848490] usb-storage: Status code 0; transferred 31/31
[ 2631.848496] usb-storage: -- transfer complete
[ 2631.848501] usb-storage: Bulk command transfer result=0
[ 2631.848508] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2631.850119] usb-storage: Status code -121; transferred 24/96
[ 2631.850123] usb-storage: -- short read transfer
[ 2631.850127] usb-storage: Bulk data transfer result 0x1
[ 2631.850131] usb-storage: Attempting to get CSW...
[ 2631.850135] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.850360] usb-storage: Status code -32; transferred 0/13
[ 2631.850365] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2631.850371] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2631.850484] usb-storage: usb_stor_clear_halt: result = 0
[ 2631.850489] usb-storage: Attempting to get CSW (2nd try)...
[ 2631.850493] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.850608] usb-storage: Status code 0; transferred 13/13
[ 2631.850612] usb-storage: -- transfer complete
[ 2631.850615] usb-storage: Bulk status result = 0
[ 2631.850620] usb-storage: Bulk Status S 0x53425355 T 0x18cb R 72 Stat 0x0
[ 2631.850625] usb-storage: -- Result from auto-sense is 0
[ 2631.850630] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2631.850637] usb-storage: Not Ready: Medium not present - tray closed
[ 2631.850644] usb-storage: scsi cmd done, result=0x2
[ 2631.850651] usb-storage: *** thread sleeping.
[ 2631.850707] usb-storage: queuecommand_lck called
[ 2631.850723] usb-storage: *** thread awakened.
[ 2631.850728] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2631.850731] usb-storage:  1e 00 00 00 00 00
[ 2631.850743] usb-storage: Bulk Command S 0x43425355 T 0x18cc L 0 F 0 Trg 0 LUN 0 CL 6
[ 2631.850748] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.850859] usb-storage: Status code 0; transferred 31/31
[ 2631.850863] usb-storage: -- transfer complete
[ 2631.850867] usb-storage: Bulk command transfer result=0
[ 2631.850871] usb-storage: Attempting to get CSW...
[ 2631.850875] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.851631] usb-storage: Status code 0; transferred 13/13
[ 2631.851637] usb-storage: -- transfer complete
[ 2631.851642] usb-storage: Bulk status result = 0
[ 2631.851649] usb-storage: Bulk Status S 0x53425355 T 0x18cc R 0 Stat 0x0
[ 2631.851656] usb-storage: scsi cmd done, result=0x0
[ 2631.851666] usb-storage: *** thread sleeping.
[ 2631.851746] usb-storage: queuecommand_lck called
[ 2631.851762] usb-storage: *** thread awakened.
[ 2631.851770] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2631.851775] usb-storage:  00 00 00 00 00 00
[ 2631.851791] usb-storage: Bulk Command S 0x43425355 T 0x9f9 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2631.851798] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.851872] usb-storage: Status code 0; transferred 31/31
[ 2631.851878] usb-storage: -- transfer complete
[ 2631.851882] usb-storage: Bulk command transfer result=0
[ 2631.851887] usb-storage: Attempting to get CSW...
[ 2631.851892] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.851998] usb-storage: Status code 0; transferred 13/13
[ 2631.852015] usb-storage: -- transfer complete
[ 2631.852021] usb-storage: Bulk status result = 0
[ 2631.852028] usb-storage: Bulk Status S 0x53425355 T 0x9f9 R 0 Stat 0x0
[ 2631.852035] usb-storage: scsi cmd done, result=0x0
[ 2631.852044] usb-storage: *** thread sleeping.
[ 2631.852115] usb-storage: queuecommand_lck called
[ 2631.852129] usb-storage: *** thread awakened.
[ 2631.852136] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2631.852141] usb-storage:  00 00 00 00 00 00
[ 2631.852157] usb-storage: Bulk Command S 0x43425355 T 0x9fa L 0 F 0 Trg 0 LUN 0 CL 6
[ 2631.852164] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2631.852245] usb-storage: Status code 0; transferred 31/31
[ 2631.852251] usb-storage: -- transfer complete
[ 2631.852256] usb-storage: Bulk command transfer result=0
[ 2631.852261] usb-storage: Attempting to get CSW...
[ 2631.852268] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2631.852372] usb-storage: Status code 0; transferred 13/13
[ 2631.852378] usb-storage: -- transfer complete
[ 2631.852383] usb-storage: Bulk status result = 0
[ 2631.852390] usb-storage: Bulk Status S 0x53425355 T 0x9fa R 0 Stat 0x0
[ 2631.852397] usb-storage: scsi cmd done, result=0x0
[ 2631.852406] usb-storage: *** thread sleeping.
[ 2633.844098] usb-storage: queuecommand_lck called
[ 2633.844121] usb-storage: *** thread awakened.
[ 2633.844128] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2633.844132] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2633.844149] usb-storage: Bulk Command S 0x43425355 T 0x18cd L 8 F 128 Trg 0 LUN 0 CL 10
[ 2633.844154] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.844244] usb-storage: Status code 0; transferred 31/31
[ 2633.844248] usb-storage: -- transfer complete
[ 2633.844252] usb-storage: Bulk command transfer result=0
[ 2633.844257] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2633.844611] usb-storage: Status code 0; transferred 8/8
[ 2633.844615] usb-storage: -- transfer complete
[ 2633.844618] usb-storage: Bulk data transfer result 0x0
[ 2633.844622] usb-storage: Attempting to get CSW...
[ 2633.844626] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.845616] usb-storage: Status code 0; transferred 13/13
[ 2633.845621] usb-storage: -- transfer complete
[ 2633.845625] usb-storage: Bulk status result = 0
[ 2633.845630] usb-storage: Bulk Status S 0x53425355 T 0x18cd R 0 Stat 0x0
[ 2633.845635] usb-storage: scsi cmd done, result=0x0
[ 2633.845643] usb-storage: *** thread sleeping.
[ 2633.845679] usb-storage: queuecommand_lck called
[ 2633.845693] usb-storage: *** thread awakened.
[ 2633.845698] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2633.845702] usb-storage:  00 00 00 00 00 00
[ 2633.845714] usb-storage: Bulk Command S 0x43425355 T 0x18ce L 0 F 0 Trg 0 LUN 0 CL 6
[ 2633.845719] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.845860] usb-storage: Status code 0; transferred 31/31
[ 2633.845864] usb-storage: -- transfer complete
[ 2633.845868] usb-storage: Bulk command transfer result=0
[ 2633.845871] usb-storage: Attempting to get CSW...
[ 2633.845876] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.847115] usb-storage: Status code 0; transferred 13/13
[ 2633.847120] usb-storage: -- transfer complete
[ 2633.847123] usb-storage: Bulk status result = 0
[ 2633.847129] usb-storage: Bulk Status S 0x53425355 T 0x18ce R 0 Stat 0x1
[ 2633.847133] usb-storage: -- transport indicates command failure
[ 2633.847137] usb-storage: Issuing auto-REQUEST_SENSE
[ 2633.847144] usb-storage: Bulk Command S 0x43425355 T 0x18cf L 96 F 128 Trg 0 LUN 0 CL 6
[ 2633.847149] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.847234] usb-storage: Status code 0; transferred 31/31
[ 2633.847238] usb-storage: -- transfer complete
[ 2633.847242] usb-storage: Bulk command transfer result=0
[ 2633.847247] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2633.848393] usb-storage: Status code -121; transferred 24/96
[ 2633.848400] usb-storage: -- short read transfer
[ 2633.848406] usb-storage: Bulk data transfer result 0x1
[ 2633.848412] usb-storage: Attempting to get CSW...
[ 2633.848418] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.848623] usb-storage: Status code -32; transferred 0/13
[ 2633.848631] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2633.848640] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2633.848744] usb-storage: usb_stor_clear_halt: result = 0
[ 2633.848750] usb-storage: Attempting to get CSW (2nd try)...
[ 2633.848756] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.848876] usb-storage: Status code 0; transferred 13/13
[ 2633.848882] usb-storage: -- transfer complete
[ 2633.848887] usb-storage: Bulk status result = 0
[ 2633.848894] usb-storage: Bulk Status S 0x53425355 T 0x18cf R 72 Stat 0x0
[ 2633.848901] usb-storage: -- Result from auto-sense is 0
[ 2633.848908] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2633.848919] usb-storage: Not Ready: Medium not present - tray closed
[ 2633.848928] usb-storage: scsi cmd done, result=0x2
[ 2633.848941] usb-storage: *** thread sleeping.
[ 2633.849043] usb-storage: queuecommand_lck called
[ 2633.849057] usb-storage: *** thread awakened.
[ 2633.849063] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2633.849068] usb-storage:  1e 00 00 00 00 00
[ 2633.849083] usb-storage: Bulk Command S 0x43425355 T 0x18d0 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2633.849089] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.849250] usb-storage: Status code 0; transferred 31/31
[ 2633.849256] usb-storage: -- transfer complete
[ 2633.849261] usb-storage: Bulk command transfer result=0
[ 2633.849266] usb-storage: Attempting to get CSW...
[ 2633.849272] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.850004] usb-storage: Status code 0; transferred 13/13
[ 2633.850025] usb-storage: -- transfer complete
[ 2633.850031] usb-storage: Bulk status result = 0
[ 2633.850038] usb-storage: Bulk Status S 0x53425355 T 0x18d0 R 0 Stat 0x0
[ 2633.850045] usb-storage: scsi cmd done, result=0x0
[ 2633.850055] usb-storage: *** thread sleeping.
[ 2633.850160] usb-storage: queuecommand_lck called
[ 2633.850177] usb-storage: *** thread awakened.
[ 2633.850184] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2633.850189] usb-storage:  00 00 00 00 00 00
[ 2633.850207] usb-storage: Bulk Command S 0x43425355 T 0x9fb L 0 F 0 Trg 0 LUN 0 CL 6
[ 2633.850214] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.850373] usb-storage: Status code 0; transferred 31/31
[ 2633.850379] usb-storage: -- transfer complete
[ 2633.850385] usb-storage: Bulk command transfer result=0
[ 2633.850390] usb-storage: Attempting to get CSW...
[ 2633.850396] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.850490] usb-storage: Status code 0; transferred 13/13
[ 2633.850495] usb-storage: -- transfer complete
[ 2633.850500] usb-storage: Bulk status result = 0
[ 2633.850506] usb-storage: Bulk Status S 0x53425355 T 0x9fb R 0 Stat 0x0
[ 2633.850512] usb-storage: scsi cmd done, result=0x0
[ 2633.850521] usb-storage: *** thread sleeping.
[ 2633.850592] usb-storage: queuecommand_lck called
[ 2633.850607] usb-storage: *** thread awakened.
[ 2633.850614] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2633.850619] usb-storage:  00 00 00 00 00 00
[ 2633.850635] usb-storage: Bulk Command S 0x43425355 T 0x9fc L 0 F 0 Trg 0 LUN 0 CL 6
[ 2633.850643] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2633.850741] usb-storage: Status code 0; transferred 31/31
[ 2633.850747] usb-storage: -- transfer complete
[ 2633.850752] usb-storage: Bulk command transfer result=0
[ 2633.850757] usb-storage: Attempting to get CSW...
[ 2633.850763] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2633.850865] usb-storage: Status code 0; transferred 13/13
[ 2633.850871] usb-storage: -- transfer complete
[ 2633.850876] usb-storage: Bulk status result = 0
[ 2633.850882] usb-storage: Bulk Status S 0x53425355 T 0x9fc R 0 Stat 0x0
[ 2633.850888] usb-storage: scsi cmd done, result=0x0
[ 2633.850897] usb-storage: *** thread sleeping.
[ 2635.845055] usb-storage: queuecommand_lck called
[ 2635.845075] usb-storage: *** thread awakened.
[ 2635.845082] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2635.845086] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2635.845102] usb-storage: Bulk Command S 0x43425355 T 0x18d1 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2635.845108] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.845244] usb-storage: Status code 0; transferred 31/31
[ 2635.845248] usb-storage: -- transfer complete
[ 2635.845252] usb-storage: Bulk command transfer result=0
[ 2635.845257] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2635.845737] usb-storage: Status code 0; transferred 8/8
[ 2635.845741] usb-storage: -- transfer complete
[ 2635.845745] usb-storage: Bulk data transfer result 0x0
[ 2635.845748] usb-storage: Attempting to get CSW...
[ 2635.845752] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.846254] usb-storage: Status code 0; transferred 13/13
[ 2635.846260] usb-storage: -- transfer complete
[ 2635.846265] usb-storage: Bulk status result = 0
[ 2635.846272] usb-storage: Bulk Status S 0x53425355 T 0x18d1 R 0 Stat 0x0
[ 2635.846279] usb-storage: scsi cmd done, result=0x0
[ 2635.846290] usb-storage: *** thread sleeping.
[ 2635.846332] usb-storage: queuecommand_lck called
[ 2635.846346] usb-storage: *** thread awakened.
[ 2635.846353] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2635.846358] usb-storage:  00 00 00 00 00 00
[ 2635.846374] usb-storage: Bulk Command S 0x43425355 T 0x18d2 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2635.846381] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.846504] usb-storage: Status code 0; transferred 31/31
[ 2635.846510] usb-storage: -- transfer complete
[ 2635.846515] usb-storage: Bulk command transfer result=0
[ 2635.846520] usb-storage: Attempting to get CSW...
[ 2635.846527] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.847365] usb-storage: Status code 0; transferred 13/13
[ 2635.847370] usb-storage: -- transfer complete
[ 2635.847374] usb-storage: Bulk status result = 0
[ 2635.847379] usb-storage: Bulk Status S 0x53425355 T 0x18d2 R 0 Stat 0x1
[ 2635.847383] usb-storage: -- transport indicates command failure
[ 2635.847387] usb-storage: Issuing auto-REQUEST_SENSE
[ 2635.847394] usb-storage: Bulk Command S 0x43425355 T 0x18d3 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2635.847399] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.847534] usb-storage: Status code 0; transferred 31/31
[ 2635.847539] usb-storage: -- transfer complete
[ 2635.847544] usb-storage: Bulk command transfer result=0
[ 2635.847551] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2635.848761] usb-storage: Status code -121; transferred 24/96
[ 2635.848767] usb-storage: -- short read transfer
[ 2635.848772] usb-storage: Bulk data transfer result 0x1
[ 2635.848775] usb-storage: Attempting to get CSW...
[ 2635.848780] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.848988] usb-storage: Status code -32; transferred 0/13
[ 2635.848992] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2635.848999] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2635.849122] usb-storage: usb_stor_clear_halt: result = 0
[ 2635.849128] usb-storage: Attempting to get CSW (2nd try)...
[ 2635.849134] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.849250] usb-storage: Status code 0; transferred 13/13
[ 2635.849255] usb-storage: -- transfer complete
[ 2635.849260] usb-storage: Bulk status result = 0
[ 2635.849266] usb-storage: Bulk Status S 0x53425355 T 0x18d3 R 72 Stat 0x0
[ 2635.849273] usb-storage: -- Result from auto-sense is 0
[ 2635.849279] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2635.849287] usb-storage: Not Ready: Medium not present - tray closed
[ 2635.849296] usb-storage: scsi cmd done, result=0x2
[ 2635.849307] usb-storage: *** thread sleeping.
[ 2635.849385] usb-storage: queuecommand_lck called
[ 2635.849400] usb-storage: *** thread awakened.
[ 2635.849407] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2635.849412] usb-storage:  1e 00 00 00 00 00
[ 2635.849429] usb-storage: Bulk Command S 0x43425355 T 0x18d4 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2635.849436] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.849498] usb-storage: Status code 0; transferred 31/31
[ 2635.849504] usb-storage: -- transfer complete
[ 2635.849509] usb-storage: Bulk command transfer result=0
[ 2635.849514] usb-storage: Attempting to get CSW...
[ 2635.849520] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.850241] usb-storage: Status code 0; transferred 13/13
[ 2635.850245] usb-storage: -- transfer complete
[ 2635.850249] usb-storage: Bulk status result = 0
[ 2635.850254] usb-storage: Bulk Status S 0x53425355 T 0x18d4 R 0 Stat 0x0
[ 2635.850259] usb-storage: scsi cmd done, result=0x0
[ 2635.850266] usb-storage: *** thread sleeping.
[ 2635.850341] usb-storage: queuecommand_lck called
[ 2635.850356] usb-storage: *** thread awakened.
[ 2635.850361] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2635.850365] usb-storage:  00 00 00 00 00 00
[ 2635.850376] usb-storage: Bulk Command S 0x43425355 T 0x9fd L 0 F 0 Trg 0 LUN 0 CL 6
[ 2635.850381] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.850487] usb-storage: Status code 0; transferred 31/31
[ 2635.850490] usb-storage: -- transfer complete
[ 2635.850494] usb-storage: Bulk command transfer result=0
[ 2635.850498] usb-storage: Attempting to get CSW...
[ 2635.850502] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.850610] usb-storage: Status code 0; transferred 13/13
[ 2635.850614] usb-storage: -- transfer complete
[ 2635.850617] usb-storage: Bulk status result = 0
[ 2635.850622] usb-storage: Bulk Status S 0x53425355 T 0x9fd R 0 Stat 0x0
[ 2635.850627] usb-storage: scsi cmd done, result=0x0
[ 2635.850633] usb-storage: *** thread sleeping.
[ 2635.850689] usb-storage: queuecommand_lck called
[ 2635.850700] usb-storage: *** thread awakened.
[ 2635.850705] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2635.850709] usb-storage:  00 00 00 00 00 00
[ 2635.850720] usb-storage: Bulk Command S 0x43425355 T 0x9fe L 0 F 0 Trg 0 LUN 0 CL 6
[ 2635.850725] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2635.850862] usb-storage: Status code 0; transferred 31/31
[ 2635.850866] usb-storage: -- transfer complete
[ 2635.850870] usb-storage: Bulk command transfer result=0
[ 2635.850873] usb-storage: Attempting to get CSW...
[ 2635.850877] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2635.850985] usb-storage: Status code 0; transferred 13/13
[ 2635.850988] usb-storage: -- transfer complete
[ 2635.850992] usb-storage: Bulk status result = 0
[ 2635.850997] usb-storage: Bulk Status S 0x53425355 T 0x9fe R 0 Stat 0x0
[ 2635.851014] usb-storage: scsi cmd done, result=0x0
[ 2635.851023] usb-storage: *** thread sleeping.
[ 2637.845171] usb-storage: queuecommand_lck called
[ 2637.845193] usb-storage: *** thread awakened.
[ 2637.845199] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2637.845203] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2637.845220] usb-storage: Bulk Command S 0x43425355 T 0x18d5 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2637.845225] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.845371] usb-storage: Status code 0; transferred 31/31
[ 2637.845375] usb-storage: -- transfer complete
[ 2637.845379] usb-storage: Bulk command transfer result=0
[ 2637.845384] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2637.845863] usb-storage: Status code 0; transferred 8/8
[ 2637.845867] usb-storage: -- transfer complete
[ 2637.845871] usb-storage: Bulk data transfer result 0x0
[ 2637.845874] usb-storage: Attempting to get CSW...
[ 2637.845878] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.846868] usb-storage: Status code 0; transferred 13/13
[ 2637.846872] usb-storage: -- transfer complete
[ 2637.846876] usb-storage: Bulk status result = 0
[ 2637.846881] usb-storage: Bulk Status S 0x53425355 T 0x18d5 R 0 Stat 0x0
[ 2637.846886] usb-storage: scsi cmd done, result=0x0
[ 2637.846895] usb-storage: *** thread sleeping.
[ 2637.846930] usb-storage: queuecommand_lck called
[ 2637.846943] usb-storage: *** thread awakened.
[ 2637.846948] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2637.846952] usb-storage:  00 00 00 00 00 00
[ 2637.846964] usb-storage: Bulk Command S 0x43425355 T 0x18d6 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2637.846969] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.847128] usb-storage: Status code 0; transferred 31/31
[ 2637.847133] usb-storage: -- transfer complete
[ 2637.847142] usb-storage: Bulk command transfer result=0
[ 2637.847147] usb-storage: Attempting to get CSW...
[ 2637.847153] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.848002] usb-storage: Status code 0; transferred 13/13
[ 2637.848021] usb-storage: -- transfer complete
[ 2637.848026] usb-storage: Bulk status result = 0
[ 2637.848033] usb-storage: Bulk Status S 0x53425355 T 0x18d6 R 0 Stat 0x1
[ 2637.848038] usb-storage: -- transport indicates command failure
[ 2637.848044] usb-storage: Issuing auto-REQUEST_SENSE
[ 2637.848053] usb-storage: Bulk Command S 0x43425355 T 0x18d7 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2637.848060] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.848121] usb-storage: Status code 0; transferred 31/31
[ 2637.848127] usb-storage: -- transfer complete
[ 2637.848132] usb-storage: Bulk command transfer result=0
[ 2637.848139] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2637.849746] usb-storage: Status code -121; transferred 24/96
[ 2637.849750] usb-storage: -- short read transfer
[ 2637.849754] usb-storage: Bulk data transfer result 0x1
[ 2637.849758] usb-storage: Attempting to get CSW...
[ 2637.849762] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.849988] usb-storage: Status code -32; transferred 0/13
[ 2637.849993] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2637.849999] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2637.850130] usb-storage: usb_stor_clear_halt: result = 0
[ 2637.850136] usb-storage: Attempting to get CSW (2nd try)...
[ 2637.850143] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.850245] usb-storage: Status code 0; transferred 13/13
[ 2637.850250] usb-storage: -- transfer complete
[ 2637.850255] usb-storage: Bulk status result = 0
[ 2637.850262] usb-storage: Bulk Status S 0x53425355 T 0x18d7 R 72 Stat 0x0
[ 2637.850268] usb-storage: -- Result from auto-sense is 0
[ 2637.850274] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2637.850283] usb-storage: Not Ready: Medium not present - tray closed
[ 2637.850291] usb-storage: scsi cmd done, result=0x2
[ 2637.850301] usb-storage: *** thread sleeping.
[ 2637.850375] usb-storage: queuecommand_lck called
[ 2637.850390] usb-storage: *** thread awakened.
[ 2637.850397] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2637.850402] usb-storage:  1e 00 00 00 00 00
[ 2637.850419] usb-storage: Bulk Command S 0x43425355 T 0x18d8 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2637.850426] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.850503] usb-storage: Status code 0; transferred 31/31
[ 2637.850509] usb-storage: -- transfer complete
[ 2637.850514] usb-storage: Bulk command transfer result=0
[ 2637.850519] usb-storage: Attempting to get CSW...
[ 2637.850525] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.851242] usb-storage: Status code 0; transferred 13/13
[ 2637.851246] usb-storage: -- transfer complete
[ 2637.851250] usb-storage: Bulk status result = 0
[ 2637.851255] usb-storage: Bulk Status S 0x53425355 T 0x18d8 R 0 Stat 0x0
[ 2637.851260] usb-storage: scsi cmd done, result=0x0
[ 2637.851267] usb-storage: *** thread sleeping.
[ 2637.851341] usb-storage: queuecommand_lck called
[ 2637.851356] usb-storage: *** thread awakened.
[ 2637.851361] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2637.851365] usb-storage:  00 00 00 00 00 00
[ 2637.851377] usb-storage: Bulk Command S 0x43425355 T 0x9ff L 0 F 0 Trg 0 LUN 0 CL 6
[ 2637.851382] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.851488] usb-storage: Status code 0; transferred 31/31
[ 2637.851492] usb-storage: -- transfer complete
[ 2637.851496] usb-storage: Bulk command transfer result=0
[ 2637.851499] usb-storage: Attempting to get CSW...
[ 2637.851503] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.851611] usb-storage: Status code 0; transferred 13/13
[ 2637.851615] usb-storage: -- transfer complete
[ 2637.851618] usb-storage: Bulk status result = 0
[ 2637.851623] usb-storage: Bulk Status S 0x53425355 T 0x9ff R 0 Stat 0x0
[ 2637.851628] usb-storage: scsi cmd done, result=0x0
[ 2637.851634] usb-storage: *** thread sleeping.
[ 2637.851689] usb-storage: queuecommand_lck called
[ 2637.851701] usb-storage: *** thread awakened.
[ 2637.851705] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2637.851709] usb-storage:  00 00 00 00 00 00
[ 2637.851720] usb-storage: Bulk Command S 0x43425355 T 0xa00 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2637.851725] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2637.851862] usb-storage: Status code 0; transferred 31/31
[ 2637.851866] usb-storage: -- transfer complete
[ 2637.851870] usb-storage: Bulk command transfer result=0
[ 2637.851874] usb-storage: Attempting to get CSW...
[ 2637.851878] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2637.851986] usb-storage: Status code 0; transferred 13/13
[ 2637.851990] usb-storage: -- transfer complete
[ 2637.851993] usb-storage: Bulk status result = 0
[ 2637.851998] usb-storage: Bulk Status S 0x53425355 T 0xa00 R 0 Stat 0x0
[ 2637.852017] usb-storage: scsi cmd done, result=0x0
[ 2637.852025] usb-storage: *** thread sleeping.
[ 2639.845126] usb-storage: queuecommand_lck called
[ 2639.845146] usb-storage: *** thread awakened.
[ 2639.845153] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2639.845157] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2639.845174] usb-storage: Bulk Command S 0x43425355 T 0x18d9 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2639.845179] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.845246] usb-storage: Status code 0; transferred 31/31
[ 2639.845252] usb-storage: -- transfer complete
[ 2639.845257] usb-storage: Bulk command transfer result=0
[ 2639.845264] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2639.845618] usb-storage: Status code 0; transferred 8/8
[ 2639.845623] usb-storage: -- transfer complete
[ 2639.845629] usb-storage: Bulk data transfer result 0x0
[ 2639.845634] usb-storage: Attempting to get CSW...
[ 2639.845640] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.846270] usb-storage: Status code 0; transferred 13/13
[ 2639.846276] usb-storage: -- transfer complete
[ 2639.846281] usb-storage: Bulk status result = 0
[ 2639.846288] usb-storage: Bulk Status S 0x53425355 T 0x18d9 R 0 Stat 0x0
[ 2639.846296] usb-storage: scsi cmd done, result=0x0
[ 2639.846306] usb-storage: *** thread sleeping.
[ 2639.846353] usb-storage: queuecommand_lck called
[ 2639.846368] usb-storage: *** thread awakened.
[ 2639.846374] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2639.846379] usb-storage:  00 00 00 00 00 00
[ 2639.846395] usb-storage: Bulk Command S 0x43425355 T 0x18da L 0 F 0 Trg 0 LUN 0 CL 6
[ 2639.846403] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.846654] usb-storage: Status code 0; transferred 31/31
[ 2639.846661] usb-storage: -- transfer complete
[ 2639.846666] usb-storage: Bulk command transfer result=0
[ 2639.846671] usb-storage: Attempting to get CSW...
[ 2639.846678] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.847889] usb-storage: Status code 0; transferred 13/13
[ 2639.847896] usb-storage: -- transfer complete
[ 2639.847902] usb-storage: Bulk status result = 0
[ 2639.847908] usb-storage: Bulk Status S 0x53425355 T 0x18da R 0 Stat 0x1
[ 2639.847914] usb-storage: -- transport indicates command failure
[ 2639.847919] usb-storage: Issuing auto-REQUEST_SENSE
[ 2639.847929] usb-storage: Bulk Command S 0x43425355 T 0x18db L 96 F 128 Trg 0 LUN 0 CL 6
[ 2639.847937] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.847994] usb-storage: Status code 0; transferred 31/31
[ 2639.847999] usb-storage: -- transfer complete
[ 2639.848021] usb-storage: Bulk command transfer result=0
[ 2639.848029] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2639.849022] usb-storage: Status code -121; transferred 24/96
[ 2639.849029] usb-storage: -- short read transfer
[ 2639.849035] usb-storage: Bulk data transfer result 0x1
[ 2639.849040] usb-storage: Attempting to get CSW...
[ 2639.849046] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.849242] usb-storage: Status code -32; transferred 0/13
[ 2639.849249] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2639.849258] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2639.849367] usb-storage: usb_stor_clear_halt: result = 0
[ 2639.849373] usb-storage: Attempting to get CSW (2nd try)...
[ 2639.849380] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.849491] usb-storage: Status code 0; transferred 13/13
[ 2639.849497] usb-storage: -- transfer complete
[ 2639.849503] usb-storage: Bulk status result = 0
[ 2639.849510] usb-storage: Bulk Status S 0x53425355 T 0x18db R 72 Stat 0x0
[ 2639.849517] usb-storage: -- Result from auto-sense is 0
[ 2639.849524] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2639.849533] usb-storage: Not Ready: Medium not present - tray closed
[ 2639.849543] usb-storage: scsi cmd done, result=0x2
[ 2639.849555] usb-storage: *** thread sleeping.
[ 2639.849635] usb-storage: queuecommand_lck called
[ 2639.849651] usb-storage: *** thread awakened.
[ 2639.849658] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2639.849663] usb-storage:  1e 00 00 00 00 00
[ 2639.849679] usb-storage: Bulk Command S 0x43425355 T 0x18dc L 0 F 0 Trg 0 LUN 0 CL 6
[ 2639.849686] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.849742] usb-storage: Status code 0; transferred 31/31
[ 2639.849747] usb-storage: -- transfer complete
[ 2639.849753] usb-storage: Bulk command transfer result=0
[ 2639.849758] usb-storage: Attempting to get CSW...
[ 2639.849763] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.850651] usb-storage: Status code 0; transferred 13/13
[ 2639.850658] usb-storage: -- transfer complete
[ 2639.850663] usb-storage: Bulk status result = 0
[ 2639.850669] usb-storage: Bulk Status S 0x53425355 T 0x18dc R 0 Stat 0x0
[ 2639.850677] usb-storage: scsi cmd done, result=0x0
[ 2639.850688] usb-storage: *** thread sleeping.
[ 2639.850795] usb-storage: queuecommand_lck called
[ 2639.850815] usb-storage: *** thread awakened.
[ 2639.850823] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2639.850827] usb-storage:  00 00 00 00 00 00
[ 2639.850844] usb-storage: Bulk Command S 0x43425355 T 0xa01 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2639.850851] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.851056] usb-storage: Status code 0; transferred 31/31
[ 2639.851063] usb-storage: -- transfer complete
[ 2639.851068] usb-storage: Bulk command transfer result=0
[ 2639.851073] usb-storage: Attempting to get CSW...
[ 2639.851080] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.851257] usb-storage: Status code 0; transferred 13/13
[ 2639.851262] usb-storage: -- transfer complete
[ 2639.851268] usb-storage: Bulk status result = 0
[ 2639.851276] usb-storage: Bulk Status S 0x53425355 T 0xa01 R 0 Stat 0x0
[ 2639.851284] usb-storage: scsi cmd done, result=0x0
[ 2639.851299] usb-storage: *** thread sleeping.
[ 2639.851486] usb-storage: queuecommand_lck called
[ 2639.851508] usb-storage: *** thread awakened.
[ 2639.851514] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2639.851518] usb-storage:  00 00 00 00 00 00
[ 2639.851535] usb-storage: Bulk Command S 0x43425355 T 0xa02 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2639.851542] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2639.851634] usb-storage: Status code 0; transferred 31/31
[ 2639.851639] usb-storage: -- transfer complete
[ 2639.851645] usb-storage: Bulk command transfer result=0
[ 2639.851650] usb-storage: Attempting to get CSW...
[ 2639.851656] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2639.851748] usb-storage: Status code 0; transferred 13/13
[ 2639.851754] usb-storage: -- transfer complete
[ 2639.851759] usb-storage: Bulk status result = 0
[ 2639.851766] usb-storage: Bulk Status S 0x53425355 T 0xa02 R 0 Stat 0x0
[ 2639.851776] usb-storage: scsi cmd done, result=0x0
[ 2639.851786] usb-storage: *** thread sleeping.
[ 2641.845207] usb-storage: queuecommand_lck called
[ 2641.845238] usb-storage: *** thread awakened.
[ 2641.845245] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2641.845249] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2641.845267] usb-storage: Bulk Command S 0x43425355 T 0x18dd L 8 F 128 Trg 0 LUN 0 CL 10
[ 2641.845273] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.845388] usb-storage: Status code 0; transferred 31/31
[ 2641.845394] usb-storage: -- transfer complete
[ 2641.845399] usb-storage: Bulk command transfer result=0
[ 2641.845406] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2641.845761] usb-storage: Status code 0; transferred 8/8
[ 2641.845768] usb-storage: -- transfer complete
[ 2641.845773] usb-storage: Bulk data transfer result 0x0
[ 2641.845778] usb-storage: Attempting to get CSW...
[ 2641.845784] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.846726] usb-storage: Status code 0; transferred 13/13
[ 2641.846733] usb-storage: -- transfer complete
[ 2641.846739] usb-storage: Bulk status result = 0
[ 2641.846746] usb-storage: Bulk Status S 0x53425355 T 0x18dd R 0 Stat 0x0
[ 2641.846754] usb-storage: scsi cmd done, result=0x0
[ 2641.846769] usb-storage: *** thread sleeping.
[ 2641.846844] usb-storage: queuecommand_lck called
[ 2641.846859] usb-storage: *** thread awakened.
[ 2641.846867] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2641.846871] usb-storage:  00 00 00 00 00 00
[ 2641.846887] usb-storage: Bulk Command S 0x43425355 T 0x18de L 0 F 0 Trg 0 LUN 0 CL 6
[ 2641.846894] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.847034] usb-storage: Status code 0; transferred 31/31
[ 2641.847039] usb-storage: -- transfer complete
[ 2641.847044] usb-storage: Bulk command transfer result=0
[ 2641.847049] usb-storage: Attempting to get CSW...
[ 2641.847055] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.848053] usb-storage: Status code 0; transferred 13/13
[ 2641.848061] usb-storage: -- transfer complete
[ 2641.848066] usb-storage: Bulk status result = 0
[ 2641.848073] usb-storage: Bulk Status S 0x53425355 T 0x18de R 0 Stat 0x1
[ 2641.848080] usb-storage: -- transport indicates command failure
[ 2641.848086] usb-storage: Issuing auto-REQUEST_SENSE
[ 2641.848097] usb-storage: Bulk Command S 0x43425355 T 0x18df L 96 F 128 Trg 0 LUN 0 CL 6
[ 2641.848104] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.848250] usb-storage: Status code 0; transferred 31/31
[ 2641.848257] usb-storage: -- transfer complete
[ 2641.848262] usb-storage: Bulk command transfer result=0
[ 2641.848269] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2641.849392] usb-storage: Status code -121; transferred 24/96
[ 2641.849399] usb-storage: -- short read transfer
[ 2641.849405] usb-storage: Bulk data transfer result 0x1
[ 2641.849410] usb-storage: Attempting to get CSW...
[ 2641.849416] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.849650] usb-storage: Status code -32; transferred 0/13
[ 2641.849657] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2641.849666] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2641.849758] usb-storage: usb_stor_clear_halt: result = 0
[ 2641.849764] usb-storage: Attempting to get CSW (2nd try)...
[ 2641.849770] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.849902] usb-storage: Status code 0; transferred 13/13
[ 2641.849908] usb-storage: -- transfer complete
[ 2641.849914] usb-storage: Bulk status result = 0
[ 2641.849921] usb-storage: Bulk Status S 0x53425355 T 0x18df R 72 Stat 0x0
[ 2641.849928] usb-storage: -- Result from auto-sense is 0
[ 2641.849935] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2641.849944] usb-storage: Not Ready: Medium not present - tray closed
[ 2641.849954] usb-storage: scsi cmd done, result=0x2
[ 2641.849966] usb-storage: *** thread sleeping.
[ 2641.850061] usb-storage: queuecommand_lck called
[ 2641.850076] usb-storage: *** thread awakened.
[ 2641.850084] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2641.850089] usb-storage:  1e 00 00 00 00 00
[ 2641.850105] usb-storage: Bulk Command S 0x43425355 T 0x18e0 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2641.850113] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.850299] usb-storage: Status code 0; transferred 31/31
[ 2641.850304] usb-storage: -- transfer complete
[ 2641.850310] usb-storage: Bulk command transfer result=0
[ 2641.850315] usb-storage: Attempting to get CSW...
[ 2641.850321] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.850894] usb-storage: Status code 0; transferred 13/13
[ 2641.850900] usb-storage: -- transfer complete
[ 2641.850906] usb-storage: Bulk status result = 0
[ 2641.850913] usb-storage: Bulk Status S 0x53425355 T 0x18e0 R 0 Stat 0x0
[ 2641.850920] usb-storage: scsi cmd done, result=0x0
[ 2641.850930] usb-storage: *** thread sleeping.
[ 2641.851028] usb-storage: queuecommand_lck called
[ 2641.851084] usb-storage: *** thread awakened.
[ 2641.851091] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2641.851095] usb-storage:  00 00 00 00 00 00
[ 2641.851108] usb-storage: Bulk Command S 0x43425355 T 0xa03 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2641.851114] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.851290] usb-storage: Status code 0; transferred 31/31
[ 2641.851296] usb-storage: -- transfer complete
[ 2641.851300] usb-storage: Bulk command transfer result=0
[ 2641.851304] usb-storage: Attempting to get CSW...
[ 2641.851310] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.851369] usb-storage: Status code 0; transferred 13/13
[ 2641.851375] usb-storage: -- transfer complete
[ 2641.851381] usb-storage: Bulk status result = 0
[ 2641.851388] usb-storage: Bulk Status S 0x53425355 T 0xa03 R 0 Stat 0x0
[ 2641.851394] usb-storage: scsi cmd done, result=0x0
[ 2641.851405] usb-storage: *** thread sleeping.
[ 2641.851477] usb-storage: queuecommand_lck called
[ 2641.851491] usb-storage: *** thread awakened.
[ 2641.851498] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2641.851503] usb-storage:  00 00 00 00 00 00
[ 2641.851519] usb-storage: Bulk Command S 0x43425355 T 0xa04 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2641.851526] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.851621] usb-storage: Status code 0; transferred 31/31
[ 2641.851627] usb-storage: -- transfer complete
[ 2641.851632] usb-storage: Bulk command transfer result=0
[ 2641.851638] usb-storage: Attempting to get CSW...
[ 2641.851644] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.851744] usb-storage: Status code 0; transferred 13/13
[ 2641.851749] usb-storage: -- transfer complete
[ 2641.851755] usb-storage: Bulk status result = 0
[ 2641.851762] usb-storage: Bulk Status S 0x53425355 T 0xa04 R 0 Stat 0x0
[ 2641.851769] usb-storage: scsi cmd done, result=0x0
[ 2641.851778] usb-storage: *** thread sleeping.
[ 2641.858232] usb-storage: queuecommand_lck called
[ 2641.858261] usb-storage: *** thread awakened.
[ 2641.858270] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2641.858274] usb-storage:  00 00 00 00 00 00
[ 2641.858292] usb-storage: Bulk Command S 0x43425355 T 0xa05 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2641.858300] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2641.858523] usb-storage: Status code 0; transferred 31/31
[ 2641.858530] usb-storage: -- transfer complete
[ 2641.858535] usb-storage: Bulk command transfer result=0
[ 2641.858540] usb-storage: Attempting to get CSW...
[ 2641.858546] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2641.858626] usb-storage: Status code 0; transferred 13/13
[ 2641.858632] usb-storage: -- transfer complete
[ 2641.858637] usb-storage: Bulk status result = 0
[ 2641.858644] usb-storage: Bulk Status S 0x53425355 T 0xa05 R 0 Stat 0x0
[ 2641.858654] usb-storage: scsi cmd done, result=0x0
[ 2641.858668] usb-storage: *** thread sleeping.
[ 2643.844565] usb-storage: queuecommand_lck called
[ 2643.844588] usb-storage: *** thread awakened.
[ 2643.844596] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2643.844601] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2643.844621] usb-storage: Bulk Command S 0x43425355 T 0x18e1 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2643.844629] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.844751] usb-storage: Status code 0; transferred 31/31
[ 2643.844757] usb-storage: -- transfer complete
[ 2643.844761] usb-storage: Bulk command transfer result=0
[ 2643.844768] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2643.845126] usb-storage: Status code 0; transferred 8/8
[ 2643.845134] usb-storage: -- transfer complete
[ 2643.845140] usb-storage: Bulk data transfer result 0x0
[ 2643.845145] usb-storage: Attempting to get CSW...
[ 2643.845151] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.845744] usb-storage: Status code 0; transferred 13/13
[ 2643.845749] usb-storage: -- transfer complete
[ 2643.845753] usb-storage: Bulk status result = 0
[ 2643.845758] usb-storage: Bulk Status S 0x53425355 T 0x18e1 R 0 Stat 0x0
[ 2643.845764] usb-storage: scsi cmd done, result=0x0
[ 2643.845773] usb-storage: *** thread sleeping.
[ 2643.845816] usb-storage: queuecommand_lck called
[ 2643.845830] usb-storage: *** thread awakened.
[ 2643.845836] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2643.845839] usb-storage:  00 00 00 00 00 00
[ 2643.845851] usb-storage: Bulk Command S 0x43425355 T 0x18e2 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2643.845856] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.845991] usb-storage: Status code 0; transferred 31/31
[ 2643.845995] usb-storage: -- transfer complete
[ 2643.845998] usb-storage: Bulk command transfer result=0
[ 2643.846013] usb-storage: Attempting to get CSW...
[ 2643.846020] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.847245] usb-storage: Status code 0; transferred 13/13
[ 2643.847250] usb-storage: -- transfer complete
[ 2643.847254] usb-storage: Bulk status result = 0
[ 2643.847259] usb-storage: Bulk Status S 0x53425355 T 0x18e2 R 0 Stat 0x1
[ 2643.847263] usb-storage: -- transport indicates command failure
[ 2643.847267] usb-storage: Issuing auto-REQUEST_SENSE
[ 2643.847274] usb-storage: Bulk Command S 0x43425355 T 0x18e3 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2643.847279] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.847365] usb-storage: Status code 0; transferred 31/31
[ 2643.847369] usb-storage: -- transfer complete
[ 2643.847373] usb-storage: Bulk command transfer result=0
[ 2643.847378] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2643.848559] usb-storage: Status code -121; transferred 24/96
[ 2643.848565] usb-storage: -- short read transfer
[ 2643.848570] usb-storage: Bulk data transfer result 0x1
[ 2643.848574] usb-storage: Attempting to get CSW...
[ 2643.848580] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.848750] usb-storage: Status code -32; transferred 0/13
[ 2643.848756] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2643.848764] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2643.848872] usb-storage: usb_stor_clear_halt: result = 0
[ 2643.848877] usb-storage: Attempting to get CSW (2nd try)...
[ 2643.848883] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.849002] usb-storage: Status code 0; transferred 13/13
[ 2643.849023] usb-storage: -- transfer complete
[ 2643.849028] usb-storage: Bulk status result = 0
[ 2643.849035] usb-storage: Bulk Status S 0x53425355 T 0x18e3 R 72 Stat 0x0
[ 2643.849042] usb-storage: -- Result from auto-sense is 0
[ 2643.849048] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2643.849056] usb-storage: Not Ready: Medium not present - tray closed
[ 2643.849065] usb-storage: scsi cmd done, result=0x2
[ 2643.849077] usb-storage: *** thread sleeping.
[ 2643.849169] usb-storage: queuecommand_lck called
[ 2643.849187] usb-storage: *** thread awakened.
[ 2643.849194] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2643.849200] usb-storage:  1e 00 00 00 00 00
[ 2643.849217] usb-storage: Bulk Command S 0x43425355 T 0x18e4 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2643.849224] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.849440] usb-storage: Status code 0; transferred 31/31
[ 2643.849446] usb-storage: -- transfer complete
[ 2643.849452] usb-storage: Bulk command transfer result=0
[ 2643.849457] usb-storage: Attempting to get CSW...
[ 2643.849463] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.850000] usb-storage: Status code 0; transferred 13/13
[ 2643.850018] usb-storage: -- transfer complete
[ 2643.850024] usb-storage: Bulk status result = 0
[ 2643.850031] usb-storage: Bulk Status S 0x53425355 T 0x18e4 R 0 Stat 0x0
[ 2643.850039] usb-storage: scsi cmd done, result=0x0
[ 2643.850051] usb-storage: *** thread sleeping.
[ 2643.850166] usb-storage: queuecommand_lck called
[ 2643.850184] usb-storage: *** thread awakened.
[ 2643.850192] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2643.850196] usb-storage:  00 00 00 00 00 00
[ 2643.850217] usb-storage: Bulk Command S 0x43425355 T 0xa06 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2643.850224] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.850372] usb-storage: Status code 0; transferred 31/31
[ 2643.850380] usb-storage: -- transfer complete
[ 2643.850386] usb-storage: Bulk command transfer result=0
[ 2643.850391] usb-storage: Attempting to get CSW...
[ 2643.850397] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.850494] usb-storage: Status code 0; transferred 13/13
[ 2643.850503] usb-storage: -- transfer complete
[ 2643.850508] usb-storage: Bulk status result = 0
[ 2643.850515] usb-storage: Bulk Status S 0x53425355 T 0xa06 R 0 Stat 0x0
[ 2643.850522] usb-storage: scsi cmd done, result=0x0
[ 2643.850531] usb-storage: *** thread sleeping.
[ 2643.850603] usb-storage: queuecommand_lck called
[ 2643.850619] usb-storage: *** thread awakened.
[ 2643.850626] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2643.850630] usb-storage:  00 00 00 00 00 00
[ 2643.850651] usb-storage: Bulk Command S 0x43425355 T 0xa07 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2643.850658] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2643.850745] usb-storage: Status code 0; transferred 31/31
[ 2643.850751] usb-storage: -- transfer complete
[ 2643.850756] usb-storage: Bulk command transfer result=0
[ 2643.850764] usb-storage: Attempting to get CSW...
[ 2643.850770] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2643.850868] usb-storage: Status code 0; transferred 13/13
[ 2643.850873] usb-storage: -- transfer complete
[ 2643.850878] usb-storage: Bulk status result = 0
[ 2643.850884] usb-storage: Bulk Status S 0x53425355 T 0xa07 R 0 Stat 0x0
[ 2643.850890] usb-storage: scsi cmd done, result=0x0
[ 2643.850898] usb-storage: *** thread sleeping.
[ 2645.843099] usb-storage: queuecommand_lck called
[ 2645.843122] usb-storage: *** thread awakened.
[ 2645.843128] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2645.843132] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2645.843149] usb-storage: Bulk Command S 0x43425355 T 0x18e5 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2645.843155] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.843250] usb-storage: Status code 0; transferred 31/31
[ 2645.843254] usb-storage: -- transfer complete
[ 2645.843258] usb-storage: Bulk command transfer result=0
[ 2645.843263] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2645.843742] usb-storage: Status code 0; transferred 8/8
[ 2645.843746] usb-storage: -- transfer complete
[ 2645.843750] usb-storage: Bulk data transfer result 0x0
[ 2645.843754] usb-storage: Attempting to get CSW...
[ 2645.843758] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.844747] usb-storage: Status code 0; transferred 13/13
[ 2645.844751] usb-storage: -- transfer complete
[ 2645.844755] usb-storage: Bulk status result = 0
[ 2645.844761] usb-storage: Bulk Status S 0x53425355 T 0x18e5 R 0 Stat 0x0
[ 2645.844766] usb-storage: scsi cmd done, result=0x0
[ 2645.844774] usb-storage: *** thread sleeping.
[ 2645.844812] usb-storage: queuecommand_lck called
[ 2645.844824] usb-storage: *** thread awakened.
[ 2645.844829] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2645.844832] usb-storage:  00 00 00 00 00 00
[ 2645.844844] usb-storage: Bulk Command S 0x43425355 T 0x18e6 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.844849] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.844991] usb-storage: Status code 0; transferred 31/31
[ 2645.844995] usb-storage: -- transfer complete
[ 2645.844999] usb-storage: Bulk command transfer result=0
[ 2645.845015] usb-storage: Attempting to get CSW...
[ 2645.845021] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.845872] usb-storage: Status code 0; transferred 13/13
[ 2645.845876] usb-storage: -- transfer complete
[ 2645.845880] usb-storage: Bulk status result = 0
[ 2645.845885] usb-storage: Bulk Status S 0x53425355 T 0x18e6 R 0 Stat 0x1
[ 2645.845889] usb-storage: -- transport indicates command failure
[ 2645.845893] usb-storage: Issuing auto-REQUEST_SENSE
[ 2645.845900] usb-storage: Bulk Command S 0x43425355 T 0x18e7 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2645.845905] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.845991] usb-storage: Status code 0; transferred 31/31
[ 2645.845995] usb-storage: -- transfer complete
[ 2645.845999] usb-storage: Bulk command transfer result=0
[ 2645.846016] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2645.847125] usb-storage: Status code -121; transferred 24/96
[ 2645.847130] usb-storage: -- short read transfer
[ 2645.847134] usb-storage: Bulk data transfer result 0x1
[ 2645.847137] usb-storage: Attempting to get CSW...
[ 2645.847142] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.847368] usb-storage: Status code -32; transferred 0/13
[ 2645.847372] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2645.847379] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2645.847492] usb-storage: usb_stor_clear_halt: result = 0
[ 2645.847496] usb-storage: Attempting to get CSW (2nd try)...
[ 2645.847500] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.847616] usb-storage: Status code 0; transferred 13/13
[ 2645.847619] usb-storage: -- transfer complete
[ 2645.847623] usb-storage: Bulk status result = 0
[ 2645.847628] usb-storage: Bulk Status S 0x53425355 T 0x18e7 R 72 Stat 0x0
[ 2645.847633] usb-storage: -- Result from auto-sense is 0
[ 2645.847638] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2645.847645] usb-storage: Not Ready: Medium not present - tray closed
[ 2645.847651] usb-storage: scsi cmd done, result=0x2
[ 2645.847658] usb-storage: *** thread sleeping.
[ 2645.847714] usb-storage: queuecommand_lck called
[ 2645.847729] usb-storage: *** thread awakened.
[ 2645.847734] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2645.847737] usb-storage:  1e 00 00 00 00 00
[ 2645.847749] usb-storage: Bulk Command S 0x43425355 T 0x18e8 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.847754] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.847868] usb-storage: Status code 0; transferred 31/31
[ 2645.847872] usb-storage: -- transfer complete
[ 2645.847875] usb-storage: Bulk command transfer result=0
[ 2645.847879] usb-storage: Attempting to get CSW...
[ 2645.847883] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.848371] usb-storage: Status code 0; transferred 13/13
[ 2645.848376] usb-storage: -- transfer complete
[ 2645.848380] usb-storage: Bulk status result = 0
[ 2645.848385] usb-storage: Bulk Status S 0x53425355 T 0x18e8 R 0 Stat 0x0
[ 2645.848390] usb-storage: scsi cmd done, result=0x0
[ 2645.848396] usb-storage: *** thread sleeping.
[ 2645.848473] usb-storage: queuecommand_lck called
[ 2645.848489] usb-storage: *** thread awakened.
[ 2645.848496] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2645.848501] usb-storage:  00 00 00 00 00 00
[ 2645.848517] usb-storage: Bulk Command S 0x43425355 T 0xa08 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.848525] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.848629] usb-storage: Status code 0; transferred 31/31
[ 2645.848635] usb-storage: -- transfer complete
[ 2645.848640] usb-storage: Bulk command transfer result=0
[ 2645.848646] usb-storage: Attempting to get CSW...
[ 2645.848652] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.848748] usb-storage: Status code 0; transferred 13/13
[ 2645.848754] usb-storage: -- transfer complete
[ 2645.848759] usb-storage: Bulk status result = 0
[ 2645.848766] usb-storage: Bulk Status S 0x53425355 T 0xa08 R 0 Stat 0x0
[ 2645.848773] usb-storage: scsi cmd done, result=0x0
[ 2645.848783] usb-storage: *** thread sleeping.
[ 2645.848854] usb-storage: queuecommand_lck called
[ 2645.848868] usb-storage: *** thread awakened.
[ 2645.848874] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2645.848879] usb-storage:  00 00 00 00 00 00
[ 2645.848895] usb-storage: Bulk Command S 0x43425355 T 0xa09 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.848902] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.849021] usb-storage: Status code 0; transferred 31/31
[ 2645.849026] usb-storage: -- transfer complete
[ 2645.849031] usb-storage: Bulk command transfer result=0
[ 2645.849036] usb-storage: Attempting to get CSW...
[ 2645.849041] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.849120] usb-storage: Status code 0; transferred 13/13
[ 2645.849124] usb-storage: -- transfer complete
[ 2645.849127] usb-storage: Bulk status result = 0
[ 2645.849132] usb-storage: Bulk Status S 0x53425355 T 0xa09 R 0 Stat 0x0
[ 2645.849137] usb-storage: scsi cmd done, result=0x0
[ 2645.849144] usb-storage: *** thread sleeping.
[ 2645.856098] usb-storage: queuecommand_lck called
[ 2645.856116] usb-storage: *** thread awakened.
[ 2645.856123] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2645.856126] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2645.856143] usb-storage: Bulk Command S 0x43425355 T 0x18e9 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2645.856149] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.856249] usb-storage: Status code 0; transferred 31/31
[ 2645.856253] usb-storage: -- transfer complete
[ 2645.856256] usb-storage: Bulk command transfer result=0
[ 2645.856261] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2645.856744] usb-storage: Status code 0; transferred 8/8
[ 2645.856748] usb-storage: -- transfer complete
[ 2645.856752] usb-storage: Bulk data transfer result 0x0
[ 2645.856755] usb-storage: Attempting to get CSW...
[ 2645.856760] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.857249] usb-storage: Status code 0; transferred 13/13
[ 2645.857253] usb-storage: -- transfer complete
[ 2645.857257] usb-storage: Bulk status result = 0
[ 2645.857262] usb-storage: Bulk Status S 0x53425355 T 0x18e9 R 0 Stat 0x0
[ 2645.857268] usb-storage: scsi cmd done, result=0x0
[ 2645.857275] usb-storage: *** thread sleeping.
[ 2645.857310] usb-storage: queuecommand_lck called
[ 2645.857322] usb-storage: *** thread awakened.
[ 2645.857329] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2645.857333] usb-storage:  00 00 00 00 00 00
[ 2645.857353] usb-storage: Bulk Command S 0x43425355 T 0x18ea L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.857361] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.857508] usb-storage: Status code 0; transferred 31/31
[ 2645.857517] usb-storage: -- transfer complete
[ 2645.857523] usb-storage: Bulk command transfer result=0
[ 2645.857528] usb-storage: Attempting to get CSW...
[ 2645.857534] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.858497] usb-storage: Status code 0; transferred 13/13
[ 2645.858501] usb-storage: -- transfer complete
[ 2645.858505] usb-storage: Bulk status result = 0
[ 2645.858510] usb-storage: Bulk Status S 0x53425355 T 0x18ea R 0 Stat 0x1
[ 2645.858515] usb-storage: -- transport indicates command failure
[ 2645.858519] usb-storage: Issuing auto-REQUEST_SENSE
[ 2645.858526] usb-storage: Bulk Command S 0x43425355 T 0x18eb L 96 F 128 Trg 0 LUN 0 CL 6
[ 2645.858531] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.858616] usb-storage: Status code 0; transferred 31/31
[ 2645.858620] usb-storage: -- transfer complete
[ 2645.858624] usb-storage: Bulk command transfer result=0
[ 2645.858629] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2645.859749] usb-storage: Status code -121; transferred 24/96
[ 2645.859754] usb-storage: -- short read transfer
[ 2645.859758] usb-storage: Bulk data transfer result 0x1
[ 2645.859762] usb-storage: Attempting to get CSW...
[ 2645.859767] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.860025] usb-storage: Status code -32; transferred 0/13
[ 2645.860033] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2645.860041] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2645.860128] usb-storage: usb_stor_clear_halt: result = 0
[ 2645.860134] usb-storage: Attempting to get CSW (2nd try)...
[ 2645.860141] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.860248] usb-storage: Status code 0; transferred 13/13
[ 2645.860253] usb-storage: -- transfer complete
[ 2645.860258] usb-storage: Bulk status result = 0
[ 2645.860265] usb-storage: Bulk Status S 0x53425355 T 0x18eb R 72 Stat 0x0
[ 2645.860271] usb-storage: -- Result from auto-sense is 0
[ 2645.860276] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2645.860283] usb-storage: Not Ready: Medium not present - tray closed
[ 2645.860290] usb-storage: scsi cmd done, result=0x2
[ 2645.860300] usb-storage: *** thread sleeping.
[ 2645.860378] usb-storage: queuecommand_lck called
[ 2645.860392] usb-storage: *** thread awakened.
[ 2645.860399] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2645.860404] usb-storage:  00 00 00 00 00 00
[ 2645.860420] usb-storage: Bulk Command S 0x43425355 T 0x18ec L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.860428] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.860499] usb-storage: Status code 0; transferred 31/31
[ 2645.860503] usb-storage: -- transfer complete
[ 2645.860507] usb-storage: Bulk command transfer result=0
[ 2645.860511] usb-storage: Attempting to get CSW...
[ 2645.860515] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.861497] usb-storage: Status code 0; transferred 13/13
[ 2645.861502] usb-storage: -- transfer complete
[ 2645.861506] usb-storage: Bulk status result = 0
[ 2645.861511] usb-storage: Bulk Status S 0x53425355 T 0x18ec R 0 Stat 0x1
[ 2645.861515] usb-storage: -- transport indicates command failure
[ 2645.861519] usb-storage: Issuing auto-REQUEST_SENSE
[ 2645.861526] usb-storage: Bulk Command S 0x43425355 T 0x18ed L 96 F 128 Trg 0 LUN 0 CL 6
[ 2645.861531] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.861616] usb-storage: Status code 0; transferred 31/31
[ 2645.861620] usb-storage: -- transfer complete
[ 2645.861624] usb-storage: Bulk command transfer result=0
[ 2645.861629] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2645.862874] usb-storage: Status code -121; transferred 24/96
[ 2645.862879] usb-storage: -- short read transfer
[ 2645.862883] usb-storage: Bulk data transfer result 0x1
[ 2645.862886] usb-storage: Attempting to get CSW...
[ 2645.862891] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.863121] usb-storage: Status code -32; transferred 0/13
[ 2645.863128] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2645.863140] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2645.863247] usb-storage: usb_stor_clear_halt: result = 0
[ 2645.863253] usb-storage: Attempting to get CSW (2nd try)...
[ 2645.863260] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.863373] usb-storage: Status code 0; transferred 13/13
[ 2645.863382] usb-storage: -- transfer complete
[ 2645.863387] usb-storage: Bulk status result = 0
[ 2645.863394] usb-storage: Bulk Status S 0x53425355 T 0x18ed R 72 Stat 0x0
[ 2645.863400] usb-storage: -- Result from auto-sense is 0
[ 2645.863407] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2645.863414] usb-storage: Not Ready: Medium not present - tray closed
[ 2645.863422] usb-storage: scsi cmd done, result=0x2
[ 2645.863432] usb-storage: *** thread sleeping.
[ 2645.863477] usb-storage: queuecommand_lck called
[ 2645.863491] usb-storage: *** thread awakened.
[ 2645.863498] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2645.863504] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2645.863524] usb-storage: Bulk Command S 0x43425355 T 0x18ee L 8 F 128 Trg 0 LUN 0 CL 10
[ 2645.863531] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.863624] usb-storage: Status code 0; transferred 31/31
[ 2645.863629] usb-storage: -- transfer complete
[ 2645.863635] usb-storage: Bulk command transfer result=0
[ 2645.863641] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2645.864003] usb-storage: Status code 0; transferred 8/8
[ 2645.864016] usb-storage: -- transfer complete
[ 2645.864021] usb-storage: Bulk data transfer result 0x0
[ 2645.864026] usb-storage: Attempting to get CSW...
[ 2645.864032] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.864892] usb-storage: Status code 0; transferred 13/13
[ 2645.864899] usb-storage: -- transfer complete
[ 2645.864904] usb-storage: Bulk status result = 0
[ 2645.864911] usb-storage: Bulk Status S 0x53425355 T 0x18ee R 0 Stat 0x0
[ 2645.864918] usb-storage: scsi cmd done, result=0x0
[ 2645.864931] usb-storage: *** thread sleeping.
[ 2645.864995] usb-storage: queuecommand_lck called
[ 2645.865024] usb-storage: *** thread awakened.
[ 2645.865032] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2645.865037] usb-storage:  1e 00 00 00 00 00
[ 2645.865054] usb-storage: Bulk Command S 0x43425355 T 0x18ef L 0 F 0 Trg 0 LUN 0 CL 6
[ 2645.865061] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2645.865128] usb-storage: Status code 0; transferred 31/31
[ 2645.865133] usb-storage: -- transfer complete
[ 2645.865139] usb-storage: Bulk command transfer result=0
[ 2645.865144] usb-storage: Attempting to get CSW...
[ 2645.865149] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2645.865752] usb-storage: Status code 0; transferred 13/13
[ 2645.865757] usb-storage: -- transfer complete
[ 2645.865761] usb-storage: Bulk status result = 0
[ 2645.865767] usb-storage: Bulk Status S 0x53425355 T 0x18ef R 0 Stat 0x0
[ 2645.865773] usb-storage: scsi cmd done, result=0x0
[ 2645.865781] usb-storage: *** thread sleeping.
[ 2647.845095] usb-storage: queuecommand_lck called
[ 2647.845117] usb-storage: *** thread awakened.
[ 2647.845123] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2647.845127] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2647.845144] usb-storage: Bulk Command S 0x43425355 T 0x18f0 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2647.845149] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.845251] usb-storage: Status code 0; transferred 31/31
[ 2647.845255] usb-storage: -- transfer complete
[ 2647.845259] usb-storage: Bulk command transfer result=0
[ 2647.845264] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2647.845619] usb-storage: Status code 0; transferred 8/8
[ 2647.845623] usb-storage: -- transfer complete
[ 2647.845626] usb-storage: Bulk data transfer result 0x0
[ 2647.845630] usb-storage: Attempting to get CSW...
[ 2647.845634] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.846378] usb-storage: Status code 0; transferred 13/13
[ 2647.846387] usb-storage: -- transfer complete
[ 2647.846393] usb-storage: Bulk status result = 0
[ 2647.846400] usb-storage: Bulk Status S 0x53425355 T 0x18f0 R 0 Stat 0x0
[ 2647.846407] usb-storage: scsi cmd done, result=0x0
[ 2647.846417] usb-storage: *** thread sleeping.
[ 2647.846462] usb-storage: queuecommand_lck called
[ 2647.846476] usb-storage: *** thread awakened.
[ 2647.846482] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2647.846487] usb-storage:  00 00 00 00 00 00
[ 2647.846503] usb-storage: Bulk Command S 0x43425355 T 0x18f1 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2647.846510] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.846624] usb-storage: Status code 0; transferred 31/31
[ 2647.846630] usb-storage: -- transfer complete
[ 2647.846639] usb-storage: Bulk command transfer result=0
[ 2647.846644] usb-storage: Attempting to get CSW...
[ 2647.846650] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.848123] usb-storage: Status code 0; transferred 13/13
[ 2647.848127] usb-storage: -- transfer complete
[ 2647.848131] usb-storage: Bulk status result = 0
[ 2647.848136] usb-storage: Bulk Status S 0x53425355 T 0x18f1 R 0 Stat 0x1
[ 2647.848141] usb-storage: -- transport indicates command failure
[ 2647.848145] usb-storage: Issuing auto-REQUEST_SENSE
[ 2647.848151] usb-storage: Bulk Command S 0x43425355 T 0x18f2 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2647.848157] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.848242] usb-storage: Status code 0; transferred 31/31
[ 2647.848246] usb-storage: -- transfer complete
[ 2647.848250] usb-storage: Bulk command transfer result=0
[ 2647.848255] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2647.849767] usb-storage: Status code -121; transferred 24/96
[ 2647.849773] usb-storage: -- short read transfer
[ 2647.849778] usb-storage: Bulk data transfer result 0x1
[ 2647.849782] usb-storage: Attempting to get CSW...
[ 2647.849787] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.849994] usb-storage: Status code -32; transferred 0/13
[ 2647.849999] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2647.850021] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2647.850130] usb-storage: usb_stor_clear_halt: result = 0
[ 2647.850136] usb-storage: Attempting to get CSW (2nd try)...
[ 2647.850142] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.850258] usb-storage: Status code 0; transferred 13/13
[ 2647.850263] usb-storage: -- transfer complete
[ 2647.850269] usb-storage: Bulk status result = 0
[ 2647.850276] usb-storage: Bulk Status S 0x53425355 T 0x18f2 R 72 Stat 0x0
[ 2647.850283] usb-storage: -- Result from auto-sense is 0
[ 2647.850290] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2647.850300] usb-storage: Not Ready: Medium not present - tray closed
[ 2647.850309] usb-storage: scsi cmd done, result=0x2
[ 2647.850319] usb-storage: *** thread sleeping.
[ 2647.850430] usb-storage: queuecommand_lck called
[ 2647.850446] usb-storage: *** thread awakened.
[ 2647.850453] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2647.850458] usb-storage:  1e 00 00 00 00 00
[ 2647.850478] usb-storage: Bulk Command S 0x43425355 T 0x18f3 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2647.850486] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.850632] usb-storage: Status code 0; transferred 31/31
[ 2647.850637] usb-storage: -- transfer complete
[ 2647.850643] usb-storage: Bulk command transfer result=0
[ 2647.850648] usb-storage: Attempting to get CSW...
[ 2647.850654] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.851248] usb-storage: Status code 0; transferred 13/13
[ 2647.851252] usb-storage: -- transfer complete
[ 2647.851256] usb-storage: Bulk status result = 0
[ 2647.851261] usb-storage: Bulk Status S 0x53425355 T 0x18f3 R 0 Stat 0x0
[ 2647.851266] usb-storage: scsi cmd done, result=0x0
[ 2647.851273] usb-storage: *** thread sleeping.
[ 2647.851347] usb-storage: queuecommand_lck called
[ 2647.851362] usb-storage: *** thread awakened.
[ 2647.851367] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2647.851371] usb-storage:  00 00 00 00 00 00
[ 2647.851383] usb-storage: Bulk Command S 0x43425355 T 0xa0a L 0 F 0 Trg 0 LUN 0 CL 6
[ 2647.851388] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.851494] usb-storage: Status code 0; transferred 31/31
[ 2647.851498] usb-storage: -- transfer complete
[ 2647.851501] usb-storage: Bulk command transfer result=0
[ 2647.851505] usb-storage: Attempting to get CSW...
[ 2647.851509] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.851617] usb-storage: Status code 0; transferred 13/13
[ 2647.851620] usb-storage: -- transfer complete
[ 2647.851624] usb-storage: Bulk status result = 0
[ 2647.851629] usb-storage: Bulk Status S 0x53425355 T 0xa0a R 0 Stat 0x0
[ 2647.851634] usb-storage: scsi cmd done, result=0x0
[ 2647.851640] usb-storage: *** thread sleeping.
[ 2647.851697] usb-storage: queuecommand_lck called
[ 2647.851709] usb-storage: *** thread awakened.
[ 2647.851713] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2647.851717] usb-storage:  00 00 00 00 00 00
[ 2647.851728] usb-storage: Bulk Command S 0x43425355 T 0xa0b L 0 F 0 Trg 0 LUN 0 CL 6
[ 2647.851733] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2647.851869] usb-storage: Status code 0; transferred 31/31
[ 2647.851873] usb-storage: -- transfer complete
[ 2647.851876] usb-storage: Bulk command transfer result=0
[ 2647.851880] usb-storage: Attempting to get CSW...
[ 2647.851884] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2647.851991] usb-storage: Status code 0; transferred 13/13
[ 2647.851995] usb-storage: -- transfer complete
[ 2647.851999] usb-storage: Bulk status result = 0
[ 2647.852019] usb-storage: Bulk Status S 0x53425355 T 0xa0b R 0 Stat 0x0
[ 2647.852025] usb-storage: scsi cmd done, result=0x0
[ 2647.852033] usb-storage: *** thread sleeping.
[ 2649.845107] usb-storage: queuecommand_lck called
[ 2649.845128] usb-storage: *** thread awakened.
[ 2649.845134] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2649.845138] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2649.845155] usb-storage: Bulk Command S 0x43425355 T 0x18f4 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2649.845160] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.845261] usb-storage: Status code 0; transferred 31/31
[ 2649.845266] usb-storage: -- transfer complete
[ 2649.845272] usb-storage: Bulk command transfer result=0
[ 2649.845278] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2649.845629] usb-storage: Status code 0; transferred 8/8
[ 2649.845634] usb-storage: -- transfer complete
[ 2649.845638] usb-storage: Bulk data transfer result 0x0
[ 2649.845642] usb-storage: Attempting to get CSW...
[ 2649.845646] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.846510] usb-storage: Status code 0; transferred 13/13
[ 2649.846516] usb-storage: -- transfer complete
[ 2649.846522] usb-storage: Bulk status result = 0
[ 2649.846529] usb-storage: Bulk Status S 0x53425355 T 0x18f4 R 0 Stat 0x0
[ 2649.846535] usb-storage: scsi cmd done, result=0x0
[ 2649.846544] usb-storage: *** thread sleeping.
[ 2649.846587] usb-storage: queuecommand_lck called
[ 2649.846598] usb-storage: *** thread awakened.
[ 2649.846604] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2649.846607] usb-storage:  00 00 00 00 00 00
[ 2649.846619] usb-storage: Bulk Command S 0x43425355 T 0x18f5 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2649.846624] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.846744] usb-storage: Status code 0; transferred 31/31
[ 2649.846748] usb-storage: -- transfer complete
[ 2649.846752] usb-storage: Bulk command transfer result=0
[ 2649.846755] usb-storage: Attempting to get CSW...
[ 2649.846760] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.847748] usb-storage: Status code 0; transferred 13/13
[ 2649.847753] usb-storage: -- transfer complete
[ 2649.847757] usb-storage: Bulk status result = 0
[ 2649.847762] usb-storage: Bulk Status S 0x53425355 T 0x18f5 R 0 Stat 0x1
[ 2649.847766] usb-storage: -- transport indicates command failure
[ 2649.847770] usb-storage: Issuing auto-REQUEST_SENSE
[ 2649.847777] usb-storage: Bulk Command S 0x43425355 T 0x18f6 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2649.847782] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.847868] usb-storage: Status code 0; transferred 31/31
[ 2649.847872] usb-storage: -- transfer complete
[ 2649.847876] usb-storage: Bulk command transfer result=0
[ 2649.847881] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2649.849503] usb-storage: Status code -121; transferred 24/96
[ 2649.849507] usb-storage: -- short read transfer
[ 2649.849511] usb-storage: Bulk data transfer result 0x1
[ 2649.849515] usb-storage: Attempting to get CSW...
[ 2649.849519] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.849745] usb-storage: Status code -32; transferred 0/13
[ 2649.849750] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2649.849756] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2649.849870] usb-storage: usb_stor_clear_halt: result = 0
[ 2649.849874] usb-storage: Attempting to get CSW (2nd try)...
[ 2649.849879] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.849993] usb-storage: Status code 0; transferred 13/13
[ 2649.849997] usb-storage: -- transfer complete
[ 2649.850014] usb-storage: Bulk status result = 0
[ 2649.850021] usb-storage: Bulk Status S 0x53425355 T 0x18f6 R 72 Stat 0x0
[ 2649.850027] usb-storage: -- Result from auto-sense is 0
[ 2649.850033] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2649.850042] usb-storage: Not Ready: Medium not present - tray closed
[ 2649.850049] usb-storage: scsi cmd done, result=0x2
[ 2649.850059] usb-storage: *** thread sleeping.
[ 2649.850121] usb-storage: queuecommand_lck called
[ 2649.850134] usb-storage: *** thread awakened.
[ 2649.850140] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2649.850145] usb-storage:  1e 00 00 00 00 00
[ 2649.850160] usb-storage: Bulk Command S 0x43425355 T 0x18f7 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2649.850166] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.850262] usb-storage: Status code 0; transferred 31/31
[ 2649.850268] usb-storage: -- transfer complete
[ 2649.850273] usb-storage: Bulk command transfer result=0
[ 2649.850279] usb-storage: Attempting to get CSW...
[ 2649.850285] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.851250] usb-storage: Status code 0; transferred 13/13
[ 2649.851255] usb-storage: -- transfer complete
[ 2649.851258] usb-storage: Bulk status result = 0
[ 2649.851264] usb-storage: Bulk Status S 0x53425355 T 0x18f7 R 0 Stat 0x0
[ 2649.851268] usb-storage: scsi cmd done, result=0x0
[ 2649.851276] usb-storage: *** thread sleeping.
[ 2649.851351] usb-storage: queuecommand_lck called
[ 2649.851365] usb-storage: *** thread awakened.
[ 2649.851371] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2649.851374] usb-storage:  00 00 00 00 00 00
[ 2649.851386] usb-storage: Bulk Command S 0x43425355 T 0xa0c L 0 F 0 Trg 0 LUN 0 CL 6
[ 2649.851391] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.851494] usb-storage: Status code 0; transferred 31/31
[ 2649.851498] usb-storage: -- transfer complete
[ 2649.851502] usb-storage: Bulk command transfer result=0
[ 2649.851506] usb-storage: Attempting to get CSW...
[ 2649.851510] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.851618] usb-storage: Status code 0; transferred 13/13
[ 2649.851621] usb-storage: -- transfer complete
[ 2649.851625] usb-storage: Bulk status result = 0
[ 2649.851630] usb-storage: Bulk Status S 0x53425355 T 0xa0c R 0 Stat 0x0
[ 2649.851635] usb-storage: scsi cmd done, result=0x0
[ 2649.851641] usb-storage: *** thread sleeping.
[ 2649.851696] usb-storage: queuecommand_lck called
[ 2649.851707] usb-storage: *** thread awakened.
[ 2649.851712] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2649.851715] usb-storage:  00 00 00 00 00 00
[ 2649.851727] usb-storage: Bulk Command S 0x43425355 T 0xa0d L 0 F 0 Trg 0 LUN 0 CL 6
[ 2649.851732] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2649.851869] usb-storage: Status code 0; transferred 31/31
[ 2649.851873] usb-storage: -- transfer complete
[ 2649.851877] usb-storage: Bulk command transfer result=0
[ 2649.851881] usb-storage: Attempting to get CSW...
[ 2649.851885] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2649.851993] usb-storage: Status code 0; transferred 13/13
[ 2649.851997] usb-storage: -- transfer complete
[ 2649.852000] usb-storage: Bulk status result = 0
[ 2649.852017] usb-storage: Bulk Status S 0x53425355 T 0xa0d R 0 Stat 0x0
[ 2649.852024] usb-storage: scsi cmd done, result=0x0
[ 2649.852032] usb-storage: *** thread sleeping.
[ 2651.845185] usb-storage: queuecommand_lck called
[ 2651.845205] usb-storage: *** thread awakened.
[ 2651.845213] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2651.845218] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2651.845238] usb-storage: Bulk Command S 0x43425355 T 0x18f8 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2651.845245] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.845384] usb-storage: Status code 0; transferred 31/31
[ 2651.845388] usb-storage: -- transfer complete
[ 2651.845392] usb-storage: Bulk command transfer result=0
[ 2651.845397] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2651.845746] usb-storage: Status code 0; transferred 8/8
[ 2651.845750] usb-storage: -- transfer complete
[ 2651.845754] usb-storage: Bulk data transfer result 0x0
[ 2651.845757] usb-storage: Attempting to get CSW...
[ 2651.845762] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.846503] usb-storage: Status code 0; transferred 13/13
[ 2651.846509] usb-storage: -- transfer complete
[ 2651.846514] usb-storage: Bulk status result = 0
[ 2651.846521] usb-storage: Bulk Status S 0x53425355 T 0x18f8 R 0 Stat 0x0
[ 2651.846527] usb-storage: scsi cmd done, result=0x0
[ 2651.846536] usb-storage: *** thread sleeping.
[ 2651.846577] usb-storage: queuecommand_lck called
[ 2651.846592] usb-storage: *** thread awakened.
[ 2651.846599] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2651.846603] usb-storage:  00 00 00 00 00 00
[ 2651.846618] usb-storage: Bulk Command S 0x43425355 T 0x18f9 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2651.846625] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.846748] usb-storage: Status code 0; transferred 31/31
[ 2651.846757] usb-storage: -- transfer complete
[ 2651.846763] usb-storage: Bulk command transfer result=0
[ 2651.846768] usb-storage: Attempting to get CSW...
[ 2651.846774] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.847749] usb-storage: Status code 0; transferred 13/13
[ 2651.847754] usb-storage: -- transfer complete
[ 2651.847758] usb-storage: Bulk status result = 0
[ 2651.847763] usb-storage: Bulk Status S 0x53425355 T 0x18f9 R 0 Stat 0x1
[ 2651.847767] usb-storage: -- transport indicates command failure
[ 2651.847771] usb-storage: Issuing auto-REQUEST_SENSE
[ 2651.847778] usb-storage: Bulk Command S 0x43425355 T 0x18fa L 96 F 128 Trg 0 LUN 0 CL 6
[ 2651.847783] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.847870] usb-storage: Status code 0; transferred 31/31
[ 2651.847873] usb-storage: -- transfer complete
[ 2651.847877] usb-storage: Bulk command transfer result=0
[ 2651.847882] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2651.849504] usb-storage: Status code -121; transferred 24/96
[ 2651.849508] usb-storage: -- short read transfer
[ 2651.849512] usb-storage: Bulk data transfer result 0x1
[ 2651.849516] usb-storage: Attempting to get CSW...
[ 2651.849520] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.849746] usb-storage: Status code -32; transferred 0/13
[ 2651.849751] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2651.849757] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2651.849871] usb-storage: usb_stor_clear_halt: result = 0
[ 2651.849875] usb-storage: Attempting to get CSW (2nd try)...
[ 2651.849880] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.849994] usb-storage: Status code 0; transferred 13/13
[ 2651.849998] usb-storage: -- transfer complete
[ 2651.850015] usb-storage: Bulk status result = 0
[ 2651.850022] usb-storage: Bulk Status S 0x53425355 T 0x18fa R 72 Stat 0x0
[ 2651.850028] usb-storage: -- Result from auto-sense is 0
[ 2651.850034] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2651.850043] usb-storage: Not Ready: Medium not present - tray closed
[ 2651.850050] usb-storage: scsi cmd done, result=0x2
[ 2651.850059] usb-storage: *** thread sleeping.
[ 2651.850119] usb-storage: queuecommand_lck called
[ 2651.850132] usb-storage: *** thread awakened.
[ 2651.850138] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2651.850143] usb-storage:  1e 00 00 00 00 00
[ 2651.850158] usb-storage: Bulk Command S 0x43425355 T 0x18fb L 0 F 0 Trg 0 LUN 0 CL 6
[ 2651.850164] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.850266] usb-storage: Status code 0; transferred 31/31
[ 2651.850272] usb-storage: -- transfer complete
[ 2651.850278] usb-storage: Bulk command transfer result=0
[ 2651.850283] usb-storage: Attempting to get CSW...
[ 2651.850289] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.850881] usb-storage: Status code 0; transferred 13/13
[ 2651.850887] usb-storage: -- transfer complete
[ 2651.850893] usb-storage: Bulk status result = 0
[ 2651.850900] usb-storage: Bulk Status S 0x53425355 T 0x18fb R 0 Stat 0x0
[ 2651.850907] usb-storage: scsi cmd done, result=0x0
[ 2651.850916] usb-storage: *** thread sleeping.
[ 2651.850996] usb-storage: queuecommand_lck called
[ 2651.851022] usb-storage: *** thread awakened.
[ 2651.851029] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2651.851034] usb-storage:  00 00 00 00 00 00
[ 2651.851051] usb-storage: Bulk Command S 0x43425355 T 0xa0e L 0 F 0 Trg 0 LUN 0 CL 6
[ 2651.851058] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.851137] usb-storage: Status code 0; transferred 31/31
[ 2651.851143] usb-storage: -- transfer complete
[ 2651.851149] usb-storage: Bulk command transfer result=0
[ 2651.851154] usb-storage: Attempting to get CSW...
[ 2651.851160] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.851258] usb-storage: Status code 0; transferred 13/13
[ 2651.851263] usb-storage: -- transfer complete
[ 2651.851268] usb-storage: Bulk status result = 0
[ 2651.851274] usb-storage: Bulk Status S 0x53425355 T 0xa0e R 0 Stat 0x0
[ 2651.851280] usb-storage: scsi cmd done, result=0x0
[ 2651.851289] usb-storage: *** thread sleeping.
[ 2651.851355] usb-storage: queuecommand_lck called
[ 2651.851369] usb-storage: *** thread awakened.
[ 2651.851376] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2651.851381] usb-storage:  00 00 00 00 00 00
[ 2651.851397] usb-storage: Bulk Command S 0x43425355 T 0xa0f L 0 F 0 Trg 0 LUN 0 CL 6
[ 2651.851404] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2651.851508] usb-storage: Status code 0; transferred 31/31
[ 2651.851514] usb-storage: -- transfer complete
[ 2651.851520] usb-storage: Bulk command transfer result=0
[ 2651.851525] usb-storage: Attempting to get CSW...
[ 2651.851530] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2651.851631] usb-storage: Status code 0; transferred 13/13
[ 2651.851637] usb-storage: -- transfer complete
[ 2651.851643] usb-storage: Bulk status result = 0
[ 2651.851650] usb-storage: Bulk Status S 0x53425355 T 0xa0f R 0 Stat 0x0
[ 2651.851656] usb-storage: scsi cmd done, result=0x0
[ 2651.851665] usb-storage: *** thread sleeping.
[ 2653.845822] usb-storage: queuecommand_lck called
[ 2653.845843] usb-storage: *** thread awakened.
[ 2653.845849] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2653.845853] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2653.845870] usb-storage: Bulk Command S 0x43425355 T 0x18fc L 8 F 128 Trg 0 LUN 0 CL 10
[ 2653.845876] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.846021] usb-storage: Status code 0; transferred 31/31
[ 2653.846026] usb-storage: -- transfer complete
[ 2653.846031] usb-storage: Bulk command transfer result=0
[ 2653.846037] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2653.846376] usb-storage: Status code 0; transferred 8/8
[ 2653.846385] usb-storage: -- transfer complete
[ 2653.846390] usb-storage: Bulk data transfer result 0x0
[ 2653.846394] usb-storage: Attempting to get CSW...
[ 2653.846398] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.846999] usb-storage: Status code 0; transferred 13/13
[ 2653.847016] usb-storage: -- transfer complete
[ 2653.847021] usb-storage: Bulk status result = 0
[ 2653.847028] usb-storage: Bulk Status S 0x53425355 T 0x18fc R 0 Stat 0x0
[ 2653.847034] usb-storage: scsi cmd done, result=0x0
[ 2653.847043] usb-storage: *** thread sleeping.
[ 2653.847092] usb-storage: queuecommand_lck called
[ 2653.847106] usb-storage: *** thread awakened.
[ 2653.847113] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2653.847118] usb-storage:  00 00 00 00 00 00
[ 2653.847134] usb-storage: Bulk Command S 0x43425355 T 0x18fd L 0 F 0 Trg 0 LUN 0 CL 6
[ 2653.847141] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.847256] usb-storage: Status code 0; transferred 31/31
[ 2653.847262] usb-storage: -- transfer complete
[ 2653.847267] usb-storage: Bulk command transfer result=0
[ 2653.847273] usb-storage: Attempting to get CSW...
[ 2653.847279] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.848250] usb-storage: Status code 0; transferred 13/13
[ 2653.848255] usb-storage: -- transfer complete
[ 2653.848259] usb-storage: Bulk status result = 0
[ 2653.848264] usb-storage: Bulk Status S 0x53425355 T 0x18fd R 0 Stat 0x1
[ 2653.848268] usb-storage: -- transport indicates command failure
[ 2653.848272] usb-storage: Issuing auto-REQUEST_SENSE
[ 2653.848279] usb-storage: Bulk Command S 0x43425355 T 0x18fe L 96 F 128 Trg 0 LUN 0 CL 6
[ 2653.848284] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.848371] usb-storage: Status code 0; transferred 31/31
[ 2653.848375] usb-storage: -- transfer complete
[ 2653.848378] usb-storage: Bulk command transfer result=0
[ 2653.848383] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2653.850012] usb-storage: Status code -121; transferred 24/96
[ 2653.850017] usb-storage: -- short read transfer
[ 2653.850021] usb-storage: Bulk data transfer result 0x1
[ 2653.850025] usb-storage: Attempting to get CSW...
[ 2653.850029] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.850248] usb-storage: Status code -32; transferred 0/13
[ 2653.850253] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2653.850259] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2653.850372] usb-storage: usb_stor_clear_halt: result = 0
[ 2653.850376] usb-storage: Attempting to get CSW (2nd try)...
[ 2653.850381] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.850495] usb-storage: Status code 0; transferred 13/13
[ 2653.850499] usb-storage: -- transfer complete
[ 2653.850503] usb-storage: Bulk status result = 0
[ 2653.850508] usb-storage: Bulk Status S 0x53425355 T 0x18fe R 72 Stat 0x0
[ 2653.850513] usb-storage: -- Result from auto-sense is 0
[ 2653.850518] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2653.850524] usb-storage: Not Ready: Medium not present - tray closed
[ 2653.850531] usb-storage: scsi cmd done, result=0x2
[ 2653.850538] usb-storage: *** thread sleeping.
[ 2653.850594] usb-storage: queuecommand_lck called
[ 2653.850607] usb-storage: *** thread awakened.
[ 2653.850613] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2653.850617] usb-storage:  1e 00 00 00 00 00
[ 2653.850628] usb-storage: Bulk Command S 0x43425355 T 0x18ff L 0 F 0 Trg 0 LUN 0 CL 6
[ 2653.850633] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.850746] usb-storage: Status code 0; transferred 31/31
[ 2653.850750] usb-storage: -- transfer complete
[ 2653.850754] usb-storage: Bulk command transfer result=0
[ 2653.850757] usb-storage: Attempting to get CSW...
[ 2653.850761] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.851764] usb-storage: Status code 0; transferred 13/13
[ 2653.851770] usb-storage: -- transfer complete
[ 2653.851776] usb-storage: Bulk status result = 0
[ 2653.851782] usb-storage: Bulk Status S 0x53425355 T 0x18ff R 0 Stat 0x0
[ 2653.851790] usb-storage: scsi cmd done, result=0x0
[ 2653.851799] usb-storage: *** thread sleeping.
[ 2653.851896] usb-storage: queuecommand_lck called
[ 2653.851913] usb-storage: *** thread awakened.
[ 2653.851920] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2653.851925] usb-storage:  00 00 00 00 00 00
[ 2653.851945] usb-storage: Bulk Command S 0x43425355 T 0xa10 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2653.851953] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.852124] usb-storage: Status code 0; transferred 31/31
[ 2653.852132] usb-storage: -- transfer complete
[ 2653.852138] usb-storage: Bulk command transfer result=0
[ 2653.852142] usb-storage: Attempting to get CSW...
[ 2653.852146] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.852249] usb-storage: Status code 0; transferred 13/13
[ 2653.852255] usb-storage: -- transfer complete
[ 2653.852260] usb-storage: Bulk status result = 0
[ 2653.852267] usb-storage: Bulk Status S 0x53425355 T 0xa10 R 0 Stat 0x0
[ 2653.852273] usb-storage: scsi cmd done, result=0x0
[ 2653.852280] usb-storage: *** thread sleeping.
[ 2653.852356] usb-storage: queuecommand_lck called
[ 2653.852371] usb-storage: *** thread awakened.
[ 2653.852377] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2653.852382] usb-storage:  00 00 00 00 00 00
[ 2653.852398] usb-storage: Bulk Command S 0x43425355 T 0xa11 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2653.852406] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2653.852499] usb-storage: Status code 0; transferred 31/31
[ 2653.852505] usb-storage: -- transfer complete
[ 2653.852510] usb-storage: Bulk command transfer result=0
[ 2653.852515] usb-storage: Attempting to get CSW...
[ 2653.852521] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2653.852632] usb-storage: Status code 0; transferred 13/13
[ 2653.852637] usb-storage: -- transfer complete
[ 2653.852643] usb-storage: Bulk status result = 0
[ 2653.852650] usb-storage: Bulk Status S 0x53425355 T 0xa11 R 0 Stat 0x0
[ 2653.852657] usb-storage: scsi cmd done, result=0x0
[ 2653.852666] usb-storage: *** thread sleeping.
[ 2655.845819] usb-storage: queuecommand_lck called
[ 2655.845840] usb-storage: *** thread awakened.
[ 2655.845846] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2655.845850] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2655.845867] usb-storage: Bulk Command S 0x43425355 T 0x1900 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2655.845873] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.846024] usb-storage: Status code 0; transferred 31/31
[ 2655.846029] usb-storage: -- transfer complete
[ 2655.846034] usb-storage: Bulk command transfer result=0
[ 2655.846040] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2655.846379] usb-storage: Status code 0; transferred 8/8
[ 2655.846385] usb-storage: -- transfer complete
[ 2655.846390] usb-storage: Bulk data transfer result 0x0
[ 2655.846395] usb-storage: Attempting to get CSW...
[ 2655.846400] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.847250] usb-storage: Status code 0; transferred 13/13
[ 2655.847254] usb-storage: -- transfer complete
[ 2655.847258] usb-storage: Bulk status result = 0
[ 2655.847263] usb-storage: Bulk Status S 0x53425355 T 0x1900 R 0 Stat 0x0
[ 2655.847269] usb-storage: scsi cmd done, result=0x0
[ 2655.847277] usb-storage: *** thread sleeping.
[ 2655.847313] usb-storage: queuecommand_lck called
[ 2655.847327] usb-storage: *** thread awakened.
[ 2655.847332] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2655.847335] usb-storage:  00 00 00 00 00 00
[ 2655.847347] usb-storage: Bulk Command S 0x43425355 T 0x1901 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2655.847352] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.847498] usb-storage: Status code 0; transferred 31/31
[ 2655.847502] usb-storage: -- transfer complete
[ 2655.847505] usb-storage: Bulk command transfer result=0
[ 2655.847509] usb-storage: Attempting to get CSW...
[ 2655.847513] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.848761] usb-storage: Status code 0; transferred 13/13
[ 2655.848766] usb-storage: -- transfer complete
[ 2655.848770] usb-storage: Bulk status result = 0
[ 2655.848775] usb-storage: Bulk Status S 0x53425355 T 0x1901 R 0 Stat 0x1
[ 2655.848780] usb-storage: -- transport indicates command failure
[ 2655.848784] usb-storage: Issuing auto-REQUEST_SENSE
[ 2655.848791] usb-storage: Bulk Command S 0x43425355 T 0x1902 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2655.848797] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.848872] usb-storage: Status code 0; transferred 31/31
[ 2655.848876] usb-storage: -- transfer complete
[ 2655.848879] usb-storage: Bulk command transfer result=0
[ 2655.848884] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2655.850013] usb-storage: Status code -121; transferred 24/96
[ 2655.850017] usb-storage: -- short read transfer
[ 2655.850021] usb-storage: Bulk data transfer result 0x1
[ 2655.850025] usb-storage: Attempting to get CSW...
[ 2655.850029] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.850249] usb-storage: Status code -32; transferred 0/13
[ 2655.850254] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2655.850260] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2655.850373] usb-storage: usb_stor_clear_halt: result = 0
[ 2655.850377] usb-storage: Attempting to get CSW (2nd try)...
[ 2655.850381] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.850496] usb-storage: Status code 0; transferred 13/13
[ 2655.850500] usb-storage: -- transfer complete
[ 2655.850504] usb-storage: Bulk status result = 0
[ 2655.850509] usb-storage: Bulk Status S 0x53425355 T 0x1902 R 72 Stat 0x0
[ 2655.850514] usb-storage: -- Result from auto-sense is 0
[ 2655.850519] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2655.850526] usb-storage: Not Ready: Medium not present - tray closed
[ 2655.850532] usb-storage: scsi cmd done, result=0x2
[ 2655.850541] usb-storage: *** thread sleeping.
[ 2655.850610] usb-storage: queuecommand_lck called
[ 2655.850623] usb-storage: *** thread awakened.
[ 2655.850629] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2655.850633] usb-storage:  1e 00 00 00 00 00
[ 2655.850644] usb-storage: Bulk Command S 0x43425355 T 0x1903 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2655.850649] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.850748] usb-storage: Status code 0; transferred 31/31
[ 2655.850752] usb-storage: -- transfer complete
[ 2655.850755] usb-storage: Bulk command transfer result=0
[ 2655.850759] usb-storage: Attempting to get CSW...
[ 2655.850763] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.851510] usb-storage: Status code 0; transferred 13/13
[ 2655.851516] usb-storage: -- transfer complete
[ 2655.851521] usb-storage: Bulk status result = 0
[ 2655.851528] usb-storage: Bulk Status S 0x53425355 T 0x1903 R 0 Stat 0x0
[ 2655.851535] usb-storage: scsi cmd done, result=0x0
[ 2655.851545] usb-storage: *** thread sleeping.
[ 2655.851650] usb-storage: queuecommand_lck called
[ 2655.851667] usb-storage: *** thread awakened.
[ 2655.851674] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2655.851680] usb-storage:  00 00 00 00 00 00
[ 2655.851700] usb-storage: Bulk Command S 0x43425355 T 0xa12 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2655.851707] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.851874] usb-storage: Status code 0; transferred 31/31
[ 2655.851883] usb-storage: -- transfer complete
[ 2655.851889] usb-storage: Bulk command transfer result=0
[ 2655.851892] usb-storage: Attempting to get CSW...
[ 2655.851897] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.851999] usb-storage: Status code 0; transferred 13/13
[ 2655.852016] usb-storage: -- transfer complete
[ 2655.852022] usb-storage: Bulk status result = 0
[ 2655.852028] usb-storage: Bulk Status S 0x53425355 T 0xa12 R 0 Stat 0x0
[ 2655.852033] usb-storage: scsi cmd done, result=0x0
[ 2655.852041] usb-storage: *** thread sleeping.
[ 2655.852115] usb-storage: queuecommand_lck called
[ 2655.852236] usb-storage: *** thread awakened.
[ 2655.852243] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2655.852248] usb-storage:  00 00 00 00 00 00
[ 2655.852265] usb-storage: Bulk Command S 0x43425355 T 0xa13 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2655.852271] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2655.852376] usb-storage: Status code 0; transferred 31/31
[ 2655.852381] usb-storage: -- transfer complete
[ 2655.852387] usb-storage: Bulk command transfer result=0
[ 2655.852392] usb-storage: Attempting to get CSW...
[ 2655.852398] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2655.852514] usb-storage: Status code 0; transferred 13/13
[ 2655.852519] usb-storage: -- transfer complete
[ 2655.852525] usb-storage: Bulk status result = 0
[ 2655.852532] usb-storage: Bulk Status S 0x53425355 T 0xa13 R 0 Stat 0x0
[ 2655.852538] usb-storage: scsi cmd done, result=0x0
[ 2655.852549] usb-storage: *** thread sleeping.
[ 2657.845710] usb-storage: queuecommand_lck called
[ 2657.845732] usb-storage: *** thread awakened.
[ 2657.845739] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2657.845743] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2657.845760] usb-storage: Bulk Command S 0x43425355 T 0x1904 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2657.845765] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.845882] usb-storage: Status code 0; transferred 31/31
[ 2657.845886] usb-storage: -- transfer complete
[ 2657.845890] usb-storage: Bulk command transfer result=0
[ 2657.845895] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2657.846387] usb-storage: Status code 0; transferred 8/8
[ 2657.846392] usb-storage: -- transfer complete
[ 2657.846397] usb-storage: Bulk data transfer result 0x0
[ 2657.846400] usb-storage: Attempting to get CSW...
[ 2657.846405] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.846751] usb-storage: Status code 0; transferred 13/13
[ 2657.846756] usb-storage: -- transfer complete
[ 2657.846760] usb-storage: Bulk status result = 0
[ 2657.846765] usb-storage: Bulk Status S 0x53425355 T 0x1904 R 0 Stat 0x0
[ 2657.846770] usb-storage: scsi cmd done, result=0x0
[ 2657.846778] usb-storage: *** thread sleeping.
[ 2657.846814] usb-storage: queuecommand_lck called
[ 2657.846828] usb-storage: *** thread awakened.
[ 2657.846833] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2657.846837] usb-storage:  00 00 00 00 00 00
[ 2657.846849] usb-storage: Bulk Command S 0x43425355 T 0x1905 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2657.846854] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.846998] usb-storage: Status code 0; transferred 31/31
[ 2657.847015] usb-storage: -- transfer complete
[ 2657.847020] usb-storage: Bulk command transfer result=0
[ 2657.847025] usb-storage: Attempting to get CSW...
[ 2657.847030] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.847879] usb-storage: Status code 0; transferred 13/13
[ 2657.847883] usb-storage: -- transfer complete
[ 2657.847887] usb-storage: Bulk status result = 0
[ 2657.847892] usb-storage: Bulk Status S 0x53425355 T 0x1905 R 0 Stat 0x1
[ 2657.847897] usb-storage: -- transport indicates command failure
[ 2657.847901] usb-storage: Issuing auto-REQUEST_SENSE
[ 2657.847907] usb-storage: Bulk Command S 0x43425355 T 0x1906 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2657.847912] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.848016] usb-storage: Status code 0; transferred 31/31
[ 2657.848021] usb-storage: -- transfer complete
[ 2657.848026] usb-storage: Bulk command transfer result=0
[ 2657.848032] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2657.849266] usb-storage: Status code -121; transferred 24/96
[ 2657.849271] usb-storage: -- short read transfer
[ 2657.849275] usb-storage: Bulk data transfer result 0x1
[ 2657.849279] usb-storage: Attempting to get CSW...
[ 2657.849284] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.849500] usb-storage: Status code -32; transferred 0/13
[ 2657.849504] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2657.849511] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2657.849624] usb-storage: usb_stor_clear_halt: result = 0
[ 2657.849628] usb-storage: Attempting to get CSW (2nd try)...
[ 2657.849633] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.849747] usb-storage: Status code 0; transferred 13/13
[ 2657.849751] usb-storage: -- transfer complete
[ 2657.849755] usb-storage: Bulk status result = 0
[ 2657.849760] usb-storage: Bulk Status S 0x53425355 T 0x1906 R 72 Stat 0x0
[ 2657.849765] usb-storage: -- Result from auto-sense is 0
[ 2657.849770] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2657.849777] usb-storage: Not Ready: Medium not present - tray closed
[ 2657.849784] usb-storage: scsi cmd done, result=0x2
[ 2657.849793] usb-storage: *** thread sleeping.
[ 2657.849863] usb-storage: queuecommand_lck called
[ 2657.849877] usb-storage: *** thread awakened.
[ 2657.849882] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2657.849886] usb-storage:  1e 00 00 00 00 00
[ 2657.849897] usb-storage: Bulk Command S 0x43425355 T 0x1907 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2657.849902] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.849999] usb-storage: Status code 0; transferred 31/31
[ 2657.850016] usb-storage: -- transfer complete
[ 2657.850022] usb-storage: Bulk command transfer result=0
[ 2657.850027] usb-storage: Attempting to get CSW...
[ 2657.850032] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.850895] usb-storage: Status code 0; transferred 13/13
[ 2657.850902] usb-storage: -- transfer complete
[ 2657.850907] usb-storage: Bulk status result = 0
[ 2657.850914] usb-storage: Bulk Status S 0x53425355 T 0x1907 R 0 Stat 0x0
[ 2657.850921] usb-storage: scsi cmd done, result=0x0
[ 2657.850932] usb-storage: *** thread sleeping.
[ 2657.851039] usb-storage: queuecommand_lck called
[ 2657.851056] usb-storage: *** thread awakened.
[ 2657.851064] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2657.851073] usb-storage:  00 00 00 00 00 00
[ 2657.851089] usb-storage: Bulk Command S 0x43425355 T 0xa14 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2657.851096] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.851262] usb-storage: Status code 0; transferred 31/31
[ 2657.851268] usb-storage: -- transfer complete
[ 2657.851273] usb-storage: Bulk command transfer result=0
[ 2657.851279] usb-storage: Attempting to get CSW...
[ 2657.851285] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.851387] usb-storage: Status code 0; transferred 13/13
[ 2657.851393] usb-storage: -- transfer complete
[ 2657.851398] usb-storage: Bulk status result = 0
[ 2657.851405] usb-storage: Bulk Status S 0x53425355 T 0xa14 R 0 Stat 0x0
[ 2657.851411] usb-storage: scsi cmd done, result=0x0
[ 2657.851421] usb-storage: *** thread sleeping.
[ 2657.851494] usb-storage: queuecommand_lck called
[ 2657.851510] usb-storage: *** thread awakened.
[ 2657.851516] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2657.851520] usb-storage:  00 00 00 00 00 00
[ 2657.851535] usb-storage: Bulk Command S 0x43425355 T 0xa15 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2657.851542] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.851638] usb-storage: Status code 0; transferred 31/31
[ 2657.851644] usb-storage: -- transfer complete
[ 2657.851649] usb-storage: Bulk command transfer result=0
[ 2657.851654] usb-storage: Attempting to get CSW...
[ 2657.851661] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.851763] usb-storage: Status code 0; transferred 13/13
[ 2657.851769] usb-storage: -- transfer complete
[ 2657.851774] usb-storage: Bulk status result = 0
[ 2657.851782] usb-storage: Bulk Status S 0x53425355 T 0xa15 R 0 Stat 0x0
[ 2657.851789] usb-storage: scsi cmd done, result=0x0
[ 2657.851798] usb-storage: *** thread sleeping.
[ 2657.858087] usb-storage: queuecommand_lck called
[ 2657.858105] usb-storage: *** thread awakened.
[ 2657.858111] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2657.858114] usb-storage:  00 00 00 00 00 00
[ 2657.858127] usb-storage: Bulk Command S 0x43425355 T 0xa16 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2657.858132] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2657.858255] usb-storage: Status code 0; transferred 31/31
[ 2657.858259] usb-storage: -- transfer complete
[ 2657.858263] usb-storage: Bulk command transfer result=0
[ 2657.858267] usb-storage: Attempting to get CSW...
[ 2657.858271] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2657.858376] usb-storage: Status code 0; transferred 13/13
[ 2657.858380] usb-storage: -- transfer complete
[ 2657.858384] usb-storage: Bulk status result = 0
[ 2657.858389] usb-storage: Bulk Status S 0x53425355 T 0xa16 R 0 Stat 0x0
[ 2657.858394] usb-storage: scsi cmd done, result=0x0
[ 2657.858401] usb-storage: *** thread sleeping.
[ 2659.845956] usb-storage: queuecommand_lck called
[ 2659.845978] usb-storage: *** thread awakened.
[ 2659.845984] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2659.845988] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2659.846026] usb-storage: Bulk Command S 0x43425355 T 0x1908 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2659.846033] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.846138] usb-storage: Status code 0; transferred 31/31
[ 2659.846144] usb-storage: -- transfer complete
[ 2659.846149] usb-storage: Bulk command transfer result=0
[ 2659.846156] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2659.846638] usb-storage: Status code 0; transferred 8/8
[ 2659.846643] usb-storage: -- transfer complete
[ 2659.846647] usb-storage: Bulk data transfer result 0x0
[ 2659.846651] usb-storage: Attempting to get CSW...
[ 2659.846656] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.847504] usb-storage: Status code 0; transferred 13/13
[ 2659.847509] usb-storage: -- transfer complete
[ 2659.847513] usb-storage: Bulk status result = 0
[ 2659.847518] usb-storage: Bulk Status S 0x53425355 T 0x1908 R 0 Stat 0x0
[ 2659.847524] usb-storage: scsi cmd done, result=0x0
[ 2659.847533] usb-storage: *** thread sleeping.
[ 2659.847576] usb-storage: queuecommand_lck called
[ 2659.847588] usb-storage: *** thread awakened.
[ 2659.847594] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2659.847597] usb-storage:  00 00 00 00 00 00
[ 2659.847609] usb-storage: Bulk Command S 0x43425355 T 0x1909 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2659.847614] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.847750] usb-storage: Status code 0; transferred 31/31
[ 2659.847754] usb-storage: -- transfer complete
[ 2659.847758] usb-storage: Bulk command transfer result=0
[ 2659.847761] usb-storage: Attempting to get CSW...
[ 2659.847766] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.848630] usb-storage: Status code 0; transferred 13/13
[ 2659.848634] usb-storage: -- transfer complete
[ 2659.848638] usb-storage: Bulk status result = 0
[ 2659.848643] usb-storage: Bulk Status S 0x53425355 T 0x1909 R 0 Stat 0x1
[ 2659.848648] usb-storage: -- transport indicates command failure
[ 2659.848652] usb-storage: Issuing auto-REQUEST_SENSE
[ 2659.848658] usb-storage: Bulk Command S 0x43425355 T 0x190a L 96 F 128 Trg 0 LUN 0 CL 6
[ 2659.848664] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.848749] usb-storage: Status code 0; transferred 31/31
[ 2659.848753] usb-storage: -- transfer complete
[ 2659.848757] usb-storage: Bulk command transfer result=0
[ 2659.848762] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2659.849758] usb-storage: Status code -121; transferred 24/96
[ 2659.849763] usb-storage: -- short read transfer
[ 2659.849767] usb-storage: Bulk data transfer result 0x1
[ 2659.849770] usb-storage: Attempting to get CSW...
[ 2659.849775] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.850001] usb-storage: Status code -32; transferred 0/13
[ 2659.850017] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2659.850026] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2659.850141] usb-storage: usb_stor_clear_halt: result = 0
[ 2659.850147] usb-storage: Attempting to get CSW (2nd try)...
[ 2659.850153] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.850263] usb-storage: Status code 0; transferred 13/13
[ 2659.850269] usb-storage: -- transfer complete
[ 2659.850274] usb-storage: Bulk status result = 0
[ 2659.850281] usb-storage: Bulk Status S 0x53425355 T 0x190a R 72 Stat 0x0
[ 2659.850288] usb-storage: -- Result from auto-sense is 0
[ 2659.850295] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2659.850304] usb-storage: Not Ready: Medium not present - tray closed
[ 2659.850312] usb-storage: scsi cmd done, result=0x2
[ 2659.850322] usb-storage: *** thread sleeping.
[ 2659.850435] usb-storage: queuecommand_lck called
[ 2659.850450] usb-storage: *** thread awakened.
[ 2659.850457] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2659.850462] usb-storage:  1e 00 00 00 00 00
[ 2659.850479] usb-storage: Bulk Command S 0x43425355 T 0x190b L 0 F 0 Trg 0 LUN 0 CL 6
[ 2659.850486] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.850639] usb-storage: Status code 0; transferred 31/31
[ 2659.850645] usb-storage: -- transfer complete
[ 2659.850651] usb-storage: Bulk command transfer result=0
[ 2659.850656] usb-storage: Attempting to get CSW...
[ 2659.850662] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.851504] usb-storage: Status code 0; transferred 13/13
[ 2659.851509] usb-storage: -- transfer complete
[ 2659.851513] usb-storage: Bulk status result = 0
[ 2659.851518] usb-storage: Bulk Status S 0x53425355 T 0x190b R 0 Stat 0x0
[ 2659.851523] usb-storage: scsi cmd done, result=0x0
[ 2659.851530] usb-storage: *** thread sleeping.
[ 2659.851600] usb-storage: queuecommand_lck called
[ 2659.851614] usb-storage: *** thread awakened.
[ 2659.851620] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2659.851623] usb-storage:  00 00 00 00 00 00
[ 2659.851635] usb-storage: Bulk Command S 0x43425355 T 0xa17 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2659.851640] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.851750] usb-storage: Status code 0; transferred 31/31
[ 2659.851754] usb-storage: -- transfer complete
[ 2659.851758] usb-storage: Bulk command transfer result=0
[ 2659.851762] usb-storage: Attempting to get CSW...
[ 2659.851766] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.851873] usb-storage: Status code 0; transferred 13/13
[ 2659.851877] usb-storage: -- transfer complete
[ 2659.851881] usb-storage: Bulk status result = 0
[ 2659.851886] usb-storage: Bulk Status S 0x53425355 T 0xa17 R 0 Stat 0x0
[ 2659.851890] usb-storage: scsi cmd done, result=0x0
[ 2659.851897] usb-storage: *** thread sleeping.
[ 2659.851951] usb-storage: queuecommand_lck called
[ 2659.851963] usb-storage: *** thread awakened.
[ 2659.851968] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2659.851971] usb-storage:  00 00 00 00 00 00
[ 2659.851983] usb-storage: Bulk Command S 0x43425355 T 0xa18 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2659.851988] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2659.852140] usb-storage: Status code 0; transferred 31/31
[ 2659.852145] usb-storage: -- transfer complete
[ 2659.852151] usb-storage: Bulk command transfer result=0
[ 2659.852156] usb-storage: Attempting to get CSW...
[ 2659.852162] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2659.852264] usb-storage: Status code 0; transferred 13/13
[ 2659.852269] usb-storage: -- transfer complete
[ 2659.852275] usb-storage: Bulk status result = 0
[ 2659.852282] usb-storage: Bulk Status S 0x53425355 T 0xa18 R 0 Stat 0x0
[ 2659.852289] usb-storage: scsi cmd done, result=0x0
[ 2659.852298] usb-storage: *** thread sleeping.
[ 2661.845316] usb-storage: queuecommand_lck called
[ 2661.845337] usb-storage: *** thread awakened.
[ 2661.845345] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2661.845350] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2661.845372] usb-storage: Bulk Command S 0x43425355 T 0x190c L 8 F 128 Trg 0 LUN 0 CL 10
[ 2661.845380] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.845512] usb-storage: Status code 0; transferred 31/31
[ 2661.845517] usb-storage: -- transfer complete
[ 2661.845522] usb-storage: Bulk command transfer result=0
[ 2661.845530] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2661.845879] usb-storage: Status code 0; transferred 8/8
[ 2661.845883] usb-storage: -- transfer complete
[ 2661.845887] usb-storage: Bulk data transfer result 0x0
[ 2661.845891] usb-storage: Attempting to get CSW...
[ 2661.845895] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.846757] usb-storage: Status code 0; transferred 13/13
[ 2661.846761] usb-storage: -- transfer complete
[ 2661.846765] usb-storage: Bulk status result = 0
[ 2661.846771] usb-storage: Bulk Status S 0x53425355 T 0x190c R 0 Stat 0x0
[ 2661.846777] usb-storage: scsi cmd done, result=0x0
[ 2661.846785] usb-storage: *** thread sleeping.
[ 2661.846830] usb-storage: queuecommand_lck called
[ 2661.846844] usb-storage: *** thread awakened.
[ 2661.846849] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2661.846853] usb-storage:  00 00 00 00 00 00
[ 2661.846864] usb-storage: Bulk Command S 0x43425355 T 0x190d L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.846870] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.847001] usb-storage: Status code 0; transferred 31/31
[ 2661.847015] usb-storage: -- transfer complete
[ 2661.847021] usb-storage: Bulk command transfer result=0
[ 2661.847025] usb-storage: Attempting to get CSW...
[ 2661.847031] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.848013] usb-storage: Status code 0; transferred 13/13
[ 2661.848017] usb-storage: -- transfer complete
[ 2661.848021] usb-storage: Bulk status result = 0
[ 2661.848026] usb-storage: Bulk Status S 0x53425355 T 0x190d R 0 Stat 0x1
[ 2661.848031] usb-storage: -- transport indicates command failure
[ 2661.848035] usb-storage: Issuing auto-REQUEST_SENSE
[ 2661.848042] usb-storage: Bulk Command S 0x43425355 T 0x190e L 96 F 128 Trg 0 LUN 0 CL 6
[ 2661.848047] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.848126] usb-storage: Status code 0; transferred 31/31
[ 2661.848130] usb-storage: -- transfer complete
[ 2661.848134] usb-storage: Bulk command transfer result=0
[ 2661.848139] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2661.849759] usb-storage: Status code -121; transferred 24/96
[ 2661.849763] usb-storage: -- short read transfer
[ 2661.849767] usb-storage: Bulk data transfer result 0x1
[ 2661.849771] usb-storage: Attempting to get CSW...
[ 2661.849775] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.850015] usb-storage: Status code -32; transferred 0/13
[ 2661.850021] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2661.850029] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2661.850143] usb-storage: usb_stor_clear_halt: result = 0
[ 2661.850149] usb-storage: Attempting to get CSW (2nd try)...
[ 2661.850155] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.850263] usb-storage: Status code 0; transferred 13/13
[ 2661.850268] usb-storage: -- transfer complete
[ 2661.850274] usb-storage: Bulk status result = 0
[ 2661.850281] usb-storage: Bulk Status S 0x53425355 T 0x190e R 72 Stat 0x0
[ 2661.850288] usb-storage: -- Result from auto-sense is 0
[ 2661.850295] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2661.850305] usb-storage: Not Ready: Medium not present - tray closed
[ 2661.850313] usb-storage: scsi cmd done, result=0x2
[ 2661.850322] usb-storage: *** thread sleeping.
[ 2661.850387] usb-storage: queuecommand_lck called
[ 2661.850402] usb-storage: *** thread awakened.
[ 2661.850409] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2661.850414] usb-storage:  1e 00 00 00 00 00
[ 2661.850430] usb-storage: Bulk Command S 0x43425355 T 0x190f L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.850438] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.850516] usb-storage: Status code 0; transferred 31/31
[ 2661.850522] usb-storage: -- transfer complete
[ 2661.850527] usb-storage: Bulk command transfer result=0
[ 2661.850532] usb-storage: Attempting to get CSW...
[ 2661.850538] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.851381] usb-storage: Status code 0; transferred 13/13
[ 2661.851386] usb-storage: -- transfer complete
[ 2661.851390] usb-storage: Bulk status result = 0
[ 2661.851395] usb-storage: Bulk Status S 0x53425355 T 0x190f R 0 Stat 0x0
[ 2661.851399] usb-storage: scsi cmd done, result=0x0
[ 2661.851406] usb-storage: *** thread sleeping.
[ 2661.851478] usb-storage: queuecommand_lck called
[ 2661.851492] usb-storage: *** thread awakened.
[ 2661.851498] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2661.851501] usb-storage:  00 00 00 00 00 00
[ 2661.851513] usb-storage: Bulk Command S 0x43425355 T 0xa19 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.851518] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.851626] usb-storage: Status code 0; transferred 31/31
[ 2661.851630] usb-storage: -- transfer complete
[ 2661.851634] usb-storage: Bulk command transfer result=0
[ 2661.851638] usb-storage: Attempting to get CSW...
[ 2661.851642] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.851750] usb-storage: Status code 0; transferred 13/13
[ 2661.851754] usb-storage: -- transfer complete
[ 2661.851757] usb-storage: Bulk status result = 0
[ 2661.851762] usb-storage: Bulk Status S 0x53425355 T 0xa19 R 0 Stat 0x0
[ 2661.851767] usb-storage: scsi cmd done, result=0x0
[ 2661.851773] usb-storage: *** thread sleeping.
[ 2661.851828] usb-storage: queuecommand_lck called
[ 2661.851840] usb-storage: *** thread awakened.
[ 2661.851844] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2661.851848] usb-storage:  00 00 00 00 00 00
[ 2661.851859] usb-storage: Bulk Command S 0x43425355 T 0xa1a L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.851864] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.852002] usb-storage: Status code 0; transferred 31/31
[ 2661.852015] usb-storage: -- transfer complete
[ 2661.852020] usb-storage: Bulk command transfer result=0
[ 2661.852025] usb-storage: Attempting to get CSW...
[ 2661.852031] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.852131] usb-storage: Status code 0; transferred 13/13
[ 2661.852136] usb-storage: -- transfer complete
[ 2661.852141] usb-storage: Bulk status result = 0
[ 2661.852147] usb-storage: Bulk Status S 0x53425355 T 0xa1a R 0 Stat 0x0
[ 2661.852153] usb-storage: scsi cmd done, result=0x0
[ 2661.852161] usb-storage: *** thread sleeping.
[ 2661.859099] usb-storage: queuecommand_lck called
[ 2661.859119] usb-storage: *** thread awakened.
[ 2661.859125] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2661.859129] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2661.859146] usb-storage: Bulk Command S 0x43425355 T 0x1910 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2661.859151] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.859257] usb-storage: Status code 0; transferred 31/31
[ 2661.859261] usb-storage: -- transfer complete
[ 2661.859265] usb-storage: Bulk command transfer result=0
[ 2661.859270] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2661.859754] usb-storage: Status code 0; transferred 8/8
[ 2661.859758] usb-storage: -- transfer complete
[ 2661.859761] usb-storage: Bulk data transfer result 0x0
[ 2661.859765] usb-storage: Attempting to get CSW...
[ 2661.859769] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.860260] usb-storage: Status code 0; transferred 13/13
[ 2661.860266] usb-storage: -- transfer complete
[ 2661.860271] usb-storage: Bulk status result = 0
[ 2661.860276] usb-storage: Bulk Status S 0x53425355 T 0x1910 R 0 Stat 0x0
[ 2661.860281] usb-storage: scsi cmd done, result=0x0
[ 2661.860289] usb-storage: *** thread sleeping.
[ 2661.860324] usb-storage: queuecommand_lck called
[ 2661.860339] usb-storage: *** thread awakened.
[ 2661.860349] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2661.860354] usb-storage:  00 00 00 00 00 00
[ 2661.860370] usb-storage: Bulk Command S 0x43425355 T 0x1911 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.860377] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.860509] usb-storage: Status code 0; transferred 31/31
[ 2661.860515] usb-storage: -- transfer complete
[ 2661.860520] usb-storage: Bulk command transfer result=0
[ 2661.860525] usb-storage: Attempting to get CSW...
[ 2661.860531] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.861506] usb-storage: Status code 0; transferred 13/13
[ 2661.861510] usb-storage: -- transfer complete
[ 2661.861514] usb-storage: Bulk status result = 0
[ 2661.861520] usb-storage: Bulk Status S 0x53425355 T 0x1911 R 0 Stat 0x1
[ 2661.861524] usb-storage: -- transport indicates command failure
[ 2661.861528] usb-storage: Issuing auto-REQUEST_SENSE
[ 2661.861535] usb-storage: Bulk Command S 0x43425355 T 0x1912 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2661.861540] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.861625] usb-storage: Status code 0; transferred 31/31
[ 2661.861629] usb-storage: -- transfer complete
[ 2661.861633] usb-storage: Bulk command transfer result=0
[ 2661.861638] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2661.862764] usb-storage: Status code -121; transferred 24/96
[ 2661.862769] usb-storage: -- short read transfer
[ 2661.862773] usb-storage: Bulk data transfer result 0x1
[ 2661.862777] usb-storage: Attempting to get CSW...
[ 2661.862781] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.863018] usb-storage: Status code -32; transferred 0/13
[ 2661.863024] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2661.863032] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2661.863134] usb-storage: usb_stor_clear_halt: result = 0
[ 2661.863140] usb-storage: Attempting to get CSW (2nd try)...
[ 2661.863146] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.863257] usb-storage: Status code 0; transferred 13/13
[ 2661.863262] usb-storage: -- transfer complete
[ 2661.863267] usb-storage: Bulk status result = 0
[ 2661.863273] usb-storage: Bulk Status S 0x53425355 T 0x1912 R 72 Stat 0x0
[ 2661.863279] usb-storage: -- Result from auto-sense is 0
[ 2661.863286] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2661.863294] usb-storage: Not Ready: Medium not present - tray closed
[ 2661.863302] usb-storage: scsi cmd done, result=0x2
[ 2661.863312] usb-storage: *** thread sleeping.
[ 2661.863378] usb-storage: queuecommand_lck called
[ 2661.863393] usb-storage: *** thread awakened.
[ 2661.863399] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2661.863404] usb-storage:  00 00 00 00 00 00
[ 2661.863419] usb-storage: Bulk Command S 0x43425355 T 0x1913 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.863425] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.863507] usb-storage: Status code 0; transferred 31/31
[ 2661.863513] usb-storage: -- transfer complete
[ 2661.863518] usb-storage: Bulk command transfer result=0
[ 2661.863523] usb-storage: Attempting to get CSW...
[ 2661.863529] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.864762] usb-storage: Status code 0; transferred 13/13
[ 2661.864767] usb-storage: -- transfer complete
[ 2661.864771] usb-storage: Bulk status result = 0
[ 2661.864776] usb-storage: Bulk Status S 0x53425355 T 0x1913 R 0 Stat 0x1
[ 2661.864781] usb-storage: -- transport indicates command failure
[ 2661.864785] usb-storage: Issuing auto-REQUEST_SENSE
[ 2661.864792] usb-storage: Bulk Command S 0x43425355 T 0x1914 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2661.864798] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.864876] usb-storage: Status code 0; transferred 31/31
[ 2661.864880] usb-storage: -- transfer complete
[ 2661.864883] usb-storage: Bulk command transfer result=0
[ 2661.864889] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2661.866013] usb-storage: Status code -121; transferred 24/96
[ 2661.866017] usb-storage: -- short read transfer
[ 2661.866022] usb-storage: Bulk data transfer result 0x1
[ 2661.866025] usb-storage: Attempting to get CSW...
[ 2661.866029] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.866253] usb-storage: Status code -32; transferred 0/13
[ 2661.866257] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2661.866264] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2661.866377] usb-storage: usb_stor_clear_halt: result = 0
[ 2661.866381] usb-storage: Attempting to get CSW (2nd try)...
[ 2661.866385] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.866500] usb-storage: Status code 0; transferred 13/13
[ 2661.866504] usb-storage: -- transfer complete
[ 2661.866507] usb-storage: Bulk status result = 0
[ 2661.866512] usb-storage: Bulk Status S 0x53425355 T 0x1914 R 72 Stat 0x0
[ 2661.866517] usb-storage: -- Result from auto-sense is 0
[ 2661.866522] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2661.866528] usb-storage: Not Ready: Medium not present - tray closed
[ 2661.866535] usb-storage: scsi cmd done, result=0x2
[ 2661.866543] usb-storage: *** thread sleeping.
[ 2661.866590] usb-storage: queuecommand_lck called
[ 2661.866603] usb-storage: *** thread awakened.
[ 2661.866608] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2661.866612] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2661.866628] usb-storage: Bulk Command S 0x43425355 T 0x1915 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2661.866633] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.866751] usb-storage: Status code 0; transferred 31/31
[ 2661.866755] usb-storage: -- transfer complete
[ 2661.866758] usb-storage: Bulk command transfer result=0
[ 2661.866763] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2661.867131] usb-storage: Status code 0; transferred 8/8
[ 2661.867137] usb-storage: -- transfer complete
[ 2661.867142] usb-storage: Bulk data transfer result 0x0
[ 2661.867151] usb-storage: Attempting to get CSW...
[ 2661.867157] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.867631] usb-storage: Status code 0; transferred 13/13
[ 2661.867637] usb-storage: -- transfer complete
[ 2661.867642] usb-storage: Bulk status result = 0
[ 2661.867649] usb-storage: Bulk Status S 0x53425355 T 0x1915 R 0 Stat 0x0
[ 2661.867656] usb-storage: scsi cmd done, result=0x0
[ 2661.867667] usb-storage: *** thread sleeping.
[ 2661.867717] usb-storage: queuecommand_lck called
[ 2661.867731] usb-storage: *** thread awakened.
[ 2661.867738] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2661.867743] usb-storage:  1e 00 00 00 00 00
[ 2661.867759] usb-storage: Bulk Command S 0x43425355 T 0x1916 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2661.867767] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2661.867879] usb-storage: Status code 0; transferred 31/31
[ 2661.867885] usb-storage: -- transfer complete
[ 2661.867889] usb-storage: Bulk command transfer result=0
[ 2661.867894] usb-storage: Attempting to get CSW...
[ 2661.867900] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2661.868631] usb-storage: Status code 0; transferred 13/13
[ 2661.868636] usb-storage: -- transfer complete
[ 2661.868640] usb-storage: Bulk status result = 0
[ 2661.868645] usb-storage: Bulk Status S 0x53425355 T 0x1916 R 0 Stat 0x0
[ 2661.868650] usb-storage: scsi cmd done, result=0x0
[ 2661.868657] usb-storage: *** thread sleeping.
[ 2663.845314] usb-storage: queuecommand_lck called
[ 2663.845338] usb-storage: *** thread awakened.
[ 2663.845345] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2663.845349] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2663.845366] usb-storage: Bulk Command S 0x43425355 T 0x1917 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2663.845371] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.845509] usb-storage: Status code 0; transferred 31/31
[ 2663.845514] usb-storage: -- transfer complete
[ 2663.845517] usb-storage: Bulk command transfer result=0
[ 2663.845522] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2663.846018] usb-storage: Status code 0; transferred 8/8
[ 2663.846024] usb-storage: -- transfer complete
[ 2663.846029] usb-storage: Bulk data transfer result 0x0
[ 2663.846033] usb-storage: Attempting to get CSW...
[ 2663.846038] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.846887] usb-storage: Status code 0; transferred 13/13
[ 2663.846892] usb-storage: -- transfer complete
[ 2663.846897] usb-storage: Bulk status result = 0
[ 2663.846903] usb-storage: Bulk Status S 0x53425355 T 0x1917 R 0 Stat 0x0
[ 2663.846910] usb-storage: scsi cmd done, result=0x0
[ 2663.846923] usb-storage: *** thread sleeping.
[ 2663.846972] usb-storage: queuecommand_lck called
[ 2663.846984] usb-storage: *** thread awakened.
[ 2663.846991] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2663.846996] usb-storage:  00 00 00 00 00 00
[ 2663.847029] usb-storage: Bulk Command S 0x43425355 T 0x1918 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2663.847036] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.847150] usb-storage: Status code 0; transferred 31/31
[ 2663.847156] usb-storage: -- transfer complete
[ 2663.847161] usb-storage: Bulk command transfer result=0
[ 2663.847166] usb-storage: Attempting to get CSW...
[ 2663.847172] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.848133] usb-storage: Status code 0; transferred 13/13
[ 2663.848137] usb-storage: -- transfer complete
[ 2663.848141] usb-storage: Bulk status result = 0
[ 2663.848146] usb-storage: Bulk Status S 0x53425355 T 0x1918 R 0 Stat 0x1
[ 2663.848151] usb-storage: -- transport indicates command failure
[ 2663.848155] usb-storage: Issuing auto-REQUEST_SENSE
[ 2663.848162] usb-storage: Bulk Command S 0x43425355 T 0x1919 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2663.848167] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.848252] usb-storage: Status code 0; transferred 31/31
[ 2663.848256] usb-storage: -- transfer complete
[ 2663.848259] usb-storage: Bulk command transfer result=0
[ 2663.848264] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2663.849885] usb-storage: Status code -121; transferred 24/96
[ 2663.849890] usb-storage: -- short read transfer
[ 2663.849894] usb-storage: Bulk data transfer result 0x1
[ 2663.849897] usb-storage: Attempting to get CSW...
[ 2663.849902] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.850142] usb-storage: Status code -32; transferred 0/13
[ 2663.850149] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2663.850158] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2663.850260] usb-storage: usb_stor_clear_halt: result = 0
[ 2663.850266] usb-storage: Attempting to get CSW (2nd try)...
[ 2663.850272] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.850382] usb-storage: Status code 0; transferred 13/13
[ 2663.850391] usb-storage: -- transfer complete
[ 2663.850397] usb-storage: Bulk status result = 0
[ 2663.850403] usb-storage: Bulk Status S 0x53425355 T 0x1919 R 72 Stat 0x0
[ 2663.850410] usb-storage: -- Result from auto-sense is 0
[ 2663.850417] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2663.850425] usb-storage: Not Ready: Medium not present - tray closed
[ 2663.850433] usb-storage: scsi cmd done, result=0x2
[ 2663.850443] usb-storage: *** thread sleeping.
[ 2663.850541] usb-storage: queuecommand_lck called
[ 2663.850558] usb-storage: *** thread awakened.
[ 2663.850564] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2663.850570] usb-storage:  1e 00 00 00 00 00
[ 2663.850590] usb-storage: Bulk Command S 0x43425355 T 0x191a L 0 F 0 Trg 0 LUN 0 CL 6
[ 2663.850597] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.850757] usb-storage: Status code 0; transferred 31/31
[ 2663.850762] usb-storage: -- transfer complete
[ 2663.850767] usb-storage: Bulk command transfer result=0
[ 2663.850772] usb-storage: Attempting to get CSW...
[ 2663.850777] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.851256] usb-storage: Status code 0; transferred 13/13
[ 2663.851261] usb-storage: -- transfer complete
[ 2663.851265] usb-storage: Bulk status result = 0
[ 2663.851270] usb-storage: Bulk Status S 0x53425355 T 0x191a R 0 Stat 0x0
[ 2663.851275] usb-storage: scsi cmd done, result=0x0
[ 2663.851282] usb-storage: *** thread sleeping.
[ 2663.851355] usb-storage: queuecommand_lck called
[ 2663.851369] usb-storage: *** thread awakened.
[ 2663.851374] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2663.851378] usb-storage:  00 00 00 00 00 00
[ 2663.851390] usb-storage: Bulk Command S 0x43425355 T 0xa1b L 0 F 0 Trg 0 LUN 0 CL 6
[ 2663.851395] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.851502] usb-storage: Status code 0; transferred 31/31
[ 2663.851506] usb-storage: -- transfer complete
[ 2663.851510] usb-storage: Bulk command transfer result=0
[ 2663.851514] usb-storage: Attempting to get CSW...
[ 2663.851518] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.851626] usb-storage: Status code 0; transferred 13/13
[ 2663.851630] usb-storage: -- transfer complete
[ 2663.851633] usb-storage: Bulk status result = 0
[ 2663.851638] usb-storage: Bulk Status S 0x53425355 T 0xa1b R 0 Stat 0x0
[ 2663.851643] usb-storage: scsi cmd done, result=0x0
[ 2663.851649] usb-storage: *** thread sleeping.
[ 2663.851703] usb-storage: queuecommand_lck called
[ 2663.851715] usb-storage: *** thread awakened.
[ 2663.851720] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2663.851723] usb-storage:  00 00 00 00 00 00
[ 2663.851735] usb-storage: Bulk Command S 0x43425355 T 0xa1c L 0 F 0 Trg 0 LUN 0 CL 6
[ 2663.851740] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2663.851878] usb-storage: Status code 0; transferred 31/31
[ 2663.851881] usb-storage: -- transfer complete
[ 2663.851885] usb-storage: Bulk command transfer result=0
[ 2663.851889] usb-storage: Attempting to get CSW...
[ 2663.851893] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2663.852001] usb-storage: Status code 0; transferred 13/13
[ 2663.852015] usb-storage: -- transfer complete
[ 2663.852021] usb-storage: Bulk status result = 0
[ 2663.852027] usb-storage: Bulk Status S 0x53425355 T 0xa1c R 0 Stat 0x0
[ 2663.852033] usb-storage: scsi cmd done, result=0x0
[ 2663.852041] usb-storage: *** thread sleeping.
[ 2665.844644] usb-storage: queuecommand_lck called
[ 2665.844666] usb-storage: *** thread awakened.
[ 2665.844674] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2665.844680] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2665.844701] usb-storage: Bulk Command S 0x43425355 T 0x191b L 8 F 128 Trg 0 LUN 0 CL 10
[ 2665.844709] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.844892] usb-storage: Status code 0; transferred 31/31
[ 2665.844896] usb-storage: -- transfer complete
[ 2665.844900] usb-storage: Bulk command transfer result=0
[ 2665.844906] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2665.845284] usb-storage: Status code 0; transferred 8/8
[ 2665.845290] usb-storage: -- transfer complete
[ 2665.845295] usb-storage: Bulk data transfer result 0x0
[ 2665.845300] usb-storage: Attempting to get CSW...
[ 2665.845306] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.845756] usb-storage: Status code 0; transferred 13/13
[ 2665.845760] usb-storage: -- transfer complete
[ 2665.845764] usb-storage: Bulk status result = 0
[ 2665.845769] usb-storage: Bulk Status S 0x53425355 T 0x191b R 0 Stat 0x0
[ 2665.845775] usb-storage: scsi cmd done, result=0x0
[ 2665.845784] usb-storage: *** thread sleeping.
[ 2665.845827] usb-storage: queuecommand_lck called
[ 2665.845841] usb-storage: *** thread awakened.
[ 2665.845847] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2665.845851] usb-storage:  00 00 00 00 00 00
[ 2665.845862] usb-storage: Bulk Command S 0x43425355 T 0x191c L 0 F 0 Trg 0 LUN 0 CL 6
[ 2665.845867] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.846015] usb-storage: Status code 0; transferred 31/31
[ 2665.846020] usb-storage: -- transfer complete
[ 2665.846025] usb-storage: Bulk command transfer result=0
[ 2665.846029] usb-storage: Attempting to get CSW...
[ 2665.846035] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.847133] usb-storage: Status code 0; transferred 13/13
[ 2665.847138] usb-storage: -- transfer complete
[ 2665.847142] usb-storage: Bulk status result = 0
[ 2665.847147] usb-storage: Bulk Status S 0x53425355 T 0x191c R 0 Stat 0x1
[ 2665.847151] usb-storage: -- transport indicates command failure
[ 2665.847155] usb-storage: Issuing auto-REQUEST_SENSE
[ 2665.847162] usb-storage: Bulk Command S 0x43425355 T 0x191d L 96 F 128 Trg 0 LUN 0 CL 6
[ 2665.847167] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.847253] usb-storage: Status code 0; transferred 31/31
[ 2665.847257] usb-storage: -- transfer complete
[ 2665.847260] usb-storage: Bulk command transfer result=0
[ 2665.847265] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2665.848761] usb-storage: Status code -121; transferred 24/96
[ 2665.848765] usb-storage: -- short read transfer
[ 2665.848769] usb-storage: Bulk data transfer result 0x1
[ 2665.848773] usb-storage: Attempting to get CSW...
[ 2665.848777] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.849014] usb-storage: Status code -32; transferred 0/13
[ 2665.849019] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2665.849025] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2665.849156] usb-storage: usb_stor_clear_halt: result = 0
[ 2665.849162] usb-storage: Attempting to get CSW (2nd try)...
[ 2665.849168] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.849271] usb-storage: Status code 0; transferred 13/13
[ 2665.849276] usb-storage: -- transfer complete
[ 2665.849282] usb-storage: Bulk status result = 0
[ 2665.849289] usb-storage: Bulk Status S 0x53425355 T 0x191d R 72 Stat 0x0
[ 2665.849296] usb-storage: -- Result from auto-sense is 0
[ 2665.849302] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2665.849309] usb-storage: Not Ready: Medium not present - tray closed
[ 2665.849315] usb-storage: scsi cmd done, result=0x2
[ 2665.849323] usb-storage: *** thread sleeping.
[ 2665.849391] usb-storage: queuecommand_lck called
[ 2665.849410] usb-storage: *** thread awakened.
[ 2665.849418] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2665.849423] usb-storage:  1e 00 00 00 00 00
[ 2665.849439] usb-storage: Bulk Command S 0x43425355 T 0x191e L 0 F 0 Trg 0 LUN 0 CL 6
[ 2665.849446] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.849508] usb-storage: Status code 0; transferred 31/31
[ 2665.849513] usb-storage: -- transfer complete
[ 2665.849517] usb-storage: Bulk command transfer result=0
[ 2665.849522] usb-storage: Attempting to get CSW...
[ 2665.849527] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.850011] usb-storage: Status code 0; transferred 13/13
[ 2665.850017] usb-storage: -- transfer complete
[ 2665.850027] usb-storage: Bulk status result = 0
[ 2665.850034] usb-storage: Bulk Status S 0x53425355 T 0x191e R 0 Stat 0x0
[ 2665.850040] usb-storage: scsi cmd done, result=0x0
[ 2665.850050] usb-storage: *** thread sleeping.
[ 2665.850136] usb-storage: queuecommand_lck called
[ 2665.850152] usb-storage: *** thread awakened.
[ 2665.850159] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2665.850164] usb-storage:  00 00 00 00 00 00
[ 2665.850180] usb-storage: Bulk Command S 0x43425355 T 0xa1d L 0 F 0 Trg 0 LUN 0 CL 6
[ 2665.850188] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.850255] usb-storage: Status code 0; transferred 31/31
[ 2665.850260] usb-storage: -- transfer complete
[ 2665.850265] usb-storage: Bulk command transfer result=0
[ 2665.850270] usb-storage: Attempting to get CSW...
[ 2665.850275] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.850380] usb-storage: Status code 0; transferred 13/13
[ 2665.850389] usb-storage: -- transfer complete
[ 2665.850395] usb-storage: Bulk status result = 0
[ 2665.850402] usb-storage: Bulk Status S 0x53425355 T 0xa1d R 0 Stat 0x0
[ 2665.850408] usb-storage: scsi cmd done, result=0x0
[ 2665.850417] usb-storage: *** thread sleeping.
[ 2665.850489] usb-storage: queuecommand_lck called
[ 2665.850503] usb-storage: *** thread awakened.
[ 2665.850510] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2665.850515] usb-storage:  00 00 00 00 00 00
[ 2665.850532] usb-storage: Bulk Command S 0x43425355 T 0xa1e L 0 F 0 Trg 0 LUN 0 CL 6
[ 2665.850539] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2665.850642] usb-storage: Status code 0; transferred 31/31
[ 2665.850648] usb-storage: -- transfer complete
[ 2665.850654] usb-storage: Bulk command transfer result=0
[ 2665.850659] usb-storage: Attempting to get CSW...
[ 2665.850665] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2665.850757] usb-storage: Status code 0; transferred 13/13
[ 2665.850762] usb-storage: -- transfer complete
[ 2665.850767] usb-storage: Bulk status result = 0
[ 2665.850773] usb-storage: Bulk Status S 0x53425355 T 0xa1e R 0 Stat 0x0
[ 2665.850779] usb-storage: scsi cmd done, result=0x0
[ 2665.850787] usb-storage: *** thread sleeping.
[ 2667.845941] usb-storage: queuecommand_lck called
[ 2667.845964] usb-storage: *** thread awakened.
[ 2667.845970] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2667.845974] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2667.845991] usb-storage: Bulk Command S 0x43425355 T 0x191f L 8 F 128 Trg 0 LUN 0 CL 10
[ 2667.845997] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.846158] usb-storage: Status code 0; transferred 31/31
[ 2667.846164] usb-storage: -- transfer complete
[ 2667.846169] usb-storage: Bulk command transfer result=0
[ 2667.846176] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2667.846509] usb-storage: Status code 0; transferred 8/8
[ 2667.846513] usb-storage: -- transfer complete
[ 2667.846517] usb-storage: Bulk data transfer result 0x0
[ 2667.846521] usb-storage: Attempting to get CSW...
[ 2667.846525] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.847015] usb-storage: Status code 0; transferred 13/13
[ 2667.847021] usb-storage: -- transfer complete
[ 2667.847025] usb-storage: Bulk status result = 0
[ 2667.847032] usb-storage: Bulk Status S 0x53425355 T 0x191f R 0 Stat 0x0
[ 2667.847038] usb-storage: scsi cmd done, result=0x0
[ 2667.847048] usb-storage: *** thread sleeping.
[ 2667.847124] usb-storage: queuecommand_lck called
[ 2667.847148] usb-storage: *** thread awakened.
[ 2667.847155] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2667.847163] usb-storage:  00 00 00 00 00 00
[ 2667.847180] usb-storage: Bulk Command S 0x43425355 T 0x1920 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2667.847187] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.847273] usb-storage: Status code 0; transferred 31/31
[ 2667.847278] usb-storage: -- transfer complete
[ 2667.847284] usb-storage: Bulk command transfer result=0
[ 2667.847289] usb-storage: Attempting to get CSW...
[ 2667.847295] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.848134] usb-storage: Status code 0; transferred 13/13
[ 2667.848138] usb-storage: -- transfer complete
[ 2667.848142] usb-storage: Bulk status result = 0
[ 2667.848147] usb-storage: Bulk Status S 0x53425355 T 0x1920 R 0 Stat 0x1
[ 2667.848152] usb-storage: -- transport indicates command failure
[ 2667.848155] usb-storage: Issuing auto-REQUEST_SENSE
[ 2667.848162] usb-storage: Bulk Command S 0x43425355 T 0x1921 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2667.848167] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.848254] usb-storage: Status code 0; transferred 31/31
[ 2667.848258] usb-storage: -- transfer complete
[ 2667.848261] usb-storage: Bulk command transfer result=0
[ 2667.848266] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2667.849388] usb-storage: Status code -121; transferred 24/96
[ 2667.849392] usb-storage: -- short read transfer
[ 2667.849396] usb-storage: Bulk data transfer result 0x1
[ 2667.849400] usb-storage: Attempting to get CSW...
[ 2667.849404] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.849630] usb-storage: Status code -32; transferred 0/13
[ 2667.849635] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2667.849641] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2667.849755] usb-storage: usb_stor_clear_halt: result = 0
[ 2667.849759] usb-storage: Attempting to get CSW (2nd try)...
[ 2667.849763] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.849878] usb-storage: Status code 0; transferred 13/13
[ 2667.849882] usb-storage: -- transfer complete
[ 2667.849886] usb-storage: Bulk status result = 0
[ 2667.849891] usb-storage: Bulk Status S 0x53425355 T 0x1921 R 72 Stat 0x0
[ 2667.849896] usb-storage: -- Result from auto-sense is 0
[ 2667.849901] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2667.849907] usb-storage: Not Ready: Medium not present - tray closed
[ 2667.849914] usb-storage: scsi cmd done, result=0x2
[ 2667.849921] usb-storage: *** thread sleeping.
[ 2667.849975] usb-storage: queuecommand_lck called
[ 2667.849990] usb-storage: *** thread awakened.
[ 2667.849995] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2667.849998] usb-storage:  1e 00 00 00 00 00
[ 2667.850026] usb-storage: Bulk Command S 0x43425355 T 0x1922 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2667.850033] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.850132] usb-storage: Status code 0; transferred 31/31
[ 2667.850137] usb-storage: -- transfer complete
[ 2667.850142] usb-storage: Bulk command transfer result=0
[ 2667.850147] usb-storage: Attempting to get CSW...
[ 2667.850153] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.851012] usb-storage: Status code 0; transferred 13/13
[ 2667.851021] usb-storage: -- transfer complete
[ 2667.851027] usb-storage: Bulk status result = 0
[ 2667.851033] usb-storage: Bulk Status S 0x53425355 T 0x1922 R 0 Stat 0x0
[ 2667.851039] usb-storage: scsi cmd done, result=0x0
[ 2667.851048] usb-storage: *** thread sleeping.
[ 2667.851122] usb-storage: queuecommand_lck called
[ 2667.851138] usb-storage: *** thread awakened.
[ 2667.851144] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2667.851149] usb-storage:  00 00 00 00 00 00
[ 2667.851164] usb-storage: Bulk Command S 0x43425355 T 0xa1f L 0 F 0 Trg 0 LUN 0 CL 6
[ 2667.851170] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.851271] usb-storage: Status code 0; transferred 31/31
[ 2667.851277] usb-storage: -- transfer complete
[ 2667.851286] usb-storage: Bulk command transfer result=0
[ 2667.851291] usb-storage: Attempting to get CSW...
[ 2667.851297] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.851383] usb-storage: Status code 0; transferred 13/13
[ 2667.851392] usb-storage: -- transfer complete
[ 2667.851397] usb-storage: Bulk status result = 0
[ 2667.851404] usb-storage: Bulk Status S 0x53425355 T 0xa1f R 0 Stat 0x0
[ 2667.851411] usb-storage: scsi cmd done, result=0x0
[ 2667.851421] usb-storage: *** thread sleeping.
[ 2667.851489] usb-storage: queuecommand_lck called
[ 2667.851505] usb-storage: *** thread awakened.
[ 2667.851512] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2667.851521] usb-storage:  00 00 00 00 00 00
[ 2667.851537] usb-storage: Bulk Command S 0x43425355 T 0xa20 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2667.851544] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2667.851640] usb-storage: Status code 0; transferred 31/31
[ 2667.851645] usb-storage: -- transfer complete
[ 2667.851650] usb-storage: Bulk command transfer result=0
[ 2667.851655] usb-storage: Attempting to get CSW...
[ 2667.851661] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2667.851762] usb-storage: Status code 0; transferred 13/13
[ 2667.851768] usb-storage: -- transfer complete
[ 2667.851773] usb-storage: Bulk status result = 0
[ 2667.851778] usb-storage: Bulk Status S 0x53425355 T 0xa20 R 0 Stat 0x0
[ 2667.851783] usb-storage: scsi cmd done, result=0x0
[ 2667.851791] usb-storage: *** thread sleeping.
[ 2669.845103] usb-storage: queuecommand_lck called
[ 2669.845125] usb-storage: *** thread awakened.
[ 2669.845131] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2669.845135] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2669.845152] usb-storage: Bulk Command S 0x43425355 T 0x1923 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2669.845157] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.845264] usb-storage: Status code 0; transferred 31/31
[ 2669.845268] usb-storage: -- transfer complete
[ 2669.845272] usb-storage: Bulk command transfer result=0
[ 2669.845277] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2669.845756] usb-storage: Status code 0; transferred 8/8
[ 2669.845760] usb-storage: -- transfer complete
[ 2669.845764] usb-storage: Bulk data transfer result 0x0
[ 2669.845768] usb-storage: Attempting to get CSW...
[ 2669.845772] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.846152] usb-storage: Status code 0; transferred 13/13
[ 2669.846158] usb-storage: -- transfer complete
[ 2669.846163] usb-storage: Bulk status result = 0
[ 2669.846170] usb-storage: Bulk Status S 0x53425355 T 0x1923 R 0 Stat 0x0
[ 2669.846177] usb-storage: scsi cmd done, result=0x0
[ 2669.846188] usb-storage: *** thread sleeping.
[ 2669.846234] usb-storage: queuecommand_lck called
[ 2669.846263] usb-storage: *** thread awakened.
[ 2669.846271] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2669.846275] usb-storage:  00 00 00 00 00 00
[ 2669.846292] usb-storage: Bulk Command S 0x43425355 T 0x1924 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2669.846299] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.846391] usb-storage: Status code 0; transferred 31/31
[ 2669.846397] usb-storage: -- transfer complete
[ 2669.846403] usb-storage: Bulk command transfer result=0
[ 2669.846408] usb-storage: Attempting to get CSW...
[ 2669.846414] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.847385] usb-storage: Status code 0; transferred 13/13
[ 2669.847390] usb-storage: -- transfer complete
[ 2669.847394] usb-storage: Bulk status result = 0
[ 2669.847399] usb-storage: Bulk Status S 0x53425355 T 0x1924 R 0 Stat 0x1
[ 2669.847403] usb-storage: -- transport indicates command failure
[ 2669.847407] usb-storage: Issuing auto-REQUEST_SENSE
[ 2669.847414] usb-storage: Bulk Command S 0x43425355 T 0x1925 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2669.847419] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.847505] usb-storage: Status code 0; transferred 31/31
[ 2669.847508] usb-storage: -- transfer complete
[ 2669.847512] usb-storage: Bulk command transfer result=0
[ 2669.847517] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2669.848638] usb-storage: Status code -121; transferred 24/96
[ 2669.848643] usb-storage: -- short read transfer
[ 2669.848647] usb-storage: Bulk data transfer result 0x1
[ 2669.848650] usb-storage: Attempting to get CSW...
[ 2669.848655] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.848882] usb-storage: Status code -32; transferred 0/13
[ 2669.848886] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2669.848893] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2669.849015] usb-storage: usb_stor_clear_halt: result = 0
[ 2669.849020] usb-storage: Attempting to get CSW (2nd try)...
[ 2669.849024] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.849158] usb-storage: Status code 0; transferred 13/13
[ 2669.849164] usb-storage: -- transfer complete
[ 2669.849170] usb-storage: Bulk status result = 0
[ 2669.849177] usb-storage: Bulk Status S 0x53425355 T 0x1925 R 72 Stat 0x0
[ 2669.849184] usb-storage: -- Result from auto-sense is 0
[ 2669.849190] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2669.849198] usb-storage: Not Ready: Medium not present - tray closed
[ 2669.849204] usb-storage: scsi cmd done, result=0x2
[ 2669.849212] usb-storage: *** thread sleeping.
[ 2669.849276] usb-storage: queuecommand_lck called
[ 2669.849306] usb-storage: *** thread awakened.
[ 2669.849313] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2669.849318] usb-storage:  1e 00 00 00 00 00
[ 2669.849334] usb-storage: Bulk Command S 0x43425355 T 0x1926 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2669.849341] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.849574] usb-storage: Status code 0; transferred 31/31
[ 2669.849580] usb-storage: -- transfer complete
[ 2669.849586] usb-storage: Bulk command transfer result=0
[ 2669.849591] usb-storage: Attempting to get CSW...
[ 2669.849597] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.850260] usb-storage: Status code 0; transferred 13/13
[ 2669.850264] usb-storage: -- transfer complete
[ 2669.850268] usb-storage: Bulk status result = 0
[ 2669.850273] usb-storage: Bulk Status S 0x53425355 T 0x1926 R 0 Stat 0x0
[ 2669.850278] usb-storage: scsi cmd done, result=0x0
[ 2669.850285] usb-storage: *** thread sleeping.
[ 2669.850353] usb-storage: queuecommand_lck called
[ 2669.850368] usb-storage: *** thread awakened.
[ 2669.850373] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2669.850377] usb-storage:  00 00 00 00 00 00
[ 2669.850389] usb-storage: Bulk Command S 0x43425355 T 0xa21 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2669.850394] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.850506] usb-storage: Status code 0; transferred 31/31
[ 2669.850510] usb-storage: -- transfer complete
[ 2669.850514] usb-storage: Bulk command transfer result=0
[ 2669.850517] usb-storage: Attempting to get CSW...
[ 2669.850522] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.850629] usb-storage: Status code 0; transferred 13/13
[ 2669.850633] usb-storage: -- transfer complete
[ 2669.850637] usb-storage: Bulk status result = 0
[ 2669.850642] usb-storage: Bulk Status S 0x53425355 T 0xa21 R 0 Stat 0x0
[ 2669.850646] usb-storage: scsi cmd done, result=0x0
[ 2669.850653] usb-storage: *** thread sleeping.
[ 2669.850710] usb-storage: queuecommand_lck called
[ 2669.850721] usb-storage: *** thread awakened.
[ 2669.850726] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2669.850730] usb-storage:  00 00 00 00 00 00
[ 2669.850741] usb-storage: Bulk Command S 0x43425355 T 0xa22 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2669.850746] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2669.850882] usb-storage: Status code 0; transferred 31/31
[ 2669.850886] usb-storage: -- transfer complete
[ 2669.850889] usb-storage: Bulk command transfer result=0
[ 2669.850893] usb-storage: Attempting to get CSW...
[ 2669.850897] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2669.851016] usb-storage: Status code 0; transferred 13/13
[ 2669.851022] usb-storage: -- transfer complete
[ 2669.851026] usb-storage: Bulk status result = 0
[ 2669.851032] usb-storage: Bulk Status S 0x53425355 T 0xa22 R 0 Stat 0x0
[ 2669.851038] usb-storage: scsi cmd done, result=0x0
[ 2669.851046] usb-storage: *** thread sleeping.
[ 2671.845197] usb-storage: queuecommand_lck called
[ 2671.845218] usb-storage: *** thread awakened.
[ 2671.845225] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2671.845229] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2671.845245] usb-storage: Bulk Command S 0x43425355 T 0x1927 L 8 F 128 Trg 0 LUN 0 CL 10
[ 2671.845251] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.845391] usb-storage: Status code 0; transferred 31/31
[ 2671.845395] usb-storage: -- transfer complete
[ 2671.845399] usb-storage: Bulk command transfer result=0
[ 2671.845404] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2671.845882] usb-storage: Status code 0; transferred 8/8
[ 2671.845886] usb-storage: -- transfer complete
[ 2671.845890] usb-storage: Bulk data transfer result 0x0
[ 2671.845894] usb-storage: Attempting to get CSW...
[ 2671.845898] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.846276] usb-storage: Status code 0; transferred 13/13
[ 2671.846282] usb-storage: -- transfer complete
[ 2671.846288] usb-storage: Bulk status result = 0
[ 2671.846295] usb-storage: Bulk Status S 0x53425355 T 0x1927 R 0 Stat 0x0
[ 2671.846302] usb-storage: scsi cmd done, result=0x0
[ 2671.846313] usb-storage: *** thread sleeping.
[ 2671.846357] usb-storage: queuecommand_lck called
[ 2671.846371] usb-storage: *** thread awakened.
[ 2671.846378] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2671.846383] usb-storage:  00 00 00 00 00 00
[ 2671.846399] usb-storage: Bulk Command S 0x43425355 T 0x1928 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2671.846406] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.846522] usb-storage: Status code 0; transferred 31/31
[ 2671.846528] usb-storage: -- transfer complete
[ 2671.846533] usb-storage: Bulk command transfer result=0
[ 2671.846539] usb-storage: Attempting to get CSW...
[ 2671.846545] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.847511] usb-storage: Status code 0; transferred 13/13
[ 2671.847516] usb-storage: -- transfer complete
[ 2671.847520] usb-storage: Bulk status result = 0
[ 2671.847525] usb-storage: Bulk Status S 0x53425355 T 0x1928 R 0 Stat 0x1
[ 2671.847529] usb-storage: -- transport indicates command failure
[ 2671.847533] usb-storage: Issuing auto-REQUEST_SENSE
[ 2671.847540] usb-storage: Bulk Command S 0x43425355 T 0x1929 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2671.847545] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.847631] usb-storage: Status code 0; transferred 31/31
[ 2671.847635] usb-storage: -- transfer complete
[ 2671.847638] usb-storage: Bulk command transfer result=0
[ 2671.847644] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2671.848764] usb-storage: Status code -121; transferred 24/96
[ 2671.848769] usb-storage: -- short read transfer
[ 2671.848773] usb-storage: Bulk data transfer result 0x1
[ 2671.848777] usb-storage: Attempting to get CSW...
[ 2671.848781] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.849017] usb-storage: Status code -32; transferred 0/13
[ 2671.849022] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2671.849028] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2671.849161] usb-storage: usb_stor_clear_halt: result = 0
[ 2671.849167] usb-storage: Attempting to get CSW (2nd try)...
[ 2671.849173] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.849279] usb-storage: Status code 0; transferred 13/13
[ 2671.849285] usb-storage: -- transfer complete
[ 2671.849290] usb-storage: Bulk status result = 0
[ 2671.849297] usb-storage: Bulk Status S 0x53425355 T 0x1929 R 72 Stat 0x0
[ 2671.849304] usb-storage: -- Result from auto-sense is 0
[ 2671.849311] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2671.849318] usb-storage: Not Ready: Medium not present - tray closed
[ 2671.849324] usb-storage: scsi cmd done, result=0x2
[ 2671.849332] usb-storage: *** thread sleeping.
[ 2671.849396] usb-storage: queuecommand_lck called
[ 2671.849420] usb-storage: *** thread awakened.
[ 2671.849427] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2671.849432] usb-storage:  1e 00 00 00 00 00
[ 2671.849449] usb-storage: Bulk Command S 0x43425355 T 0x192a L 0 F 0 Trg 0 LUN 0 CL 6
[ 2671.849455] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.849511] usb-storage: Status code 0; transferred 31/31
[ 2671.849516] usb-storage: -- transfer complete
[ 2671.849520] usb-storage: Bulk command transfer result=0
[ 2671.849525] usb-storage: Attempting to get CSW...
[ 2671.849530] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.850386] usb-storage: Status code 0; transferred 13/13
[ 2671.850390] usb-storage: -- transfer complete
[ 2671.850394] usb-storage: Bulk status result = 0
[ 2671.850399] usb-storage: Bulk Status S 0x53425355 T 0x192a R 0 Stat 0x0
[ 2671.850404] usb-storage: scsi cmd done, result=0x0
[ 2671.850411] usb-storage: *** thread sleeping.
[ 2671.850479] usb-storage: queuecommand_lck called
[ 2671.850493] usb-storage: *** thread awakened.
[ 2671.850498] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2671.850502] usb-storage:  00 00 00 00 00 00
[ 2671.850513] usb-storage: Bulk Command S 0x43425355 T 0xa23 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2671.850518] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.850632] usb-storage: Status code 0; transferred 31/31
[ 2671.850636] usb-storage: -- transfer complete
[ 2671.850639] usb-storage: Bulk command transfer result=0
[ 2671.850643] usb-storage: Attempting to get CSW...
[ 2671.850647] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.850755] usb-storage: Status code 0; transferred 13/13
[ 2671.850759] usb-storage: -- transfer complete
[ 2671.850763] usb-storage: Bulk status result = 0
[ 2671.850768] usb-storage: Bulk Status S 0x53425355 T 0xa23 R 0 Stat 0x0
[ 2671.850773] usb-storage: scsi cmd done, result=0x0
[ 2671.850779] usb-storage: *** thread sleeping.
[ 2671.850835] usb-storage: queuecommand_lck called
[ 2671.850847] usb-storage: *** thread awakened.
[ 2671.850852] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2671.850855] usb-storage:  00 00 00 00 00 00
[ 2671.850867] usb-storage: Bulk Command S 0x43425355 T 0xa24 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2671.850872] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2671.851018] usb-storage: Status code 0; transferred 31/31
[ 2671.851023] usb-storage: -- transfer complete
[ 2671.851028] usb-storage: Bulk command transfer result=0
[ 2671.851032] usb-storage: Attempting to get CSW...
[ 2671.851038] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2671.851137] usb-storage: Status code 0; transferred 13/13
[ 2671.851141] usb-storage: -- transfer complete
[ 2671.851146] usb-storage: Bulk status result = 0
[ 2671.851152] usb-storage: Bulk Status S 0x53425355 T 0xa24 R 0 Stat 0x0
[ 2671.851158] usb-storage: scsi cmd done, result=0x0
[ 2671.851166] usb-storage: *** thread sleeping.
[ 2673.845096] usb-storage: queuecommand_lck called
[ 2673.845117] usb-storage: *** thread awakened.
[ 2673.845124] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2673.845128] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2673.845144] usb-storage: Bulk Command S 0x43425355 T 0x192b L 8 F 128 Trg 0 LUN 0 CL 10
[ 2673.845150] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.845272] usb-storage: Status code 0; transferred 31/31
[ 2673.845278] usb-storage: -- transfer complete
[ 2673.845283] usb-storage: Bulk command transfer result=0
[ 2673.845290] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2673.845645] usb-storage: Status code 0; transferred 8/8
[ 2673.845652] usb-storage: -- transfer complete
[ 2673.845657] usb-storage: Bulk data transfer result 0x0
[ 2673.845662] usb-storage: Attempting to get CSW...
[ 2673.845667] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.846536] usb-storage: Status code 0; transferred 13/13
[ 2673.846543] usb-storage: -- transfer complete
[ 2673.846549] usb-storage: Bulk status result = 0
[ 2673.846556] usb-storage: Bulk Status S 0x53425355 T 0x192b R 0 Stat 0x0
[ 2673.846563] usb-storage: scsi cmd done, result=0x0
[ 2673.846575] usb-storage: *** thread sleeping.
[ 2673.846633] usb-storage: queuecommand_lck called
[ 2673.846648] usb-storage: *** thread awakened.
[ 2673.846656] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2673.846660] usb-storage:  00 00 00 00 00 00
[ 2673.846677] usb-storage: Bulk Command S 0x43425355 T 0x192c L 0 F 0 Trg 0 LUN 0 CL 6
[ 2673.846684] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.846844] usb-storage: Status code 0; transferred 31/31
[ 2673.846850] usb-storage: -- transfer complete
[ 2673.846855] usb-storage: Bulk command transfer result=0
[ 2673.846860] usb-storage: Attempting to get CSW...
[ 2673.846866] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.848147] usb-storage: Status code 0; transferred 13/13
[ 2673.848152] usb-storage: -- transfer complete
[ 2673.848156] usb-storage: Bulk status result = 0
[ 2673.848162] usb-storage: Bulk Status S 0x53425355 T 0x192c R 0 Stat 0x1
[ 2673.848166] usb-storage: -- transport indicates command failure
[ 2673.848170] usb-storage: Issuing auto-REQUEST_SENSE
[ 2673.848178] usb-storage: Bulk Command S 0x43425355 T 0x192d L 96 F 128 Trg 0 LUN 0 CL 6
[ 2673.848184] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.848258] usb-storage: Status code 0; transferred 31/31
[ 2673.848261] usb-storage: -- transfer complete
[ 2673.848265] usb-storage: Bulk command transfer result=0
[ 2673.848270] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2673.849891] usb-storage: Status code -121; transferred 24/96
[ 2673.849895] usb-storage: -- short read transfer
[ 2673.849899] usb-storage: Bulk data transfer result 0x1
[ 2673.849903] usb-storage: Attempting to get CSW...
[ 2673.849907] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.850163] usb-storage: Status code -32; transferred 0/13
[ 2673.850171] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2673.850180] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2673.850281] usb-storage: usb_stor_clear_halt: result = 0
[ 2673.850288] usb-storage: Attempting to get CSW (2nd try)...
[ 2673.850294] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.850383] usb-storage: Status code 0; transferred 13/13
[ 2673.850392] usb-storage: -- transfer complete
[ 2673.850397] usb-storage: Bulk status result = 0
[ 2673.850404] usb-storage: Bulk Status S 0x53425355 T 0x192d R 72 Stat 0x0
[ 2673.850411] usb-storage: -- Result from auto-sense is 0
[ 2673.850418] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2673.850428] usb-storage: Not Ready: Medium not present - tray closed
[ 2673.850436] usb-storage: scsi cmd done, result=0x2
[ 2673.850448] usb-storage: *** thread sleeping.
[ 2673.850552] usb-storage: queuecommand_lck called
[ 2673.850567] usb-storage: *** thread awakened.
[ 2673.850574] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2673.850579] usb-storage:  1e 00 00 00 00 00
[ 2673.850599] usb-storage: Bulk Command S 0x43425355 T 0x192e L 0 F 0 Trg 0 LUN 0 CL 6
[ 2673.850606] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.850766] usb-storage: Status code 0; transferred 31/31
[ 2673.850772] usb-storage: -- transfer complete
[ 2673.850781] usb-storage: Bulk command transfer result=0
[ 2673.850786] usb-storage: Attempting to get CSW...
[ 2673.850791] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.851387] usb-storage: Status code 0; transferred 13/13
[ 2673.851391] usb-storage: -- transfer complete
[ 2673.851395] usb-storage: Bulk status result = 0
[ 2673.851400] usb-storage: Bulk Status S 0x53425355 T 0x192e R 0 Stat 0x0
[ 2673.851405] usb-storage: scsi cmd done, result=0x0
[ 2673.851413] usb-storage: *** thread sleeping.
[ 2673.851487] usb-storage: queuecommand_lck called
[ 2673.851501] usb-storage: *** thread awakened.
[ 2673.851506] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2673.851510] usb-storage:  00 00 00 00 00 00
[ 2673.851521] usb-storage: Bulk Command S 0x43425355 T 0xa25 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2673.851527] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.851633] usb-storage: Status code 0; transferred 31/31
[ 2673.851637] usb-storage: -- transfer complete
[ 2673.851641] usb-storage: Bulk command transfer result=0
[ 2673.851644] usb-storage: Attempting to get CSW...
[ 2673.851648] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.851756] usb-storage: Status code 0; transferred 13/13
[ 2673.851760] usb-storage: -- transfer complete
[ 2673.851764] usb-storage: Bulk status result = 0
[ 2673.851769] usb-storage: Bulk Status S 0x53425355 T 0xa25 R 0 Stat 0x0
[ 2673.851773] usb-storage: scsi cmd done, result=0x0
[ 2673.851780] usb-storage: *** thread sleeping.
[ 2673.851836] usb-storage: queuecommand_lck called
[ 2673.851847] usb-storage: *** thread awakened.
[ 2673.851852] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2673.851855] usb-storage:  00 00 00 00 00 00
[ 2673.851867] usb-storage: Bulk Command S 0x43425355 T 0xa26 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2673.851872] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.852020] usb-storage: Status code 0; transferred 31/31
[ 2673.852025] usb-storage: -- transfer complete
[ 2673.852030] usb-storage: Bulk command transfer result=0
[ 2673.852035] usb-storage: Attempting to get CSW...
[ 2673.852040] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.852138] usb-storage: Status code 0; transferred 13/13
[ 2673.852143] usb-storage: -- transfer complete
[ 2673.852148] usb-storage: Bulk status result = 0
[ 2673.852154] usb-storage: Bulk Status S 0x53425355 T 0xa26 R 0 Stat 0x0
[ 2673.852160] usb-storage: scsi cmd done, result=0x0
[ 2673.852168] usb-storage: *** thread sleeping.
[ 2673.859081] usb-storage: queuecommand_lck called
[ 2673.859099] usb-storage: *** thread awakened.
[ 2673.859105] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2673.859108] usb-storage:  00 00 00 00 00 00
[ 2673.859121] usb-storage: Bulk Command S 0x43425355 T 0xa27 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2673.859126] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2673.859264] usb-storage: Status code 0; transferred 31/31
[ 2673.859268] usb-storage: -- transfer complete
[ 2673.859272] usb-storage: Bulk command transfer result=0
[ 2673.859275] usb-storage: Attempting to get CSW...
[ 2673.859280] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2673.859385] usb-storage: Status code 0; transferred 13/13
[ 2673.859389] usb-storage: -- transfer complete
[ 2673.859393] usb-storage: Bulk status result = 0
[ 2673.859398] usb-storage: Bulk Status S 0x53425355 T 0xa27 R 0 Stat 0x0
[ 2673.859403] usb-storage: scsi cmd done, result=0x0
[ 2673.859410] usb-storage: *** thread sleeping.
[ 2675.845091] usb-storage: queuecommand_lck called
[ 2675.845114] usb-storage: *** thread awakened.
[ 2675.845120] usb-storage: Command GET EVENT/STATUS NOTIFICATION (10 bytes)
[ 2675.845124] usb-storage:  4a 01 00 00 10 00 00 00 08 00
[ 2675.845141] usb-storage: Bulk Command S 0x43425355 T 0x192f L 8 F 128 Trg 0 LUN 0 CL 10
[ 2675.845146] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.845264] usb-storage: Status code 0; transferred 31/31
[ 2675.845268] usb-storage: -- transfer complete
[ 2675.845272] usb-storage: Bulk command transfer result=0
[ 2675.845277] usb-storage: usb_stor_bulk_transfer_sglist: xfer 8 bytes, 1 entries
[ 2675.845635] usb-storage: Status code 0; transferred 8/8
[ 2675.845639] usb-storage: -- transfer complete
[ 2675.845642] usb-storage: Bulk data transfer result 0x0
[ 2675.845646] usb-storage: Attempting to get CSW...
[ 2675.845650] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.846262] usb-storage: Status code 0; transferred 13/13
[ 2675.846271] usb-storage: -- transfer complete
[ 2675.846276] usb-storage: Bulk status result = 0
[ 2675.846283] usb-storage: Bulk Status S 0x53425355 T 0x192f R 0 Stat 0x0
[ 2675.846290] usb-storage: scsi cmd done, result=0x0
[ 2675.846301] usb-storage: *** thread sleeping.
[ 2675.846345] usb-storage: queuecommand_lck called
[ 2675.846366] usb-storage: *** thread awakened.
[ 2675.846372] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2675.846377] usb-storage:  00 00 00 00 00 00
[ 2675.846394] usb-storage: Bulk Command S 0x43425355 T 0x1930 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2675.846401] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.846513] usb-storage: Status code 0; transferred 31/31
[ 2675.846522] usb-storage: -- transfer complete
[ 2675.846527] usb-storage: Bulk command transfer result=0
[ 2675.846532] usb-storage: Attempting to get CSW...
[ 2675.846538] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.847389] usb-storage: Status code 0; transferred 13/13
[ 2675.847394] usb-storage: -- transfer complete
[ 2675.847398] usb-storage: Bulk status result = 0
[ 2675.847403] usb-storage: Bulk Status S 0x53425355 T 0x1930 R 0 Stat 0x1
[ 2675.847407] usb-storage: -- transport indicates command failure
[ 2675.847411] usb-storage: Issuing auto-REQUEST_SENSE
[ 2675.847418] usb-storage: Bulk Command S 0x43425355 T 0x1931 L 96 F 128 Trg 0 LUN 0 CL 6
[ 2675.847423] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.847508] usb-storage: Status code 0; transferred 31/31
[ 2675.847512] usb-storage: -- transfer complete
[ 2675.847516] usb-storage: Bulk command transfer result=0
[ 2675.847521] usb-storage: usb_stor_bulk_transfer_sglist: xfer 96 bytes, 1 entries
[ 2675.848650] usb-storage: Status code -121; transferred 24/96
[ 2675.848655] usb-storage: -- short read transfer
[ 2675.848659] usb-storage: Bulk data transfer result 0x1
[ 2675.848663] usb-storage: Attempting to get CSW...
[ 2675.848668] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.848885] usb-storage: Status code -32; transferred 0/13
[ 2675.848890] usb-storage: clearing endpoint halt for pipe 0xc0008280
[ 2675.848896] usb-storage: usb_stor_control_msg: rq=01 rqtype=02 value=0000 index=81 len=0
[ 2675.849310] usb-storage: usb_stor_clear_halt: result = 0
[ 2675.849315] usb-storage: Attempting to get CSW (2nd try)...
[ 2675.849319] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.849388] usb-storage: Status code 0; transferred 13/13
[ 2675.849394] usb-storage: -- transfer complete
[ 2675.849399] usb-storage: Bulk status result = 0
[ 2675.849410] usb-storage: Bulk Status S 0x53425355 T 0x1931 R 72 Stat 0x0
[ 2675.849417] usb-storage: -- Result from auto-sense is 0
[ 2675.849424] usb-storage: -- code: 0x70, key: 0x2, ASC: 0x3a, ASCQ: 0x1
[ 2675.849433] usb-storage: Not Ready: Medium not present - tray closed
[ 2675.849443] usb-storage: scsi cmd done, result=0x2
[ 2675.849454] usb-storage: *** thread sleeping.
[ 2675.849539] usb-storage: queuecommand_lck called
[ 2675.849557] usb-storage: *** thread awakened.
[ 2675.849564] usb-storage: Command ALLOW_MEDIUM_REMOVAL (6 bytes)
[ 2675.849569] usb-storage:  1e 00 00 00 00 00
[ 2675.849589] usb-storage: Bulk Command S 0x43425355 T 0x1932 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2675.849596] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.849764] usb-storage: Status code 0; transferred 31/31
[ 2675.849770] usb-storage: -- transfer complete
[ 2675.849779] usb-storage: Bulk command transfer result=0
[ 2675.849784] usb-storage: Attempting to get CSW...
[ 2675.849790] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.850265] usb-storage: Status code 0; transferred 13/13
[ 2675.850271] usb-storage: -- transfer complete
[ 2675.850279] usb-storage: Bulk status result = 0
[ 2675.850286] usb-storage: Bulk Status S 0x53425355 T 0x1932 R 0 Stat 0x0
[ 2675.850292] usb-storage: scsi cmd done, result=0x0
[ 2675.850301] usb-storage: *** thread sleeping.
[ 2675.850403] usb-storage: queuecommand_lck called
[ 2675.850422] usb-storage: *** thread awakened.
[ 2675.850429] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2675.850434] usb-storage:  00 00 00 00 00 00
[ 2675.850454] usb-storage: Bulk Command S 0x43425355 T 0xa28 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2675.850461] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.850641] usb-storage: Status code 0; transferred 31/31
[ 2675.850647] usb-storage: -- transfer complete
[ 2675.850652] usb-storage: Bulk command transfer result=0
[ 2675.850657] usb-storage: Attempting to get CSW...
[ 2675.850664] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.850762] usb-storage: Status code 0; transferred 13/13
[ 2675.850767] usb-storage: -- transfer complete
[ 2675.850773] usb-storage: Bulk status result = 0
[ 2675.850780] usb-storage: Bulk Status S 0x53425355 T 0xa28 R 0 Stat 0x0
[ 2675.850786] usb-storage: scsi cmd done, result=0x0
[ 2675.850796] usb-storage: *** thread sleeping.
[ 2675.850865] usb-storage: queuecommand_lck called
[ 2675.850881] usb-storage: *** thread awakened.
[ 2675.850891] usb-storage: Command TEST_UNIT_READY (6 bytes)
[ 2675.850896] usb-storage:  00 00 00 00 00 00
[ 2675.850912] usb-storage: Bulk Command S 0x43425355 T 0xa29 L 0 F 0 Trg 0 LUN 0 CL 6
[ 2675.850919] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
[ 2675.851025] usb-storage: Status code 0; transferred 31/31
[ 2675.851030] usb-storage: -- transfer complete
[ 2675.851035] usb-storage: Bulk command transfer result=0
[ 2675.851040] usb-storage: Attempting to get CSW...
[ 2675.851046] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2675.851139] usb-storage: Status code 0; transferred 13/13
[ 2675.851144] usb-storage: -- transfer complete
[ 2675.851147] usb-storage: Bulk status result = 0
[ 2675.851152] usb-storage: Bulk Status S 0x53425355 T 0xa29 R 0 Stat 0x0
[ 2675.851157] usb-storage: scsi cmd done, result=0x0
[ 2675.851165] usb-storage: *** thread sleeping.
[user@localhost ~]$ 



[user@localhost ~]$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   202524  1 
snd_hda_intel          16311  2 
snd_hda_codec          52502  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               3582  1 snd_hda_codec
snd_pcm                46209  2 snd_hda_intel,snd_hda_codec
uvcvideo               46605  0 
rtl8192de             182025  0 
videodev               53102  1 uvcvideo
processor              20647  0 
snd_timer              11813  1 snd_pcm
r8169                  29131  0 
snd                    30016  10 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
thermal                 6138  0 
soundcore                596  1 snd
rtlwifi                91784  1 rtl8192de
snd_page_alloc          4829  2 snd_hda_intel,snd_pcm
uas                     5351  0 
usb_storage            35094  1 
i915                  288250  2 
drm_kms_helper         17832  1 i915
drm                   123912  3 i915,drm_kms_helper
i2c_algo_bit            3526  1 i915
button                  3359  1 i915
video                   9344  1 i915

---

### Post by chili555 on 2012-06-06
> Not sure what you mean by pastebinI meant this:> It would be most helpful if you could copy over those readings here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)My hope was that you wouldn't flood the forum with hundreds of lines of data, 99% of which is not relevant.> [user@localhost ~]$ dmesg
-storage: usb_stor_clear_halt: result = 0
[ 2613.866853] usb-storage: Attempting to get CSW (2nd try)...
[ 2613.866857] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
[ 2613.866972] usb-storage: Status code 0; transferred 13/13
[ 2613.866976] usb-storage: -- transfer complete
[ 2613.866980] usb-storage: Bulk status result = 0
[ 2613.866985] usb-storage: Bulk Status S 0x53425355 T 0x189f R 72 Stat 0x0
[ 2613.866990] usb-storage: -- Result from auto-sense is 0In this case, since every line involves usb-storage, it's 100% not relevant. It appears that something interesting is going on with a USB storage device, possibly a USB thumbdrive, and dmesg fills up to overflowing and is archived before we can see what Linpus is doing that Ubuntu isn't to start the wireless device. Can you please try:```
dmesg > jeff.txt
sudo cat /var/log/dmesg.1 >> jeff.txt
```Look for the file jeff.txt and post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

According to *lsmod*, Linpus is using rtl8192de as well.

---

### Post by Jeffbuntu on 2012-06-06
> **chili555 said:**
> I meant this:My hope was that you wouldn't flood the forum with hundreds of lines of data, 99% of which is not relevant.In this case, since every line involves usb-storage, it's 100% not relevant. It appears that something interesting is going on with a USB storage device, possibly a USB thumbdrive, and dmesg fills up to overflowing and is archived before we can see what Linpus is doing that Ubuntu isn't to start the wireless device. Can you please try:```
dmesg > jeff.txt
sudo cat /var/log/dmesg.1 >> jeff.txt
```Look for the file jeff.txt and post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

According to *lsmod*, Linpus is using rtl8192de as well.

Sorry - I'm pretty much a noob so please bear with me. 

[user@localhost ~]$ dmesg > jeff.txt
[user@localhost ~]$ sudo cat /var/log/dmesg.1 >> jeff.txt
cat: /var/log/dmesg.1: No such file or directory
[user@localhost ~]$ ls

[root@localhost log]# pwd
/var/log
[root@localhost log]# ls
audit     ConsoleKit  dmesg      gdm    maillog   pm-powersave.log  prelink  spooler             Xorg.0.log
boot.log  cron        dmesg.old  httpd  messages  pm-suspend.log    samba    wpa_supplicant.log  Xorg.0.log.old
btmp      cups        fax        mail   ntpstats  ppp               secure   wtmp                yum.log
[root@localhost log]# 


[user@localhost ~]$ dmesg > jeff.txt
[user@localhost ~]$ sudo cat /var/log/dmesg.1 >> jeff.txt
cat: /var/log/dmesg.1: No such file or directory
[user@localhost ~]$ ls
citizens card app.pdf  Desktop  Documents  Downloads  jeff.txt  Music  Pictures  Public  Templates  Videos
[user@localhost ~]$ cd /
[user@localhost /]$ sudo cat /var/log/dmesg.1 >> jeff.txt
bash: jeff.txt: Permission denied
[user@localhost /]$ su root
Password: 
[root@localhost /]# sudo cat /var/log/dmesg.1 >> jeff.txt
cat: /var/log/dmesg.1: No such file or directory
[root@localhost /]#

---

### Post by chili555 on 2012-06-07
> [root@localhost log]# ls
audit ConsoleKit [COLOR="Red"]dmesg[/COLOR] gdm maillog pm-powersave.log prelink spooler Xorg.0.log
boot.log cron [COLOR="Red"]dmesg.old[/COLOR] httpd messages pm-suspend.log samba wpa_supplicant.log Xorg.0.log.old
btmp cups fax mail ntpstats ppp secure wtmp yum.logAs we can see, Linpus organizes things a bit differently than Ubuntu. Let's try this again:```
dmesg > jeff.txt
sudo cat /var/log/dmesg.old >> jeff.txt
```Now please post the file jeff.txt here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

I will be fascinated to see the result.

---

### Post by Jeffbuntu on 2012-06-07
Should be there now.

---

### Post by chili555 on 2012-06-07
> **Jeffbuntu said:**
> Should be there now.When you pasted the text in, it gave a link, like this: [http://paste.ubuntu.com/1028576/](http://paste.ubuntu.com/1028576/)

Which is your link?

---

### Post by Jeffbuntu on 2012-06-07
> **chili555 said:**
> When you pasted the text in, it gave a link, like this: [http://paste.ubuntu.com/1028576/](http://paste.ubuntu.com/1028576/)

Which is your link?

Sorry it's [http://paste.ubuntu.com/1028547/](http://paste.ubuntu.com/1028547/)

---

### Post by chili555 on 2012-06-07
I see this, that I haven't seen before:> ieee80211 phy0: Selected rate control algorithm '[COLOR="Red"]rtl_rc[/COLOR]'When booted into Ubuntu, check:```
dmesg | grep ieee8
```Is it the same?

I will continue studying and post more.

EDIT: Ditto for this:> rtl92d_download_fw down load fw now```
dmesg | grep rtl92
```

---

### Post by Jeffbuntu on 2012-06-07
jeff@jeff-Veriton-N281G:~$ dmesg | grep ieee8
[   15.665378] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.694072] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
jeff@jeff-Veriton-N281G:~$ 

Looks the same.

jeff@jeff-Veriton-N281G:~$ dmesg | grep rtl192
jeff@jeff-Veriton-N281G:~$ 

Yields no results.



Took out the 192 to see if there was any difference.

jeff@jeff-Veriton-N281G:~$ dmesg | grep rtl
[   13.294390] rtl8192de 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.294408] rtl8192de 0000:02:00.0: setting latency timer to 64
[   13.296264] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   13.311595] rtl8192de: rtl8192ce: FW Power Save off (module option)
[   13.373726] rtl8192de: Driver for Realtek RTL8192DE WLAN interface
[   13.373745] rtl8192de: Loading firmware file rtlwifi/rtl8192defw.bin
[   15.665378] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.667349] rtlwifi: wireless switch is on
[   15.668327] rtl8192de 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.668345] rtl8192de 0000:02:00.1: setting latency timer to 64
[   15.672020] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   15.685609] rtl8192de: rtl8192ce: FW Power Save off (module option)
[   15.694072] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[   15.701429] rtlwifi: wireless switch is on

---

### Post by chili555 on 2012-06-07
> rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!That's the only suspicious thing I see. As you might surmise, it's not listed in pastebin, i.e. Linpus.

Please hook up the ethernet and do:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```After it and its dependencies install, please reboot. Check again:```
dmesg | grep rtl
```Thanks.

---

### Post by Jeffbuntu on 2012-06-07
Well something interesting happened on the reboot.The wireless icon in the top RH corner of the screen flashed on momentarily and for a brief moment it appeared that it could see some wap's.  Unfortunately this seems to have been short lived.  I'm back to seeing no access points again.

Output: 

jeff@jeff-Veriton-N281G:~$ dmesg | grep rtl
[   16.019676] rtl8192de 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.019695] rtl8192de 0000:02:00.0: setting latency timer to 64
[   16.023815] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   16.036993] rtl8192de: rtl8192ce: FW Power Save off (module option)
[   16.039381] rtl8192de: Driver for Realtek RTL8192DE WLAN interface
[   16.039390] rtl8192de: Loading firmware file rtlwifi/rtl8192defw.bin
[   17.711594] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   17.732823] rtlwifi: wireless switch is on
[   17.734904] rtl8192de 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   17.734923] rtl8192de 0000:02:00.1: setting latency timer to 64
[   17.736012] rtl8192de:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!
[   17.752074] rtl8192de: rtl8192ce: FW Power Save off (module option)
[   17.838185] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[   17.859916] rtlwifi: wireless switch is on

---

### Post by chili555 on 2012-06-07
Frankly, I'm out of ideas. It's obviously a bug, perhaps in the driver because:> [COLOR="Red"]rtl8192de[/COLOR]:_rtl92de_efuse_update_chip_version():<0-0> Unkown CUT!I suggest you report a bug. If the developers think it's actually against Network Manager, they'll refer you elsewhere. I recommend you follow through vigorously so this gets fixed for your Ubuntu brothers and sisters.

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

They will ask for a lot of data and you should feel free to also refer them to this thread.

I wish I had a better solution.

---

### Post by Jeffbuntu on 2012-06-07
> **chili555 said:**
> Frankly, I'm out of ideas. It's obviously a bug, perhaps in the driver because:I suggest you report a bug. If the developers think it's actually against Network Manager, they'll refer you elsewhere. I recommend you follow through vigorously so this gets fixed for your Ubuntu brothers and sisters.

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

They will ask for a lot of data and you should feel free to also refer them to this thread.

I wish I had a better solution.

No worries - you've been more than generous with your help.  Thanks.  I'll get a bug logged asap.  I even went out and bought another wireless router just in the off-chance it was something related to wireless standards etc.  But still no luck.  No loss though because the old linksys I had been using didn't support the newer wireless speeds.

Thanks again

regards

Jeff

---

### Post by Jeffbuntu on 2012-06-07
Logged bug #1010226 

Thanks again Chili

---

### Post by linux6994 on 2012-06-27
I have the same PC, it has a dual channel N card, mine tries to connect to my BG APs but it fails. I need to puck up a N router someday, direct connect works fine. I will of course keep working on it to connect to my BG, like it should it should drop to one channel automatically. With the 8192de driver I can see all networks but not connecting on WPA2 shared key?

bedroom@bedroom-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:de:2b:e2:71:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11an
       resources: irq:18 ioport:d800(size=256) memory:feafc000-feafffff
  *-network:1
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: wlan1
       version: 01
       serial: 74:de:2b:e2:79:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192de driverversion=3.2.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:d400(size=256) memory:feaf8000-feafbfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:ab:6c:0b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.031.00-NAPI duplex=full ip=192.168.1.99 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff

---

### Post by Jeffbuntu on 2012-11-01
Latest update on mine.  Still no solution - I've now used the lan connection into a spare switch I had lying around.  Using remote desktop on my laptop to access it.   Not an ideal solution but the only one that really works at the moment.

---

