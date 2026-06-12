---
title: "Linksys AE1000 under 64bit 10.10"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by jokerhero9 on 2011-02-18
Here is the situation:
  I am currently running Ubuntu 10.10 64 bit. I'm trying to get my Linksys AE1000 to run correctly. I have followed many tutorials but most notably was:
[http://ubuntuforums.org/showthread.php?t=1507793&page=3](http://ubuntuforums.org/showthread.php?t=1507793&page=3)
lsmod shows that rt3572sta is loaded.
network manager in gnome is able to find my router.
my problem occurs when it tries to connect to the router using wpa2 security.
It continually asks for the wireless password then will freeze the system after a number of attempts.
After digging in for a bit, I was able to dig out a dmesg trapping the error:

BUG: unable to handle kernel paging request at ffffcfb0138af1ec
IP: [<ffffffffa021c7e8>] Cntl0idRTBssidProc+0x78/0x570 [rt3572sta]
PGD 0
Oops: 0000 [#1] SMP
last sysfs file: /sys/devices/system/cpu/cpu7/cache/index2/shared_cpu_map
CPU 2

I really don't see the need to continue on with those error messages

lsmod still shows rt3572sta after the failure.

In case anyone wants to see the changes I have made to the files before the make, I have included them. but changed the extension to "txt" to accommodate the up-loader and my rt_linux is too big to fit here, just not that it was 2 lines that were changed to work with the kernel.

If anyone wants to know what I mean by the system freezes, I do mean just that. The mouse will continue to work, but I am then unable to open any programs, unable to reboot the computer. it requires a hard reset.

I have uninstalled the drivers, installed them, make them, make install them, make clean, start from scratch a few times, and am getting no give here. 

Any help would be appreciated.

---

### Post by judderwocky on 2011-02-19
> **jokerhero9 said:**
> Here is the situation:
I am currently running Ubuntu 10.10 64 bit. I'm trying to get my Linksys AE1000 to run correctly. I have followed many tutorials but most notably was:
[http://ubuntuforums.org/showthread.php?t=1507793&page=3](http://ubuntuforums.org/showthread.php?t=1507793&page=3)
lsmod shows that rt3572sta is loaded.
network manager in gnome is able to find my router.
my problem occurs when it tries to connect to the router using wpa2 security.
It continually asks for the wireless password then will freeze the system after a number of attempts.
After digging in for a bit, I was able to dig out a dmesg trapping the error:

BUG: unable to handle kernel paging request at ffffcfb0138af1ec
IP: [<ffffffffa021c7e8>] Cntl0idRTBssidProc+0x78/0x570 [rt3572sta]
PGD 0
Oops: 0000 [#1] SMP
last sysfs file: /sys/devices/system/cpu/cpu7/cache/index2/shared_cpu_map
CPU 2

I really don't see the need to continue on with those error messages

lsmod still shows rt3572sta after the failure.

In case anyone wants to see the changes I have made to the files before the make, I have included them. but changed the extension to "txt" to accommodate the up-loader and my rt_linux is too big to fit here, just not that it was 2 lines that were changed to work with the kernel.

If anyone wants to know what I mean by the system freezes, I do mean just that. The mouse will continue to work, but I am then unable to open any programs, unable to reboot the computer. it requires a hard reset.

I have uninstalled the drivers, installed them, make them, make install them, make clean, start from scratch a few times, and am getting no give here.

Any help would be appreciated.

I can't get the driver to work either. I downloaded the source, but keep getting errors when I make ... so I haven't been able to make+install yet and actually try it.

Supposedly the old kernel before the last update allowed it to work, but there is no way I'm rolling the kernel back.

I guess I'm just stuck with my G class Belkin for now


  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_wep.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/action.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_data.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtmp_init.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_aes.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_sync.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/eeprom.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_info.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/dfs.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/spectrum.o
/home/myuser/ldriver/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/myuser/ldriver/os/linux/../../common/spectrum.c:1983: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rt_channel.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_profile.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_asic.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/rt_profile.o
/home/myuser/ldriver/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/home/myuser/ldriver/os/linux/../../os/linux/rt_profile.c:420: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/myuser/ldriver/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/assoc.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/auth.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/sync.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/sanity.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/connect.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/wpa.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/ags.o
  CC [M]  /home/myuser/ldriver/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rt_os_util.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/rt_linux.o
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c:528: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c:530: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c:682: warning: assignment makes integer from pointer without a cast
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c:701: warning: assignment makes integer from pointer without a cast
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/myuser/ldriver/os/linux/../../os/linux/rt_linux.c:728: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/ba_action.o
/home/myuser/ldriver/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/myuser/ldriver/os/linux/../../common/ba_action.c:1578: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.o
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:235: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:242: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:280: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:509: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:568: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:598: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:612: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:630: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/myuser/ldriver/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtusb_io.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtusb_data.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/ee_prom.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/ee_efuse.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/myuser/ldriver/os/linux/../../chips/rt30xx.o
/home/myuser/ldriver/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xx_ChipSwitchChannel&#8217;:
/home/myuser/ldriver/os/linux/../../chips/rt30xx.c:614: warning: unused variable &#8216;BbpR109&#8217;
/home/myuser/ldriver/os/linux/../../chips/rt30xx.c:613: warning: unused variable &#8216;Tx1FinePowerCtrl&#8217;
/home/myuser/ldriver/os/linux/../../chips/rt30xx.c:613: warning: unused variable &#8216;Tx0FinePowerCtrl&#8217;
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rt_rf.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/myuser/ldriver/os/linux/../../chips/rt28xx.o
  CC [M]  /home/myuser/ldriver/os/linux/../../chips/rt35xx.o
  CC [M]  /home/myuser/ldriver/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/myuser/ldriver/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /home/myuser/ldriver/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/myuser/ldriver/os/linux/rt3572sta.mod.o
  LD [M]  /home/myuser/ldriver/os/linux/rt3572sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'

---

### Post by waydaws on 2011-02-21
> **jokerhero9 said:**
> Here is the situation:
  I am currently running Ubuntu 10.10 64 bit. I'm trying to get my Linksys AE1000 to run correctly. I have followed many tutorials but most notably was:
[http://ubuntuforums.org/showthread.php?t=1507793&page=3](http://ubuntuforums.org/showthread.php?t=1507793&page=3)
lsmod shows that rt3572sta is loaded.
network manager in gnome is able to find my router.
my problem occurs when it tries to connect to the router using wpa2 security.
It continually asks for the wireless password then will freeze the system after a number of attempts.
After digging in for a bit, I was able to dig out a dmesg trapping the error:

BUG: unable to handle kernel paging request at ffffcfb0138af1ec
IP: [<ffffffffa021c7e8>] Cntl0idRTBssidProc+0x78/0x570 [rt3572sta]
PGD 0
Oops: 0000 [#1] SMP
last sysfs file: /sys/devices/system/cpu/cpu7/cache/index2/shared_cpu_map
CPU 2

I really don't see the need to continue on with those error messages

lsmod still shows rt3572sta after the failure.

In case anyone wants to see the changes I have made to the files before the make, I have included them. but changed the extension to "txt" to accommodate the up-loader and my rt_linux is too big to fit here, just not that it was 2 lines that were changed to work with the kernel.

If anyone wants to know what I mean by the system freezes, I do mean just that. The mouse will continue to work, but I am then unable to open any programs, unable to reboot the computer. it requires a hard reset.

I have uninstalled the drivers, installed them, make them, make install them, make clean, start from scratch a few times, and am getting no give here. 

Any help would be appreciated.


Sorry, no help here, but a fellow sufferer. I have the same situation, it built fine, module is loaded, can see networks -- but can't connect to them.  

I'm thinking that it's possibly because I'm on a 64 bit machine.  It's notable that when I took it to work and set it up on windows 7, the blue "cisco" light comes on.  That doesn't happen on my Ubuntu 10.04.2 64 bit machine (2.6.32-29 Kernel).

---

### Post by jokerhero9 on 2011-03-11
Waydaws: you can make the light work in the config.mk file:
  HAS_LED_CONTROL_SUPPORT=y
mine does light up when I enable that setting, but still haven't found a way around the kernel panic.

I also have gone through and upgraded my kernel to 2.6.37.3 and am still having the exact same issue.

---

### Post by ericrichards420 on 2011-03-11
follow this step by step [http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000](http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000)

---

### Post by jokerhero9 on 2011-03-11
well it seems that the drivers from ralink just do not work for this card.

the zip file from[ this]("http://ubuntuforums.org/showthread.php?t=1701471&highlight=linksys+ae1000") post does work and I did a quick diff and it seems a lot of files are changed or replaced with very few similarities. Just get the .zip file and do the normal steps required to get a good compile.

---

### Post by ericrichards420 on 2011-03-11
yeah the drivers from that post are good, its what I'm using on both ubuntu and xubuntu

---

### Post by ugmoe2000 on 2011-07-23
It could be the VERSION of the drivers you're running... In my experience the newest version of the 3572 drivers don't function correctly on 64-bit machines. Follow the write-up I wrote --> [http://confignewton.com/?p=104](http://confignewton.com/?p=104)

---

