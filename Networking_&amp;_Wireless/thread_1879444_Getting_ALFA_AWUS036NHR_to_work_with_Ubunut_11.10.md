---
title: "Getting ALFA AWUS036NHR to work with Ubunut 11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by khurtsiya on 2011-11-11
Hello! Any chance to install this Wi-Fi adapter?

Following instructions I am getting error:

> laptop:/home/amnesia/Desktop/linux# ./install.sh
		Auto install for 8192cu
		September, 1 2010 v 1.0.0
rtl8192CU_linux_v2.0.1212.20101208/
rtl8192CU_linux_v2.0.1212.20101208/os_dep/
rtl8192CU_linux_v2.0.1212.20101208/include/
rtl8192CU_linux_v2.0.1212.20101208/hal/
rtl8192CU_linux_v2.0.1212.20101208/core/
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/
rtl8192CU_linux_v2.0.1212.20101208/core/led/
rtl8192CU_linux_v2.0.1212.20101208/core/efuse/
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/
rtl8192CU_linux_v2.0.1212.20101208/Kconfig
rtl8192CU_linux_v2.0.1212.20101208/wpa1.conf
rtl8192CU_linux_v2.0.1212.20101208/wlan0dhcp
rtl8192CU_linux_v2.0.1212.20101208/runwpa
rtl8192CU_linux_v2.0.1212.20101208/Makefile
rtl8192CU_linux_v2.0.1212.20101208/ifcfg-wlan0
rtl8192CU_linux_v2.0.1212.20101208/clean
rtl8192CU_linux_v2.0.1212.20101208/autoconf_rtl8192c_usb_linux.h
rtl8192CU_linux_v2.0.1212.20101208/os_dep/osdep_service.c
rtl8192CU_linux_v2.0.1212.20101208/include/xmit_osdep.h
rtl8192CU_linux_v2.0.1212.20101208/include/wlan_bssdef.h
rtl8192CU_linux_v2.0.1212.20101208/include/wifi.h
rtl8192CU_linux_v2.0.1212.20101208/include/version.h
rtl8192CU_linux_v2.0.1212.20101208/include/usb_vendor_req.h
rtl8192CU_linux_v2.0.1212.20101208/include/usb_osintf.h
rtl8192CU_linux_v2.0.1212.20101208/include/usb_ops.h
rtl8192CU_linux_v2.0.1212.20101208/include/usb_hal.h
rtl8192CU_linux_v2.0.1212.20101208/include/sta_info.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_osintf.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_ops_xp.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_ops_linux.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_ops_ce.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_ops.h
rtl8192CU_linux_v2.0.1212.20101208/include/sdio_hal.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_xmit.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_version.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_security.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_rf.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_recv.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_qos.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_pwrctrl.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_mp_phy_regdef.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_mp_ioctl.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_mp.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_mlme_ext.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_mlme.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_led.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_ioctl_set.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_ioctl_rtl.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_ioctl_query.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_ioctl.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_io.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_ht.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_event.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_eeprom.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_debug.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_cmd.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtw_byteorder.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_xmit.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_spec.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_rf.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_regdef.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_recv.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_hal.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_event.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_efuse.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_cmd.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8712_bitdef.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_xmit.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_spec.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_recv.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_hal.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_event.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_dm.h
rtl8192CU_linux_v2.0.1212.20101208/include/rtl8192c_cmd.h
rtl8192CU_linux_v2.0.1212.20101208/include/recv_osdep.h
rtl8192CU_linux_v2.0.1212.20101208/include/osdep_service.h
rtl8192CU_linux_v2.0.1212.20101208/include/osdep_intf.h
rtl8192CU_linux_v2.0.1212.20101208/include/osdep_ce_service.h
rtl8192CU_linux_v2.0.1212.20101208/include/nic_spec.h
rtl8192CU_linux_v2.0.1212.20101208/include/mp_custom_oid.h
rtl8192CU_linux_v2.0.1212.20101208/include/mlme_osdep.h
rtl8192CU_linux_v2.0.1212.20101208/include/ip.h
rtl8192CU_linux_v2.0.1212.20101208/include/if_ether.h
rtl8192CU_linux_v2.0.1212.20101208/include/ieee80211_ext.h
rtl8192CU_linux_v2.0.1212.20101208/include/ieee80211.h
rtl8192CU_linux_v2.0.1212.20101208/include/hal_init.h
rtl8192CU_linux_v2.0.1212.20101208/include/HalRf.h
rtl8192CU_linux_v2.0.1212.20101208/include/Hal8192CUHWImg.h
rtl8192CU_linux_v2.0.1212.20101208/include/Hal8192CPhyReg.h
rtl8192CU_linux_v2.0.1212.20101208/include/Hal8192CPhyCfg.h
rtl8192CU_linux_v2.0.1212.20101208/include/h2clbk.h
rtl8192CU_linux_v2.0.1212.20101208/include/farray.h
rtl8192CU_linux_v2.0.1212.20101208/include/ethernet.h
rtl8192CU_linux_v2.0.1212.20101208/include/drv_types_xp.h
rtl8192CU_linux_v2.0.1212.20101208/include/drv_types_linux.h
rtl8192CU_linux_v2.0.1212.20101208/include/drv_types_ce.h
rtl8192CU_linux_v2.0.1212.20101208/include/drv_types.h
rtl8192CU_linux_v2.0.1212.20101208/include/drv_conf.h
rtl8192CU_linux_v2.0.1212.20101208/include/cmd_osdep.h
rtl8192CU_linux_v2.0.1212.20101208/include/circ_buf.h
rtl8192CU_linux_v2.0.1212.20101208/include/basic_types.h
rtl8192CU_linux_v2.0.1212.20101208/include/autoconf.h
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c_d_hal_init.c
rtl8192CU_linux_v2.0.1212.20101208/hal/hal_init.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_xmit.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_wlan_util.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_sta_mgt.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_security.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_rf.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_recv.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_pwrctrl.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_mp_ioctl.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_mp.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_mlme_ext.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_mlme.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_ioctl_set.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_ioctl_rtl.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_ioctl_query.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_io.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_eeprom.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_debug.c
rtl8192CU_linux_v2.0.1212.20101208/core/rtw_cmd.c
rtl8192CU_linux_v2.0.1212.20101208/core/ieee80211.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/xmit_linux.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/usb_intf.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/sdio_intf.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/recv_linux.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/os_intfs.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/mlme_linux.c
rtl8192CU_linux_v2.0.1212.20101208/os_dep/linux/ioctl_linux.c
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/swabb.h
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/swab.h
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/little_endian.h
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/generic.h
rtl8192CU_linux_v2.0.1212.20101208/include/byteorder/big_endian.h
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/rtl8192c_dm.c
rtl8192CU_linux_v2.0.1212.20101208/core/led/rtl8192c_led.c
rtl8192CU_linux_v2.0.1212.20101208/core/efuse/rtl8712_efuse.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/usb_halinit.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/rtl8192c_cmd.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192CU_linux_v2.0.1212.20101208/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192CU_linux_v2.0.1212.20101208
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.0.0-12-generic/build M=/home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208/core/rtw_cmd.o
In file included from /home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208/include/drv_types.h:86:0,
                 from /home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208/core/rtw_cmd.c:24:
/home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208/include/rtw_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208/core/rtw_cmd.o] **Error 1**
make[1]: *** [_module_/home/amnesia/Desktop/linux/driver/rtl8192CU_linux_v2.0.1212.20101208] **Error 2**
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] **Error 2**
Compile make driver error: 2, Please check error Mesg



---

### Post by praseodym on 2011-11-11
Please show:

```
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by chili555 on 2011-11-11
> fatal error: **linux/smp_lock.h**: No such file or directoryThis suggests the file you downloaded to compile is too old for kernel >= 3.0. Maybe there is another way. May we see:```
lsusb
```Thanks.

EDIT: I see that praseodym is here to help. Please excuse me.

---

### Post by khurtsiya on 2011-11-11
**lsusb**
> $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 008: ID 0bda:817f Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 04f2:b257 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 147e:1002 Upek 
Bus 002 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller

**lsmod**
> $ lsmod
Module                  Size  Used by
rtl8192cu              97651  0 
nls_utf8               12493  1 
isofs                  39549  1 
rfcomm                 38408  10 
bnep                   17923  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
ip6t_LOG               16846  4 
xt_hl                  12465  6 
parport_pc             32114  0 
ip6t_rt                12473  3 
ppdev                  12849  0 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_multiport           12533  8 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
binfmt_misc            17292  1 
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
arc4                   12473  2 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
rtl8192ce              75448  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
rtl8192c_common        69519  2 rtl8192cu,rtl8192ce
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
rtlwifi                95614  2 rtl8192cu,rtl8192ce
mac80211              272785  4 rtl8192cu,rtl8192ce,rtl8192c_common,rtlwifi
i915                  505108  3 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          73942  0 
joydev                 17393  0 
btusb                  18160  2 
drm_kms_helper         32889  1 i915
snd_seq_midi           13132  0 
cfg80211              172392  2 rtlwifi,mac80211
snd_rawmidi            25241  1 snd_seq_midi
drm                   192226  4 i915,drm_kms_helper
bluetooth             148839  23 rfcomm,bnep,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
soundcore              12600  1 snd
nvram                  14029  1 thinkpad_acpi
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

**rfkill list**
> $ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
**iwconfig**
> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"tesla"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:B7:DE:01   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2827   Missed beacon:0


---

### Post by khurtsiya on 2011-11-11
**sudo iwlist scan**
> $ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:B7:DE:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"tesla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f574b99a0
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 00057465736C61
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200200
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A000110103B000103104700104B6A7850350F4E001BE3001E58B7DE01104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
          Cell 02 - Address: 52:43:84:C3:5E:C0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Connectify-MY-FI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000028eb3e3
                    Extra: Last beacon: 172ms ago
                    IE: Unknown: 0010436F6E6E6563746966792D4D592D4649
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD070050F202000100
          Cell 03 - Address: 00:21:91:0D:45:81
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Chudo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001abb0c09fef
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 0005436875646F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050400000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D1603051000000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010761F5006458A3DAAA8B127ABE2B5F8721021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F7574657210080002008C
          Cell 04 - Address: B0:48:7A:C2:FC:6E
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"DeanWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d01f6d28
                    Extra: Last beacon: 684ms ago
                    IE: Unknown: 00084465616E57694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 05 - Address: 00:24:01:BC:38:87
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"kupriki"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086ad9cc181
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 00076B757072696B69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010060FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 08:10:74:8E:89:EE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Foxgate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ffb21d19b
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 0007466F7867617465
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD0700E04C01020300
          Cell 07 - Address: 00:27:19:CF:E5:2C
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"R-3-145"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000146376d181
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 0007522D332D313435
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002719CFE52C022719CFE52C64002C010808
          Cell 08 - Address: B0:48:7A:AF:99:76
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"admin23"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000146b0d96180
                    Extra: Last beacon: 732ms ago
                    IE: Unknown: 000761646D696E3233
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 09 - Address: 00:22:B0:3F:4F:6F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"whomelan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000058cd2c3181
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 000877686F6D656C616E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010060FF7F
          Cell 10 - Address: F4:EC:38:C0:D4:10
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Tochka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b460f21181
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 0006546F63686B61
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:90:4C:C0:00:03
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"PORNO2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000109f929183
                    Extra: Last beacon: 572ms ago
                    IE: Unknown: 0006504F524E4F32
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: 00:21:91:EF:52:B4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016cbe6a181
                    Extra: Last beacon: 944ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4120010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 13 - Address: F0:7D:68:4F:DB:72
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"yp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b45f89274c
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 00027970
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3408050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 14 - Address: 00:11:F5:25:E9:58
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"itv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a299d6feb
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 0003697476
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
          Cell 15 - Address: F4:EC:38:BA:19:EC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"if0s"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000bc067f70
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 000469663073
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0800000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000


---

### Post by praseodym on 2011-11-11
There are already two drivers loaded:

```
rtl8192cu 97651 0
...
rtl8192ce 75448 0 
```
Blacklist the wrong one:

```
echo "blacklist rtl8192ce" | sudo tee /etc/modprobe.d/blacklist-rtl8192ce.conf
sudo modprobe -rfv rtl8192ce rtl8192cu
```
Reload the driver:
```
 
sudo modprobe -v rtl8192cu
```
Replug the stick and check:
```
iwconfig
dmesg | egrep 'rtl8|r8'
lsmod
modinfo rtl8192cu | grep 817F
```

---

### Post by khurtsiya on 2011-11-11
Now my integrated Wi-Fi module switched off and I lost internet at all... But things are not so bad when your wife has notebook too with Ubuntu on it :)

So now I have two questions already:

1) how to switch my integrated wi-fi module on and
2) how to install that ALFA

Meanwhile whe have new output:

> $ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.


> $ **dmesg | egrep 'rtl8|r8'**
[    3.480785] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.480817] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.486795] r8169 0000:02:00.0: setting latency timer to 64
[    3.487019] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    3.488295] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xf8036000, f0:de:f1:82:5e:c0, XID 0c200000 IRQ 40
[    8.354428] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.354438] rtl8192ce 0000:08:00.0: setting latency timer to 64
[   14.588428] r8169 0000:02:00.0: eth0: link down
[   14.593927] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   15.347645] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1343.497678] usbcore: registered new interface driver rtl8192cu
[11233.153226] rtl8192ce 0000:08:00.0: PCI INT A disabled
[11233.161367] usbcore: deregistering interface driver rtl8192cu
[11257.404679] usbcore: registered new interface driver rtl8192cu


> $ **lsmod**
Module                  Size  Used by
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
nls_utf8               12493  1 
isofs                  39549  1 
rfcomm                 38408  10 
bnep                   17923  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
ip6t_LOG               16846  4 
xt_hl                  12465  6 
parport_pc             32114  0 
ip6t_rt                12473  3 
ppdev                  12849  0 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_multiport           12533  8 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
binfmt_misc            17292  1 
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
arc4                   12473  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
i915                  505108  3 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          73942  0 
joydev                 17393  0 
btusb                  18160  2 
drm_kms_helper         32889  1 i915
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
drm                   192226  4 i915,drm_kms_helper
bluetooth             148839  23 rfcomm,bnep,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
soundcore              12600  1 snd
nvram                  14029  1 thinkpad_acpi
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

---

### Post by praseodym on 2011-11-11
Remove the blacklist-file and load the other driver again:

```
sudo rm /etc/modprobe.d/blacklist-rtl8192ce.conf
sudo modprobe -v rtl8192ce
```
(Maybe rebooting?!)

Please show completely:

```
lspci -nnk | grep -iA2 net
modinfo rtl8192ce
modinfo rtl8192cu
```
Seems like "ce" is for the internal card.

---

### Post by khurtsiya on 2011-11-11
Thanks! I am back with my own notebook and wife is happy :)

Lets go to new output:

> $ **lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:21e2]
	Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce


> $ **modinfo rtl8192ce**
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     88D2C6ADED1C5FC2EAE88BB
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
vermagic:       3.0.0-12-generic SMP mod_unload modversions 686 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


> $ **modinfo rtl8192cu**
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     9550D79A3F9B707741FF904
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-12-generic SMP mod_unload modversions 686 

---

### Post by praseodym on 2011-11-11
Ok, the module **rtl8192cu** doesnt contain the product ID of your stick. Upgrade the driver via:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/blacklist-rtl8192cu.conf
```
and reboot.

Check:

```
lsmod
iwconfig
```
The driver does contain your vendor ID:
> 	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x[COLOR="Red"]817F[/COLOR])},//8188RU

---

### Post by khurtsiya on 2011-11-11
After reboot ALFA light is blinkin sometimes. Here is output.> $ **lsmod**
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
rfcomm                 38408  10 
bnep                   17923  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
8192cu                464562  0 
btusb                  18160  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
bluetooth             148839  23 rfcomm,bnep,btusb
arc4                   12473  2 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
snd_rawmidi            25241  1 snd_seq_midi
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
thinkpad_acpi          73942  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ipt_REJECT             12512  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ipt_LOG                12783  5 
nvram                  14029  1 thinkpad_acpi
xt_multiport           12533  8 
xt_limit               12541  12 
binfmt_misc            17292  1 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
snd_timer              28932  2 snd_pcm,snd_seq
xt_state               12514  14 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
ip6table_filter        12711  1 
rtl8192ce              75448  0 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95614  1 rtl8192ce
iptable_filter         12706  1 
mac80211              272785  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
ip_tables              18106  1 iptable_filter
x_tables               21975  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci


> $ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"tesla"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:58:B7:DE:01   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:103   Missed beacon:0

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Moreover, it is working! But how come that my integrated adapter (green) shows more network than ALFA's long range (red)?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206981&stc=1&d=1321059941[/IMG]

---

### Post by praseodym on 2011-11-11
Your internal card (wlan0) seems connected. Do you want to connect to the same NW with the stick (wlan1)?

There is a lot of traffic around channel 6, try to change to "automatic" mode or channel 1 in your router.

Please show:

```
iwlist chan
dmesg | grep 8192
```
Check the outputs now of

```
sudo iwlist scan
```
for both devices and check which channels/networks are shown on both interfaces.

---

### Post by khurtsiya on 2011-11-11
> Your internal card (wlan0) seems connected. Do you want to connect to the same NW with the stick (wlan1)?

I bought ALFA to find out more networks when riding on streets in car. My integrated adapter is good with my router at home.

> There is a lot of traffic around channel 6, try to change to "automatic" mode or channel 1 in your router.

Changed to channel 1, but what is the point? Automatic mode was enabled already.

> $ **iwlist chan**
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


> $ **dmesg | grep 8192**
[   14.586633] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.586646] rtl8192ce 0000:08:00.0: setting latency timer to 64
[   15.333436] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   15.698067] CHIP TYPE: RTL8188C_8192C
[   15.699891] ====> ReadAdapterInfo8192C
[   15.856290] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   15.856296] <==== ReadAdapterInfo8192C in 156 ms
[   15.857474] usbcore: registered new interface driver rtl8192cu
[   16.810932] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   18.027327] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   19.149804] ==> rtl8192cu_hal_deinit 
[   39.647012] ==> rtl8192cu_hal_deinit 
[   69.587332] ==> rtl8192cu_hal_deinit 
[  109.525821] ==> rtl8192cu_hal_deinit 
[  159.415677] ==> rtl8192cu_hal_deinit 
[  219.298230] ==> rtl8192cu_hal_deinit 
[  279.174500] ==> rtl8192cu_hal_deinit 
[  339.064392] ==> rtl8192cu_hal_deinit 
[  398.953151] ==> rtl8192cu_hal_deinit 
[  458.842668] ==> rtl8192cu_hal_deinit 
[  518.722083] ==> rtl8192cu_hal_deinit 
[  578.590749] ==> rtl8192cu_hal_deinit 
[  638.508970] ==> rtl8192cu_hal_deinit 
[  698.373152] ==> rtl8192cu_hal_deinit 
[  758.292386] ==> rtl8192cu_hal_deinit 
[  818.212090] ==> rtl8192cu_hal_deinit 
[  878.118344] ==> rtl8192cu_hal_deinit 
[  938.024460] ==> rtl8192cu_hal_deinit 
[  973.878192] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1e:58:b7:de:01:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56888 PROTO=2 
[  997.934688] ==> rtl8192cu_hal_deinit 
[ 1057.829704] ==> rtl8192cu_hal_deinit 
[ 1117.769638] ==> rtl8192cu_hal_deinit 
[ 1177.675908] ==> rtl8192cu_hal_deinit 
[ 1237.558165] ==> rtl8192cu_hal_deinit 
[ 1297.481007] ==> rtl8192cu_hal_deinit 
[ 1357.383629] ==> rtl8192cu_hal_deinit 
[ 1417.298484] ==> rtl8192cu_hal_deinit 
[ 1477.217331] ==> rtl8192cu_hal_deinit 
[ 1537.136555] ==> rtl8192cu_hal_deinit 
[ 1597.034810] ==> rtl8192cu_hal_deinit 
[ 1656.941424] ==> rtl8192cu_hal_deinit 
[ 1716.872502] ==> rtl8192cu_hal_deinit 
[ 1776.775508] ==> rtl8192cu_hal_deinit 
[ 1836.681865] ==> rtl8192cu_hal_deinit 
[ 1896.594961] ==> rtl8192cu_hal_deinit 
[ 1956.514068] ==> rtl8192cu_hal_deinit 
[ 2012.490892] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2013.728192] wlan0: associate with 00:1e:58:b7:de:01 (try 1)
[ 2016.478713] ==> rtl8192cu_hal_deinit 
[ 2027.940627] [UFW BLOCK] IN=wlan0 OUT= MAC=d0:df:9a:da:52:42:00:1e:58:b7:de:01:08:00 SRC=99.61.255.14 DST=192.168.0.101 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=18436 DF PROTO=TCP SPT=51314 DPT=55789 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2030.966348] [UFW BLOCK] IN=wlan0 OUT= MAC=d0:df:9a:da:52:42:00:1e:58:b7:de:01:08:00 SRC=99.61.255.14 DST=192.168.0.101 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=18725 DF PROTO=TCP SPT=51314 DPT=55789 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2036.928589] [UFW BLOCK] IN=wlan0 OUT= MAC=d0:df:9a:da:52:42:00:1e:58:b7:de:01:08:00 SRC=99.61.255.14 DST=192.168.0.101 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=19289 DF PROTO=TCP SPT=51314 DPT=55789 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2076.346897] ==> rtl8192cu_hal_deinit 
[ 2136.304687] ==> rtl8192cu_hal_deinit 


> $ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:25:E9:58
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"itv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c6df0487c
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0003697476
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
          Cell 02 - Address: B0:48:7A:C2:FC:6E
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"DeanWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005147450f4
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 00084465616E57694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 03 - Address: F4:EC:38:BD:BF:6E
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"ANTON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c6ad465f9
                    Extra: Last beacon: 272ms ago
                    IE: Unknown: 0005414E544F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409071900000000000000000000000000000000000000
                    IE: Unknown: 3D1609071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000101103B0001031047001000000000000010000000F4EC38BDBF6E1021000754502D4C494E4B10230009544C2D57523734314E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734314E100800020086103C000101
          Cell 04 - Address: 00:1E:58:B7:DE:01
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"tesla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001cd0f9c6
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 00057465736C61
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200200
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A000110103B000103104700104B6A7850350F4E001BE3001E58B7DE01104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
          Cell 05 - Address: BC:AE:C5:BA:92:44
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"triolan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a67a26e157
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 00077472696F6C616E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000005127A
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: 00:27:19:CF:E5:2C
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"R-3-145"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b6efccdc
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 0007522D332D313435
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000002719CFE52C022719CFE52C64002C010808
          Cell 07 - Address: 00:1B:11:37:56:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ArmadaLine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008169d5e6f7
                    Extra: Last beacon: 464ms ago
                    IE: Unknown: 000A41726D6164614C696E65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001061B508A5DEE14D1195B7001B1137560110210006442D4C696E6B102300074449522D333230102400074449522D3332301042000830303030303030301054000800060050F2040001101100074449522D33323010080002008E
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD090010180201F0000000
          Cell 08 - Address: F4:EC:38:BA:19:EC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"if0s"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000300588052
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 000469663073
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0800000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 09 - Address: 00:18:E7:ED:1F:FF
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Neos-MJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c193479d80
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 00074E656F732D4D4A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001

wlan1     Scan completed :
          Cell 01 - Address: 00:1E:58:B7:DE:01
                    ESSID:"tesla"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Quality=44/100  Signal level=44/100  

I did not understand what means:

> for both devices and check which channels/networks are shown on both interfaces.

---

### Post by praseodym on 2011-11-12
As you see: wlan0 finds 13, wlan1 only 11 channels. Which country do you live? We may set the country code.

---

### Post by khurtsiya on 2011-11-12
I live in Ukraine.

By the way I was talking about my wi-fi router D-Link (not adapter ALFA) when said that channel changed to 1 and type is automatic.

---

### Post by praseodym on 2011-11-12
For Ukraine:

```
sudo apt-get install iw
sudo iw reg set UA
sudo service network-manager restart
```
Check:

```
iwlist chan
dmesg | grep country
```

---

### Post by khurtsiya on 2011-11-12
> $ **iwlist chan**
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

> $ **dmesg | grep country**
[65986.548888] cfg80211: Calling CRDA for country: UA
[65986.558085] cfg80211: Regulatory domain changed to country: UA
[65996.945902] cfg80211: Calling CRDA for country: UA
[65996.949805] cfg80211: Regulatory domain changed to country: UA

and here is screenshot

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207032&stc=1&d=1321126089[/IMG]

---

### Post by khurtsiya on 2011-11-12
after reboot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207034&stc=1&d=1321127699[/IMG]

---

### Post by khurtsiya on 2011-11-14
praseodym, come back! need your help!

---

### Post by praseodym on 2011-11-14
Hi,

maybe both devices dont work in parallel. So we setup an UDEV-rule for unloading the internal module if the stick is plugged in:
```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```
Insert:
```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for internal WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick plugged, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf rtl8192ce"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick removed, Onboard-Karte aktivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe rtl8192ce"

LABEL="rules_end"
```
save, close, reload UDEV via
```
sudo service udev reload
```
and replug the stick. Check then
```
iwlist chan
iwconfig
sudo iwlist scan
```
Do you need a firewall/iptables? If not uninstall it and remove the iptables:
```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by khurtsiya on 2011-11-14
Sorry, I must have told you. When I was buying ALFA in the office they have tested it on two notebooks. One with Windows 7 (was 2-3 networks too) and second with Windows XP (which after installing drivers showed about 10 new networks. I think this shows that built in device do not change anything in work of the stick. Can this info help to find out what is the problem?

---

### Post by praseodym on 2011-11-14
Yes, but the Linux drivers are maybe different from the Win drivers; firmware, too. Even with the Windows drivers using ndiswrapper you most of the time dont have "the same" software quality

---

### Post by khurtsiya on 2011-11-14
Ok. So I have done all you told. Now only ALFA is working and it sees only one Wi-Fi network. And what pisses me off is that there are only 3 of 4 lines in signal strength even though adapter is laing in two cm from router!

Here is output:

> $ **iwlist chan**
lo        no frequency information.

eth0      no frequency information.

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


> $ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"tesla"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:58:B7:DE:01   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/100  Signal level=69/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> $ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1E:58:B7:DE:01
                    ESSID:"tesla"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Quality=68/100  Signal level=68/100  
          Cell 02 - Address: 00:11:F5:25:E9:58
                    ESSID:"itv"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=11/100  Signal level=11/100 

No need of firewall/iptables (do not know what it is and never used) so done all you wrote. Still one network - mine.

---

### Post by praseodym on 2011-11-14
You are using no encryption with your "tesla" resp. WEP encryption with "itv"?! Tried Wicd instead of the NM (maybe I am getting lost here ;-) )?

---

### Post by khurtsiya on 2011-11-14
tesla is mine unsecured and itv is not mine. Installed wicd. It shows exactly the same two networks. I believe there is something wrong with driver or configuration...

---

### Post by praseodym on 2011-11-14
Maybe the driver is too old for kernel 3? Uninstall it via

```
make clean
make
sudo make uninstall
```
And install a newer one:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz
sudo tar xvf rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8712u -v 2.6.6.0.2
sudo dkms build -m rtl8712u -v 2.6.6.0.2
sudo dkms install -m rtl8712u -v 2.6.6.0.2 
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/blacklist-rtl8192cu.conf
```
Reboot.

---

### Post by khurtsiya on 2011-11-14
I am not guru in Linux...
> $ **make clean**
make: *** No rule to make target `clean'.  Stop.
What is the problem?

---

### Post by praseodym on 2011-11-14
It doesnt matter, the module will be blacklisted. Continue with "sudo apt-get"

---

### Post by khurtsiya on 2011-11-14
New error:

> $ **wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz)**
--2011-11-15 01:12:08--  [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_11.10_dkms.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-11-15 01:12:08 ERROR 404: Not Found.


---

### Post by praseodym on 2011-11-14
Sorry that package was removed:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz)
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590
```

---

### Post by khurtsiya on 2011-11-14
Next error:

> $ **sudo dkms add -m rtl8192cu -v 3.1.2590**
Error! DKMS tree already contains: rtl8192cu-3.1.2590
You cannot add the same module/version combo more than once.


---

### Post by praseodym on 2011-11-15
```
gksu nautilus /usr/src
```
Remove the folder and unpack it again with "sudo tar". Then try it again

---

### Post by khurtsiya on 2011-11-15
Done, but same error appears:

> $ **sudo dkms add -m rtl8192cu -v 3.1.2590**
Error! DKMS tree already contains: rtl8192cu-3.1.2590
You cannot add the same module/version combo more than once.

---

### Post by praseodym on 2011-11-15
Remove the dkms tree with

```
sudo dkms remove -m rtl8192cu -v 3.1.2590 --all 
```

---

### Post by khurtsiya on 2011-11-15
All done, but still only two networks and bad signal...

---

### Post by praseodym on 2011-11-15
Reboot and check:

```
iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'rtl8|r8'
lsmod
ifconfig -a
```

---

### Post by khurtsiya on 2011-11-15
I have rebooted before, so here is the output:

> $ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"tesla"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:58:B7:DE:01   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/100  Signal level=53/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> $ **iwlist chan**
lo        no frequency information.

eth0      no frequency information.

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)



> $ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1E:58:B7:DE:01
                    ESSID:"tesla"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Quality=52/100  Signal level=52/100  
          Cell 02 - Address: 00:11:F5:25:E9:58
                    ESSID:"itv"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality:0  Signal level:0  Noise level:0

> $ **dmesg | egrep 'rtl8|r8'**
[    3.492807] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.492838] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.492947] r8169 0000:02:00.0: setting latency timer to 64
[    3.493759] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    3.495508] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xf804a000, f0:de:f1:82:5e:c0, XID 0c200000 IRQ 40
[    7.162416] rtl8192ce 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.162429] rtl8192ce 0000:08:00.0: setting latency timer to 64
[    8.303498] usbcore: registered new interface driver rtl8192cu
[    9.160600] rtl8192ce 0000:08:00.0: PCI INT A disabled
[   15.291048] r8169 0000:02:00.0: eth0: link down
[   18.015683] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   19.129887] rtl8192c_dm_RF_Saving(): RF_Normal
[   29.130527] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   36.077539] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   39.143825] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   67.172310] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   71.176103] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   76.037491] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   79.184192] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   81.186287] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  181.287247] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  185.295285] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  275.386093] rtl8192c_dm_RF_Saving(): RF_Normal
[  279.389864] rtl8192c_dm_RF_Saving(): RF_Normal
[  285.396108] rtl8192c_dm_RF_Saving(): RF_Normal
[  289.400399] rtl8192c_dm_RF_Saving(): RF_Normal
[  293.404130] rtl8192c_dm_RF_Saving(): RF_Normal
[  299.410140] rtl8192c_dm_RF_Saving(): RF_Normal
[  301.412272] rtl8192c_dm_RF_Saving(): RF_Normal
[  307.418416] rtl8192c_dm_RF_Saving(): RF_Normal
[  309.420425] rtl8192c_dm_RF_Saving(): RF_Normal
[  315.426813] rtl8192c_dm_RF_Saving(): RF_Normal
[  317.428570] rtl8192c_dm_RF_Saving(): RF_Normal
[  319.430446] rtl8192c_dm_RF_Saving(): RF_Normal
[  321.432770] rtl8192c_dm_RF_Saving(): RF_Normal
[  323.434580] rtl8192c_dm_RF_Saving(): RF_Normal
[  327.439088] rtl8192c_dm_RF_Saving(): RF_Normal
[  335.446857] rtl8192c_dm_RF_Saving(): RF_Normal
[  337.451598] rtl8192c_dm_RF_Saving(): RF_Normal
[  341.453122] rtl8192c_dm_RF_Saving(): RF_Normal
[  343.455007] rtl8192c_dm_RF_Saving(): RF_Normal
[  347.458877] rtl8192c_dm_RF_Saving(): RF_Normal
[  353.465044] rtl8192c_dm_RF_Saving(): RF_Normal
[  355.466777] rtl8192c_dm_RF_Saving(): RF_Normal
[  397.509370] rtl8192c_dm_RF_Saving(): RF_Normal
[  399.511127] rtl8192c_dm_RF_Saving(): RF_Normal
[  419.531413] rtl8192c_dm_RF_Saving(): RF_Normal
[  421.533418] rtl8192c_dm_RF_Saving(): RF_Normal
[  487.600455] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[  489.602640] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[  497.614465] rtl8192c_dm_RF_Saving(): RF_Normal
[  499.616721] rtl8192c_dm_RF_Saving(): RF_Normal
[  503.620604] rtl8192c_dm_RF_Saving(): RF_Normal
[  505.623988] rtl8192c_dm_RF_Saving(): RF_Normal
[  513.630369] rtl8192c_dm_RF_Saving(): RF_Normal
[  515.636769] rtl8192c_dm_RF_Saving(): RF_Normal
[  633.751650] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1150.135273] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1154.137034] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1156.137793] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1184.152243] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1186.153392] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1190.155270] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1192.156705] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1254.188338] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1256.189219] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1268.195128] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1336.227601] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1336.227611] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1338.227028] rtl8192: delete STA
[ 1338.235708] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1338.235972] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1340.231345] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1340.472919] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1340.703134] ==> rtl8192cu_hal_deinit 
[ 1341.725615] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1341.890317] r8169 0000:02:00.0: eth0: link down
[ 1344.573970] ==> rtl8192cu_hal_deinit 
[ 1347.187210] ==> rtl8192cu_hal_deinit 
[ 1352.155140] ==> rtl8192cu_hal_deinit 
[ 1357.163773] ==> rtl8192cu_hal_deinit 
[ 1362.605517] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[ 1365.136083] rtl8192c_dm_RF_Saving(): RF_Normal
[ 1385.135199] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1389.135481] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1395.135324] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1397.135640] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1399.135397] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1409.135635] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[ 1635.175323] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[ 1637.176491] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0


> $ **lsmod**
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
rfcomm                 38408  10 
bnep                   17923  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  6 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
8192cu                464562  0 
btusb                  18160  2 
bluetooth             148839  23 rfcomm,bnep,btusb
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  0 
snd_pcm                80468  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          73942  0 
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  21 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
drm_kms_helper         32889  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
soundcore              12600  1 snd
drm                   192226  4 i915,drm_kms_helper
nvram                  14029  1 thinkpad_acpi
psmouse                73673  0 
i2c_algo_bit           13199  1 i915
serio_raw              12990  0 
wmi                    18744  0 
mei                    36466  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
sdhci_pci              13658  0 
r8169                  43104  0 
sdhci                  27360  1 sdhci_pci


> $ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr f0:de:f1:82:5e:c0  
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
          RX packets:473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34529 (34.5 KB)  TX bytes:34529 (34.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:c0:ca:52:c2:4f  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe52:c24f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21356 errors:0 dropped:22464 overruns:0 frame:0
          TX packets:14252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108082938 (108.0 MB)  TX bytes:480074411 (480.0 MB)


---

### Post by praseodym on 2011-11-15
Too many dropped packages in "ifconfig". Deactivate IPv6 system-wide:

```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
and reboot. Check the mtu-value of your ISP and add it as a number instead of "Automatic" in the network-manager applet, even if it is 1500 as shown there.

---

### Post by khurtsiya on 2011-11-15
Deactivated and rebooted - no change.

I do not know what is mtu-value and how to check it...

I find out that there are two mode in wi-fi connection properties also: infrastructure and ad-hoc. Does this make any sense?

---

### Post by praseodym on 2011-11-15
Ad-Hoc means Internet Connection Sharing, which is wrong here. So if it is Ad-Hoc, remove (not edit) the wireless profile and setup a new one in Infrastructure mode.

MTU is the Maximum Transmission Unit, see:
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)
Try 1500 or 1492

---

### Post by khurtsiya on 2011-11-15
> So if it is Ad-Hoc, remove (not edit) the wireless profile and setup a new one in Infrastructure mode.
It was infrastructure by default so I will live this connection.
> Try 1500 or 1492
Tried both - no changes.

Can you tell me how to enable my built in wi-fi adapter back again so I can compare network counts?

---

### Post by praseodym on 2011-11-15
Unplug the stick, the UDEV rule should do the trick. If not, load the module by hand:

```
sudo modprobe rtl8192ce
```

---

### Post by khurtsiya on 2011-11-15
It worked.

So I have 13 connections with my built in adapter with at least 3 lines strength and mine is full - 4 lines. On the other hand with ALFA I have only two with 1-2 lines strength...

You already give many suggestions. Can you suggest any more?

---

### Post by praseodym on 2011-11-15
The data sheet

[http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NHR&Category=0](http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NHR&Category=0)

shows channels 1-11 for North America, maybe there is nothing more you can do, except waiting for a newer driver from Realtek. The Realtek HP only shows the driver for kernel 2.6.38 and earlier:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Edit: Or try

```
sudo iw reg set US
```

;-)

---

### Post by khurtsiya on 2011-11-15
> $ **sudo iw reg set US**
nl80211 not found.


Well, that is sad... I think I will go change this one AWUS036NHR to older AWUS036NH then.

---

### Post by praseodym on 2011-11-15
Check the device ID, maybe its a problem with kernel 3?! You may want to translate this page and the links therein:

[http://wiki.ubuntuusers.de/WLAN/Karten/Alfanet](http://wiki.ubuntuusers.de/WLAN/Karten/Alfanet)

---

### Post by khurtsiya on 2011-11-15
How can I check device ID?

Read both links but don't get clue what's it all about :(

---

### Post by praseodym on 2011-11-15
With "lsusb"

---

### Post by khurtsiya on 2011-11-15
Ok, here

> $ **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
[COLOR="Red"]Bus 001 Device 008: ID 0bda:817f Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 04f2:b257 Chicony Electronics Co., Ltd [/COLOR]
Bus 002 Device 003: ID 147e:1002 Upek 
Bus 002 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller


I do not sure, but think it is one of the colored. What should I do next?

---

### Post by praseodym on 2011-11-15
> Bus 001 Device 008: ID 0bda:817f Realtek Semiconductor Corp. 

is the stick we just tried to get to work, see on page 1 #4. If you try another stick check the ID with "lsusb"

---

### Post by khurtsiya on 2011-11-15
I do not have another. And IDs the same as I see. What should I do with it?

---

### Post by praseodym on 2011-11-15
You wrote in #45:

> **khurtsiya said:**
> Well, that is sad... I think I will go change this one AWUS036NHR to older AWUS036NH then.
I thought you still have another one.

---

### Post by khurtsiya on 2011-11-15
I bought AWUS036NHR view days ago so I will ask shop to change it for AWUS036NH

---

### Post by khurtsiya on 2011-11-15
praseodym, can this help?

> Getting the AWUS036NH working in Ubuntu 11.10 (Oneric)
Just upgraded to ubuntu 11.10 and my AWUS036nh card wouldn't work anymore. Luckily the rt2800usb driver is functioning with the new linux 3 kernel. We just have to let it know that it is supposed to drive the card. I modified my TX power boosting script to do this. If you are having the same problem, you can download the script and use it to fix the problem. You can also use it to boost your TX Power if you want. I recommend doing this (if it is legal where you are) because Ubuntu defaults TX power to 100mW.

#!/bin/bash
#A little script to get the AWUS036NH working in ubuntu 11.10
#It also boosts the tx power to 1W
#Coded by GUNN4R, 15 Oct 2011
if [ "$#" -eq 0 ]
then
  echo -e "Not Enough Arguements!\\nUsage:\\nboost.sh start  -- starts the card"
  echo "boost.sh wlan5  -- this boosts the tx power to 1MW"
  exit
fi

sudo modprobe rt2800usb
sleep 2

if [ "$1" = "start" ]
then
  echo '148f 3070' | sudo tee /sys/bus/usb/drivers/rt2800usb/new_id
  ifconfig
else
  sudo ifconfig $1 up
  sudo iw reg set BO
  sudo iwconfig $1 txpower 30
  iwconfig
fi

  

How to use the script

    Save it as boost.sh (and don't forget to make it executable)
    start your card by typing ./boost.sh start
    (optional) boost your power by typing ./boost.sh wlanX where X is the number assigned to your card

---

### Post by praseodym on 2011-11-15
Check with

```
modinfo rt2800usb | egrep '148F|3070'
```
if the device ID is present. Ralink-chipsets normally work ootb

---

### Post by khurtsiya on 2011-11-15
The output:

> $ **modinfo rt2800usb | egrep '148F|3070'**
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p[COLOR="Red"]3070d[/COLOR]*dc*dsc*dp*ic*isc*ip*


I guess I need to change that adapter to older one?

---

### Post by praseodym on 2011-11-15
> alias: usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
You shouldnt need that script, the device ID is present (if it is the real one of the stick, some manufacturers use different chipsets in the same product).

---

### Post by khurtsiya on 2011-11-15
Thanks for all your help. It is sad that we can not mark this thread as solved. Tomorrow I will sent this one to the shop and take an older one. Hope it will be easier to make it work.

---

### Post by jed823 on 2012-02-09
Hello.

I am having issues getting my new Alfa AWUS036NH(not the AWUS036NHR previously in this post) working in Ubuntu 11.10.

I have blacklisted my default drivers:
rt2800usb
rt2800lib
rt2x00usb
rt2x00lib
rtl8192se

I originally only blacklisted the first 4 as instructed from another website, but it was still connecting with my integrated NIC.  So I performed an lsmod and noticed the rtl8192se.  Blacklisted it and now it is not getting to the net at all.

I have downloaded they latest linux drivers via Alfa's website, and proceeded to unpack and make && make install the tar.bz2 file.

I can unpack the files fine, but when I perform a make or sudo make I get this.

> kl0ud@kl0ud-Satellite-L655:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ sudo make
make -C tools
make[1]: Entering directory `/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4002:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406:1: warning: the frame size of 1584 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type [enabled by default]
/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
cc1: some warnings being treated as errors

make[2]: *** [/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/kl0ud/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [LINUX] Error 2

Any information would be much appreciated.

Possibly the amazing Praseodym can come to the rescue again.

---

### Post by jed823 on 2012-02-10
I'm sure it is probably something to do with the instructions in the readme.

> 1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3>[B] In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d[/B]

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta

I do not understand what it means in the bold section.  Tried searching Google, but wasn't really finding any answers.

New to Linux so please pardon my ignorance.

---

### Post by praseodym on 2012-02-10
Hi,

did you try the blacklisted rt2800usb?

```
sudo modprobe -v rt2800usb
```
Check:
```
lsmod
lsusb
iwconfig
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by jed823 on 2012-02-10
Your the man.  Works like a charm.

If you don't mind what would be the UDEV-rule script so it only uses the Alfa adapter when plugged in?

Thanks again! Keep up the great work.

---

### Post by praseodym on 2012-02-11
See here

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace b43 from the script with the module name of your internal card

---

### Post by jed823 on 2012-02-12
Thanks. I really appreciate your help.

I am having another issue now.  When I am running aireplay I keep getting a "mon0 is using channel -1, but the access point is using channel 6" error.

I have done a bunch of reading on it, and it is a known bug with aircrack-ng, but I have no managed to find a way to fix it.  Found a couple of possible solutions where you have to use a diff patch, but not really sure to do with the code he provides..

Was also considering maybe it is an issue with using these generic drivers. I noticed that when I run airmon-ng it listed my chipset as "unknown".  I checked the Alfa website, and found that this card runs off the RT3070 chipset.  

Went to ralink website, and downloaded said drivers, and am now trying to get them installed. Via the readme I have managed to get through running make, but then it is telling me to run a cp command to copy the RT2870STA.dat file in the etc/Wireless/RT2870STA/RT2870STA.dat, but it keeps returning that there is no such file or directory.

Of course using the generic chipset could have nothing to do with the -1 channel error, but I figure I would ask the master what he thinks could be causing the issue.

Again, any guidance is greatly appreciated.

---

### Post by praseodym on 2012-02-12
Create this directory:

```
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
```

---

### Post by jed823 on 2012-02-12
The RT2870STA dir already exists with a RT2870STA.dat file inside it.  Went ahead and tried running these commands anyway.  When I do the mkdir it didn't throw out any errors or anything, but when I do the cp it still says no such file or directory.

---

### Post by praseodym on 2012-02-12
output of:

> locate RT2870STA.dat

---

### Post by jed823 on 2012-02-12
E:~/Documents/Drivers$ locate RT2870STA.dat
/home/kl0ud/Documents/Driver/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat
kl0ud@Kl0ud-E:~/Documents/Drivers$

---

### Post by praseodym on 2012-02-12
> sudo cp /home/kl0ud/Documents/Driver/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
Like this?

---

### Post by jed823 on 2012-02-12
~$ sudo cp /home/kl0ud/Documents/Driver/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
cp: target `/etc/Wireless/RT2870STA/RT2870STA.dat' is not a directory

---

### Post by praseodym on 2012-02-12
No blanks in folder names! Rename the folder and try it again:

> /2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPO
between "V2" and ".5"

---

### Post by jed823 on 2012-02-12
Possibly issue because this readme is written for kernel 2.4 or 2.6?  I'm running kernel 3.

---

### Post by jed823 on 2012-02-12
There is no blank in the dir name.  Had copied directly from your post.  Went and changed the command, but same response.

> ~$ sudo cp  /home/kl0ud/Documents/Driver/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
cp: cannot stat  `/home/kl0ud/Documents/Driver/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat':  No such file or directoryHeading to bed I'll check for a response in the morning!

Thanks again!

---

### Post by eric948470 on 2012-08-22
Hi Guys,

About the original question posted in this thread about the Alfa AWUS036NHR.

I tried the official driver from the Alpha networks site, and I ran in to the same problem with "smp_lock.h".

Then I found this page : [http://store.rokland.com/blogs/news/3821712-alfa-awus036nhr-is-backtrack-5-linux-compatible](http://store.rokland.com/blogs/news/3821712-alfa-awus036nhr-is-backtrack-5-linux-compatible)

I downloaded their driver and ran in to the same problem. Then I followed the advice given in the comments by "Mu", which says edit two files replacing the strings "smp_lock.h" with "smp.h".

Then the driver compiled.

I haven't tried it with the official Alfa driver. Just the driver given in the forum given in the link.

---

