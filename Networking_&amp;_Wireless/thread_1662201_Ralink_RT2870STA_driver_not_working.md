---
title: "Ralink RT2870STA driver not working"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by Bellboy on 2011-01-07
Hi 

I am using Mythbuntu 10.10

I managed to configure my wireless N USB device using the RT2870 driver that comes with the system.

However, I could only connect at G speeds.

After searching this forum, I read that updating the driver with the current version from ralink would give me N speeds.

I followed the steps here:-

[http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/](http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/)


Now.... the new driver appears to be loaded... but I have no wireless device listed.

Details below. Thank you for your time.

```


root@htpc:~# uname -a
Linux htpc 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU 

root@htpc:~# lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a80] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aac] (rev b2)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.4 RAM memory [0500]: nVidia Corporation Device [10de:0a98] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab4] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
01:06.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 62)
01:06.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 65)
03:00.0 VGA compatible controller [0300]: nVidia Corporation C79 [GeForce 9300 / nForce 730i] [10de:086c] (rev b1)
05:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]

root@htpc:~# lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 05af:0408 Jing-Mold Enterprise Co., Ltd
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2040:8400 Hauppauge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0411:016f MelCo., Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@htpc:~# dmesg | grep -i rt2
[    6.571139] usbcore: registered new interface driver rt2870


root@htpc:~# modinfo rt2870sta | grep -i version
version:        2.4.0.0
srcversion:     5598BFE60F8B720D8D64062
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686

root@htpc:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:65:9c:43
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe65:9c43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:398949 (398.9 KB)  TX bytes:146189 (146.1 KB)
          Interrupt:23 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12595 (12.5 KB)  TX bytes:12595 (12.5 KB)


```

---

### Post by chili555 on 2011-01-08
> Bus 001 Device 002: ID [COLOR="Red"]0411:016f[/COLOR] MelCo., Inc.I don't think the compiled version claims your usb.id. Check with:```
modinfo rt2870sta | grep -i 016f
```If it comes up blank, your driver doesn't claim your device. Either it's an omission by Ralink, which we can fix, or it's because another more suitable driver is available. Google doesn't suggest the latter.

Therefor, let's add the device usb.id. In the file you compiled, you will find a file, common/rtusb_dev_id.c. It will have a listing of usb.ids something like this; not these exact ones:> {USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
	{USB_DEVICE(0x0DF6,0x0039)}, /* Sitecom 2770 */Please add your device something like this:> {USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
        [COLOR="Red"]{USB_DEVICE(0x0411,0x016F)}, /* Melco */[/COLOR]
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
	{USB_DEVICE(0x0DF6,0x0039)}, /* Sitecom 2770 */Don't add or subtract anything else. The brackets, spaces, etc. are crucial. Proofread twice, save and close your text editor.

Now open the terminal and do:```
cd Downloads/2010_whatever
```Navigate to where you downloaded and extracted the file. Now do:```
sudo su
rmmod rt2870sta
make clean
make
make install
modprobe rt2870sta
exit
```Any improvement?

---

### Post by Bellboy on 2011-01-08
Thanks chilli555 !

Interestingly, my USB device in rtusb_dev_id.c is listed as:-

```
{USB_DEVICE(0x0411,0x00e8)}, /* Buffalo WLI-UC-G300N*/
```

As you said, I included a new line for 

```
 {USB_DEVICE(0x0411,0x016F)}, /* Melco */

```

and recompiled the driver.

(Found below on the net - looks like I have the G301N !)

```


vendor: 0411 ("MelCo., Inc."), product: 00e8 ("Buffalo WLI-UC-G300N Wireless LAN Adapter")
vendor: 0411 ("MelCo., Inc."), product: 015d ("Buffalo WLI-UC-GN Wireless LAN Adapter")
vendor: 0411 ("MelCo., Inc."), product: 016f ("Buffalo WLI-UC-G301N Wireless LAN Adapter")


```


ra0 is now found:-

```

root@htpc:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:65:9c:43
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe65:9c43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39515 (39.5 KB)  TX bytes:71987 (71.9 KB)
          Interrupt:23

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12474 (12.4 KB)  TX bytes:12474 (12.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:24:a5:86:de:d9
          inet6 addr: fe80::224:a5ff:fe86:ded9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:53496 (53.4 KB)

ra0:avahi Link encap:Ethernet  HWaddr 00:24:a5:86:de:d9
          inet addr:169.254.11.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

Problem now, I am unable to connect to my wireless network.

```
root@htpc:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@htpc:/# iwlist ra0 scan
ra0       No scan results

```

Thanks for your help with this.

---

### Post by chili555 on 2011-01-08
How does it work if you detach the ethernet cable? Does Network Manager see your network?

---

### Post by Bellboy on 2011-01-09
I'm not too familiar with NetworkManager.

I tried to access via the Mythbuntu Desktop (think its XFCE) ... so had to install an applet to run Gnome apps... but gave up easily and configured the wireless in CLI. (This was prior to updating the driver).

Wireless configure that used to work:-

```


# Manually set ra0
auto ra0
iface ra0 inet dhcp
wpa-driver wext
wpa-ssid mysid
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk myhexstring


```

and is still set up in interfaces file.


Does this help?

---

### Post by chili555 on 2011-01-09
> # Manually set ra0
auto ra0
iface ra0 inet dhcp
wpa-driver wext
wpa-ssid mysid
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk myhexstringThat's a bit busy. Try this:```
# Manually set ra0
auto ra0
iface ra0 inet dhcp
wpa-ssid mysid
wpa-psk myhexstring
```You might also need to set these details in /etc/Wireless/RT2870STA/RT2870STA.dat.

You might get an idea of what's happening with:```
sudo cat /var/log/syslog | grep ra0
```If there is no data here, also check syslog.1.

---

### Post by Bellboy on 2011-01-10
Thanks.

cat /var/log/syslog | grep ra0

```

Jan 10 23:39:04 htpc kernel: [   19.272023] ra0: no IPv6 routers present
Jan 10 23:39:05 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPluginIfupdown: guessed connection type (ra0) = 802-11-wireless
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:ra0, type:802-11-wireless, id:Ifupdown (ra0), uuid: 1fcc0a42-6596-6ee6-4c98-78291019f536
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPlugin-Ifupdown: update wireless settings (ra0).
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPlugin-Ifupdown: update wireless security settings (ra0).
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0)
Jan 10 23:39:05 htpc NetworkManager[1443]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Jan 10 23:39:05 htpc NetworkManager[1443]: <error> [1294702745.527883] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 3)
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): now managed
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): device state change: 1 -> 2 (reason 2)
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): preparing device.
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): deactivating device (reason: 2).
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): supplicant manager state:  down -> idle
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): device state change: 2 -> 3 (reason 0)
Jan 10 23:39:05 htpc NetworkManager[1443]: <info> (ra0): supplicant interface state:  starting -> ready
Jan 10 23:39:25 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
Jan 10 23:39:45 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Jan 10 23:39:56 htpc avahi-autoipd(ra0)[2277]: Found user 'avahi-autoipd' (UID 106) and group 'avahi-autoipd' (GID 111).
Jan 10 23:39:56 htpc avahi-autoipd(ra0)[2277]: Successfully called chroot().
Jan 10 23:39:56 htpc avahi-autoipd(ra0)[2277]: Successfully dropped root privileges.
Jan 10 23:39:56 htpc avahi-autoipd(ra0)[2277]: Starting with address 169.254.11.182
Jan 10 23:40:01 htpc avahi-autoipd(ra0)[2277]: Callout BIND, address 169.254.11.182 on interface ra0
Jan 10 23:40:05 htpc avahi-autoipd(ra0)[2277]: Successfully claimed IP address 169.254.11.182
Jan 10 23:40:05 htpc ntpd[2389]: Listening on interface #3 ra0, fe80::224:a5ff:fe86:ded9#123 Enabled
Jan 10 23:40:05 htpc ntpd[2389]: Listening on interface #7 ra0:avahi, 169.254.11.182#123 Enabled

```

I am going to configure the wireless using the .dat file. Will let you know how it goes.

Thanks

---

### Post by chili555 on 2011-01-11
Can you please confirm that the ethernet cable is ***de***tached as you are trying to connect?

---

### Post by Bellboy on 2011-01-13
Sorry, on the previous occasion Ethernet cable was still plugged in.

Below is example when not plugged in.

```



Jan 11 23:50:26 htpc NetworkManager[1203]:    SCPluginIfupdown: guessed connection type (ra0) = 802-3-ethernet
Jan 11 23:50:26 htpc NetworkManager[1203]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:ra0, type:802-3-ethernet, id:Ifupdown (ra0), u
uid: 1fcc0a42-6596-6ee6-4c98-78291019f536
Jan 11 23:58:13 htpc NetworkManager[1203]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0)
Jan 11 23:58:13 htpc NetworkManager[1203]: <error> [1294790293.798060] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read perm
anent MAC address (error 0)
Jan 11 23:58:13 htpc NetworkManager[1203]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Jan 11 23:58:13 htpc NetworkManager[1203]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 3)
Jan 11 23:58:13 htpc NetworkManager[1203]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 23:58:14 htpc dhclient: Listening on LPF/ra0/00:24:a5:86:de:d9
Jan 11 23:58:14 htpc dhclient: Sending on   LPF/ra0/00:24:a5:86:de:d9
Jan 11 23:58:14 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Jan 11 23:58:17 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
Jan 11 23:58:22 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Jan 11 23:58:25 htpc kernel: [  498.256028] ra0: no IPv6 routers present
Jan 11 23:58:29 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
Jan 11 23:58:39 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Jan 11 23:58:53 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Jan 11 23:59:07 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Jan 11 23:59:15 htpc avahi-autoipd(ra0)[2778]: Found user 'avahi-autoipd' (UID 106) and group 'avahi-autoipd' (GID 111).
Jan 11 23:59:15 htpc avahi-autoipd(ra0)[2778]: Successfully called chroot().
Jan 11 23:59:15 htpc avahi-autoipd(ra0)[2778]: Successfully dropped root privileges.
Jan 11 23:59:15 htpc avahi-autoipd(ra0)[2778]: Starting with address 169.254.11.182
Jan 11 23:59:20 htpc avahi-autoipd(ra0)[2778]: Callout BIND, address 169.254.11.182 on interface ra0
Jan 11 23:59:24 htpc avahi-autoipd(ra0)[2778]: Successfully claimed IP address 169.254.11.182
Jan 12 00:00:20 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Jan 12 00:00:23 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPluginIfupdown: guessed connection type (ra0) = 802-11-wireless
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:ra0, type:802-11-wireless, id:Ifupdown (ra0), uuid: 1fcc0a42-6596-6ee6-4c98-78291019f536
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: update wireless settings (ra0).
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: update wireless security settings (ra0).
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0)
Jan 12 00:00:23 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Jan 12 00:00:23 htpc NetworkManager[1189]: <error> [1294790423.134416] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 3)
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): now managed
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): device state change: 1 -> 2 (reason 2)
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): preparing device.
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): deactivating device (reason: 2).
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): supplicant manager state:  down -> idle
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): device state change: 2 -> 3 (reason 0)
Jan 12 00:00:23 htpc NetworkManager[1189]: <info> (ra0): supplicant interface state:  starting -> ready
Jan 12 00:00:26 htpc kernel: [   21.312023] ra0: no IPv6 routers present
Jan 12 00:00:27 htpc ntpd[1422]: Listening on interface #2 ra0, fe80::224:a5ff:fe86:ded9#123 Enabled
Jan 12 00:00:31 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Jan 12 00:00:46 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
Jan 12 00:01:05 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
Jan 12 00:01:14 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Jan 12 00:01:18 htpc avahi-autoipd(ra0)[2159]: Found user 'avahi-autoipd' (UID 106) and group 'avahi-autoipd' (GID 111).
Jan 12 00:01:18 htpc avahi-autoipd(ra0)[2159]: Successfully called chroot().
Jan 12 00:01:18 htpc avahi-autoipd(ra0)[2159]: Successfully dropped root privileges.
Jan 12 00:01:18 htpc avahi-autoipd(ra0)[2159]: Starting with address 169.254.11.182
Jan 12 00:01:23 htpc avahi-autoipd(ra0)[2159]: Callout BIND, address 169.254.11.182 on interface ra0
Jan 12 00:01:27 htpc avahi-autoipd(ra0)[2159]: Successfully claimed IP address 169.254.11.182
Jan 12 00:02:06 htpc ntpd[2374]: Listening on interface #2 ra0, fe80::224:a5ff:fe86:ded9#123 Enabled
Jan 12 00:02:06 htpc ntpd[2374]: Listening on interface #6 ra0:avahi, 169.254.11.182#123 Enabled
Jan 12 00:02:57 htpc ntpd[2428]: Listening on interface #2 ra0, fe80::224:a5ff:fe86:ded9#123 Enabled
Jan 12 00:02:57 htpc ntpd[2428]: Listening on interface #6 ra0:avahi, 169.254.11.182#123 Enabled
Jan 12 00:06:01 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Jan 12 00:06:04 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Jan 12 00:06:10 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Jan 12 00:06:11 htpc dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 2267
Jan 12 00:06:11 htpc dhclient: Listening on LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:06:11 htpc dhclient: Sending on   LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:06:11 htpc avahi-autoipd(ra0)[2159]: SIOCSIFFLAGS failed: Permission denied
Jan 12 00:06:11 htpc avahi-autoipd(ra0)[2159]: Callout STOP, address 169.254.11.182 on interface ra0
Jan 12 00:06:11 htpc avahi-autoipd(ra0)[2160]: client: RTNETLINK answers: No such process
Jan 12 00:07:07 htpc dhclient: Listening on LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:07:07 htpc dhclient: Sending on   LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:07:07 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Jan 12 00:07:10 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Jan 12 00:07:13 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Jan 12 00:07:15 htpc kernel: [  430.840024] ra0: no IPv6 routers present
Jan 12 00:07:20 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Jan 12 00:07:34 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
Jan 12 00:07:46 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
Jan 12 00:08:07 htpc dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 1
Jan 12 00:08:08 htpc avahi-autoipd(ra0)[2576]: Found user 'avahi-autoipd' (UID 106) and group 'avahi-autoipd' (GID 111).
Jan 12 00:08:08 htpc avahi-autoipd(ra0)[2576]: Successfully called chroot().
Jan 12 00:08:08 htpc avahi-autoipd(ra0)[2576]: Successfully dropped root privileges.
Jan 12 00:08:08 htpc avahi-autoipd(ra0)[2576]: Starting with address 169.254.11.182
Jan 12 00:08:14 htpc avahi-autoipd(ra0)[2576]: Callout BIND, address 169.254.11.182 on interface ra0
Jan 12 00:08:18 htpc avahi-autoipd(ra0)[2576]: Successfully claimed IP address 169.254.11.182
Jan 12 00:08:41 htpc dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 2583
Jan 12 00:08:41 htpc dhclient: Listening on LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:08:41 htpc dhclient: Sending on   LPF/ra0/00:24:a5:86:de:d9
Jan 12 00:08:41 htpc avahi-autoipd(ra0)[2576]: SIOCSIFFLAGS failed: Permission denied
Jan 12 00:08:41 htpc avahi-autoipd(ra0)[2576]: Callout STOP, address 169.254.11.182 on interface ra0
Jan 12 00:08:41 htpc avahi-autoipd(ra0)[2577]: client: RTNETLINK answers: No such process
Jan 12 00:09:02 htpc kernel: [  537.588952] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
Jan 12 00:09:02 htpc NetworkManager[1189]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-3/net/ra0, iface: ra0)
Jan 12 00:09:02 htpc NetworkManager[1189]: <info> (ra0): now unmanaged
Jan 12 00:09:02 htpc NetworkManager[1189]: <info> (ra0): device state change: 3 -> 1 (reason 36)
Jan 12 00:09:02 htpc NetworkManager[1189]: <info> (ra0): cleaning up...


```

I'm going to rebuild the kernel to get the old driver back... if that works ok... I will try to install the new one again and see if I can get it to work.

Thanks

---

### Post by ilna on 2011-02-08
I have tried to follow all steps, driver was loaded after inserting USB WiFi adapter, ra0 interface appeared. But at starting "Connect" via wicd-gtk I have got a message about wrong password, and my workstation hanged. The only way to reboot was r-e-i-s-u-b kernel hacking. Kernel in use is:

2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

Has anybody success with **this** kernel/arch and the driver?

---

