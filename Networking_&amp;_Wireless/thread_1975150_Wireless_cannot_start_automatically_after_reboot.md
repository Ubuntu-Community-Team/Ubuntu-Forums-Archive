---
title: "Wireless cannot start automatically after reboot"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by jy109 on 2012-05-07
Dear All,

I'm green on both Linux and Ubuntu, and using Ubuntu 12.04 now. 

The issue of my wireless NIC, and I tried to fix it by follow the link: [http://ubuntuforums.org/archive/index.php/t-1714552.html](http://ubuntuforums.org/archive/index.php/t-1714552.html)

The solution is work, however when I reboot the PC the setting seems back to before. and I need to repeat the following command on every reboot:

The command as following:

jim@Jim-GATEWAY:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jim@Jim-GATEWAY:~$ sudo modprobe -v iwlagn
[sudo] password for jim: 
insmod /lib/modules/3.2.0-24-generic/updates/compat/compat.ko 
insmod /lib/modules/3.2.0-24-generic/updates/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-24-generic/updates/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-24-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko 
jim@Jim-GATEWAY:~$ sudo depmod -a
jim@Jim-GATEWAY:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 1990

Can any expert to help? how can I "save" for the configuration permanently?

Many thanks,
Jim

---

### Post by chili555 on 2012-05-07
If *iwlagn* is correct for your device, it ought to start and run perfectly. Let's check a few things:```
lspci -nn | grep 0280
dmesg | grep iwl
```I wonder if it is Network Manager that's misbehaving.

---

### Post by jy109 on 2012-05-07
Thanks for your reply

Here is the output:

jim@Jim-GATEWAY:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
jim@Jim-GATEWAY:~$ dmesg | grep iwl
jim@Jim-GATEWAY:~$ 
jim@Jim-GATEWAY:~$ 
jim@Jim-GATEWAY:~$

---

### Post by chili555 on 2012-05-07
That's the correct driver for your device. Let's dig deeper.```
sudo modprobe iwlwifi
dmesg | grep iwlwifi
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Thanks.

---

### Post by jy109 on 2012-05-08
please~~~~

jim@Jim-GATEWAY:~$  
jim@Jim-GATEWAY:~$ sudo modprobe iwlwifi 
[sudo] password for jim:  
jim@Jim-GATEWAY:~$ dmesg | grep iwlwifi 
[   85.574898] iwlwifi 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   85.574912] iwlwifi 0000:02:00.0: setting latency timer to 64 
[   85.574941] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000 
[   85.574946] iwlwifi 0000:02:00.0: pci_resource_base = f806c000 
[   85.574950] iwlwifi 0000:02:00.0: HW Revision ID = 0x0 
[   85.575057] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X 
[   85.584213] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138 
[   85.584544] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled 
[   85.584549] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled 
[   85.584553] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled 
[   85.584557] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE disabled 
[   85.584560] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P enabled 
[   85.584566] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C 
[   85.584646] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S 
[   85.603974] iwlwifi 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6 
[   85.603979] iwlwifi 0000:02:00.0: Device SKU: 0x50 
[   85.603984] iwlwifi 0000:02:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3 
[   85.604041] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels 
[   85.629719] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S 
[   85.690820] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S 
jim@Jim-GATEWAY:~$  
jim@Jim-GATEWAY:~$ cat /etc/modprobe.d/blacklist.conf | tail -n10 
 
# ugly and loud noise, getting on everyone's nerves; this should be done by a 
# nice pulseaudio bing (Ubuntu: #77010) 
blacklist pcspkr 
 
# EDAC driver for amd76x clashes with the agp driver preventing the aperture 
# from being initialised (Ubuntu: #297750). Blacklist so that the driver 
# continues to build and is installable for the few cases where its 
# really needed. 
blacklist amd76x_edac 
jim@Jim-GATEWAY:~$

---

### Post by chili555 on 2012-05-08
Ordinarily, the module *iwlwifi* will load automatically when the system sees the device; once in a great while, it needs a little help. Please open a terminal and do:```
sudo su
echo iwlwifi >> /etc/modules
exit
```Now does it start on boot?

---

### Post by jy109 on 2012-05-08
Oh... work perfectly!!!!!!!!!!

Many thanks for your kindly help guy

I love Ubuntu~~~~~~

---

### Post by chili555 on 2012-05-08
Glad it's working! Would you please use thread tools at the top to Mark Solved?

---

