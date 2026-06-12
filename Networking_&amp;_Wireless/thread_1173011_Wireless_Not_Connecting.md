---
title: "Wireless Not Connecting"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by Julian_318 on 2009-05-29
Issue: I can see my network and several others when I click on the wireless network connection icon.
I have 4/4 bars (sometimes 3/4 but that worked before just fine)
When I input my wireless Password my icon just thinks for a while and then asks for it again. I know I am inputting the correct password and have selected the only drop down "Wireless Security" option.
 
I am completely new to ubuntu and have just installed today. I run 9.04 64-bit. I 've searched for hours to no avail. Please help!

j@j-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:e1:5a:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:11:3d:da
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:31:b0:06:8c:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


j@j-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by reismith on 2009-05-29
I am having a very similar issue. I'm currently running v8.04, the 
EEE varient, with no issues but am looking to upgrade to the jaunty EEE Remix varient. I downloaded Remix, installed on a USB drive, and successfully booted to it. It saw my home wireless network immediately and asked for the password as expected for the first connect. But the jaunty boot failed to recognize the correct password (same one used for the 8.04 install and for my Windows PCs) that time and on several subsequent reattempts. The system sees my wireless router, just doesn't seem to resolve the password correctly. I am using a Asus EEE 1000. Anybody have any ideas?

---

