---
title: "wireless showing but cant connect"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by zoerat on 2011-09-23
hi there i have read through the forum and see other people have the same problem as me but i still cant figure out whats going on, ive done fresh installments of ubuntu 11.04 many a time and when i first install it my wireless works fine, then it says im connected but i cant use the net.  im using a hp mini netbook, i need help

---

### Post by praseodym on 2011-09-23
Hi,

please show the terminal outputs of the commands:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by jas1291 on 2011-09-24
i have the same problem......i am using edimax usb router
here is my output
```
jasleen@jasleen-desktop:~$ uname -a
Linux jasleen-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
jasleen@jasleen-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications L2 100 Mbit Ethernet Adapter [1969:2048] (rev a0)
	Kernel driver in use: atl2
	Kernel modules: atl2
jasleen@jasleen-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 7392:7811  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jasleen@jasleen-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
ndiswrapper           184677  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
8192cu                247698  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
parport_pc             25962  1 
asus_atk0110            9017  0 
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
atl2                   22383  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
jasleen@jasleen-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F7:2E:4D   
          Bit Rate:48 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jasleen@jasleen-desktop:~$ rfkill list
jasleen@jasleen-desktop:~$ sudo iwlist scan
[sudo] password for jasleen: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:57:F7:2E:4D
                    ESSID:"UTStarcom"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=100/100 
```

---

### Post by praseodym on 2011-09-24
Hi jas1291,

uninstall ndiswrapper completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```and reboot. You may want to update the driver according to [this]("http://forum.ubuntuusers.de/topic/belkin-micro-usb-adapter/#post-2717574") thread.

---

### Post by jas1291 on 2011-09-24
praseodym
i did as you said........no luck.......
there is some dns server resolution problem........
pls help

---

### Post by praseodym on 2011-09-24
Your router allows new clients (MAC-filter off)? Firmware is up-to-date? Add the nameservers of your ISP or the google public NSs 8.8.8.8 and 8.8.4.4 directly in the NM-applet (IPv4-settings->Choose "Automatic (DHCP), addresses only" and add the NSs in DNS, separated by comma. Restart your network:

```
sudo service network-manager restart
```
Check:

```
route -n
cat /etc/resolv.conf
ifconfig -a
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by jas1291 on 2011-09-24
```
jasleen@jasleen-desktop:~$ sudo service network-manager restart
[sudo] password for jasleen: 
network-manager start/running, process 1998
jasleen@jasleen-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
jasleen@jasleen-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
nameserver 202.164.51.21
nameserver 202.164.32.82
jasleen@jasleen-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:24:2e  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe0a:242e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:244744 (244.7 KB)  TX bytes:52285 (52.2 KB)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7360 (7.3 KB)  TX bytes:7360 (7.3 KB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:11:dd:56  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe11:dd56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:298 errors:0 dropped:3465 overruns:0 frame:0
          TX packets:458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60817 (60.8 KB)  TX bytes:48542 (48.5 KB)

jasleen@jasleen-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F7:2E:4D   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jasleen@jasleen-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:57:F7:2E:4D
                    ESSID:"UTStarcom"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=100/100  

jasleen@jasleen-desktop:~$ rfkill list

```
firmware is up to date

---

### Post by praseodym on 2011-09-24
Try to upgrade the driver, see here (incl. Download-link):

[http://forum.ubuntuusers.de/post/3386772/](http://forum.ubuntuusers.de/post/3386772/)

unpack the driver into you /hme folder, set the executable flag (Right-click->properties->checkbox) and install the driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
cd NameOfFolder/ # <-------substitute
sudo chmod +x install.sh
sudo sh ./install.sh

```
reboot

---

### Post by jas1291 on 2011-09-24
thank u so much for your help........but i tried it didnt work......i am switching back to wired.......wish i could pay u back in some way......thanks a lot

---

### Post by praseodym on 2011-09-25
Please show:

```
modinfo 8192cu
locate 8192cu | grep lib
lsmod
dmesg | grep 8192
```

---

### Post by jas1291 on 2011-09-27
hello sir.........
here's your req info
```

jasleen@jasleen-desktop:~$ modinfo 8192cu
filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v3.0.2164.20110715
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     43717D922DB2B0EAD001526
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
parm:           rtw_ips_mode:int
parm:           ifname:charp
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_max_roaming_times:uint
jasleen@jasleen-desktop:~$ locate 8192cu | grep lib
/lib/modules/2.6.32-28-generic/kernel/drivers/net/wireless/8192cu.ko
/lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/8192cu.ko
jasleen@jasleen-desktop:~$ lsmod
Module                  Size  Used by
iptable_filter          1369  0 
ip_tables               9899  1 iptable_filter
x_tables               14175  1 ip_tables
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                11385  0 
vgastate                8961  1 vga16fb
8192cu                446110  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
i915                  288611  3 
psmouse                63677  0 
drm_kms_helper         29329  1 i915
asus_atk0110            9017  0 
parport_pc             25962  1 
serio_raw               3978  0 
atl2                   22383  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
intel_agp              24375  2 i915
drm                   162377  4 i915,drm_kms_helper
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
jasleen@jasleen-desktop:~$ dmesg | grep 8192
[   11.685783] CHIP TYPE: RTL8188C_8192C
[   11.688718] ====> ReadAdapterInfo8192C
[   11.970362] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   11.970365] <==== ReadAdapterInfo8192C in 280 ms
[   11.971288] usbcore: registered new interface driver rtl8192cu
[   13.803735] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   14.560121] rtl8192c_dm_RF_Saving(): RF_Normal
[   15.079085] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   16.366651] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  270.103786] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  271.340292] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  276.227868] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  276.335130] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  277.586375] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  308.039161] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  309.330673] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  314.223870] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  314.319048] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  315.371253] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
```

---

### Post by praseodym on 2011-09-27
Do you really need the firewall? Router-settings are DHCP?

Check

```
iwconfig
rfkill list
sudo iwlist scan
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by jas1291 on 2011-09-30
i have disabled firewall........
```

jasleen@jasleen-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F7:2E:4D   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/100  Signal level=58/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jasleen@jasleen-desktop:~$ rfkill list
jasleen@jasleen-desktop:~$ sudo iwlist scan
[sudo] password for jasleen: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:57:F7:2E:4D
                    ESSID:"UTStarcom"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=57/100  Signal level=57/100  

jasleen@jasleen-desktop:~$ ifonfig -a
No command 'ifonfig' found, did you mean:
 Command 'ifconfig' from package 'net-tools' (main)
ifonfig: command not found
jasleen@jasleen-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:24:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dffc0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:11:dd:56  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe11:dd56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:913 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25752 (25.7 KB)  TX bytes:6372 (6.3 KB)

jasleen@jasleen-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
jasleen@jasleen-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1


```

---

### Post by praseodym on 2011-09-30
Upgrade the firmware (11.10 package):

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb)

and reboot. Did you try WPA2 encryption instead of "none"?

---

