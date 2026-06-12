---
title: "Wireless not working: driver installed, network disabled"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by shpar on 2010-08-17
Hi
I'm a complete beginner at Ubuntu and Linux. I was trying to get my Belkin F5D7000 v1133yy wireless card to work. I followed [http://help.ubuntu.com/community/WifiDocs/Device/F5D7000](http://help.ubuntu.com/community/WifiDocs/Device/F5D7000) , installing windows drivers through ndiswrapper but even though ndiswrapper -l gives 
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 1: ignoring bad line starting with '&#65279;#'
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
oem99 : invalid driver!
raspppoe : invalid driver!
```i cant seem to find the wireless connection in network tools, nor an option to enable it or whatever.

I tried some troubleshooting and blacklisting b43 in /etc/modprobe.d/blacklist.conf resulted in ubuntu not even recognising the device and returning "no wireless extensions" to iwconfig.

Here are a few results:
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```sudo ifconfig wlan0 up
```
SIOCSIFFLAGS: No such file or directory
```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```sudo lshw -C network
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:50:fc:56:94:07
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:c000(size=256) memory:eb002000-eb0020ff memory:20000000-2000ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:eb000000-eb001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:0b:49:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```Thank you for taking your time and looking at this. I have tried a million things and none has worked until now.

---

### Post by shpar on 2010-08-18
Solved it!

I blacklisted b43 and did: 
sudo update-initramfs -k all -u
after restart there was no wireless device detected and lshw -C network gave : UNCLAIMED
then I typed in: sudo modprobe ndiswrapper and the device popped up working
I also had to type :
echo 'ndiswrapper' | sudo tee -a /etc/modules
to make it work without having to type in modprobe ndiswrapper after every reboot.

Thanks sticky post, sorry for not completely checking it through before posting.

---

