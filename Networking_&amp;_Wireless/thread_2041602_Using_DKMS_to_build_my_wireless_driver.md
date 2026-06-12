---
title: "Using DKMS to build my wireless driver"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by Gleasonator on 2012-08-12
Hello,

I'm using an **[Asus PCE-N53]("http://www.asus.com/Networks/Wireless_Adapters/PCEN53/")** wireless card (**[RT5592]("http://www.ralinktech.com/en/02_products/product.php?sn=1013")**). The installation disc came with a driver (**[rt5592sta]("http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip")**) that I must build after every kernel update.

The driver builds and installs with errors, but works anyway. The ideal situation would be to find and fix the errors, but that is lower priority for me than ensuring I wont have to rebuild/install the driver after each update. I have two questions:

[LIST=1]
[*]How can I force DKMS to build my driver anyway? It does build it, but it doesn't know that it succeeded. [FONT="Courier New"]$ dkms status[/FONT] shows that the module has only been added and not built even though the compiled files appear in the build directory.
[*]How do I make DKMS install the module as well? I don't completely understand how a makefile works, but I know that [FONT="Courier New"]$ make install[/FONT] is the command which normally needs to be run in order for the module to be installed. [FONT="Courier New"]$dkms install [...][/FONT] seems to do the same thing as [FONT="Courier New"]$dkms build [...][/FONT] when I run it. Maybe that's because it wont even build correctly?
[/LIST]

To reiterate, the driver *does* work correctly when I [FONT="Courier New"]cd[/FONT] into the directory and run:
```
$ make
$ make install
```

I just want this process to be automated so I don't have to run it after every update.

Here are the contents of **/usr/src/rt5592sta-2.6.0.0-20120326/** (the driver) in a directory listing: [Click](http://gobblegourd.com/rt5592sta-2.6.0.0-20120326/)

Here are some outputs and file contents:

**dkms.conf**
```
PACKAGE_NAME="rt5592sta"
PACKAGE_VERSION="2.6.0.0-20120326"
MAKE[0]="make"
BUILT_MODULE_NAME="rt5592sta"
DEST_MODULE_LOCATION="/kernel/drivers/net/wireless/"
AUTOINSTALL="yes"
```

**Output for** [FONT="Courier New"]alex@ubuntu:~$ sudo dkms build -m rt5592sta -v 2.6.0.0-20120326[/FONT]
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.2.0-29-generic...................
ERROR (dkms apport): binary package for rt5592sta: 2.6.0.0-20120326 not found
Error!  Build of rt5592sta.ko failed for: 3.2.0-29-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/ for more information.
```

**/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/make.log**
```
DKMS make.log for rt5592sta-2.6.0.0-20120326 for kernel 3.2.0-29-generic (x86_64)
Sun Aug 12 22:26:48 CDT 2012
make -C tools
make[1]: Entering directory `/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/tools'
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/tools/bin2h
cp -f os/linux/Makefile.6 /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/Makefile
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_md5.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_sha2.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_hmac.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_aes.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_aes.c:1459:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_aes.c:1554:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/crypt_arc4.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c:526:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c:526:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c: In function &#8216;RTMPAdjustFrequencyOffset&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c:4990:2: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;FreqOffset&#8217; will never be NULL [-Waddress]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/mlme.c:4990:2: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;HighCurrentBit&#8217; will never be NULL [-Waddress]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_wep.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/action.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_init.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_tkip.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_aes.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_sync.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/eeprom.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_sanity.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_info.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_cfg.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_wpa.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_radar.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/spectrum.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/spectrum.c:1972:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_timer.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rt_channel.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_profile.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_asic.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_cmd.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ps.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/uapsd.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_profile.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_profile.c:411:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rtmp_chip.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/rtmp_data.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/sta_cfg.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/sta_cfg.c:3953:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rt_os_util.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c:505:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-29-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c:507:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-29-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c:659:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c:678:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_linux.c:705:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ba_action.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ba_action.c:1577:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../sta/dls.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rt_led.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data_pci.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPFreeTXDUponTxDmaDone&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPHandleMgmtRingDmaDoneInterrupt&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/cmm_data_pci.c:735:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_rbus_pci_drv.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function &#8216;RTMPInitPCIeDevice&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_rbus_pci_drv.c:1382:23: warning: unused variable &#8216;Index&#8217; [-Wunused-variable]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ee_prom.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/frq_cal.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibrationMode&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/frq_cal.c:128:13: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/frq_cal.c:141:3: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;RfReg&#8217; will never be NULL [-Waddress]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/ee_efuse.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:558:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [enabled by default]
include/linux/pci.h:756:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:564:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:564:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:578:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [enabled by default]
include/linux/pci.h:756:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:587:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rtmp_mcu.c:587:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../common/rt_rf.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt30xx.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xxLoadRFSleepModeSetup&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt30xx.c:477:9: warning: unused variable &#8216;MACValue&#8217; [-Wunused-variable]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xxReverseRFSleepModeSetup&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt30xx.c:515:9: warning: unused variable &#8216;MACValue&#8217; [-Wunused-variable]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c:120:26: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c:179:42: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c: In function &#8216;RT5592_ChipSwitchChannel&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c:1985:4: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;RfReg&#8217; will never be NULL [-Waddress]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c: At top level:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c:2223:2: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../chips/rt5592.c:857:13: warning: &#8216;RT5592FilterCalibration&#8217; defined but not used [-Wunused-function]
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/pci_main_dev.o
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/pci_main_dev.c: In function &#8216;rt2860_probe&#8217;:
/var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/../../os/linux/pci_main_dev.c:318:13: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  LD [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/rt5592sta.o
see include/linux/module.h for more information
  CC      /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/rt5592sta.mod.o
  LD [M]  /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/rt5592sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
cp -f /var/lib/dkms/rt5592sta/2.6.0.0-20120326/build/os/linux/rt5592sta.ko /tftpboot
```

Thanks in advance.

---

