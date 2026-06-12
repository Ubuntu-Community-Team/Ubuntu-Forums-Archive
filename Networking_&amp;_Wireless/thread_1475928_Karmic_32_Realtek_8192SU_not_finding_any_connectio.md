---
title: "Karmic 32 Realtek 8192SU not finding any connections"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Jun-01 on 2010-05-07
Hello Ubuntu users,

I have a Realtek 8192SU USB Wireless adapter, and I'm having trouble to get it working on Ubuntu Karmic 32bit in my laptop, because I'm a noob at installing drivers for Ubuntu.

```
uname -r
2.6.31-21-generic
```Apparently, there is native support for the device in Ubuntu, as the Network Manager listed the device the first time I plugged it. But the device's led didn't start to flash, it only turned on, meaning that it wasn't working properly, and coudn't find any connections. I've also read somewhere that the drivers that come with Ubuntu are "stagged" versions. No idea what that means, but I guess they're not stable, or are beta versions.

Then I followed the steps in threads [http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254), [http://ubuntuforums.org/showthread.php?t=1425697](http://ubuntuforums.org/showthread.php?t=1425697)

make (as root):
```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/akiller/Desktop/realtek/cmd/rtl871x_cmd.o
  CC [M]  /home/akiller/Desktop/realtek/cmd/rtl8712_cmd.o
  CC [M]  /home/akiller/Desktop/realtek/crypto/rtl871x_security.o
  CC [M]  /home/akiller/Desktop/realtek/debug/rtl871x_debug.o
  CC [M]  /home/akiller/Desktop/realtek/eeprom/rtl871x_eeprom.o
  CC [M]  /home/akiller/Desktop/realtek/efuse/rtl8712_efuse.o
  CC [M]  /home/akiller/Desktop/realtek/hal/rtl8712/hal_init.o
  CC [M]  /home/akiller/Desktop/realtek/hal/rtl8712/usb_ops.o
  CC [M]  /home/akiller/Desktop/realtek/hal/rtl8712/usb_ops_linux.o
  CC [M]  /home/akiller/Desktop/realtek/hal/rtl8712/usb_halinit.o
  CC [M]  /home/akiller/Desktop/realtek/io/rtl871x_io.o
  CC [M]  /home/akiller/Desktop/realtek/io/rtl8712_io.o
  CC [M]  /home/akiller/Desktop/realtek/ioctl/rtl871x_ioctl_query.o
  CC [M]  /home/akiller/Desktop/realtek/ioctl/rtl871x_ioctl_set.o
  CC [M]  /home/akiller/Desktop/realtek/ioctl/rtl871x_ioctl_linux.o
  CC [M]  /home/akiller/Desktop/realtek/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /home/akiller/Desktop/realtek/led/rtl8712_led.o
  CC [M]  /home/akiller/Desktop/realtek/mlme/ieee80211.o
  CC [M]  /home/akiller/Desktop/realtek/mlme/rtl871x_mlme.o
  CC [M]  /home/akiller/Desktop/realtek/mp/rtl871x_mp.o
  CC [M]  /home/akiller/Desktop/realtek/mp/rtl871x_mp_ioctl.o
  CC [M]  /home/akiller/Desktop/realtek/os_dep/linux/io_linux.o
  CC [M]  /home/akiller/Desktop/realtek/os_dep/linux/xmit_linux.o
  CC [M]  /home/akiller/Desktop/realtek/os_dep/linux/cmd_linux.o
  CC [M]  /home/akiller/Desktop/realtek/os_dep/linux/mlme_linux.o
  CC [M]  /home/akiller/Desktop/realtek/os_dep/linux/recv_linux.o
  CC [M]  /home/akiller/Desktop/realtek/os_intf/osdep_service.o
  CC [M]  /home/akiller/Desktop/realtek/os_intf/linux/os_intfs.o
  CC [M]  /home/akiller/Desktop/realtek/os_intf/linux/usb_intf.o
  CC [M]  /home/akiller/Desktop/realtek/pwrctrl/rtl871x_pwrctrl.o
  CC [M]  /home/akiller/Desktop/realtek/recv/rtl871x_recv.o
  CC [M]  /home/akiller/Desktop/realtek/recv/rtl8712_recv.o
  CC [M]  /home/akiller/Desktop/realtek/rf/rtl871x_rf.o
  CC [M]  /home/akiller/Desktop/realtek/rf/rtl8712_rf.o
  CC [M]  /home/akiller/Desktop/realtek/sta_mgt/rtl871x_sta_mgt.o
  CC [M]  /home/akiller/Desktop/realtek/xmit/rtl871x_xmit.o
  CC [M]  /home/akiller/Desktop/realtek/xmit/rtl8712_xmit.o
  LD [M]  /home/akiller/Desktop/realtek/8712u.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/akiller/Desktop/realtek/8712u.mod.o
  LD [M]  /home/akiller/Desktop/realtek/8712u.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
```make install (as root)
```
install -p -m 644 8712u.ko  /lib/modules/2.6.31-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.31-21-generic
```

Then I followed the other steps and added line "8712u" to /etc/modules, in order to load the module when booting.

Rebooted.

Plugged the device with the built-in adapter switched off. The LED this time started to flash. That would meant that now I'm enjoying a nice wireless experience, but that wasn't the case. Network Manager still couldn't find any wireless connections, although the device is now apparently working.

iwconfig returns (after a reboot, plugging 8192SU first and then switching on the laptop's built-in wireless adapter)
```
wlan3     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ICMC"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:33:7F:64:70   
          Bit Rate=36 Mb/s   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Where wlan0 is the internal adapter and wlan3 is 8192SU


lsusb returns (after a reboot, plugging 8192SU first and then switching on the laptop's built-in wireless adapter)```

Bus 001 Device 005: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```Where "Ralink Technology, Corp" is 8192SU and "Micro Star International RT2573" is the laptop's internal wireless adapter.

So, any ideas? If there's lack of information tell me what you need, please. I'm going to post them asap.

---

### Post by Jun-01 on 2010-05-07
ifconfig returns
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:a8:6a:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49009 (49.0 KB)  TX bytes:49009 (49.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:21:46:6d:73  
          inet addr:192.168.231.37  Bcast:192.168.231.255  Mask:255.255.254.0
          inet6 addr: fe80::224:21ff:fe46:6d73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5812996 (5.8 MB)  TX bytes:439213 (439.2 KB)

wlan3     Link encap:Ethernet  HWaddr 00:0d:09:30:d6:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0D-09-30-D6-72-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-24-21-46-6D-73-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Jun-01 on 2010-05-07
Solved the problem by myself. Found what I still needed to do in thread [http://ubuntuforums.org/showthread.php?t=1394281&highlight=rtl8192su](http://ubuntuforums.org/showthread.php?t=1394281&highlight=rtl8192su)

I blacklisted the following devices
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Now both of the 8192SU and the the laptop's built-in adapter are working fine in my Ubuntu installation.

Hope this thread will help other users.

---

### Post by Jun-01 on 2010-05-07
Only posting what users are meant to see if 8192SU is working properly.

iwconfig (with the laptop's built-in adapter switched off)
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"ICMC"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:23:33:7F:64:70   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level:-72 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

