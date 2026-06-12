---
title: "Device 002: 8176 Realtek Semiconductor Corp"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2011-01-02
Bus 001 Device 002: ID xxxx:8176 Realtek Semiconductor Corp

Is there driver for this wireless USB dongle? At least it does not load when plug-in like rtl8187.

---

### Post by chili555 on 2011-01-02
> Bus 001 Device 002: ID [COLOR="Red"]xxxx[/COLOR]:8176 Realtek Semiconductor CorpIn order to research and answer your question, we need the vendor id that you have carefully obscured with xxxx. Please post.

---

### Post by cd-r80 on 2011-01-03
Bus 002 Device 003: ID 0bda:8176 Realtek Semiconductor Corp.

I have RTL8188CUS_v2.0.1212.zip but I could not compile it like in [http://ubuntuforums.org/showthread.php?t=1534918](http://ubuntuforums.org/showthread.php?t=1534918) . Or when I do ./clean:

ERROR: Module r8192s_usb does not exist in /proc/modules
ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules

---

### Post by chili555 on 2011-01-03
All that does is remove any conflicting drivers that may be loaded. The error simply means that the module we want to remove is not loaded so we can't remove it. No problem!

I think all you really need to do is:```
cd Downloads/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1212.20101208
sudo su
chmod +x install.sh
./install.sh
```Substitute the location you downloaded the file if it's not Downloads. Press any key followed by Enter to exit the install process.```
modprobe 8192su
exit
```Is your wireless working now?

---

### Post by cd-r80 on 2011-01-03
No. It is not working. 

make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'
Compile make driver ok!!
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-27-generic
################################################################
The Setup Script is completed !
Plese Press any keyword to exit.

sudo modprobe 8192su
FATAL: Module 8192su not found.

dmesg:

[ 7860.390168] usb_write8...error(-19)
[ 7860.390174] reg 0xf0, usb read TimeOut! status:-19 value=0xff
[ 7860.390181] usb_read_port_cancel 
[ 7860.390187] usb_read_port_cancel 
[ 7860.390192] -rtw_dev_unload
[ 7860.390196] +r871xu_dev_remove, hw_init_completed=1
[ 7860.390296] free_recv_skb_queue not empty, 8
[ 7860.390353] -r871xu_dev_remove, done

---

### Post by chili555 on 2011-01-03
Oops! Sorry, I goofed. It's supposed to be:```
sudo modprobe 8192cu
```

---

### Post by cd-r80 on 2011-01-03
sudo modprobe 8192cu

dmesg
[13027.242592] usb_write8...error(-19)
[13027.242595] reg 0xf0, usb read TimeOut! status:-19 value=0xff
[13027.242597] usb_read_port_cancel 
[13027.242600] usb_read_port_cancel 
[13027.242602] -rtw_dev_unload
[13027.242603] +r871xu_dev_remove, hw_init_completed=1
[13027.242648] free_recv_skb_queue not empty, 8
[13027.242663] -r871xu_dev_remove, done

---

### Post by chili555 on 2011-01-03
Please try a reboot and post:```
dmesg | grep 819
lsmod | grep 819
```Thanks.

---

### Post by cd-r80 on 2011-01-03
dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    1.881954] Linux agpgart interface v0.103
[    2.763609] ata3: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684100 irq 26
[    2.763613] ata4: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684180 irq 26
[    2.763616] ata5: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684200 irq 26
[    2.763620] ata6: SATA max UDMA/133 abar m8192@0xf2684000 port 0xf2684280 irq 26
[    9.968819] Disabling lock debugging due to kernel taint

lsmod | grep 819

I cannot boot dongle plugged in.

---

### Post by chili555 on 2011-01-03
> I cannot boot dongle plugged in.I don't understand that. The driver 8192cu is correct for your device:>  modinfo 8192cu | grep 8176
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8176[/COLOR]d*dc*dsc*dp*ic*isc*ip*May I assume that the install process went without incident aside from this, which is to be expected?> ERROR: Module 8192cu does not exist in /proc/modulesPlease do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you insert the device and note any errors or warnings. Post them here.

---

### Post by cd-r80 on 2011-01-03
Jan  3 22:09:28 lightning kernel: [ 4148.927437] reg 0x33, usb read TimeOut! status:-19 value=0x0
Jan  3 22:09:28 lightning kernel: [ 4148.927447] pdmpriv->TxPowerTrackControl = 1
Jan  3 22:09:28 lightning kernel: [ 4148.927453] reg 0x40, usb read TimeOut! status:-19 value=0x0
Jan  3 22:09:28 lightning kernel: [ 4148.927459] reg 0x40, usb write TimeOut! status:-19 value=0x0
Jan  3 22:09:28 lightning kernel: [ 4148.927464] usb_write8...error(-19)
Jan  3 22:09:28 lightning kernel: [ 4148.927470] reg 0xf0, usb read TimeOut! status:-19 value=0x0
Jan  3 22:09:28 lightning kernel: [ 4148.927477] reg 0x15, usb write TimeOut! status:-19 value=0xe9
Jan  3 22:09:28 lightning kernel: [ 4148.927482] usb_write8...error(-19)
Jan  3 22:09:28 lightning kernel: [ 4148.927487] reg 0xf0, usb read TimeOut! status:-19 value=0xe9
Jan  3 22:09:28 lightning kernel: [ 4148.927496] MAC Address = 0-e0-4c-3-23-21
Jan  3 22:09:28 lightning kernel: [ 4148.927569] -871x_drv - drv_open, bup=1
Jan  3 22:09:28 lightning kernel: [ 4148.928692] ADDRCONF(NETDEV_UP): wlan2: link is not ready
Jan  3 22:09:28 lightning kernel: [ 4148.952827] (2)8192cu_drv - drv_close, bup=1, hw_init_completed=1
Jan  3 22:09:28 lightning kernel: [ 4148.952856] -871x_drv - drv_close, bup=1
Jan  3 22:09:28 lightning kernel: [ 4148.954554] ###> rtw_cmd_thread break.................
Jan  3 22:09:28 lightning kernel: [ 4149.022566] +rtw_dev_unload
Jan  3 22:09:28 lightning kernel: [ 4149.022579] reg 0x522, usb write TimeOut! status:-19 value=0xff
Jan  3 22:09:28 lightning kernel: [ 4149.022582] usb_write8...error(-19)
Jan  3 22:09:28 lightning kernel: [ 4149.022585] reg 0xf0, usb read TimeOut! status:-19 value=0xff
Jan  3 22:09:28 lightning kernel: [ 4149.022588] usb_read_port_cancel 
Jan  3 22:09:28 lightning kernel: [ 4149.022590] usb_read_port_cancel 
Jan  3 22:09:28 lightning kernel: [ 4149.022592] -rtw_dev_unload
Jan  3 22:09:28 lightning kernel: [ 4149.022594] +r871xu_dev_remove, hw_init_completed=1
Jan  3 22:09:28 lightning kernel: [ 4149.022637] free_recv_skb_queue not empty, 8
Jan  3 22:09:28 lightning kernel: [ 4149.022653] -r871xu_dev_remove, done

2011-01-03 22:09:28	lightning	NetworkManager	<WARN>  wireless_get_range(): (wlan2): couldn't get driver range information (19).
2011-01-03 22:09:28	lightning	NetworkManager	   SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/net/wlan2, iface: wlan2)
2011-01-03 22:09:28	lightning	NetworkManager	<info>  (wlan2): now unmanaged
2011-01-03 22:09:28	lightning	NetworkManager	<info>  (wlan2): device state change: 2 -> 1 (reason 36)
2011-01-03 22:09:28	lightning	NetworkManager	<info>  (wlan2): cleaning up...
2011-01-03 22:09:28	lightning	wpa_supplicant[1108]	Could not get interface 'wlan2' flags
2011-01-03 22:09:28	lightning	wpa_supplicant[1108]	Failed to initialize driver interface
2011-01-03 22:09:28	lightning	NetworkManager	<WARN>  nm_supplicant_interface_add_cb(): Unexpected supplicant error getting interface: wpa_supplicant couldn't grab this interface.

---

### Post by cd-r80 on 2011-01-04
I found new driver package rtl8192CU_linux_v2.0.939.20100726.tar.gz
. But how I should uninstall the module which I compiled first? It gives error / conflicts & lsusb does not show the device anymore.

---

### Post by chili555 on 2011-01-04
The file you found is actually older; it was written in July of 2010. The version you compiled previously was written in December. However, perhaps the older version is better suited to your older 2.6.32 kernel. Please do:```
cd Downloads/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1212.20101208/driver/rtl8192CU_linux_v2.0.1212.20101208
sudo su
make uninstall
exit
```Substitute the location you downloaded the file if it's not Downloads. What errors are you getting?

---

### Post by cd-r80 on 2011-01-04
It compiled ok & insmod 8192cu.ko. But same errors like in dmesg or messages when I plug the dongle. I have ath5k & mac80211 at same time. Perhaps I need ieee80211 or something? Or it does not work with mac80211 like rtl8187?

---

### Post by cd-r80 on 2011-01-04
Perhaps these drivers do not support 64bit?

CPU supported:
	x86
	ARM

---

### Post by chili555 on 2011-01-04
Why do you also have ath5k? Do you have two wireless cards? I think it's likely that 64-bit is a problem.

---

### Post by cd-r80 on 2011-01-05
Ath5k is my laptop internal card. I have been just testing aircarack-ng & my AP. Ath5k & rtk8187 work well together in that. I also thought to use later 8192cu with separate IP & make also wireless Backup unit. Edup EP-N8508 is just that 5mm size tiny dongle which totally integrates to my laptop.

---

### Post by damencho on 2011-01-06
I have the same problem, Ubuntu 10.10, kernel: 2.6.35-24-generic x86_64.
Installed latest drivers I found 
RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1212.20101208

[  693.984598] rtw driver version=v2.0.1212.20101205
[  693.984660] usbcore: registered new interface driver rtw_usb_drv

When plugs the dongle a lot of logs most of them : 
kernel: [  755.489604] reg 0x4, usb write TimeOut! status:-19 value=0x0

Here is the whole output [http://pastebin.com/7xhkzYNC](http://pastebin.com/7xhkzYNC)

Anything I can try.

---

### Post by chili555 on 2011-01-06
> **damencho said:**
> I have the same problem, Ubuntu 10.10, kernel: 2.6.35-24-generic x86_64.
Installed latest drivers I found 
RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1212.20101208

[  693.984598] rtw driver version=v2.0.1212.20101205
[  693.984660] usbcore: registered new interface driver rtw_usb_drv

When plugs the dongle a lot of logs most of them : 
kernel: [  755.489604] reg 0x4, usb write TimeOut! status:-19 value=0x0

Here is the whole output [http://pastebin.com/7xhkzYNC](http://pastebin.com/7xhkzYNC)

Anything I can try.We are not at all sure that this driver works with 64-bit. You might email the developer. 

Are you quite sure there was ***no*** error or warning in the install.sh process, or did you use make and make install from the folder containing the Makefile?

---

### Post by damencho on 2011-01-06
No errors, some warnings. Used install.sh and also tried make and make install, no error with both methods.

---

### Post by chili555 on 2011-01-06
I think it's a 64-bit issue, although I am not knowledgable enough to have more than a hunch. When I Google this:> reg 0x4, usb write TimeOut! status:-19 value=0x0...it is usually a 64-bit system. I think the Larry Finger mentioned here is the developer.

[http://www.spinics.net/lists/linux-wireless/msg59124.html](http://www.spinics.net/lists/linux-wireless/msg59124.html)

---

### Post by adamis on 2011-01-22
I am getting these same issues with a RealTek 8912cu driver as well. I am running a the Ubuntu 2.6.35 kernel compiled for AMD64. Sort of frustrating, but hoping that somebody will be able to figure it out.

---

### Post by oldgold97 on 2011-01-29
Realtek has a new RTL8192CU driver on their website, released on 1/28/2011.  I used this driver to get the device working on an HP Pavilion AMD64X2 Turion

---

### Post by cd-r80 on 2011-01-30
It seems to install ok. But I cannot get it to connect to AP (WPA).

2011-01-30 11:46:02	lightning	kernel	[12211.522552] issue_auth auth_algo= #####(algo:2) auth_seq=1
2011-01-30 11:46:02	lightning	kernel	[12211.522558] ==>issue_auth ,auth_algm(0x00)
2011-01-30 11:46:02	lightning	kernel	[12211.522564] ==> issue_auth set auth_seq_num(1)
2011-01-30 11:46:02	lightning	kernel	[12211.570063] link_timer_hdl: auth timeout and try again
2011-01-30 11:46:02	lightning	kernel	[12211.570085] issue_auth auth_algo= #####(algo:2) auth_seq=1
2011-01-30 11:46:02	lightning	kernel	[12211.570090] ==>issue_auth ,auth_algm(0x00)
2011-01-30 11:46:02	lightning	kernel	[12211.570095] ==> issue_auth set auth_seq_num(1)
2011-01-30 11:46:03	lightning	kernel	[12211.622534] report_join_res(-1)

---

### Post by cd-r80 on 2011-01-30
2011-01-30 11:18:57	lightning	kernel	[10586.500520] <==== ReadAdapterInfo8192C
2011-01-30 11:18:57	lightning	kernel	[10586.500533] MAC Address from efuse= mac
2011-01-30 11:18:57	lightning	NetworkManager	   SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/net/wlan2, iface: wlan2)
2011-01-30 11:18:57	lightning	kernel	[10586.527327] udev: renamed network interface wlan1 to wlan2
2011-01-30 11:18:57	lightning	kernel	[10586.531061] rtw_wx_set_scan padapter->bup=0
2011-01-30 11:18:57	lightning	NetworkManager	   SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/net/wlan2, iface: wlan2): no ifupdown configuration found.
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): driver supports SSID scans (scan_capa 0x3F).
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): new 802.11 WiFi device (driver: 'rtw_usb_drv')
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): exported as /org/freedesktop/NetworkManager/Devices/2
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): now managed
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): device state change: 1 -> 2 (reason 2)
2011-01-30 11:18:57	lightning	NetworkManager	<info>  (wlan2): bringing up device.
2011-01-30 11:18:57	lightning	kernel	[10586.535603] +8192cu_drv - drv_open, bup=0
2011-01-30 11:18:58	lightning	kernel	[10586.630521]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
2011-01-30 11:18:58	lightning	kernel	[10586.630559] fw_ver=v60, fw_subver=0, sig=0x88c0
2011-01-30 11:18:58	lightning	kernel	[10586.675629] fw download ok!
2011-01-30 11:18:58	lightning	kernel	[10586.675640] Set RF Chip ID to RF_6052 and RF type to 1T1R.
2011-01-30 11:18:58	lightning	kernel	[10586.675647] rf_chip=0x4, rf_type=0x3
2011-01-30 11:18:58	lightning	kernel	[10587.025239] IQK:Start!!!
2011-01-30 11:18:58	lightning	kernel	[10587.036111] Path A IQK Success!!
2011-01-30 11:18:58	lightning	kernel	[10587.043736] Path A IQK Success!!
2011-01-30 11:18:58	lightning	kernel	[10587.048360] IQK: final_candidate is 0
2011-01-30 11:18:58	lightning	kernel	[10587.048364] IQK: Reg RegEBC=0 RegEC4=0 RegECC=0
2011-01-30 11:18:58	lightning	kernel	[10587.048365]  Path A IQ Calibration Success !
2011-01-30 11:18:58	lightning	kernel	[10587.157238] MAC Address from REG = mac
2011-01-30 11:18:58	lightning	kernel	[10587.158114] pdmpriv->TxPowerTrackControl = 1
2011-01-30 11:18:58	lightning	kernel	[10587.158489] MAC Address = 0-e0-4c-3-23-21
2011-01-30 11:18:58	lightning	kernel	[10587.162369] -871x_drv - drv_open, bup=1
2011-01-30 11:18:58	lightning	NetworkManager	<info>  (wlan2): preparing device.
2011-01-30 11:18:58	lightning	NetworkManager	<info>  (wlan2): deactivating device (reason: 2).
2011-01-30 11:18:58	lightning	kernel	[10587.162808] ADDRCONF(NETDEV_UP): wlan2: link is not ready
2011-01-30 11:18:58	lightning	kernel	[10587.163336] set_mode = IW_MODE_INFRA
2011-01-30 11:18:58	lightning	kernel	[10587.165154] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
2011-01-30 11:18:58	lightning	kernel	[10587.165163] set_mode = IW_MODE_INFRA
2011-01-30 11:18:58	lightning	NetworkManager	<info>  (wlan2): supplicant interface state:  starting -> ready
2011-01-30 11:18:58	lightning	NetworkManager	<info>  (wlan2): device state change: 2 -> 3 (reason 42)

---

