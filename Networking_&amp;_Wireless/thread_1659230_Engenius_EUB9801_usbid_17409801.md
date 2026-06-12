---
title: "Engenius EUB9801 usb:id 1740:9801"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by chili555 on 2011-01-03
######################################################
#WARNING WARNING WARNING                             
#                                                    
#   See edit below for instructions          
#   in Natty Narwal 11.04                            
#                                                    
#WARNING WARNING WARNING                             
######################################################

******************************************************
*
*For Ubuntu 12.04, this device works perfectly with the driver rt2800usb. 
*No compiling is required.
*
******************************************************



This USB device was sent to me by a forum friend Walt. I appreciate his thoughtful gift. It was quite challenging to figure out and, at times, I wondered if Walt sent it to torture me!

The device works with the Ralink driver rt3572sta. It can be downloaded here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

In order to compile drivers, you must install build-essential and kernel-headers-generic. Obtain a wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Download the file referenced above; by default, downloads in Maverick go to a folder called Downloads. Open a terminal and do:```
cd Downloads
tar xjvf 2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO.bz2
cd 2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
gedit os/linux/config.mk
```Change as shown. The remainder of the file remains unchanged:```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```Now do:```
gedit include/os/rt_linux.h 
```Change lines 1161 and 1162 as noted. The remainder of the file is unchanged:```
#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)		[COLOR="Red"]usb_alloc_coherent[/COLOR](_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)	[COLOR="Red"]usb_free_coherent[/COLOR](_dev, _size, _addr, _dma)
```In both cases, proofread carefully, save and close gedit. Now do:```
sudo su
make
make install
modprobe rt3572sta
exit
```On reboot, your device should be working. I am posting using it now.```
ra0       Ralink STA  ESSID:"mylilrouter"  Nickname:"RT3572STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:24:56:2A:D7:29   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```At no time does the light flicker or light up. If you have any questions, please post back.

##########################################

I got this working well in Natty Narway 11.04. I downloaded the April 27, 2011 version of the driver. I changed os/linux/config.mk as follows:```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]

--- snip ---
HAS_LED_CONTROL_SUPPORT=[COLOR="Red"]y[/COLOR]
```I then made, made install and modprobed and then the device showed up in Network Manager and connected.

EDIT: In Ubuntu 13.04, this device works perfectly with the driver rt2800usb. Insert, connect and enjoy!

---

### Post by walt.smith1960 on 2011-01-04
I'm glad you were able to get it to work.  I don't have the knowledge or patience for what Chili did.  The lesson for others is that just because something is advertised as supporting Linux which this device was, that doesn't mean the device in questions supports linux **WELL.**  For anyone considering a hardware purchase, an hour spent on this and other forums searching for others' experiences might save many hours of aggravation later.

---

### Post by jeraldjunkmail on 2011-02-19
I know I am probably supposed to post this somewhere in the Debian forums, but Chili seems to have this somewhat figured out.

I had a problem with the make command, so googled the error, and got this: [http://crunchbanglinux.org/forums/topic/8463/solved-make-having-trouble-finding-libmoduleskernelbuild/](http://crunchbanglinux.org/forums/topic/8463/solved-make-having-trouble-finding-libmoduleskernelbuild/)

OK, so that got me up to this point here:




> root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO# make
make -C tools
make[1]: Entering directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-5-amd64/build SUBDIRS=/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make: *** /lib/modules/2.6.32-5-amd64/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# make
make -C tools
make[1]: Entering directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-5-amd64/build SUBDIRS=/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-5-amd64'
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c:1478: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c:1573: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c:918: warning: cast from pointer to integer of different size
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c:918: warning: cast from pointer to integer of different size
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/action.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/dfs.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.c:1983: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_profile.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_profile.c:420: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sync.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/connect.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/ags.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c:528: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-5-common/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c:530: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.32-5-common/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c:682: warning: assignment makes integer from pointer without a cast
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c:701: warning: assignment makes integer from pointer without a cast
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.c:728: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.c:1578: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:235: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:242: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:280: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:509: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:568: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:598: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:612: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:630: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[4]: *** [/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[3]: *** [_module_/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-amd64'
make: *** [LINUX] Error 2
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# gedit /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c


I hope someone can fill in the blanks because I am not a programmer, and am fairly new to linux...  This seems to be the only thread on google that addresses this issue.

Kindest regards, jeraldjunkmail!


EDIT:  Just to follow up, (and logically, this was to be expected, but I will put it here for completeness)

> root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO# make install
make -C /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-5-amd64/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.32-5-amd64/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
make: *** [install] Error 2
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# modprobe rt3572sta
FATAL: Module rt3572sta not found.

Oh, I am using debian 6.0 stable

Cheers, jeraldjunkmail!

---

### Post by chili555 on 2011-02-19
> common/cmm_mac_usb.c:52: error: implicit declaration of function ‘[COLOR="Red"]usb_alloc_coherent[/COLOR]’I suspect that, because of your kernel version, you do ***NOT*** need the change I described above:> Change lines 1161 and 1162 as noted. The remainder of the file is unchanged:
Code:

#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)		usb_alloc_coherent(_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)	usb_free_coherent(_dev, _size, _addr, _dma)

Since you changed the file and probably don't quite remember how it read before the change, I'd suggest you download a fresh copy of 2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO and follow all the instructions except that and try again. I will be following the thread, so post back for the benefit of any searchers.

---

### Post by jeraldjunkmail on 2011-02-22
Sorry about the delay in posting a reply, I only have time to do this in the evenings, and have been very busy.  As for you helping me out, what can I say, a total stranger somewhere out there putting time towards fixing the problems of another total stranger is so generous.  Thank you.  I will pay it forward.

Here is the output of terminal for the unedited file as suggested.

> root@debian:/home/jerald/Downloads# cd 2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# gedit os/linux/config.mk

(gedit:15616): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# gedit include/os/rt_linux.h

(gedit:15628): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# sudo su
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# make
make -C tools
make[1]: Entering directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-5-amd64/build SUBDIRS=/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make: *** /lib/modules/2.6.32-5-amd64/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# make install
make -C /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-5-amd64/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.32-5-amd64/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
make: *** [install] Error 2
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# modprobe rt3572sta
FATAL: Module rt3572sta not found.
[email]root@debian:/home/jerald/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]# exit 


I'll also check back on this thread before bedtime and tomorrow, as I didn't expect a reply as quickly as I got one, once again, your help is appreciated...  I bought this adapter thinking that it would work if I followed your directions, along with the fact that it was a cheap 300mbps 2.4/5ghz adapter, all the features and half the cost...  Nothings free :)

---

### Post by chili555 on 2011-02-22
Can you please confirm you have followed this step?> In order to compile drivers, you must install build-essential and kernel-headers-generic. Obtain a wired ethernet connection and do:
```
sudo apt-get install build-essential kernel headers-generic

```
> EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported
I don't understand this at all. Do you have the standard Ubuntu (Gnome) install, or xubuntu or kubuntu or Klingon-ubuntu or...what?

---

### Post by jeraldjunkmail on 2011-02-22
I am using Debian 6.0 Squeeze (stable) with the standard gnome desktop.  Also, I used the software center to get those apps because it wasn't agreeing with me.  It did seem to install when I searched the software center.  Sorry for the noobishness :)

the command you wanted me to confirm gives me this:

```
sudo apt-get install build-essential kernel headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel
E: Unable to locate package headers-generic

```


As for the gedit error, not too sure, as this is a fresh install of debian.  I am at the "oops, time to reformat the OS" stage of learning linux, so it gets rewritten quite a bit.  The home folder has been the only constant as my raid array is being used as a backup for my data.    Anyhoo, let mew know what  else I can do to help you out, and thanks again for the quick reply.  I'll be here for the next few hours.  Oh, and all of this is being done from a root terminal (they let us have those in debian...scary ;) )

---

### Post by chili555 on 2011-02-22
Oops, sorry about that:```
sudo apt-get install build-essential [COLOR="Red"]linux-[/COLOR]headers-generic

```Debian, eh? I hope we can help you.

I'll check in tomorrow morning.

---

### Post by jeraldjunkmail on 2011-02-22
> root@debian:/home/jerald# sudo apt-get install build-essential linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate
root@debian:/home/jerald# 


could be due to the limited software sources available to debian out of the box?  Also, should I post something in the debian forums and point them to this thread?

Thanks!

---

### Post by chili555 on 2011-02-23
> could be due to the limited software sources available to debian out of the box?Either that or Debian has a different name for the equivalent package; I have no idea what it might be.> should I post something in the debian forumsYes, please.

---

### Post by jeraldjunkmail on 2011-02-23
Ok, I'll reference this thread for them, and when I get a copy of Ubuntu running, I'll be back :D

Thanks for all your help!

Cheers, Jeraldjunkmail!

---

### Post by noob.bot76 on 2011-03-19
Chili555, 

will the above tutorial work for RALink's 3070sta driver for my usb device?

can you tell me what changes i need to make: for example, do i simply substitute rt3572sta with 3070sta? 

oh, and how to you know what kernel you are running. i have Ubuntu 10.04 on a Starling netbook. 

thanks

---

### Post by chili555 on 2011-03-19
> will the above tutorial work for RALink's 3070sta driver for my usb device?No. You have a very different device.> oh, and how to you know what kernel you are running. i have Ubuntu 10.04 on a Starling netbook.In a terminal, type:```
uname -r
```Please see your other thread.

---

### Post by FReQ Z on 2011-04-06
not sure where to start, but I'm attempting this fix to get my AE1000 to work on my secondary PC with the beta build of Ubuntu.  I have two issues:

1.  The Ralink site seems to be down.  I've been trying all morning.

2.  Getting a hardwired connection in my garage is going to be all but impossible.  My only recourse is to get a 30+ foot cable and run it temporarily through my house from my router.

I see that I need to get two apps that aren't currently in Ubuntu (build-essential and kernel-headers-generic), as well as the Linux RT3572sta driver.

I have the PC version (RT3572usb) downloaded, but I cannot find the Linux driver hosted anywhere.  Can anyone host it for me?

Also, are the build-essential and kernel-headers-generic files hosted anywhere so I can download them to my PC and transfer them via thumbdrive to my Ubuntu machine?

Sorry for being so newbish... I really do want to learn Ubuntu as best as I can.

Thanks!

**edit:  just found the .deb packages for the build-essential and kernel-headers-generic files.  :)  now I just need the RT3572 file.

---

### Post by chili555 on 2011-04-06
Both of the packages you found are what is called a meta-package. It contains virtually nothing but has dependencies such as gcc, g++, make, etc. If you don't also install the dependencies, the installation of the meta-package will fail. Try it, however, and find and install the additional debs as needed.

Check here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I hope the attached will be helpful.

---

### Post by FReQ Z on 2011-04-07
thank you so very much for your help.

I downloaded the .deb files from packages.ubuntu.com and transferred them over to the PC via thumbdrive.  when I attempted to install them, I got a message stating that they were already installed.  so hopefully the dependencies are there also.

and thanks for uploading the driver file!  I'm going to get to work on it right now.  :)

---

### Post by effay on 2011-04-23
Is there any way to implement this solution without first obtaining a wired connection? My problem is that my desktop has Windows 7 and Ubuntu, but I can't move my desktop to somewhere with wired access. Is it possible to download the driver in Windows and put it on a usb drive and get it to Ubuntu that way?

---

### Post by effay on 2011-04-23
And, alternatively, it wouldn't really be that big of a deal to just buy another wireless adapter. Is there a brand that is consistently compatible with Linux/Ubuntu out of the box? D-Link? Netgear? Cisco/Linksys?

---

### Post by xxlunarxx on 2011-09-02
hello chili,

I'm trying to install a ralink driver onto my laptop but i'm not using an usb wireless adapter. I was wondering if you can help me figure out why it won't compile. 

Thanks in advance.

huy@huy-HP-Pavilion-dv6-Notebook-PC:~/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ sudo make
make -C tools
make[1]: Entering directory `/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-11-generic-pae/build SUBDIRS=/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.o
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:463:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:482:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
  CC [M]  /home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: ‘enum tx_power_setting’ declared inside parameter list
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: its scope is only this definition or declaration, which is probably not what you want
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:678:29: error: parameter 2 (‘Type’) has incomplete type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:676:12: warning: function declaration isn’t a prototype
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1355:2: warning: initialization from incompatible pointer type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1378:2: warning: initialization from incompatible pointer type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1379:2: warning: initialization from incompatible pointer type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1380:2: warning: initialization from incompatible pointer type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1381:2: warning: initialization from incompatible pointer type
/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1388:2: warning: initialization from incompatible pointer type
make[2]: *** [/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/huy/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [LINUX] Error 2
huy@huy-HP-Pavilion-dv6-Notebook-PC:~/Desktop/2010_1216_RT5390_LinuxSTA_V2.4.0.4

---

### Post by wildmanne39 on 2011-09-02
Hi, chili is out of town I will see if I can help you.

Please these commands:
```
lspci -nn | grep 0280
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by brec on 2011-12-20
The driver's URL has changed to:

[http://www.ralinktech.com/en/04_support/license.php?sn=5017](http://www.ralinktech.com/en/04_support/license.php?sn=5017)

Fill in your name and email address (not verified), click Accept, and it will start the download.

The downloaded file's name:
2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO.bz2

Release notes:```
[2.5.0.0]
1.Support Linux Kernel 2.6.35.
2.Fixed Ad-hoc issue: STA didn't use legacy rate when STA is Ad-hoc OPEN-WEP or WPAPSK-TKIP.
3.Fixed issue: STA had problem to show 32-bytes SSID when user uses "iwpriv ra0 show SSID".
4.Fixed connection issue: If there are two APs have same SSID, AuthMode and EncrypType
5.Refine the stack size of all functions to be smaller than 1024B.
6.Improve scan mechanism.
```

Kernel 2.6.35!?  I'm running 3.0 (Ubuntu 11.10).  I have my fingers crossed...

---

### Post by brec on 2011-12-24
Not SOLVED for me.

11.04:  finds network SSIDs but doesn't connect.

---

### Post by chili555 on 2011-12-24
> **brec said:**
> Not SOLVED for me.

11.04:  finds network SSIDs but doesn't connect.May we see:```
sudo iwlist ra0 scan
sudo cat /var/log/syslog | grep etwork | tail -n20
```Can you confirm that you made the changes in post #1?> I changed os/linux/config.mk as follows:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

--- snip ---
HAS_LED_CONTROL_SUPPORT=y

```


---

### Post by brec on 2011-12-24
> **chili555 said:**
> May we see:```
sudo iwlist ra0 scan
sudo cat /var/log/syslog | grep etwork | tail -n20
```

With or without ethernet connector inserted and wired connection present?  With or without Engenius USB device inserted?

> 
Can you confirm that you made the changes in post #1?

Confirmed.   Note that I have a slightly later driver from ralink -- Apr 2011 vs. Dec 2010, which is all that is currently available at their site; see my post #21, immediately prior to the one which drew your kind attention (at time of that post I was running 11.10, but now 11.04).

P.S. Was puzzled by the big WARNING annotation in post #1, as all the referenced change does is enable the device's LED, and all that does is blink and glow.

Edit: see my next post, being composed at time time of this edit.

---

### Post by brec on 2011-12-24
> **brec said:**
> Confirmed.   Note that I have a slightly later driver from ralink -- Apr 2011 vs. Dec 2010, which is all that is currently available at their site; see my post #21, immediately prior to the one which drew your kind attention (at time of that post I was running 11.10, but now 11.04).

P.S. Was puzzled by the big WARNING annotation in post #1, as all the referenced change does is enable the device's LED, and all that does is blink and glow.

Since posting that I see that the Natty user quoted in post #1 also downloaded the later (April) driver.  So in theory I should be in the same state -- same Ubuntu, same driver, same device.  But...

After installing the driver per post #1, shut down and inserted Engenius USB device.  Booted.  Was greeted with a request for password to unlock login keychain.  On clicking the OK (or whatever it was called) button on that dialog, immediate crash -- display of white text on black background.  Part of text was modules loaded, and I saw that rt3572sta was among them.  After very approximately 20 seconds the crash screen disappeared and desktop returned with Authenticate dialog asking for WPA/WPA2 key; I supplied it.  Panel wireless icon animated the same way the one on my Mac does when it's looking for networks.  After a while the Authenticate dialog came up again; process repeated.  After a while, Authenticate presented for third time.  40 seconds after that, the panel icon stopped animating.  A while after that, the wireless icon was replaced by the wired up-and-down-arrows icon.  At this point I can't ssh into the Ubuntu system from my Mac, and Chrome Browser won't start on Ubuntu.  sudo iwlist ra0 scan outputs nothing and doesn't return to a prompt, Ctrl-C is merely echoed ^C.  I quit the terminal (killing the process) and rebooted without the Engenius device.

---

### Post by chili555 on 2011-12-28
> **brec said:**
> Since posting that I see that the Natty user quoted in post #1 also downloaded the later (April) driver.  So in theory I should be in the same state -- same Ubuntu, same driver, same device.  But...

Please confirm you have the same device:```
lsusb
```Let's rebuild the driver and look for errors or warnings:```
cd Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
```^^ or wherever the file was downloaded and extracted.```
sudo su
make clean
make
make install
exit
```Look for any warnings and errors and post them here.

Can you confirm you made these changes?> # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

--- snip ---
HAS_LED_CONTROL_SUPPORT=y

---

### Post by brec on 2011-12-30
Chili, thanks but I've abandoned the EUB9801 in favor of a WiFi -> Ethernet converter as another way to get 802.11/n 5GHz WiFi at the Ubuntu system.

---

### Post by cleduc on 2012-04-07
Thanks chili555, these are fantastic instructions.

I've forked the Ralink driver/firmware on Github and included a simple setup script.  I've tested this on Ubuntu 12.04 (beta2) with a Sitecom 300N adapter.

If you do not have Git installed:

```
sudo apt-get install git
```)

Then the following line will download the driver and firmware, compile it, install it, and load it at boot.

```
git clone git@github.com:celeduc/rt3572sta.git; cd rt3572sta; ./install.bash
```

---

### Post by dutara on 2012-05-28
Thanks to all who worked on this.  I got it to compile!
Unfortunately I can't get my D-Link DWA-140 USB (rt2870) (2001:3c15) device to light up.  
It shows up when I do lsusb, and rt3572 shows up in lsmod, but nothing changes in iwconfig. Yes, I've rebooted, unplugged/replugged lots of times.
I'm running Mint 13, which is the same internally as Ubuntu 12.04.

Any words of help?  I also tried compiling the rt2870 drivers from the Ralink site, but same-same.
Also, the net is full of different modifications to the code and config files, I tried lots of different advice but nothing makes the little feller light up, with several days effort.  I'd appreciate hearing from anyone who got the DWA-140 to work on Ubuntu 12.04 or other releases based on it.

---

### Post by chili555 on 2012-05-28
> **dutara said:**
> Thanks to all who worked on this.  I got it to compile!
*Unfortunately I can't get my D-Link DWA-140 USB (rt2870) ([COLOR="Red"]2001:3c15[/COLOR]) device to light up.*  
It shows up when I do lsusb, and rt3572 shows up in lsmod, but nothing changes in iwconfig. Yes, I've rebooted, unplugged/replugged lots of times.
I'm running Mint 13, which is the same internally as Ubuntu 12.04.

Any words of help?  I also tried compiling the rt2870 drivers from the Ralink site, but same-same.
Also, the net is full of different modifications to the code and config files, I tried lots of different advice but nothing makes the little feller light up, with several days effort.  I'd appreciate hearing from anyone who got the DWA-140 to work on Ubuntu 12.04 or other releases based on it.Since the title of this thread specifies usb.id 1740:9801 and that's not what you have, I suggest you start your own new thread.

---

### Post by xkev on 2012-08-18
************************************************** ****
*
*For Ubuntu 12.04, this device works perfectly with the driver rt2800usb. 
*No compiling is required.
*
************************************************** ****

How so? More detail? I modprobe this and some 80211 messages are in the kernel log, but no wlan0 appears.

Fresh 12.04 install in EFI mode from 12.04 desktop cd.

```

$ lsusb
USB: 1740:9801 Senao EUB9801 802.11abgn Wireless Adapter [Ralink RT3572]

$ sudo modprobe rt2800usb 
$ dmesg | tail
[   36.233976] type=1400 audit(1345242572.304:21): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1946 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 2034.004140] cfg80211: Calling CRDA to update world regulatory domain
[ 2034.011597] cfg80211: World regulatory domain updated:
[ 2034.011601] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2034.011604] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2034.011607] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2034.011610] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2034.011613] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2034.011615] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2034.022281] usbcore: registered new interface driver rt2800usb

$ sudo lsmod | head
Module                  Size  Used by
usb_storage            49198  0 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              55301  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
rfcomm                 47604  0 

$ iwconfig wlan0
wlan0     No such device

$ uname -a
Linux AFK 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

$ ls /lib/firmware/rt*bin
/lib/firmware/rt2561.bin   /lib/firmware/rt2860.bin  /lib/firmware/rt3071.bin
/lib/firmware/rt2561s.bin  /lib/firmware/rt2870.bin  /lib/firmware/rt3090.bin
/lib/firmware/rt2661.bin   /lib/firmware/rt3070.bin  /lib/firmware/rt73.bin

```

---

### Post by chili555 on 2012-08-18
Please run and post:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep -i rt2
```Thanks.

---

### Post by xkev on 2012-08-21
> **chili555 said:**
> Please run and post:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep -i rt2
```Thanks.

I basically did that, if you consider the timetamps and order of operations...

[LIST]
[*] modprobe rt2800usb produced no output
[*] my dmesg output included all results after the modprobe - note the time delta - none included rt2
[*] iwconfig had no wlan0 device, but I did not clarify that there was no other network device available other than eth0 and lo
[/LIST]

I am away from the affected system for the next week or so. It is remote and shut down (I travel weekly - affected system is in my non-home apartment).  If you insist on exactly your output, it will take a bit.

---

### Post by chili555 on 2012-08-21
> my dmesg output included all results after the modprobe - note the time delta - none included rt2Are you certain?> [ 2034.022281] usbcore: registered new interface driver [COLOR="Red"]rt2[/COLOR]800usbdmesg is the quickest and easiest way to look for clues as to why the driver didn't marry the physical device and create a wireless interface. That's where I suggest you and I look. If you'd prefer, you can modprobe rt2800usb and zip up your entire dmesg and attach it to your reply:```
dmesg > xkev.txt
zip xkev.zip xkev.txt
```

---

### Post by xkev on 2012-08-22
> **chili555 said:**
> Are you certain?dmesg is the quickest and easiest way to look for clues as to why the driver didn't marry the physical device and create a wireless interface. That's where I suggest you and I look. If you'd prefer, you can modprobe rt2800usb and zip up your entire dmesg and attach it to your reply:```
dmesg > xkev.txt
zip xkev.zip xkev.txt
```

Yep, my eyeballs missed the rt2800 line at the end there.  That's the end of it though.  I'll get you more detail once I'm back at that machine, but it'll be at least a week.

p.s. Linux user since 1994, Debian since 1999.  I can handle whatever you throw at me.

---

### Post by chili555 on 2012-08-22
> **xkev said:**
> Yep, my eyeballs missed the rt2800 line at the end there.  That's the end of it though.  I'll get you more detail once I'm back at that machine, but it'll be at least a week.

p.s. Linux user since 1994, Debian since 1999.  I can handle whatever you throw at me.I'll look forward to it.

Your bean count tricked me! Of course my bean count doesn't reflect all the years I spent on Mandrake.

---

