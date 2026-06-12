---
title: "RTL8187B wireless connection very slow"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by BubuIIC on 2012-02-02
Hi there,
I just tried to get Ubuntu working on my notebook. Everything seemed to be fine until I noticed that my wireless connection is just crawling along at 100-120 kb/s, even on the local network, no internet involved.

I discovered that the card manages to transfer at full speed after an  "ifconfig wlan1 down & up" for a bit, but slows down again after a minute or so.

After reading some threads here, my best guess is, that the RTL8187B driver is the cause, as it seems to have a history for being unstable and slow.
So my question is, anyone has a different guess, some things I might try to get a stable connection?
What is the status of the RTL8187B Driver? Will it get fixed eventually or is it abandoned? Who exactly is working on it, where might I get more info?

Thanks a lot for your help!

Below are some specs:
Using a fresh Ubuntu 11.10 with all updates.

```
$ uname -mr
3.0.0-15-generic i686
``````
 $ lsusb | grep Realtek
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
``````
$ iwconfig wlan1
wlan1     IEEE 802.11bg  ESSID:"-----"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:25:5E:1C:4C:33   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0

``````
$ lshw -C Network
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan1
       serial: 00:15:af:81:dc:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.0.0-15-generic firmware=N/A ip=192.168.1.55 link=yes multicast=yes wireless=IEEE 802.11bg
``````
$ lsmod | grep rtl
rtl8187                56323  0 
mac80211              393459  1 rtl8187
cfg80211              172427  2 rtl8187,mac80211
eeprom_93cx6           12653  1 rtl8187

```

---

### Post by BubuIIC on 2012-02-05
Bump.
Anyone any ideas?

---

