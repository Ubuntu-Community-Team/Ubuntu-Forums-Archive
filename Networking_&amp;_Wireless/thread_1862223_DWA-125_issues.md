---
title: "DWA-125 issues"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by sandyd on 2011-10-16
Im currently trying to get a DWA-125 to work on 11.10.

In 11.04, there was the rt2870sta driver for the DWA-125, in 10.10, it doesn´t exist (replaced by rt2800usb, rt2x00lib, and rt2x00usb).

Ive tried compiling it from the ralink site, but it doesn´t work either.
```

  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/dfs.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rt_channel.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_profile.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/assoc.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1094:1: warning: the frame size of 1296 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:764:1: warning: the frame size of 1260 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1764:1: warning: the frame size of 1300 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sanity.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c:355:1: warning: the frame size of 1744 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/wpa.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/ags.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1479:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:599:1: warning: the frame size of 1288 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1979:1: warning: the frame size of 1652 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/uaccess.h:570:0,
                 from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:351,
                 from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/include/os/rt_linux.h:49,
                 from /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/include/rtmp_os.h:42,
                 from /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/include/rt_config.h:72,
                 from /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:40:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:3059:28:
/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:3544:28:
/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:5836:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:6035:1: warning: the frame size of 1340 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1694:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1731:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c:117:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/dls.o
  CC [M]  /home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78:3: error: implicit declaration of function ‘usb_buffer_free’ [-Werror=implicit-function-declaration]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278:11: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507:12: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
cc1: some warnings being treated as errors

make[2]: *** [/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/sandyd/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [LINUX] Error 2


```

---

### Post by wildmanne39 on 2011-10-16
Hi, please post the results of:
```
lsusb
```
That driver is not only gone but it is not going to work now since it was removed but the rt2800usb should if that is what is called for.
Thank you

---

### Post by brunoag on 2011-10-16
hi, iam having the same issue and in my case the adapter's line in lsusb reads:

```
Bus 001 Device 003: ID 07d1:3c0d D-Link System DWA-125 Wireless N 150 Adapter (rev.A1) [Ralink RT2870}
```

---

### Post by wildmanne39 on 2011-10-16
Hi, please try:
```
sudo modprobe rt2800usb
```
Thank you

---

### Post by brunoag on 2011-10-16
Worked instantly, thank you very very much!!

---

### Post by wildmanne39 on 2011-10-16
Hi, your welcome!
Enjoy

---

### Post by brunoag on 2011-10-16
just another question:

how do i ensure that's the driver loaded each time i boot?
i remember blacklisting some drivers last time i went through this, but i don' remember how to :)

---

### Post by wildmanne39 on 2011-10-16
Hi, you do not need to blacklist drivers now.

If it does not start on its own do this please:
```
sudo su 
echo rt2800usb >> /etc/modules 
exit
```
Thank you

---

