---
title: "Big problem with rt3370. Warning: unused variable"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by jamita on 2011-11-09
Yes I'm new and I'm blond. But before I put this message I did some research for over 6 weeks. Yes I'm a patient women... but that's enough for me.
To speak briefly:

I have kernel
root@bt:~# uname -r
2.6.39.4

and for over 6 weeks molesting google, trying to install
2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO

I need Ralink rt3370 for DWA 123, so what I did:
blacklist, lsusb and ({USB_DEVICE(0x1737,0x0078)}, /* Ralink */), all SUPPORT staff =y, config.mk, TARGET=Linux an do on... before installing

what I have is :
root@bt:/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO# sudo make
make -C tools
make[1]: Entering directory `/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/tools'
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/Makefile
make -C /lib/modules/2.6.39.4/build SUBDIRS=/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/mlme.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/action.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/eeprom.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/dfs.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/spectrum.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffset&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:939: warning: unused variable &#8216;bTempSuccess&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:938: warning: unused variable &#8216;LookupTableIndex&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:937: warning: unused variable &#8216;CurrentTemp&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:936: warning: unused variable &#8216;BbpValue&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:935: warning: unused variable &#8216;pTxPowerTuningEntry2&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:932: warning: unused variable &#8216;RFValue&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:931: warning: unused variable &#8216;pTxPowerTuningEntry&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAdjustTxPower&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:1585: warning: unused variable &#8216;pFinalTxPwr&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_asic.c:1583: warning: unused variable &#8216;bAutoTxAgc&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/rt_profile.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/assoc.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/auth.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/sync.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/sanity.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/connect.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/wpa.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/ags.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/rt_linux.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/ba_action.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_led.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:235: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:242: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:280: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:509: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:568: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:598: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:612: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:630: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtusb_io.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtusb_data.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/cmm_data_usb.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtusb_bulk.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /usr/src/[COLOR="Black"][/COLOR]rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_mcu.o
/usr/src/[COLOR="red"]rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicLoadFirmware&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtmp_mcu.c:383: warning: unused variable &#8216;MacReg1&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/rt_usb.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:202: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:215: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:230: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:252: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:265: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:280: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/frq_cal.c:136: warning: unused variable &#8216;bUpdateRFR&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt3070.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt30xx.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xx_ChipSwitchChannel&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt30xx.c:619: warning: unused variable &#8216;BbpR109&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt30xx.c:618: warning: unused variable &#8216;Tx1FinePowerCtrl&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt30xx.c:618: warning: unused variable &#8216;Tx0FinePowerCtrl&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt33xx.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xxSetRxAnt&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt33xx.c:164: warning: unused variable &#8216;x&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xx_ChipSwitchChannel&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt33xx.c:409: warning: unused variable &#8216;BbpR109&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt3370.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt3370.c: In function &#8216;NICInitRT3370RFRegisters&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt3370.c:51: warning: unused variable &#8216;bbpreg&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_Init&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:490: warning: assignment makes integer from pointer without a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390SetRxAnt&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:756: warning: unused variable &#8216;Value&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390LoadRFSleepModeSetup&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:915: warning: unused variable &#8216;RFValue&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390ReverseRFSleepModeSetup&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:991: warning: unused variable &#8216;RFValue&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ChipSwitchChannel&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:1609: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:1620: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:1634: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:1498: warning: unused variable &#8216;BbpR110&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:1497: warning: unused variable &#8216;BbpR109&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetDesiredTssiAndCurrentTssi&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3085: warning: missing braces around initializer
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3085: warning: (near initialization for &#8216;htTssiInfo.PartA.field&#8217;)
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ATETssiCalibration&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3364: warning: ISO C90 forbids mixed declarations and code
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3453: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/include/rtmp.h:5774: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3365: warning: unused variable &#8216;ChannelPower&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetPowerDeltaFromTssiRatio&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3595: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;LONG&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../chips/rt5390.c:3624: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;LONG&#8217;
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.o
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DefaultATEAsicSwitchChannel&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:1276: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:1044: warning: unused variable &#8216;RFValue2&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;ATETxPwrHandler&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:5358: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TX_FREQOFFSET_Proc&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:7770: warning: comparison of distinct pointer types lacks a cast
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_EX_Proc&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9496: warning: unused variable &#8216;CurrentChannel&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9495: warning: unused variable &#8216;BSSID_ADDR&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9494: warning: unused variable &#8216;ChannelPower&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9493: warning: unused variable &#8216;EEPData&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9492: warning: unused variable &#8216;TssiDeltaPerChannel&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9492: warning: unused variable &#8216;TssiRefPerChannel&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9491: warning: unused variable &#8216;BBP49Value&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9491: warning: unused variable &#8216;RF28Value&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9491: warning: unused variable &#8216;RF27Value&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9491: warning: unused variable &#8216;RFValue&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9491: warning: unused variable &#8216;BbpData&#8217;
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9499: warning: control reaches end of non-void function
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:9483: warning: control reaches end of non-void function
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_WRITE_BULK&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:4070: warning: the frame size of 1040 bytes is larger than 1024 bytes[/COLOR]
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_READ_BULK&#8217;:
/usr/src/[COLOR="Red"]rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:4037: warning: the frame size of 1032 bytes is larger than 1024 bytes
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_E2PROM_READ_ALL&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:3044: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_E2PROM_WRITE_ALL&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:3061: warning: the frame size of 1032 bytes is larger than 1024 bytes
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_Load_E2P_Proc&#8217;:
/usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/../../common/rt_ate.c:8563: warning: the frame size of 1040 bytes is larger than 1024 bytes[/COLOR]
  LD [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/rt5370sta.mod.o
  LD [M]  /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'
cp -f /usr/src/rt3370/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.03_DPO/os/linux/rt5370sta.ko /tftpboot


root@bt:/usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO# sudo make install
make -C /usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.39.4
make[1]: Leaving directory `/usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO/os/linux'

root@bt:/usr/src/rt3370/2011_0719_RT3370_Linux_STA_V2.5.0.3_DPO# sudo modprobe rt3370sta
FATAL: Module rt3370sta not found.


PLEASE really need help,
sorry I'm new to Linux world. :)
any help really helpful

---

### Post by ratcheer on 2011-11-09
Please post the output of the wireless adapter section of "sudo lspci -v".

Tim

---

### Post by praseodym on 2011-11-09
Hi,

> install -m 644 -c [COLOR="Red"]rt5370sta[/COLOR].ko /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
;-)
Warnings can be ignored, errors not! Try

```
sudo modprobe -v rt5370sta
```
and please show:

```
lspci -nnk
lsusb
lsmod
iwconfig
```

---

