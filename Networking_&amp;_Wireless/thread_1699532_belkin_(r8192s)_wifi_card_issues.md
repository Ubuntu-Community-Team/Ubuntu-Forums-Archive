---
title: "belkin (r8192s) wifi card issues"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by n-alexander on 2011-03-03
Please help. I have a Belkin WiFi USB thing.

I did this: [http://ubuntuforums.org/showthread.php?t=1515747](http://ubuntuforums.org/showthread.php?t=1515747)
which is same as this but with product number per lsusb: [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)

The card can see my network, but can not connect. I've removed all obstracles I could - open network, no data encryption, no MAC filtering. Still, dmesg shows the below repeated in a loop over and over again:

```
[ 1831.250862] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1831.252868] This is enable turbo mode IE process
[ 1831.258863] Association response status code 0x1
[ 1831.258877] ===>ieee80211_associate_procedure_wq(), chan:11
[ 1831.307485] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 1831.321111] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1831.324363] This is enable turbo mode IE process
[ 1831.335991] rtl819xU:rtl8192_qos_association_resp: network->flags = 2,0
[ 1831.335994] 
[ 1831.336007] rtl819xU:qos active process with associate response received
[ 1831.336009] 
[ 1831.336017] Associated successfully
[ 1831.336020] Using G rates:108
[ 1831.336023] Successfully associated, ht not enabled(0, 0)
[ 1831.338982] =============>ARFR0+rate_index*4:0xfff
[ 1831.346484] ============>normal associate
[ 1831.346686] Linking with Losemyak,channel:11, qos:0, myHT:0, networkHT:0, mode:6
[ 1831.347864] ===>ieee80211_associate_procedure_wq(), chan:11
[ 1831.397111] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth

```

I'm a bit confused as to which driver is used:

```
~: ls /lib/firmware/RTL8192*
/lib/firmware/RTL8192E:
boot.img  data.img  main.img

/lib/firmware/RTL8192SE:
rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin

/lib/firmware/RTL8192SU:
rtl8192sfw.bin

```

```
~: cat /etc/modprobe.d/network_drivers.conf
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xS/new_id
~: cat /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"
~: lsusb | grep elkin
Bus 001 Device 002: ID 050d:845a Belkin Components 

```

And the router sees the desktop, but that's all - no reason for disconnect:
```
Mar  4 03:41:55 wlan0: A wireless client is associated - 94:44:52:17:0B:11
Mar  4 03:41:55 wlan0: A wireless client is associated - 94:44:52:17:0B:11
Mar  4 03:41:56 wlan0: A wireless client is associated - 94:44:52:17:0B:11
```

---

