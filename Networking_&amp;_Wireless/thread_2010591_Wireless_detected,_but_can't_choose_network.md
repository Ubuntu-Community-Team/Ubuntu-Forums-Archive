---
title: "Wireless detected, but can't choose network?"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by Cameronmo on 2012-06-25
After deciding to just ditch using my old slow linksys USB adapter, I bought an ASUS N13 USB adapter.  From various sources, I learned that the adapter should be usable immediately after plugging in.  As soon as I plugged it in, wireless networks, including my own, were detected.  Upon clicking on my network to enter the password, nothing happens, and if I go into the wireless network set up, I can't actually select my connection (even though it is displayed.)  I couldn't find anyone with the same problem.  Most people with wireless issues are fine as soon as they are able to connect to there router from what I can see.

---

### Post by clay7 on 2012-06-26
Try
```
sudo /etc/init.d/networking restart
```

If that doesn't work, let's check the wireless driver. To do this:
```
sudo lspci
``` 
This will list info about a lot of your hardware. Find the line that says something about your wireless driver (you could possibly get the single line with your info with this command instead of the last ```
sudo lspci | grep -i wireless
```)

Each line will have numbers in front of it. For example, my output is:
[COLOR="DimGray"]02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)[/COLOR]

Take that number and run this command (using your numbers instead of mine)
```
sudo lspci -vv -s 02:00.0
```

This will tell you the driver. Mine is ath5k.

Take your wireless down (use your wireless device...mine is wlan0...you can find your wireless device by /sbin/ifconfig )
```
sudo /sbin/ifconfig wlan0 down
```

Now, do the following, using your driver info instead of mine:

```
sudo rmmod ath5k
sudo rfkill block all
sudo rfkill unblock all
sudo modprobe ath5k
sudo rfkill unblock all
sudo /sbin/ifconfig wlan0 up
```

hth

---

### Post by wildmanne39 on 2012-06-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Cameronmo on 2012-07-08
Some Results:

```
cameron@Cameron-2:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Cameron-2 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 athlon i386 GNU/Linux

```

```
cameron@Cameron-2:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Device [103c:2a34]
	Kernel driver in use: forcedeth
cameron@Cameron-2:~$ 

```

```
cameron@Cameron-2:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 002: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded

```

```
cameron@Cameron-2:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```


```
cameron@Cameron-2:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
cameron@Cameron-2:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  0 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211
snd                    62064  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
nv_tco                 13399  0 
nouveau               712294  2 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  4 nouveau,ttm,drm_kms_helper
i2c_nforce2            12906  0 
mac_hid                13077  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
ndiswrapper           192268  0 
video                  19068  1 nouveau
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
usb_storage            39646  0 
uas                    17828  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_amd               13750  0 
forcedeth              58096  0 
sata_nv                23360  2 

```


Hope it helps.

---

### Post by wildmanne39 on 2012-07-08
Hi, please do:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Watch for errors.
Then:
```
gksudo gedit /etc/modprobe.d/rtl8192cu.conf
```
A new empty file will open, paste this one line into the file.

```
options rtl8192cu swenc=1
```

Proofread, save and close gedit, then reboot.
Thanks

---

### Post by Cameronmo on 2012-07-09
```
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

These three commands didn't seem to work, where the given files were not located and the third command didn't seem to do anything. I did do all the other commands though.

---

### Post by wildmanne39 on 2012-07-10
Hi, please post the output of:
```
nm-tool
lsmod | grep rtl
dmesg | egrep 'rtl|firm|wpa|etork|wlan0'
ndiswrapper -l
```
do no install ndiswrapper, we are just checking to make sure it is not still installed.
Thanks

---

### Post by Cameronmo on 2012-07-10
```
cameron@Cameron-2:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:18:F3:DE:12:A9

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        C8:60:00:D4:6F:13

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE535:        Infra, 64:0F:28:F1:46:B9, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    NETGEAR02:       Infra, 20:4E:7F:B7:BC:E1, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA2


```


```
cameron@Cameron-2:~$ lsmod | grep rtl
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211

```

```
cameron@Cameron-2:~$ lsmod | grep rtl
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211
cameron@Cameron-2:~$ dmesg | egrep 'rtl|firm|wpa|etork|wlan0'
[   14.162906] rtl8192cu: MAC address: c8:60:00:d4:6f:13
[   14.162915] rtl8192cu: Board Type 0
[   15.194401] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   15.344079] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.344823] usbcore: registered new interface driver rtl8192cu
[   21.293522] rtl8192cu: MAC auto ON okay!
[   21.326957] rtl8192cu: Tx queue select: 0x05
[   21.327668] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   21.736725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.737433] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

```
cameron@Cameron-2:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```

 Thanks for all this help by the way.

---

### Post by wildmanne39 on 2012-07-10
Hi, this driver is very troublesome please do the following one line at a time and watch for errors.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192
```
Thanks

---

### Post by Cameronmo on 2012-07-10
```
cameron@Cameron-2:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
[sudo] password for cameron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 16 not upgraded.
Need to get 5,974 B/1,032 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main build-essential i386 11.5ubuntu2 [5,974 B]
Fetched 5,974 B in 0s (13.1 kB/s)          
(Reading database ... 231540 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using .../build-essential_11.5ubuntu2_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1ubuntu3 (using .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.2.0-25-generic-pae 3.2.0-25.40 (using .../linux-headers-3.2.0-25-generic-pae_3.2.0-25.40_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-25-generic-pae ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu2) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up linux-headers-3.2.0-25-generic-pae (3.2.0-25.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
cameron@Cameron-2:~$ 

```

```
cameron@Cameron-2:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
--2012-07-10 15:49:16--  http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1202618 (1.1M) [application/octet-stream]
Saving to: `2844083-rtl8192cu-3.3.23192_dkms.tar.gz'

100%[======================================>] 1,202,618    567K/s   in 2.1s    

2012-07-10 15:49:18 (567 KB/s) - `2844083-rtl8192cu-3.3.23192_dkms.tar.gz' saved [1202618/1202618]

```

```
cameron@Cameron-2:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
rtl8192cu-3.3.23192/
rtl8192cu-3.3.23192/src/
rtl8192cu-3.3.23192/src/os_dep/
rtl8192cu-3.3.23192/src/include/
rtl8192cu-3.3.23192/src/hal/
rtl8192cu-3.3.23192/src/core/
rtl8192cu-3.3.23192/src/os_dep/linux/
rtl8192cu-3.3.23192/src/include/byteorder/
rtl8192cu-3.3.23192/src/hal/rtl8192d/
rtl8192cu-3.3.23192/src/hal/rtl8192c/
rtl8192cu-3.3.23192/src/core/efuse/
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/
rtl8192cu-3.3.23192/Makefile
rtl8192cu-3.3.23192/dkms.conf
rtl8192cu-3.3.23192/src/wlan0dhcp
rtl8192cu-3.3.23192/src/Makefile
rtl8192cu-3.3.23192/src/make_drv
rtl8192cu-3.3.23192/src/Kconfig
rtl8192cu-3.3.23192/src/ifcfg-wlan0
rtl8192cu-3.3.23192/src/clean
rtl8192cu-3.3.23192/src/autoconf_rtl8192d_usb_linux.h
rtl8192cu-3.3.23192/src/autoconf_rtl8192c_usb_linux.h
rtl8192cu-3.3.23192/src/os_dep/osdep_service.c
rtl8192cu-3.3.23192/src/include/rtw_ioctl.h
rtl8192cu-3.3.23192/src/include/rtw_mp.h
rtl8192cu-3.3.23192/src/include/rtl8192c_sreset.h
rtl8192cu-3.3.23192/src/include/xmit_osdep.h
rtl8192cu-3.3.23192/src/include/if_ether.h
rtl8192cu-3.3.23192/src/include/rtw_led.h
rtl8192cu-3.3.23192/src/include/ip.h
rtl8192cu-3.3.23192/src/include/rtl8192c_hal.h
rtl8192cu-3.3.23192/src/include/basic_types.h
rtl8192cu-3.3.23192/src/include/circ_buf.h
rtl8192cu-3.3.23192/src/include/rtw_br_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyReg.h
rtl8192cu-3.3.23192/src/include/rtw_io.h
rtl8192cu-3.3.23192/src/include/sdio_hal.h
rtl8192cu-3.3.23192/src/include/rtw_security.h
rtl8192cu-3.3.23192/src/include/autoconf.h
rtl8192cu-3.3.23192/src/include/usb_hal.h
rtl8192cu-3.3.23192/src/include/rtw_rf.h
rtl8192cu-3.3.23192/src/include/rtw_mp_phy_regdef.h
rtl8192cu-3.3.23192/src/include/rtw_iol.h
rtl8192cu-3.3.23192/src/include/sta_info.h
rtl8192cu-3.3.23192/src/include/osdep_intf.h
rtl8192cu-3.3.23192/src/include/rtw_debug.h
rtl8192cu-3.3.23192/src/include/mlme_osdep.h
rtl8192cu-3.3.23192/src/include/rtw_event.h
rtl8192cu-3.3.23192/src/include/rtl8192c_cmd.h
rtl8192cu-3.3.23192/src/include/pci_ops.h
rtl8192cu-3.3.23192/src/include/rtl8192d_rf.h
rtl8192cu-3.3.23192/src/include/rtw_cmd.h
rtl8192cu-3.3.23192/src/include/pci_osintf.h
rtl8192cu-3.3.23192/src/include/h2clbk.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_set.h
rtl8192cu-3.3.23192/src/include/rtl8192d_cmd.h
rtl8192cu-3.3.23192/src/include/rtw_version.h
rtl8192cu-3.3.23192/src/include/rtl8192d_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_byteorder.h
rtl8192cu-3.3.23192/src/include/drv_types_xp.h
rtl8192cu-3.3.23192/src/include/rtw_eeprom.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_query.h
rtl8192cu-3.3.23192/src/include/osdep_service.h
rtl8192cu-3.3.23192/src/include/usb_vendor_req.h
rtl8192cu-3.3.23192/src/include/drv_conf.h
rtl8192cu-3.3.23192/src/include/pci_hal.h
rtl8192cu-3.3.23192/src/include/rtw_p2p.h
rtl8192cu-3.3.23192/src/include/Hal8192CEHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_osintf.h
rtl8192cu-3.3.23192/src/include/Hal8192DETestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_xp.h
rtl8192cu-3.3.23192/src/include/rtw_mp_ioctl.h
rtl8192cu-3.3.23192/src/include/rtl8192d_led.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyCfg.h
rtl8192cu-3.3.23192/src/include/drv_types_ce.h
rtl8192cu-3.3.23192/src/include/ieee80211_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DEHWImg.h
rtl8192cu-3.3.23192/src/include/drv_types.h
rtl8192cu-3.3.23192/src/include/hal_init.h
rtl8192cu-3.3.23192/src/include/rtw_mlme.h
rtl8192cu-3.3.23192/src/include/rtl8192c_spec.h
rtl8192cu-3.3.23192/src/include/Hal8192DUHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_linux.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_rtl.h
rtl8192cu-3.3.23192/src/include/mp_custom_oid.h
rtl8192cu-3.3.23192/src/include/ethernet.h
rtl8192cu-3.3.23192/src/include/rtw_ht.h
rtl8192cu-3.3.23192/src/include/usb_ops.h
rtl8192cu-3.3.23192/src/include/Hal8192DUTestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_ce.h
rtl8192cu-3.3.23192/src/include/Hal8192CUHWImg.h
rtl8192cu-3.3.23192/src/include/rtw_efuse.h
rtl8192cu-3.3.23192/src/include/drv_types_linux.h
rtl8192cu-3.3.23192/src/include/recv_osdep.h
rtl8192cu-3.3.23192/src/include/ieee80211.h
rtl8192cu-3.3.23192/src/include/sdio_ops.h
rtl8192cu-3.3.23192/src/include/osdep_ce_service.h
rtl8192cu-3.3.23192/src/include/rtl8192d_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_pwrctrl.h
rtl8192cu-3.3.23192/src/include/rtw_qos.h
rtl8192cu-3.3.23192/src/include/rtl8192c_event.h
rtl8192cu-3.3.23192/src/include/rtw_xmit.h
rtl8192cu-3.3.23192/src/include/rtl8192d_dm.h
rtl8192cu-3.3.23192/src/include/usb_osintf.h
rtl8192cu-3.3.23192/src/include/nic_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_rf.h
rtl8192cu-3.3.23192/src/include/rtl8192c_dm.h
rtl8192cu-3.3.23192/src/include/rtl8192d_hal.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyCfg.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyReg.h
rtl8192cu-3.3.23192/src/include/farray.h
rtl8192cu-3.3.23192/src/include/rtl8192d_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_led.h
rtl8192cu-3.3.23192/src/include/wifi.h
rtl8192cu-3.3.23192/src/include/rtw_mlme_ext.h
rtl8192cu-3.3.23192/src/include/rtw_recv.h
rtl8192cu-3.3.23192/src/include/cmd_osdep.h
rtl8192cu-3.3.23192/src/include/wlan_bssdef.h
rtl8192cu-3.3.23192/src/hal/hal_init.c
rtl8192cu-3.3.23192/src/core/rtw_iol.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_set.c
rtl8192cu-3.3.23192/src/core/rtw_mp_ioctl.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_rtl.c
rtl8192cu-3.3.23192/src/core/rtw_io.c
rtl8192cu-3.3.23192/src/core/rtw_mlme_ext.c
rtl8192cu-3.3.23192/src/core/rtw_wlan_util.c
rtl8192cu-3.3.23192/src/core/rtw_pwrctrl.c
rtl8192cu-3.3.23192/src/core/rtw_rf.c
rtl8192cu-3.3.23192/src/core/rtw_sta_mgt.c
rtl8192cu-3.3.23192/src/core/rtw_mp.c
rtl8192cu-3.3.23192/src/core/rtw_mlme.c
rtl8192cu-3.3.23192/src/core/rtw_cmd.c
rtl8192cu-3.3.23192/src/core/rtw_security.c
rtl8192cu-3.3.23192/src/core/rtw_ieee80211.c
rtl8192cu-3.3.23192/src/core/rtw_p2p.c
rtl8192cu-3.3.23192/src/core/rtw_debug.c
rtl8192cu-3.3.23192/src/core/rtw_eeprom.c
rtl8192cu-3.3.23192/src/core/rtw_br_ext.c
rtl8192cu-3.3.23192/src/core/rtw_recv.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_query.c
rtl8192cu-3.3.23192/src/core/rtw_xmit.c
rtl8192cu-3.3.23192/src/os_dep/linux/xmit_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/sdio_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/pci_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/mlme_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/usb_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/os_intfs.c
rtl8192cu-3.3.23192/src/os_dep/linux/recv_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/ioctl_linux.c
rtl8192cu-3.3.23192/src/include/byteorder/generic.h
rtl8192cu-3.3.23192/src/include/byteorder/little_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/big_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/swabb.h
rtl8192cu-3.3.23192/src/include/byteorder/swab.h
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_cmd.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_sreset.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_cmd.c
rtl8192cu-3.3.23192/src/core/efuse/rtw_efuse.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_led.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUTestHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c

```

```
cameron@Cameron-2:~$ sudo dkms add -m rtl8192cu -v 3.3.23192

Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->
                 /usr/src/rtl8192cu-3.3.23192

DKMS: add completed.

```

```
cameron@Cameron-2:~$ sudo dkms build -m rtl8192cu -v 3.3.23192

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all...............
cleaning build area....

DKMS: build completed.

```

```
cameron@Cameron-2:~$ sudo dkms install -m rtl8192cu -v 3.3.23192

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-25-generic-pae/updates/dkms/

depmod........

DKMS: install completed.

```

Nothing appeared to have gone wrong.

---

### Post by wildmanne39 on 2012-07-10
Hi, did you reboot? are you able to connect?
Thanks

---

### Post by Cameronmo on 2012-07-10
I rebooted, but still had no luck, everything is acting the same way (nothing happens when I click on a network.)

---

### Post by wildmanne39 on 2012-07-10
Hi, please do:
```
sudo make unload
```
Then reboot.
Thanks

---

### Post by Cameronmo on 2012-07-10
Still no changes.

---

### Post by wildmanne39 on 2012-07-11
Hi, please post the output of:
```
dmesg | grep 819
lsmod | grep 819
```

What is the name of the network you want to connect too?
Thanks

---

### Post by Cameronmo on 2012-07-11
```
cameron@Cameron-2:~$ dmesg | grep 819
[    0.000000] Memory: 944868k/981952k available (5814k kernel code, 36632k reserved, 2841k data, 740k init, 68552k highmem)
[    1.908198] ata2.00: configured for UDMA/100
[   24.514941] rtl8192cu: MAC address: c8:60:00:d4:6f:13
[   24.514949] rtl8192cu: Board Type 0
[   26.207122] usbcore: registered new interface driver rtl8192cu
[   33.875431] rtl8192cu: MAC auto ON okay!
[   33.909933] rtl8192cu: Tx queue select: 0x05
[   33.910695] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[  252.222819] forcedeth 0000:00:14.0: eth0: link up
[  262.773729] rtl8192cu: MAC address: c8:60:00:d4:6f:13
[  262.773743] rtl8192cu: Board Type 0
[  262.822629] rtl8192cu: MAC auto ON okay!
[  262.856268] rtl8192cu: Tx queue select: 0x05
[  262.857039] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 7442.536204] rtl8192cu: MAC address: c8:60:00:d4:6f:13
[ 7442.536217] rtl8192cu: Board Type 0
[ 7442.591959] rtl8192cu: MAC auto ON okay!
[ 7442.625327] rtl8192cu: Tx queue select: 0x05
[ 7442.626099] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin

```

```
cameron@Cameron-2:~$ lsmod | grep 819
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi

```

I'm trying to connect to NETGEAR02

---

### Post by wildmanne39 on 2012-07-13
Hi, sorry for the late reply I am travelling right now. 

First unplug your wired connection so it does not interfere with the wireless connection then see if it will connect if not post the output of:
```
cat /etc/modprobe.d/blacklist.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/network/interfaces
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Cameronmo on 2012-07-13
```
cameron@Cameron-2:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

```
```
cameron@Cameron-2:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```
```
cameron@Cameron-2:~$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

```
```
cameron@Cameron-2:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```
 The last command didn't do anything after I entered my password.
Even with my ethernet cable unplugged, I can see the connection but nothing happens when I click on it.

---

### Post by Cameronmo on 2012-07-21
Anyone else care to lend a hand? It would be nice to get my wifi working so that typing this didn't involve putting another tower next to my desk for internet.

---

