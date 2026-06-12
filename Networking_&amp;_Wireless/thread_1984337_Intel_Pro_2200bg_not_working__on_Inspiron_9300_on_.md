---
title: "Intel Pro 2200b/g not working  on Inspiron 9300 on 12.04"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by paulsantorello on 2012-05-21
I have an Inspiron 9300 that I recently upgraded to Ubuntu 12.04. Up until yesterday I was using Feisty Fawn (yes I know way out of date) and wireless worked perfectly. Now that I am using 12.04 wireless is not recognized. It does not show any available networks. When I type in lspci -v it says:

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN
    Flags: medium devsel, IRQ 17
    Memory at dcffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: ipw2200

Im not that well versed in ubuntu, any help in solving my wireless woes would be appreciated. Again, it worked perfectly in Fiesty Fawn, just not in 12.04.

---

### Post by chili555 on 2012-05-21
Oooh! I love these cases. Let's look around and see what's wrong. Please open a terminal and run and post:```
rfkill list all
lsmod | grep dell
dmesg | grep ipw
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by paulsantorello on 2012-05-21
pax@pax-Inspiron-9300:~$ rfkill list all
pax@pax-Inspiron-9300:~$ lsmod | grep dell
dell_laptop            13671  0 
dcdbas                 14098  1 dell_laptop
pax@pax-Inspiron-9300:~$ dmesg | grep ipw
[   16.519761] libipw: 802.11 data/management/control stack, git-1.1.13
[   16.519770] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.529770] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.529778] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.529965] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.530004] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.400327] ipw2200: Unable to load ucode: -22
[   19.428149] ipw2200: Unable to load firmware: -22
[   19.428166] ipw2200: failed to register network device
[   19.436250] ipw2200 0000:03:03.0: PCI INT A disabled
[   19.436315] ipw2200: probe of 0000:03:03.0 failed with error -5
pax@pax-Inspiron-9300:~$ 

Thanks for the quick reply

---

### Post by chili555 on 2012-05-21
> [ 19.400327] ipw2200: Unable to load ucode: -22
[ 19.428149] ipw2200: Unable to load firmware: -22
[ 19.428166] ipw2200: failed to register network deviceUh oh!

The driver requires firmware; here is a snip from *modinfo ipw2200*:> filename:       /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
[COLOR="Red"]firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw[/COLOR]
license:        GPL
author:         Copyright(c) 2003-2006 Intel CorporationLet's see if you actually have the firmware and check its integrity, all in one step:```
md5sum /lib/firmware/ipw*
```If you don't have it or it's corrupted, we'll get some new copies.

---

### Post by paulsantorello on 2012-05-21
pax@pax-Inspiron-9300:~$ md5sum /lib/firmware/ipw*
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/ipw2100-1.3.fw
b956daaa9e59be94ebdf6df0b3365cb6  /lib/firmware/ipw2100-1.3-i.fw
a03e4e0a85242356b1d5a1d489fa3a7f  /lib/firmware/ipw2100-1.3-p.fw
045a46163341514ef17490c76bd0c858  /lib/firmware/ipw2200-bss.fw
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fw
pax@pax-Inspiron-9300:~$

---

### Post by chili555 on 2012-05-21
Bad news. You have it and it's evidently not corrupted. Let's see if it has the correct ownership and permission:```
ls -al /lib/firmware ipw*
```Does it help to unload and reload the driver?```
sudo modprobe -r ipw2200
sudo modprobe ipw2200
dmesg | grep ipw
```Look for messages after the 19.4xx timestamp.

The doctor is reaching for his biggest saw...

---

### Post by paulsantorello on 2012-05-21
Thank you for all the help so far....i'm kinda in the deep end of the pool without my swimmies right now.....



pax@pax-Inspiron-9300:~$ ls -al /lib/firmware ipw*
ls: cannot access ipw*: No such file or directory
/lib/firmware:
total 19620
drwxr-xr-x 63 root root    4096 May 20 22:24 .
drwxr-xr-x 23 root root    4096 May 20 22:25 ..
drwxr-xr-x 32 root root    4096 Apr 23 07:35 3.2.0-23-generic-pae
drwxr-xr-x 32 root root    4096 May 20 22:24 3.2.0-24-generic-pae
drwxr-xr-x  2 root root    4096 Apr 23 07:35 3com
drwxr-xr-x  2 root root    4096 Apr 23 07:35 acenic
drwxr-xr-x  2 root root    4096 Apr 23 07:35 adaptec
drwxr-xr-x  2 root root    4096 Apr 23 07:35 advansys
-rw-r--r--  1 root root   50698 Feb 23 14:07 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 Feb 23 14:07 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 Apr  2 15:51 aic94xx-seq.fw
drwxr-xr-x  6 root root    4096 Apr 23 07:35 ar3k
-rw-r--r--  1 root root   70624 Feb 23 14:07 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 Mar 19 14:32 ar7010.fw
-rw-r--r--  1 root root   83968 Feb 23 14:07 ar9170-1.fw
-rw-r--r--  1 root root    3508 Feb 23 14:07 ar9170-2.fw
-rw-r--r--  1 root root   15960 Apr  2 15:51 ar9170.fw
-rw-r--r--  1 root root   51312 Mar 19 14:32 ar9271.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 asihpi
-rw-r--r--  1 root root  246804 Apr  2 15:51 ath3k-1.fw
drwxr-xr-x  5 root root    4096 Apr 23 07:35 ath6k
-rw-r--r--  1 root root   30348 Apr  2 15:51 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 Apr  2 15:51 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 Apr  2 15:51 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 Apr  2 15:51 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 Apr  2 15:51 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 Apr  2 15:51 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 Apr  2 15:51 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 Apr  2 15:51 atmel_at76c506.bin
-rw-r--r--  1 root root    9726 Feb 23 14:07 atmsar11.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 av7110
drwxr-xr-x  2 root root    4096 Apr 23 07:35 bnx2
drwxr-xr-x  2 root root    4096 Apr 23 07:35 bnx2x
drwxr-xr-x  2 root root    4096 Apr 23 07:35 brcm
-rw-r--r--  1 root root   13424 Apr  2 15:51 carl9170-1.fw
drwxr-xr-x  3 root root    4096 Apr 23 07:35 cis
drwxr-xr-x  2 root root    4096 Apr 23 07:35 cpia2
drwxr-xr-x  2 root root    4096 Apr 23 07:35 cxgb3
drwxr-xr-x  2 root root    4096 Apr 23 07:35 cxgb4
drwxr-xr-x  2 root root    4096 Apr 23 07:35 dabusb
drwxr-xr-x  2 root root    4096 Apr 23 07:35 dsp56k
-rw-r--r--  1 root root   12401 Feb 23 14:07 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 Feb 23 14:07 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   50222 Mar 19 14:32 dvb-usb-terratec-h5-drxk.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 e100
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ea
drwxr-xr-x  2 root root    4096 Apr 23 07:35 edgeport
drwxr-xr-x  2 root root    4096 Apr 23 07:35 emi26
drwxr-xr-x  2 root root    4096 Apr 23 07:35 emi62
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ene-ub6250
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ess
-rw-r--r--  1 root root  180776 Mar 19 14:32 f2255usb.bin
-rw-r--r--  1 root root   35068 Mar 19 14:32 GPL-3
drwxr-xr-x  2 root root    4096 Feb 14 04:02 hp
-rw-r--r--  1 root root   72992 Mar 19 14:32 htc_7010.fw
-rw-r--r--  1 root root   51272 Mar 19 14:32 htc_9271.fw
-rw-r--r--  1 root root 1251036 Feb 23 14:07 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root 1334532 Mar 19 14:32 i2400m-fw-usb-1.5.sbcf
-rw-r--r--  1 root root 1531932 Mar 19 14:32 i6050-fw-usb-1.5.sbcf
-rw-r--r--  1 root root   34304 Feb 23 14:07 intelliport2.bin
-rw-r--r--  1 root root  209190 Apr  2 15:51 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Apr  2 15:51 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Apr  2 15:51 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Apr  2 15:51 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Apr  2 15:51 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Apr  2 15:51 ipw2200-sniffer.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 isci
-rw-r--r--  1 root root  337520 Feb 10  2011 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 Mar 19 14:32 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  689680 Feb 23 14:07 iwlwifi-105-6.ucode
-rw-r--r--  1 root root  701228 Feb 23 14:07 iwlwifi-135-6.ucode
-rw-r--r--  1 root root  695876 Feb 23 14:07 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root  707392 Feb 23 14:07 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root  150100 Feb 23 14:07 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 Feb 23 14:07 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  340696 Apr  2 15:51 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 Feb 23 14:07 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 Mar 19 14:32 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 Mar 19 14:32 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  679436 Feb 23 14:07 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root  469780 Feb 23 14:07 iwlwifi-6050-5.ucode
drwxr-xr-x  2 root root    4096 Apr 23 07:35 kaweth
drwxr-xr-x  2 root root    4096 Apr 23 07:35 keyspan
drwxr-xr-x  2 root root    4096 Apr 23 07:35 keyspan_pda
drwxr-xr-x  2 root root    4096 Apr 23 07:35 korg
-rw-r--r--  1 root root  118888 Mar 19 14:32 lbtf_usb.bin
-rw-r--r--  1 root root     262 Mar 19 14:32 lgs8g75.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 libertas
drwxr-xr-x  2 root root    4096 Apr 23 07:35 matrox
drwxr-xr-x  2 root root    4096 Apr 23 07:35 mrvl
-rw-r--r--  1 root root   13847 Feb 23 14:07 mts_cdma.fw
-rw-r--r--  1 root root   14067 Feb 23 14:07 mts_edge.fw
-rw-r--r--  1 root root   13847 Feb 23 14:07 mts_gsm.fw
-rw-r--r--  1 root root   13769 Mar 19 14:32 mts_mt9234mu.fw
-rw-r--r--  1 root root   13769 Mar 19 14:32 mts_mt9234zba.fw
-rw-r--r--  1 root root   51596 Mar 19 14:32 mwl8335_duplex.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 mwl8k
-rw-r--r--  1 root root  377784 Mar 19 14:32 myri10ge_ethp_z8e.dat
-rw-r--r--  1 root root  367464 Mar 19 14:32 myri10ge_eth_z8e.dat
-rw-r--r--  1 root root  563592 Mar 19 14:32 myri10ge_rss_ethp_z8e.dat
-rw-r--r--  1 root root  553192 Mar 19 14:32 myri10ge_rss_eth_z8e.dat
drwxr-xr-x  2 root root    4096 Apr 23 07:35 myricom
-rw-r--r--  1 root root   15664 Apr  2 15:51 NPE-B
-rw-r--r--  1 root root   15664 Apr  2 15:51 NPE-C
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ositech
-rw-r--r--  1 root root 1825359 Mar 19 14:32 phanfw.bin
-rw-r--r--  1 root root   76802 Feb 23 14:07 ql2100_fw.bin
-rw-r--r--  1 root root   84566 Feb 23 14:07 ql2200_fw.bin
-rw-r--r--  1 root root  123170 Feb 23 14:07 ql2300_fw.bin
-rw-r--r--  1 root root  132978 Feb 23 14:07 ql2322_fw.bin
-rw-r--r--  1 root root  228056 Feb 23 14:07 ql2400_fw.bin
-rw-r--r--  1 root root  199776 Feb 23 14:07 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 Apr 23 07:35 qlogic
drwxr-xr-x  2 root root    4096 Apr 23 07:35 r128
drwxr-xr-x  2 root root    4096 Apr 23 07:35 radeon
-rw-r--r--  1 root root    8192 Feb 23 14:07 rt2561.bin
-rw-r--r--  1 root root    8192 Feb 23 14:07 rt2561s.bin
-rw-r--r--  1 root root    8192 Feb 23 14:07 rt2661.bin
-rw-r--r--  1 root root    8192 Mar 19 14:32 rt2860.bin
-rw-r--r--  1 root root    8192 Mar 19 14:32 rt2870.bin
lrwxrwxrwx  1 root root      10 May 15 21:15 rt3070.bin -> rt2870.bin
-rw-r--r--  1 root root    4096 Mar 19 14:32 rt3071.bin
lrwxrwxrwx  1 root root      10 May 15 21:15 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    2048 Feb 23 14:07 rt73.bin
drwxr-xr-x  2 root root    4096 Apr 23 07:35 RTL8192E
drwxr-xr-x  2 root root    4096 Apr 23 07:35 RTL8192SE
drwxr-xr-x  2 root root    4096 Apr 23 07:35 rtl_nic
drwxr-xr-x  2 root root    4096 Apr 23 07:35 rtlwifi
-rw-r--r--  1 root root    9508 Mar 19 14:32 s2250.fw
-rw-r--r--  1 root root    1092 Mar 19 14:32 s2250_loader.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 sb16
drwxr-xr-x  2 root root    4096 Apr 23 07:35 scripts
drwxr-xr-x  2 root root    4096 Apr 23 07:35 slicoss
drwxr-xr-x  2 root root    4096 Apr 23 07:35 sun
drwxr-xr-x  2 root root    4096 Apr 23 07:35 sxg
-rw-r--r--  1 root root   37028 Mar 19 14:32 TDA7706_OM_v2.5.1_boot.txt
-rw-r--r--  1 root root   10509 Mar 19 14:32 TDA7706_OM_v3.0.2_boot.txt
drwxr-xr-x  2 root root    4096 Apr 23 07:35 tehuti
-rw-r--r--  1 root root   13765 Feb 23 14:07 ti_3410.fw
-rw-r--r--  1 root root   13764 Feb 23 14:07 ti_5052.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ti-connectivity
drwxr-xr-x  2 root root    4096 Apr 23 07:35 tigon
-rw-r--r--  1 root root   51972 Mar 19 14:32 tlg2300_firmware.bin
-rw-r--r--  1 root root    7614 Feb 23 14:07 tr_smctr.bin
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ttusb-budget
drwxr-xr-x  2 root root    4096 Apr 23 07:35 ueagle-atm
drwxr-xr-x  2 root root    4096 Apr 23 07:35 usbdux
-rw-r--r--  1 root root     999 Feb 23 14:07 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 Feb 23 14:07 usbdux_firmware.bin
-rw-r--r--  1 root root    8192 Mar 19 14:32 usbduxsigma_firmware.bin
-rw-r--r--  1 root root   16382 Feb 23 14:07 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 Feb 23 14:07 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 Feb 23 14:07 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 Feb 23 14:07 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 Apr  2 15:51 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 Apr  2 15:51 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 Apr  2 15:51 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 Feb 23 14:07 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 Feb 23 14:07 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 Feb 23 14:07 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 Apr  2 15:51 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 Apr  2 15:51 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 vicam
-rw-r--r--  1 root root   11341 Mar 19 14:32 vntwusb.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 vxge
-rw-r--r--  1 root root    5208 Apr  2 15:51 WHENCE.ubuntu
-rw-r--r--  1 root root   23554 Feb 23 14:07 whiteheat.fw
-rw-r--r--  1 root root    5626 Feb 23 14:07 whiteheat_loader.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 yam
drwxr-xr-x  2 root root    4096 Apr 23 07:35 yamaha
-rw-r--r--  1 root root   62484 Apr  2 15:51 zd1201-ap.fw
-rw-r--r--  1 root root   70612 Apr  2 15:51 zd1201.fw
drwxr-xr-x  2 root root    4096 Apr 23 07:35 zd1211
pax@pax-Inspiron-9300:~$ sudo modprobe -r ipw2200
[sudo] password for pax: 
pax@pax-Inspiron-9300:~$ sudo modprobe ipw2200
pax@pax-Inspiron-9300:~$ dmesg | grep ipw
[   16.519761] libipw: 802.11 data/management/control stack, git-1.1.13
[   16.519770] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.529770] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.529778] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.529965] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.530004] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.400327] ipw2200: Unable to load ucode: -22
[   19.428149] ipw2200: Unable to load firmware: -22
[   19.428166] ipw2200: failed to register network device
[   19.436250] ipw2200 0000:03:03.0: PCI INT A disabled
[   19.436315] ipw2200: probe of 0000:03:03.0 failed with error -5
[ 4916.197411] libipw: 802.11 data/management/control stack, git-1.1.13
[ 4916.197418] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 4916.210659] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 4916.210668] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 4916.210858] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4916.210899] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 4916.279353] ipw2200: Unable to load ucode: -22
[ 4916.279534] ipw2200: Unable to load firmware: -22
[ 4916.279541] ipw2200: failed to register network device
[ 4916.279598] ipw2200 0000:03:03.0: PCI INT A disabled
[ 4916.279662] ipw2200: probe of 0000:03:03.0 failed with error -5
pax@pax-Inspiron-9300:~$

---

### Post by chili555 on 2012-05-21
Still weird and perfect. May I see:```
dmesg | grep -e eth -e 80211
dmesg | grep -i udev
```Have you updated since you installed? Do you have the latest kernel image?```
uname -r
```I believe the latest is 3.2.0-24. If not, I wonder if an updated kernel and a reboot wouldn't help.

---

### Post by paulsantorello on 2012-05-21
pax@pax-Inspiron-9300:~$ dmesg | grep -e eth -e 80211
[    0.216207] i2c-core: driver [aat2870] using legacy suspend method
[    0.216213] i2c-core: driver [aat2870] using legacy resume method
[    2.284273] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    2.305555] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:12:3f:e1:b6:84
[   15.752196] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.301110] lib80211: common routines for IEEE802.11 drivers
[   16.301118] lib80211_crypt: registered algorithm 'NULL'
[   16.440102] cfg80211: Calling CRDA to update world regulatory domain
[   19.210852] cfg80211: World regulatory domain updated:
[   19.210861] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.210870] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.210878] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.210886] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.210894] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.210901] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.307416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.313959] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.816187] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   23.816196] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   23.914150] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.832036] eth0: no IPv6 routers present
[ 4878.247834] lib80211_crypt: unregistered algorithm 'NULL'
[ 4916.174946] lib80211: common routines for IEEE802.11 drivers
[ 4916.174957] lib80211_crypt: registered algorithm 'NULL'
[ 4916.194605] cfg80211: Calling CRDA to update world regulatory domain
[ 4916.257322] cfg80211: World regulatory domain updated:
[ 4916.257330] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4916.257339] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4916.257348] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4916.257356] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4916.257363] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4916.257371] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
pax@pax-Inspiron-9300:~$ dmesg | grep -i udev
[    1.827110] udevd[84]: starting version 175
[   15.847605] udevd[297]: starting version 175
[   21.346026] init: udev-fallback-graphics main process (960) terminated with status 1
pax@pax-Inspiron-9300:~$ uname -r
3.2.0-23-generic-pae
pax@pax-Inspiron-9300:~$

---

### Post by paulsantorello on 2012-05-21
its so weird, i just popped in my feisty fawn live cd....as soon as it starts it shows wireless network list

---

### Post by chili555 on 2012-05-21
It also looks pretty perfect. I don't see anything broken to fix. You might try:```
sudo apt-get update && sudo apt-get upgrade
```See if you get a newer linux-image. Install it and reboot.

Also try:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
sudo modprobe -r ipw2200
sudo modprobe ipw2200
```Any improvement?

My toolbox is getting awfully light!

---

### Post by paulsantorello on 2012-05-21
help me obi wan kenobi.....you're my only hope lol

---

### Post by paulsantorello on 2012-05-21
sorry it took so long for me to reply back, after i did that last update for some unknown reason I had to rebuild the GRUB.....ugh....but...thats not the issue at hand. Wireless is still not showing as available. When i click on the network icon it shows my wired connection. When I click on the wireless tab there are no wireless networks showing as being available. I read that it wont allow wireless if a wired connection is available but i tried disconnecting the wired connection and still no dice......

---

### Post by paulsantorello on 2012-05-21
I also installed WiFi Radar from the ubuntu software center.....it doesn't show any networks as being available, under preferences it doesnt show any wireless device as being available

---

### Post by sonic the on 2012-05-22
hi guys! 

there is a bug in ubuntu 12.04 3.2.0-23 with the wlan connection. for me worked the following. 

**update to 3.2.0-24 **(already mentioned) - make sure the right pae/none pae kernel is installed 

do the propose updates over update manager. i think only the update of **"network manager**" is required but i am not 100% sure. 

to conclude - do the updates and it should be running without any issues after reboot. 

good luck :)

---

### Post by chili555 on 2012-05-22
> **paulsantorello said:**
> help me obi wan kenobi.....you're my only hope lolDid you do the updates I suggested? If so and it still doesn't work, I'd try:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Then reboot and check:```
dmesg | grep iwl
```Do we still have the issue:> [ 19.400327] ipw2200: Unable to load ucode: -22
[ 19.428149] ipw2200: Unable to load firmware: -22
[ 19.428166] ipw2200: failed to register network device

---

