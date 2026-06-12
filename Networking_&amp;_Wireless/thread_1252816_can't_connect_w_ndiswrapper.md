---
title: "can't connect w/ ndiswrapper"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by w00ly on 2009-08-29
Hi all, I was having problems with my wireless adapter (wusb54g v4) going too slow on my lan (around 300kb/sec). Also it would not show proper signal strength in the plasma widget, under bit rate would have random numbers like 3000 mbit/s and 1000mbit/s, link quality was low (in the 30s) and the link light didnt blink.

So I installed the proper linksys driver via these instructions [http://ubuntuforums.org/showthread.php?t=588045&page=13](http://ubuntuforums.org/showthread.php?t=588045&page=13) but now I cant get connected. The plasma widget is stuck on "activating" (not a very useful tooltip). 
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf will associate but dhclient will not pull an IP. 
> DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
No DHCPOFFERS received.                                     
No working leases in persistent database - sleeping.Also cant get airmon-ng to work any more:
> 
Interface       Chipset         Driver

wlan0           Unknown         ndiswrapper (MONITOR MODE NOT SUPPORTED)Probably something simple but I have no idea...never used ndiswrapper before but I followed those directions to a T (well, I installed ndiswrapper-common and ndiswrapper-utils from apt)
> root@woolybox:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0c:41:6a:b9:72
          inet6 addr: fe80::20c:41ff:fe6a:b972/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20725 (20.7 KB)  TX bytes:30467 (30.4 KB)

root@woolybox:~# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"interwebs"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:64:1D:D6
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:xxxxxxxxxxxxxxxxxxxxxxxxxxxx   Security mode:restricted
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by w00ly on 2009-08-29
Bump
the other weird problem (though not very important) i'm having with it is the connection shows as wep only in the plasma network manager (yellow shield symbol). It still accepts the WPA passkey, and reports as WPA in it's configuration page and in airodump...just makes me nervous that the network manager is trying to tell me my network's unsecure. It's strange too because I have 7 other wireless networks in range and they all report their proper security

---

### Post by w00ly on 2009-08-29
bump
root@woolybox:~# dmesg|grep lan                                                       
[ 11.821226] wlan0: ethernet device 00:0c:41:6a:b9:72 using NDIS driver: rt2500usb, version: 0x20000, NDIS version: 0x500, vendor: 'Linksys Wireless-G USB Network A', 13B1:000D.F.conf 
[ 11.826742] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   27.470751] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                   
[   98.106380] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                              
[  108.472025] wlan0: no IPv6 routers present                                                                  
[  171.997540] ndiswrapper (mp_reset:64): wlan0 is being reset                                                 
[  172.042743] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                   
[  539.508681] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                              
[  549.676026] wlan0: no IPv6 routers present                                                                  
[ 1336.188400] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                   
[ 1339.616863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                              
[ 1357.528033] wlan0: no IPv6 routers present                                                                  
[ 1460.518514] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1461.793030] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1472.716031] wlan0: no IPv6 routers present
[11837.564443] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[22840.335084] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[22850.696032] wlan0: no IPv6 routers present

---

### Post by w00ly on 2009-08-29
[IMG]http://twitpic.com/show/full/frp1s[/IMG]

---

### Post by w00ly on 2009-08-29
SUCCESS (somewhat). I saw one instance of rt2x00 in /var/log/syslog or lshw or ndiswrapper -l or dmesg (or one of the other commands..) but either way, blacklisted it in /etc/modprobe.d/blacklist.conf, rebooted and it worked! Unfortunately after finally getting that to work, the original problem of slow network speed continues :\ Transfering from the wusb54g PC to an ethernet PC I can still only get a max of 300-320kb/sec no matter which transfer protocol I use. The router is set on "G only mode" and I used iwconfig to set the rate to 54g (which the plasma applet shows properly now). If anyone has any advice, please let me know :\

---

### Post by w00ly on 2009-08-30
Ok, I was wrong. It connected fine for a little while, but after a reboot it's getting stuck when pulling an IP again. I have no idea why, because I didnt touch a single setting. I tried to rmmod rt2500usb and rt2x00usb but it says those modules dont exist! Please help, i'm really in the dark here :(

---

### Post by w00ly on 2009-08-30
[IMG]http://twitpic.com/show/full/fwkzg[/IMG]

I tried compiling from source but that didnt solve anything
PLEASE
PLEASE
PLEASE
PLEASE
PLEASE
PLEASE
PLEASE
PLEASE
HELP!

---

### Post by w00ly on 2009-08-30
[IMG]http://twitpic.com/show/full/fxt9p[/IMG]

I've tried using the default rt2500usb drivers, the v2 XP drivers with ndiswrapper, the v3 vista driver with ndiswrapper and the rt2570usb driver.

---

### Post by w00ly on 2009-08-31
If no one knows how to get ndiswrapper working, i'd be more than happy to use the rt2500usb driver if anybody knows how to get it to have the proper signal strength and transfer speeds. The plasma widget shows a bit rate of 36,000mbit/s while only showing 1mbit in iwconfig
```
root@woolybox:~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"interwebs"
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:11:50:64:1D:D6
          **Bit Rate=1 Mb/s**   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:   Security mode:open
          Power Management:off
          **Link Quality=37/100**  Signal level:-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
as you can see the signal level is good but the link quality is awful

---

### Post by w00ly on 2009-08-31
[IMG]http://twitpic.com/show/full/fz77a[/IMG]

---

### Post by w00ly on 2009-08-31
[IMG]http://twitpic.com/show/full/g004j[/IMG]

---

### Post by w00ly on 2009-08-31
Running out of bump pictures :\
Reposting from first page:
If no one knows how to get ndiswrapper working, i'd be more than happy to use the rt2500usb driver if anybody knows how to get it to have the proper signal strength and transfer speeds. The plasma widget shows a bit rate of 36,000mbit/s while only showing 1mbit in iwconfig
```
root@woolybox:~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"interwebs"
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:11:50:64:1D:D6
          **Bit Rate=1 Mb/s**   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:   Security mode:open
          Power Management:off
          **Link Quality=37/100**  Signal level:-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```as you can see the signal level is good but the link quality is awful

---

