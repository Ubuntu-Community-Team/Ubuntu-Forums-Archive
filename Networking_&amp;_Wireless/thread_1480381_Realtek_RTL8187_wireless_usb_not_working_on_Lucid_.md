---
title: "Realtek RTL8187 wireless usb not working on Lucid 10.04 ( Hard blocked )"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Dearhell on 2010-05-11
So I have a dell laptop and a Realtek RTL8187 device. 

The device it's properly recognized and iwlist scan even list the networks, but the "activate wifi network" on the network manager on right-top of the screen it's grey and therefore cannot be activated. 

This seems to be the problem ( rfkill list ouput ):

> 1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: yes

So I've tried rmmod dell_laptop but still the same output with rfkill list.

My dell laptop doesn't have any button to stop or start the wifi ( Dell Inspiron 9300 ).

This same device worked fine with Ubuntu 9.10, stopped working after upgrade to Lucid 10.04

---

### Post by Dearhell on 2010-05-12
Bump!

---

### Post by chili555 on 2010-05-12
Let's have a look at:```
lsmod
iwconfig
```Thanks.

---

### Post by chili555 on 2010-05-12
> My dell laptop doesn't have any button to stop or start the wifi ( Dell Inspiron 9300 ).When you press Fn+F2, does rfkill change? Please do:```
sudo tail -f /var/log/messages
```Leave it open as you press the key combination. Does the kernel recognize the buttons at all?

---

### Post by Dearhell on 2010-05-12
> When you press Fn+F2, does rfkill change? 

That did the trick, thanks! =D>

---

### Post by pejal1312 on 2010-12-10
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"STREAMYX@APB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:5D:4C:E6:C1:2E   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
@ubuntu:~$ sudo tail -f /var/log/messages[sudo] password for cipher: 
Dec 10 15:56:56 ubuntu kernel: [   13.680420] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
Dec 10 15:56:56 ubuntu kernel: [   13.824440] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 10 15:56:56 ubuntu kernel: [   13.903424] ppdev: user-space parallel port driver
Dec 10 15:57:01 ubuntu kernel: [   19.380635] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 10 15:57:01 ubuntu kernel: [   19.401090] r8169: eth0: link up
Dec 10 15:57:01 ubuntu kernel: [   19.401104] r8169: eth0: link up
Dec 10 15:57:03 ubuntu kernel: [   20.491355] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[COLOR=Red]Dec 10 15:57:05 ubuntu kernel: [   23.346672] ADDRCONF(NETDEV_UP): wlan1: link is not ready[/COLOR]
Dec 10 15:57:11 ubuntu pulseaudio[1476]: ratelimit.c: 13 events suppressed
Dec 10 15:57:13 ubuntu kernel: [   31.085146] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

model hornettek usb dongle ht-2223bk

can anyone help me??

---

### Post by grahammechanical on 2010-12-10
You have posted a new question on an old thread that should have been marked as solved.

From the information that you have provided you have 2 wlan. And wlan0 is connecting to a router/modem, that has the connection name or ESSID of STREAMYX@APB.

Note also the comment: > Dec 10 15:57:01 ubuntu kernel: [   19.380635] ADDRCONF(NETDEV_UP): wlan0: link is not ready and now this comment: > Dec 10 15:57:13 ubuntu kernel: [   31.085146] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes readyWhat are you doing to try to connect? And are you using the wireless adapter/card/device that is connected to the modem? Are you trying to use wlan1 when you should be trying to use wlan0?

These are just some questions that I would ask myself.

Regards.

---

