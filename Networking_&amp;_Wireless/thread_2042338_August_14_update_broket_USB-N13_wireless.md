---
title: "August 14 update broket USB-N13 wireless"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by Placidia428 on 2012-08-14
I am using LTS 12.04 and an ASUS USB-N13 wireless usb dongle. It was working this morning, then after I accepted the updates, I lost the ability to connect to the Internet. It can see the wireless network, but halts at "Authentication required by wireless network."

The driver for this is rtl8192cu. I tried modprobe, but to no effect.

This is what I found:

placidia@Sandbox:~$ lsmod | grep rtl
rtl8192cu             103297  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111202  1 rtl8192cu
mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211

placidia@Sandbox:~$ dmesg | grep rtl
[   14.332961] rtl8192cu: MAC address: c8:60:00:d3:8a:43
[   14.332965] rtl8192cu: Board Type 0
[   14.373251] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   14.375298] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.375707] usbcore: registered new interface driver rtl8192cu
[   15.063830] rtl8192cu: MAC auto ON okay!
[   15.096596] rtl8192cu: Tx queue select: 0x05
[   15.097348] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin

placidia@Sandbox:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


I also tried rfkill list all.  I got:

0: phy0: Wireless LAN

               Soft blocked: no
               Hard blocked: no

I hope someone can help.

Cheers.

---

