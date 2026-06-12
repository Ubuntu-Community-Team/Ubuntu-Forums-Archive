---
title: "TP-Link wifi USB adapter issues: scanning, master mode"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by 0x656b694d on 2010-06-10
Hello,

I got two issues with my wifi usb adapter:
1) it cannot see any networks around
2) i cannot setup it in master mode to use my PC as a router

As far as i can see, the device is recognized and the correct driver (rt73usb) is loaded. I was able to connect to a laptop somehow (the laptop could see other networks and the adapter's PC-to-PC network).
I'd like to make it work as a router, i.e. share my internet connection (eth0) via wlan0.

Thanks.

Here is what i have:
```

Ubuntu 10.04
Linux 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

TP-Link TL-WN321G wifi usb adapter as seen as
Bus 001 Device 006: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

$ lsmod | grep rt
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11260  1 rt73usb
rt2x00lib              32133  2 rt73usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211

$ lshw -C network
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:27:19:b1:bf:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

$ iwlist wlan0 scan
wlan0     No scan results

$ dmesg
[13517.803590] phy0: Selected rate control algorithm 'minstrel'
[13517.804610] Registered led device: rt73usb-phy0::radio
[13517.804627] Registered led device: rt73usb-phy0::assoc
[13517.804643] Registered led device: rt73usb-phy0::quality
[13517.805391] usbcore: registered new interface driver rt73usb
[13517.860324] rt73usb 1-5.1.2:1.0: firmware: requesting rt73.bin
[13518.096351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13552.594228] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14433.623004] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15438.582666] wlan0: Trigger new scan to find an IBSS to join
[15446.749667] wlan0: Creating new IBSS network, BSSID 32:70:fd:39:32:35
[15449.112858] wlan0: no IPv6 routers present
[15484.103562] wlan0: Creating new IBSS network, BSSID e2:e2:46:7d:e0:5a

```

---

### Post by 0x656b694d on 2010-06-13
second issue is solved. I just needed to disable the eth0 interface on the notebook that i wanted to share the Internet with.

---

### Post by airtonix on 2010-10-14
see, what would be REALLY awesome : 

if you shared how you go over you're intial problem.

expecting others to help you without helping them is fairly selfish.

---

### Post by 0x656b694d on 2011-02-23
Oops. Sorry for such a delay.
Not sure I understood your wishes.
I didn't solve the issue. Sometimes the stick can see the networks, sometimes not. It works well as an ad-hoc wifi access point on Ubuntu 10.10 without any extra manipulation than standard creating a wifi network.

The issue now is that my android cannot connect to this ad-hoc.
I was able to make an APN with internet sharing in Vista, but don't see the super check box in Ubuntu.

---

### Post by 0x656b694d on 2011-04-18
Wow, got master mode working!

[LIST=1]
[*] No blacklisted wireless drivers.
[*] Have a hostapd installed.
[*] Have a conf file like this:
```

$ cat hostapd.conf
interface=wlan0
driver=nl80211
ssid=test
channel=1

```
[*] Run:
```
sudo hostapd hostapd.conf
```
or for daemon mode:
```
sudo hostapd -B hostapd.conf
```
[/LIST]

---

