---
title: "Asus USB-N13 Wireless-N300 connection issue (Almost working)"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by victor97 on 2013-03-31
Dear Ubuntu users,

I installed the latest XBMCBuntu linux on my dell desktop, to use this system as my mediacenter.
This is working ok and without any errors.

I also bought an Asus USB N13 wireless network adaptor to connect to my wireless router. As I am a beginner with Linux I have bought this adaptor as it was mentioned on the box that it is linux supported. Nevertheless, I have issues getting it working.
I do see my wireless networks (also mine), but it is not accepting my password to connect to my wireless router (and I am 100% sure my password is correct).

Hereby some info from my system:
```
[FONT=Courier New]xbmc@XBMC-Client:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10 - XBMCbuntu"
Linux XBMC-Client 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:41:11 UTC 2013 i686 i686 i686 GNU/Linux

lsusb
xbmc@XBMC-Client:~$ lsusb
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 002: ID 1241:e000 Belkin
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 045e:002b Microsoft Corp. Internet Keyboard Pro


iwconfig
xbmc@XBMC-Client:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

lo        no wireless extensions.

eth0      no wireless extensions.


lsmod | grep rtl
xbmc@XBMC-Client:~$ lsmod | grep rtl
rtl8192cu              66628  0
rtl8192c_common        47076  1 rtl8192cu
rtlwifi                64173  1 rtl8192cu
mac80211              461203  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              175574  2 rtlwifi,mac80211
 
dmesg | grep -e rtl -e wlan
xbmc@XBMC-Client:~$ dmesg | grep -e rtl -e wlan
[   13.627659] rtl8192cu: Chip version 0x11
[   15.060538] rtl8192cu: MAC address: 50:46:5d:af:f8:56
[   15.060546] rtl8192cu: Board Type 0
[   15.060782] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   15.060915] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   15.066303] usbcore: registered new interface driver rtl8192cu
[   15.331211] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.333186] rtlwifi: wireless switch is on
[   21.298534] rtl8192cu: MAC auto ON okay!
[   21.331423] rtl8192cu: Tx queue select: 0x05
[   21.700358] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.701110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.534356] wlan0: authenticate with 00:23:69:30:02:6b
[   23.549497] wlan0: send auth to 00:23:69:30:02:6b (try 1/3)
[   23.552592] wlan0: authenticated
[   23.568033] wlan0: associate with 00:23:69:30:02:6b (try 1/3)
[   23.570312] wlan0: RX AssocResp from 00:23:69:30:02:6b (capab=0x411 status=0 aid=4)
[   23.570464] wlan0: associated
[   23.570560] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.551967] wlan0: deauthenticated from 00:23:69:30:02:6b (Reason: 15)
[   32.401277] wlan0: authenticate with 00:23:69:30:02:6b
[   32.419271] wlan0: send auth to 00:23:69:30:02:6b (try 1/3)
[   32.428478] wlan0: authenticated
[   32.448046] wlan0: associate with 00:23:69:30:02:6b (try 1/3)
[   32.450221] wlan0: RX AssocResp from 00:23:69:30:02:6b (capab=0x411 status=0 aid=4)
[   32.450332] wlan0: associated
[   40.431681] wlan0: deauthenticated from 00:23:69:30:02:6b (Reason: 15)
[   41.265156] wlan0: authenticate with 00:23:69:30:02:6b
[   41.277624] wlan0: send auth to 00:23:69:30:02:6b (try 1/3)
[   41.303079] wlan0: authenticated
[   41.316038] wlan0: associate with 00:23:69:30:02:6b (try 1/3)
[   41.321806] wlan0: RX AssocResp from 00:23:69:30:02:6b (capab=0x411 status=0 aid=4)
[   41.321942] wlan0: associated
[   48.003582] wlan0: deauthenticating from 00:23:69:30:02:6b by local choice (reason=3)
[/FONT]
```

On the internet I have seen the following command, but this is not working for me:
```
[FONT=Courier New]sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1[/FONT]

```

I also updated my linux-backports-modules, this was mentioned on the internet and could solve this issue. This also didn't resolved it.

I hope someone can help me as I don't know what to do.
Many thanks!

Regards,
Victor

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by victor97 on 2013-04-01
ahallubuntu,

MANY MANY MANY THANKS!
It is working! :) You made my day! I was trying to get it working for 4 weeks and you solved it within 24 hours!

Many thanks!

Regards,
Victor

---

### Post by victor97 on 2013-04-11
I haven't used the pc for a week and now i have the same issue again. I tried the same, but it is not working :(
Any ideas how I can resolve this issue?

thanks in advance!

---

### Post by Hadaka on 2013-04-11
Hi, chilli555 just fixed one of these today..
see post #23

[http://ubuntuforums.org/showthread.php?t=2133710&page=3](http://ubuntuforums.org/showthread.php?t=2133710&page=3)

make note of the final entry on that thread. Next update you will
have to compile again.
good luck.

---

### Post by ahallubuntu on 2013-04-11
~

---

### Post by ahallubuntu on 2013-04-11
~

---

### Post by victor97 on 2013-04-12
I know the issue. The pc was moved to another room, very close by my living room. If I move the pc back to the living room, it is working. But when I put it back to another room it is not working. Somit seems like the wifi signal is not strong enough. But this is weird because I can connect in that room with my phone and ipad. also, the router is only 2,5 meters away from the pc and the door is open. Can I change a setting so the adaptop can read the wifi signal better? This performance is really poor. Or do I make a wrong assumption?

thanks for your help, it is much appreciated!

---

### Post by Darth Buh on 2013-05-10
Blacklisting causes kernel panic crashes on 64-bit Ubuntu 12.04.

---

