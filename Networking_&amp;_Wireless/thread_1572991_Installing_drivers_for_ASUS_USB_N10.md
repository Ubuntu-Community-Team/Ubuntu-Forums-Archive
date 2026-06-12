---
title: "Installing drivers for ASUS USB N10"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by zelibobla on 2010-09-12
Hi guys!
I've got Dell Inspiron 1300 with Ubuntu 10.04 on it. Recently I've bought usb wifi adapter ASUS USB N10. Provided with this adapter drivers on CD:
rtl8192su_linux_2.4_2.6.0003.1019.2009.tar.gz
It didn't installed with error:
```
zeliboba@zeliboba:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12317: error: ‘struct net_device’ has no member named ‘open’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12318: error: ‘struct net_device’ has no member named ‘stop’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12319: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12320: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12321: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12322: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12323: error: ‘struct net_device’ has no member named ‘get_stats’
/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12324: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/zeliboba/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2

```

Then I came here to find some solution and found it this post:
[http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13)
My replies begins from 8 page. As we found on finish installed later driver isn't for my adapter.

Here are last configs and system reports:
```
zeliboba@zeliboba:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

```

```
zeliboba@zeliboba:~$ cat /etc/NetworkManager/nm-system-settings.conf 
[main]
plugins=ifupdown,keyfile

no-auto-default=00:15:c5:6a:8a:c7,

[ifupdown]
managed=false

```

```
zeliboba@zeliboba:~$ sudo cat /var/log/syslog | grep rt2
[sudo] password for zeliboba: 
Sep 11 17:56:43 zeliboba kernel: [    9.371940] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Sep 11 17:56:43 zeliboba kernel: [    9.383477] usbcore: registered new interface driver rt2870
Sep 11 18:36:28 zeliboba kernel: [    8.965228] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Sep 11 18:36:28 zeliboba kernel: [    8.993147] usbcore: registered new interface driver rt2870

```

```
zeliboba@zeliboba:~$ dmesg | grep -e rt2 -e rt3
[    9.371940] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.383477] usbcore: registered new interface driver rt2870

```

```
zeliboba@zeliboba:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
zeliboba@zeliboba:~$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/modprobe.d/network_drivers.conf
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1786" > /sys/bus/usb/drivers/rt2870/new_id

```

/etc/udev/rules.d/network_drivers.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1786", RUN+="/sbin/modprobe -qba rt2870sta"

```

---

### Post by chili555 on 2010-09-12
Let's try the easy way first. This is a bit of a gamble, but may be an easy way out. Please remove the device and do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Change it as indicated:```
install [COLOR="Red"]r8192s_usb[/COLOR] /sbin/modprobe --ignore-install [COLOR="Red"]r8192s_usb[/COLOR] $CMDLINE_OPTS; /bin/echo "0b05 1786" > /sys/bus/usb/drivers/[COLOR="Red"]r8192s[/COLOR]/new_id
```Proofread carefully, save and close gedit. Next, do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Change it as indicated:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1786", RUN+="/sbin/modprobe -qba [COLOR="Red"]r8192s_usb[/COLOR]"
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modules
```I suspect there is an entry, rt2870sta. Change it to r8192s_usb, or add such a line if it's not there. Proofread carefully, save and close gedit.

Now do:```
sudo modprobe r8192s_usb
```Insert the device and give us a report.

If it does not work, the next step is to download the newer version here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Make sure you have installed build-essential and unpack and build the module. It will build and you will use 8712u.

Post back and let us know.

---

### Post by zelibobla on 2010-09-12
Hi Chili!

I've unplugged the device and made all you wrote:

/etc/udev/rules.d/network_drivers.rules 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1786", RUN+="/sbin/modprobe -qba r8192s_usb"

```

/etc/modprobe.d/network_drivers.conf 
```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "0b05 1786" > /sys/bus/usb/drivers/r8192s/new_id

```

modules didn't contain record with previous driver, so I've add a new one
/etc/modules
```
loop
r8192s_usb

```

modprobe returned an error:
```
zeliboba@zeliboba:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ sudo modprobe r8192s_usb 
sh: cannot create /sys/bus/usb/drivers/r8192s/new_id: Directory nonexistent
FATAL: Error running install command for r8192s_usb

```

I've plug device back, but saw the same result. Device looks like working but no any networks found.
System reports:
```
zeliboba@zeliboba:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"11n-AP"  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
zeliboba@zeliboba:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
zeliboba@zeliboba:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ sudo iwlist wlan0 scan
wlan0     No scan results

```

Peform next step...

---

### Post by zelibobla on 2010-09-12
At link you provided I've found 2 drivers RTL8192SE and RTL8192SU. I don't know the difference so I've pray for a luck and chose the second one: RTL8192SU.
Error came in the first step:
```
zeliboba@zeliboba:~/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625$ sudo make
[sudo] password for zeliboba: 
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'. Stop.
```

---

### Post by zelibobla on 2010-09-12
Then I've decided that luck isn't on my side today so I downloaded another driver: rtl8192se_linux_2.6.0017.0705.2010 and tried to install it. Make finished without errors, but wlan still don't recognize any wireless networks. System reports are the same as in previous post.

---

### Post by chili555 on 2010-09-12
> zeliboba@zeliboba:~/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625$ sudo make
[sudo] password for zeliboba: 
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'. Stop.Please try:```
sudo su
make clean
make
make install
modprobe 8712u
exit
```You may need to remove these two files, since they are doing us no good:```
sudo rm /etc/udev/rules.d/network_drivers.rules 
sudo rm /etc/modprobe.d/network_drivers.conf
```Reboot and let us know your report.

---

### Post by chili555 on 2010-09-12
From my compile:```
$ modinfo 8712u
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/8712u.ko
author:         ...
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     8832118B798C3C81A426B33
--- snip ---
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]1786[/COLOR]d*dc*dsc*dp*ic*isc*ip*
--- snip ---
```

---

### Post by zelibobla on 2010-09-12
Chili! This helped:
```
sudo su
rm /etc/udev/rules.d/network_drivers.rules 
rm /etc/modprobe.d/network_drivers.conf
make clean
make
make install
modprobe 8712u
exit
```
With this driver: RTL8192SU_usb_linux_v2.6.0006.20100625.zip
```
zeliboba@zeliboba:~$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
zeliboba@zeliboba:~$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:21:29:6D:07:A2
                    ESSID:"vjaz6-223"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=10/100  
          Cell 02 - Address: 00:1E:58:81:C2:E7
                    ESSID:"vyaz6"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=10/100  
          Cell 03 - Address: E0:CB:4E:ED:B9:E8
                    ESSID:"Kellogg_UB"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=10/100  

```
My wifi radar found 6 wireless networks, so I guess now it works properly. Thank you very much!

---

### Post by chili555 on 2010-09-12
So, are you connected to ye olde internet?

---

### Post by zelibobla on 2010-09-12
I still have my LAN connection via eth1. I haven't got shared wireless networks here which I could connect to, but I can see locked networks of some neighbours.
My target at now is to make my laptop access point for some other devices (mobile for example).

Still can't find good manual to set my wifi adapter as access point. Best for me is not using a network manager. I'll appreciate if you'll throw some useful link on this subject.

---

### Post by chili555 on 2010-09-12
[http://www.linuxquestions.org/questions/linux-general-1/make-ubuntu-linux-work-as-a-wireless-router-wireless-internet-sharing-820615/](http://www.linuxquestions.org/questions/linux-general-1/make-ubuntu-linux-work-as-a-wireless-router-wireless-internet-sharing-820615/)

This might help.

---

### Post by vcrpex on 2010-12-01
Hi, I followed the instructions in this thread to install the driver for asus USB n10 and got it working for Maverick. But when I recently updated the kernel image, the wireless just can't seems to work again. Have tried to re-make with the new kernel image but to no valid. Currently using the previous kernel image that I have got it working to surf. Any idea how I can solve this? I have created a separate thread for this with my logs. Really hope I can get it working again else I will have to stick to the previous kernel image. Thanks

---

### Post by chili555 on 2010-12-01
Please try, in the new kernel image:```
cd downloaded/folder/location
make clean 
make
sudo make install
```Now does it work? Let us know of any errors or problems.

---

### Post by vcrpex on 2010-12-01
hi Chilli, 
tried that. it make install without error, but simply dun read any network. below is the log from that kernel image:

terence@terence-M68MT-D3:~$ uname -a
Linux terence-M68MT-D3 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux

terence@terence-M68MT-D3:~$ iwconfig wlan0
wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

terence@terence-M68MT-D3:~$ lsmod | grep "r8192"
r8192s_usb            317763  0 
eeprom_93cx6            1789  1 r8192s_usb

terence@terence-M68MT-D3:~$ sudo iwlist wlan0 scan
[sudo] password for terence: 
wlan0     Interface doesn't support scanning : Network is down

terence@terence-M68MT-D3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:54:4d:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177072 (177.0 KB)  TX bytes:177072 (177.0 KB)

my current driver I am using is the 8712u, this work perfectly fine on this kernel image Linux terence-M68MT-D3 2.6.35-22-generic #35 but not 2.6.35-23-generic #40. Tried other drivers from the realtek website, but have Error 2 making the file.

---

### Post by chili555 on 2010-12-01
I'm confused. You said you are using 8712u, however lsmod shows r8192s_usb. Let's have a look at:```
dmesg | grep -e 871 -e 819
```

---

### Post by vcrpex on 2010-12-01
Below is the output for the working wireless kernel:
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   12.745882] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   12.759485] Linux kernel driver for RTL8192 based WLAN cards
[   13.274850] usbcore: registered new interface driver rtl819xU
[   13.277501] usbcore: registered new interface driver r871x_usb_drv
[   15.298610] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 902b, size: 30, imemsize: 7408, sram size: 9688
[   15.300115] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[   15.304248] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[   15.304497] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[   15.305870] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[   15.306870] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   15.307120] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[   15.307123] rtl819xU:FirmwareDownload92S(): Firmware Download Success
[   32.626920] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[   32.655192] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[   32.655209] rtl819xU:qos active process with associate response received
[   32.758643] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 2, SECR_value: c
[   32.758816] rtl819xU:setKey(): dev: ffff8801140d0000, EntryNo: 4, KeyIndex: 0, KeyType: 2, MacAddr: 00:0b:2b:41:53:cd
[   32.811766] rtl819xU:setKey(): dev: ffff8801140d0000, EntryNo: 1, KeyIndex: 1, KeyType: 2, MacAddr: ff:ff:ff:ff:ff:ff

you are right that I am using the 8192 instead of the 8712 even though that is being installed as well.

Below is the output for the one that is not working:
terence@terence-M68MT-D3:~$ dmesg | grep -e 871 -e 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   13.543813] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.546411] Linux kernel driver for RTL8192 based WLAN cards
[   13.793264] usbcore: registered new interface driver rtl819xU
[   14.336929] usbcore: registered new interface driver r871x_usb_drv
[   16.202111] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.202362] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.215851] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.216101] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.216104] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.262158] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.263371] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.275486] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   16.275747] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   16.275750] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.981962] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

Perhaps I would try to make install the 8192 driver again. Might have to find the header file to put in as I remember there is a Error 2 when I made just now.

---

### Post by chili555 on 2010-12-01
I think it's important to figure out which driver is correct. Please let us see:```
lsusb
```The firmware issue is quite easy to fix. r8192s_usb seems to drive the device but is missing firmware.> rtl819xU:FirmwareRequest92S(): failed with TCR-Status: aIf we can get the native driver going, that seems preferable to compiling a tarball.

---

### Post by vcrpex on 2010-12-01
Below is the output of lsusb:
terence@terence-M68MT-D3:~$ lsusb
Bus 002 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 0718:1902 Imation Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

This is the same for the working wireless and the non-working one. I downloaded the latest 8192se driver from realtek. when i tried to Make install, I get the following error:

terence@terence-M68MT-D3:~/Desktop/rtl8192se_linux_2.6.0018.1025.2010$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make[1]: Entering directory `/home/terence/Desktop/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-23-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/terence/Desktop/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make: *** [install] Error 2

I have located the version.h and utsrelease.h. both the files are already in there.

---

### Post by chili555 on 2010-12-01
Before you go compile a driver that may or may not work just as well, let's fix the firmware issue. Is the file rtl8192sfw.bin in the package you downloaded? If so, please do:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp downloaded/file/location/rtl8192sfw.bin /lib/firmware/RTL8192SU
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
```Any improvements?

---

### Post by vcrpex on 2010-12-01
Thank you Chilli555!
it work!!!! thanks. :) I can skip the grub menu now.

---

### Post by zerothorder on 2010-12-03
i use windows wireless driver software 

see link below

[http://newyork.ubuntuforums.org/showthread.php?p=10193583#post10193583](http://newyork.ubuntuforums.org/showthread.php?p=10193583#post10193583)

---

### Post by vcrpex on 2011-05-06
Hi Chilli555, 
my usb n10 have been working for the past 6 mths very well til today.  suddenly it just did not connect anymore. Though I have updated the  linux kernel quite a few times, it was still working properly. The usb  n10 is connected to my desktop all the time, as I did not want to run a  cable round the room to connect to it. I have followed the steps that I  have done previously but to no valid. I am starting to wonder if it is a  problem on the usb n 10 itself as I have plug it out and feel that the  connector to the desktop is very hot. 

It started with being able to connect to the network, but I could not  get on the internet. After I plug it out and put it back, i can see the  network but I cant connect to it. I did the steps in post #19 but to no valid.
Please advise.

thanks in advance.

---

### Post by chili555 on 2011-05-06
> **vcrpex said:**
> Hi Chilli555, 
my usb n10 have been working for the past 6 mths very well til today.  suddenly it just did not connect anymore. Though I have updated the  linux kernel quite a few times, it was still working properly. The usb  n10 is connected to my desktop all the time, as I did not want to run a  cable round the room to connect to it. I have followed the steps that I  have done previously but to no valid. I am starting to wonder if it is a  problem on the usb n 10 itself as I have plug it out and feel that the  connector to the desktop is very hot. 

It started with being able to connect to the network, but I could not  get on the internet. After I plug it out and put it back, i can see the  network but I cant connect to it. I did the steps in post #19 but to no valid.
Please advise.

thanks in advance.Let's do some diagnostics. Please post:```
lsmod | grep 819
dmesg | grep -e 819 -e wlan
```Thanks.

---

### Post by vcrpex on 2011-05-06
lsmod | grep 819
r8192s_usb            317763  0 
eeprom_93cx6            1789  1 r8192s_usb

dmesg | grep -e 819 -e wlan
[ 2402.891882] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2402.958604] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2403.022771] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2403.046656] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2403.046711] rtl819xU:qos active process with associate response received
[ 2403.085769] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2403.152643] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2403.215660] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2405.708679] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2405.731973] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2405.732028] rtl819xU:qos active process with associate response received
[ 2405.770699] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2405.838569] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2405.901872] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2405.925620] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2405.925674] rtl819xU:qos active process with associate response received
[ 2405.964861] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2406.030984] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2406.095377] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2406.119144] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2406.119197] rtl819xU:qos active process with associate response received
[ 2406.159000] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2406.226370] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2408.778541] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2408.807209] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2408.807264] rtl819xU:qos active process with associate response received
[ 2408.846571] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2408.914068] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2408.976957] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.005359] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.005413] rtl819xU:qos active process with associate response received
[ 2409.044226] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.110219] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.174118] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.203131] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.203186] rtl819xU:qos active process with associate response received
[ 2409.242131] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.309101] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.371936] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.395530] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.395584] rtl819xU:qos active process with associate response received
[ 2409.435146] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.501644] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.564411] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.590806] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.590862] rtl819xU:qos active process with associate response received
[ 2409.630529] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.697900] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.726320] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.726374] rtl819xU:qos active process with associate response received
[ 2409.765681] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.832306] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.896504] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.925091] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2409.925146] rtl819xU:qos active process with associate response received
[ 2409.964210] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2409.981960] =============>ARFR0+rate_index*4:0xff005
[ 2410.031209] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2410.093977] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2410.152510] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2410.178997] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2410.179052] rtl819xU:qos active process with associate response received
[ 2410.218478] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2410.284853] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2412.828519] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2412.856313] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2412.856367] rtl819xU:qos active process with associate response received
[ 2412.895166] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2412.962410] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2412.992328] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2412.992383] rtl819xU:qos active process with associate response received
[ 2413.030929] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.098176] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.160075] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.220453] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.280092] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.305992] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2413.306046] rtl819xU:qos active process with associate response received
[ 2413.345606] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.411979] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.474872] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.534374] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.559022] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2413.559076] rtl819xU:qos active process with associate response received
[ 2413.598752] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.666122] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.695038] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2413.695092] rtl819xU:qos active process with associate response received
[ 2413.734282] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.801151] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.865791] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.888807] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2413.888881] rtl819xU:qos active process with associate response received
[ 2413.928540] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2413.997658] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2414.027330] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2414.027386] rtl819xU:qos active process with associate response received
[ 2414.067061] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2414.134184] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2414.197451] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.689102] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.712519] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2416.712574] rtl819xU:qos active process with associate response received
[ 2416.751372] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.819236] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.882280] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.941967] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2416.965423] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2416.965477] rtl819xU:qos active process with associate response received
[ 2417.005039] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.071286] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.100072] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2417.100129] rtl819xU:qos active process with associate response received
[ 2417.140168] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.208034] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.270680] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.299461] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2417.299515] rtl819xU:qos active process with associate response received
[ 2417.339566] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.407311] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.470208] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.500237] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2417.500291] rtl819xU:qos active process with associate response received
[ 2417.539964] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.620583] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2417.650752] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2417.650792] rtl819xU:qos active process with associate response received
[ 2417.691229] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2422.703819] Linking with alright,channel:1, qos:1, myHT:1, networkHT:1, mode:10
[ 2422.744836] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2422.774233] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2422.774289] rtl819xU:qos active process with associate response received
[ 2422.813977] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2422.870717] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2422.897748] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2422.897781] rtl819xU:qos active process with associate response received
[ 2422.937373] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2423.957683] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 2, SECR_value: c
[ 2423.957983] rtl819xU:setKey(): dev: ffff88011b570000, EntryNo: 4, KeyIndex: 0, KeyType: 2, MacAddr: 00:0b:2b:41:53:cd
[ 2424.019261] rtl819xU:setKey(): dev: ffff88011b570000, EntryNo: 1, KeyIndex: 1, KeyType: 2, MacAddr: ff:ff:ff:ff:ff:ff
[ 2434.430047] wlan0: no IPv6 routers present
[ 2444.835420] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2444.865839] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2444.865923] rtl819xU:qos active process with associate response received
[ 2444.904697] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2444.972202] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.035463] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.059486] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.059540] rtl819xU:qos active process with associate response received
[ 2445.100095] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.156478] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.186002] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.186057] rtl819xU:qos active process with associate response received
[ 2445.225616] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.291241] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.355629] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.414888] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.438406] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.438460] rtl819xU:qos active process with associate response received
[ 2445.478014] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.544636] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.572672] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.572726] rtl819xU:qos active process with associate response received
[ 2445.611424] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.678892] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.742559] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.767068] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.767123] rtl819xU:qos active process with associate response received
[ 2445.806431] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.873430] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.936743] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2445.959841] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2445.959895] rtl819xU:qos active process with associate response received
[ 2445.999199] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.065694] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.130334] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.154364] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2446.154418] rtl819xU:qos active process with associate response received
[ 2446.194108] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.260733] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.323127] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.346944] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2446.347009] rtl819xU:qos active process with associate response received
[ 2446.386540] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.453123] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.521902] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.545662] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2446.545710] rtl819xU:qos active process with associate response received
[ 2446.585278] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.651776] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.681803] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2446.681857] rtl819xU:qos active process with associate response received
[ 2446.720778] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.788026] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.851568] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.874451] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2446.874499] rtl819xU:qos active process with associate response received
[ 2446.914319] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2446.985554] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.055083] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.080349] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2447.080403] rtl819xU:qos active process with associate response received
[ 2447.119981] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.187529] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.249969] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.273873] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2447.273921] rtl819xU:qos active process with associate response received
[ 2447.313117] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.379529] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.410143] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2447.410201] rtl819xU:qos active process with associate response received
[ 2447.450244] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.517986] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.582900] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.610670] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2447.610726] rtl819xU:qos active process with associate response received
[ 2447.650887] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2447.718590] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2450.268934] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2450.296358] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2450.296418] rtl819xU:qos active process with associate response received
[ 2450.335965] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2450.403463] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2450.432745] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2450.432832] rtl819xU:qos active process with associate response received
[ 2450.471620] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2450.537343] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.088765] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.116936] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.116970] rtl819xU:qos active process with associate response received
[ 2453.156922] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.224293] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.253202] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.253256] rtl819xU:qos active process with associate response received
[ 2453.292078] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.359546] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.421842] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.448599] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.448632] rtl819xU:qos active process with associate response received
[ 2453.488457] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.554922] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.618097] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.643373] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.643427] rtl819xU:qos active process with associate response received
[ 2453.682745] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.749966] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.814630] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.838021] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.838074] rtl819xU:qos active process with associate response received
[ 2453.877265] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.943505] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2453.971162] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2453.971216] rtl819xU:qos active process with associate response received
[ 2454.011411] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.078758] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.141302] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.165559] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2454.165613] rtl819xU:qos active process with associate response received
[ 2454.205171] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.272423] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.336936] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.361454] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2454.361480] rtl819xU:qos active process with associate response received
[ 2454.400553] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.468554] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2454.531473] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.028981] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.053026] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.053081] rtl819xU:qos active process with associate response received
[ 2457.092404] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.159868] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.191169] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.191224] rtl819xU:qos active process with associate response received
[ 2457.231142] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.298763] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.327186] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.327244] rtl819xU:qos active process with associate response received
[ 2457.367667] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.433667] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.500179] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.524206] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.524260] rtl819xU:qos active process with associate response received
[ 2457.563700] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.630081] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.659221] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.659254] rtl819xU:qos active process with associate response received
[ 2457.698321] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.765576] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.829717] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.858120] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2457.858174] rtl819xU:qos active process with associate response received
[ 2457.858198] Associated successfully
[ 2457.897855] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2457.964478] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.028119] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.057768] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2458.057823] rtl819xU:qos active process with associate response received
[ 2458.097629] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.193011] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.221663] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2458.221718] rtl819xU:qos active process with associate response received
[ 2458.260404] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.328025] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.357428] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2458.357482] rtl819xU:qos active process with associate response received
[ 2458.397159] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.464162] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.528301] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 2458.552452] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 2458.552486] rtl819xU:qos active process with associate response received
[ 2458.591452] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 3142.709465] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 3142.747395] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 3142.747432] rtl819xU:qos active process with associate response received
[ 3142.786504] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 3142.843306] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 3142.869910] rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
[ 3142.869965] rtl819xU:qos active process with associate response received
[ 3142.909636] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[ 3143.872593] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 2, SECR_value: c
[ 3143.872893] rtl819xU:setKey(): dev: ffff88011b570000, EntryNo: 4, KeyIndex: 0, KeyType: 2, MacAddr: 00:0b:2b:41:53:cd
[ 3143.933172] rtl819xU:setKey(): dev: ffff88011b570000, EntryNo: 1, KeyIndex: 1, KeyType: 2, MacAddr: ff:ff:ff:ff:ff:ff

I can now connect to my network, but the internet seems very intermittent on the desktop that is using the n10. Typing this on another pc that is connected by cable to the same router. For the last half year, I was using the wireless to do my normal surfing n downloading of files and streaming of some sites, thus I was wondering is it my hardware or the driver that is causing the problem.

---

