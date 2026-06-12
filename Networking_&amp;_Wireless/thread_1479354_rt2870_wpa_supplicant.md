---
title: "rt2870 wpa_supplicant"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by jipajapa on 2010-05-10
Hi,

Today I was a bit excited because my rt2870 interface was finally recognized and, according to iwconfig,  seems to work:


wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:1F:3F:A1:A8:57 
          Bit Rate=1 Mb/s   
          RTS thrff   Fragment thrff
          Link Quality=10/100  Signal level:-45 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Unfortunately, WPA does not seem to work and I can't connect to my router. I've tested the rt2870 interface and the router with other systems and I know they are working. When I try to connect using the Network Connections tool, these entries show up in /var/log/daemon.log

[FONT=Arial]May 10 21:35:57 bistro NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Nimh' has security, and secrets exist.  No new secrets needed.
May 10 21:35:57 bistro NetworkManager: <info>  Config: added 'ssid' value 'Nimh'
May 10 21:35:57 bistro NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May 10 21:35:57 bistro NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May 10 21:35:57 bistro NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May 10 21:35:57 bistro NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 10 21:35:57 bistro NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 10 21:35:57 bistro NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 10 21:35:57 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May 10 21:35:57 bistro NetworkManager: <info>  Config: set interface ap_scan to 1
May 10 21:35:57 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:02 bistro wpa_supplicant[1189]: Trying to associate with 00:1f:3f:a1:a8:57 (SSID='Nimh' freq=2412 MHz)
May 10 21:36:02 bistro wpa_supplicant[1189]: Association request to the driver failed
May 10 21:36:02 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 10 21:36:07 bistro wpa_supplicant[1189]: Authentication with 00:1f:3f:a1:a8:57 timed out.
May 10 21:36:07 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 10 21:36:07 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:13 bistro NetworkManager: <info>  wlan0: link timed out.
May 10 21:36:22 bistro wpa_supplicant[1189]: Trying to associate with 00:1f:3f:a1:a8:57 (SSID='Nimh' freq=2412 MHz)
May 10 21:36:22 bistro wpa_supplicant[1189]: Association request to the driver failed
May 10 21:36:22 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 10 21:36:27 bistro wpa_supplicant[1189]: Authentication with 00:1f:3f:a1:a8:57 timed out.
May 10 21:36:27 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 10 21:36:27 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:32 bistro wpa_supplicant[1189]: Trying to associate with 00:1f:3f:a1:a8:57 (SSID='Nimh' freq=2412 MHz)
May 10 21:36:32 bistro wpa_supplicant[1189]: Association request to the driver failed
May 10 21:36:32 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 10 21:36:37 bistro wpa_supplicant[1189]: Authentication with 00:1f:3f:a1:a8:57 timed out.
May 10 21:36:37 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 10 21:36:37 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:42 bistro wpa_supplicant[1189]: Trying to associate with 00:1f:3f:a1:a8:57 (SSID='Nimh' freq=2412 MHz)
May 10 21:36:42 bistro wpa_supplicant[1189]: Association request to the driver failed
May 10 21:36:42 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 10 21:36:47 bistro wpa_supplicant[1189]: Authentication with 00:1f:3f:a1:a8:57 timed out.
May 10 21:36:47 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 10 21:36:47 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:52 bistro wpa_supplicant[1189]: Trying to associate with 00:1f:3f:a1:a8:57 (SSID='Nimh' freq=2412 MHz)
May 10 21:36:52 bistro wpa_supplicant[1189]: Association request to the driver failed
May 10 21:36:52 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 10 21:36:57 bistro wpa_supplicant[1189]: Authentication with 00:1f:3f:a1:a8:57 timed out.
May 10 21:36:57 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 10 21:36:57 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 21:36:58 bistro NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
May 10 21:36:58 bistro NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May 10 21:36:58 bistro NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
May 10 21:36:58 bistro NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May 10 21:36:59 bistro NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
May 10 21:36:59 bistro NetworkManager: <info>  Activation (wlan0) failed for access point (Nimh)
May 10 21:36:59 bistro NetworkManager: <info>  Marking connection 'Auto Nimh' invalid.
May 10 21:36:59 bistro NetworkManager: <info>  Activation (wlan0) failed.
May 10 21:36:59 bistro NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
May 10 21:36:59 bistro NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
[/FONT]
Any suggestions would be appreciated.

Cheers,
Sam

---

### Post by AlmightyBob on 2010-05-10
This is the same problem I've been having as well :(

---

### Post by sysiphysus on 2010-05-11
i'm not sure how do you drive your rt2870 chipset, but if you install third party driver, you need modified the file "config.mk" to open the WPA connection.

---

### Post by HedgeBoar on 2010-05-11
I'm having the same trouble.  I'm using an edimax ew-7711uan usb adapter with the same rt2870 driver -- was working fine in 9.10 (after blacklisting a few drivers as normal for this adapter).  After doing a clean install of 10.04 I'm having the same issue -- I can see access points and try to connect, but after trying for a bit it just asks for the password again.  Daemon.log (similar to the one posted above really) is attached.

---

### Post by Lithaerien on 2010-05-11
I've been trying to get someone to help me on this too for quite some time. [http://ubuntuforums.org/showthread.php?t=1468938]("http://ubuntuforums.org/showthread.php?t=1468938")

I tried compiling the driver from the ralink page after enabling WPA in the config.mk file. In all cases; the wireless USB would see the access point and show the strength, but it would only connect if it were WEP secured and not WPA. Now WEP for me is not an option.

---

### Post by jipajapa on 2010-05-11
After doing a little research, it seems one of my problems is that I was using the rt2870sta driver included with ubuntu 10.04. Unfortunately, it appears that this driver has wpa disabled. 

I used these instructions to obtain and install the new driver. They are a little out of date (maybe this is the problem): [http://ubuntuforums.org/showthread.php?t=960642&highlight=wpa_supplicant+rt2870+config.mk](http://ubuntuforums.org/showthread.php?t=960642&highlight=wpa_supplicant+rt2870+config.mk)

I stopped at step 17, since I don't have an /etc/network/interfaces file. 

Since the link to ralink in the instructions is no longer accurate, I downloaded the source for the driver  (RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2) from 

[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpFMUwyUnZkMjVzYjJGa05UYzBNVFExTkRNNU5TNWllakk5UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakF1ZEdGeUxuUmhjZz09Qw%3D%3D]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpFMUwyUnZkMjVzYjJGa05UYzBNVFExTkRNNU5TNWllakk5UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakF1ZEdGeUxuUmhjZz09Qw%3D%3D")

I added the following line to /etc/modules

```
alias ra0 rt2870sta
```and the following line to /eetc/modprobe.d/blacklist.conf
```
blacklist rt2800usb
```Also, I did the following to get the new driver in the right spot for loading in the future: 

```
cd /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/
mv rt2870sta.ko  rt2870sta.ko.old
cp ~Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/rt2870sta.ko  /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870

```The new error (obtained after a reboot, I would love to know how to reset network settings and reload modules without rebooting) is as follows:

daemon.log:May 11 21:21:00 bistro NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/net/ra0, iface: ra0)
daemon.log:May 11 21:21:00 bistro NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/net/ra0, iface: ra0): no ifupdown configuration found.
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): now managed
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): bringing up device.
daemon.log:May 11 21:21:01 bistro NetworkManager: <info>  (ra0): deactivating device (reason: 2).
daemon.log:May 11 21:21:02 bistro NetworkManager: <info>  (ra0): supplicant manager state:  down -> idle
daemon.log:May 11 21:21:02 bistro NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 0)
daemon.log:May 11 21:21:02 bistro wpa_supplicant[1184]: Could not set interface 'ra0' UP

Any suggestions would be greatly appreciated. 

Cheers,
Sam

---

### Post by jipajapa on 2010-05-13
It seems to be up! These instructions were very helpful:
[http://wiki.archlinux.org/index.php/Rt2870](http://wiki.archlinux.org/index.php/Rt2870)

---

### Post by biji on 2010-12-14
It seems rt2870 driver dont support scanning (but iwlist scan does)
to connect easily use Connect to Hidden Network or Create New Wireless Network

---

