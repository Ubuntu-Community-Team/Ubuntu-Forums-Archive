---
title: "USB Wireless Works With NM, not with terminal config"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by whitewizardcoder on 2010-10-06
I recently purchased a Netgear WG111v2 802.11g wireless usb adapter for use with an ARM embedded device (loaded with the ARM port of ubuntu).  It uses the rtl8187 driver and, when attached to my laptop, connects perfectly through NetworkManager.  Unfortunately, I am not working with any ui on my embedded device so I won't have that luxury and must connect via the terminal.  Unfortunately, I'm not able to connect this way on either my laptop or the embedded device (they both CAN pick up surrounding AP's through iwlist scan though).  I'm able to set the ssid through
```
sudo iwlist wlan0 essid "woot"
```
and my access point is temporarily open (no wep/wpa).  When I bring the device up using
```
sudo ifconfig wlan0 up
```
the light on the adapter starts blinking but I'm still not able to connect.  iwconfig wlan0 outputs:
```
wlan0     IEEE 802.11bg  ESSID:"woot"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

and dmesg says:
```
[ 9898.211522] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

When connecting via Network Manager, iwconfig wlan0 output is normal for a connected wireless and dmesg outputs a whole bunch of messages:
```
[10140.729783] wlan0: direct probe to AP xx:xx:xx:xx:xx:xx (try 1)
[10140.928057] wlan0: direct probe to AP xx:xx:xx:xx:xx:xx (try 2)
[10140.931506] wlan0: direct probe responded
[10140.931509] wlan0: authenticate with AP xx:xx:xx:xx:xx:xx (try 1)
[10140.933895] wlan0: authenticated
[10140.933914] wlan0: associate with AP xx:xx:xx:xx:xx:xx (try 1)
[10140.936387] wlan0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x401 status=0 aid=2)
[10140.936390] wlan0: associated
[10140.939986] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Is there something I am missing when trying to bring up this wireless interface?  Again, I know it works with the driver since it connects with Network Manager, I just can't connect through the terminal.

---

### Post by chili555 on 2010-10-06
> sudo ifconfig wlan0 upI think you need to specify an IP address or specify DHCP; viz:```
sudo ifconfig wlan0 192.168.1.xyz up
```Or:```
sudo dhclient wlan0
```

---

