---
title: "unstable WLAN on HP 650 notebook (with driver rt2800pci)"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by MojoDodo on 2012-11-27
Hello,

the wireless network connection of my HP 650 notebook is very unstable. I'm using Ubuntu 12.10 but the network was unstable as well with 12.04 (and even with the preinstalled SUSE Linux Enterprise 11).

Here's some useful information about my system (I hope):
```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Lagidium-viscacia 1] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        84:4B:F5:1A:3C:D0

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

``````
lsmod | grep rt2800pci
rt2800pci              18152  0 
rt2800lib              57144  1 rt2800pci
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48562  3 rt2800pci,rt2800lib,rt2x00pci
eeprom_93cx6           13134  1 rt2800pci
``````
test@test-HP-650-Notebook-PC:~$ sudo lshw -C network
[sudo] password for test: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: b4:b5:2f:30:a2:35
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:92404000-92404fff memory:92400000-92403fff
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 84:4b:f5:1a:3c:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-17-generic firmware=0.34 ip=192.168.1.91 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:92500000-9250ffff
```I followed the instructions of this tutorial ([http://michael-peeters.blogspot.de/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html](http://michael-peeters.blogspot.de/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html)) until I get some problems at step 5 (dowloaded the drive here: [http://www.ralinktech.com/en/04_support/license.php?sn=5018](http://www.ralinktech.com/en/04_support/license.php?sn=5018)). 

```
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./os/linux/config.mk 
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./common/cmm_wpa.c
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1368 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1368 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/mlme.c:5547:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:1473:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:603:1: warning: the frame size of 1284 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/uaccess.h:584:0,
                 from /usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:362,
                 from /usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/os/rt_linux.h:49,
                 from /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_os.h:42,
                 from /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rt_config.h:72,
                 from /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:40:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:3063:28:
/usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:3540:28:
/usr/src/linux-headers-3.5.0-17-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:5839:1: warning: the frame size of 1372 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/sta_ioctl.c:6038:1: warning: the frame size of 1348 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1698:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_linux.c:1735:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_main_dev.c:120:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/ba_action.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:37:13: warning: unused variable ‘num’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:120:16: warning: unused variable ‘IrqFlags’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:119:16: warning: unused variable ‘pPacket’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:118:15: warning: unused variable ‘pTxD’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:117:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:116:19: warning: unused variable ‘j’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:116:6: warning: unused variable ‘index’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:448:11: warning: unused variable ‘BufBaseVa’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:447:11: warning: unused variable ‘BufBasePaLow’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:446:11: warning: unused variable ‘BufBasePaHigh’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:433:15: warning: unused variable ‘pPacket’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:432:15: warning: unused variable ‘pDmaBuf’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:431:16: warning: unused variable ‘pTxRing’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:429:14: warning: unused variable ‘pRxD’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:428:14: warning: unused variable ‘pTxD’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:426:10: warning: unused variable ‘RingBaseVa’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:425:10: warning: unused variable ‘RingBasePaLow’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:424:10: warning: unused variable ‘RingBasePaHigh’ [-Wunused-variable]
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_mac_pci.c:490:4: warning: ‘index’ may be used uninitialized in this function [-Wuninitialized]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_rbus_pci_util.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_rbus_pci_util.c: In function ‘RTMP_AllocateRxPacketBuffer’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/rt_rbus_pci_util.c:166:22: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.o
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../os/linux/pci_main_dev.c:322:13: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  LD [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.mod.o
  LD [M]  /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make install
make -C /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.5.0-17-generic
make[1]: Leaving directory `/home/test/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo ifconfig wlan0 down 
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo rmmod rt2860sta
ERROR: Module rt2860sta does not exist in /proc/modules
```I don't understand why this error in the last line occures:

```
test@test-HP-650-Notebook-PC:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo rmmod rt2860sta
ERROR: Module rt2860sta does not exist in /proc/modules
```Has anybody an idea what to do? I really need to get the wireless connection running.

Thanks for your suggestions in advance!

---

### Post by NYXEL on 2012-12-01
BUMP, 
Same problem here, anyone with any tip to resolve this issue?

I also tried two another USB wlan cards and the issue was stiil same, wlan connection is slowing down in the time and even through i have succifient signal, after some time it begins to drop pings and lost connection .... but - wifi icion is still measuring signal and saying to me that i am connected. Weird :-/
At first i was suspecting my wifi router, TPLINK TL-WR1043ND, but my another W7 HP's lap. connection was OK, as well as connection on my seven-years-old ubuntu 12.04 running HP lap. with i2200 wlan was OK. 
I simply checked both laptops at the time when the connection at HP650 was lost.   

So, i think its WPA / firmware / driver / kernel issue on this HW, but, i dont know how i can prove it :-/
 
I plan to borrow & try different pci express wlan card. We wiil see :-)


I will appreciate any tip pointing me to resolve this issue.

---

### Post by NikitaUbunt on 2013-01-17
0     down vote         
                           I own an HP650 which came with preinstalled SUSE Linux Enterprise Novell.
  The wireless card on this laptop is the Ralink 539a. The  driver/module for this wlan card loaded by the kernel is the rt2800pci.  The problem ofcourse is that by default they do not work or if they work  its unstable and practicly unusable. After reading many threads and  following a lot of different lines to build the  2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO the result was never  successful failing either at the build with >make returning an error  for Antenna being changed to y for yes or the driver not starting the  wlan0 interface if the Antenna switch remains n for off.
  Later I found a bug report and exchange specificly for the Ralink  539a where the solution to the problem was finallzy found. Essentially  
1. Download latest Compat-Wireless drivers from [http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases)  
2. Unpack to a directory 
3. cd to directory 
4. sudo make 
5. sudo make  install 
6 reboot your computer 
7. make sure the wireless card light/led  is on by using the wireless on/off button....
  That did it for me. A note I also read is that any time the kernel or  drivers are updated the old rt2800pci driver/module gets unpacked and  thus the wireless gets back to not working .... So the same procedure of  make and make install to overwrite with the compat-wireless drivers  that work is to be done...
  Good luck

---

### Post by bjacques on 2013-06-14
> **MojoDodo said:**
> Hello,

the wireless network connection of my HP 650 notebook is very unstable. I'm using Ubuntu 12.10 but the network was unstable as well with 12.04 (and even with the preinstalled SUSE Linux Enterprise 11).


I have the same problem on my HP 650 (Pentium 2020M) that was shipped with Ubuntu by HP. After an hour or two the wireless disconnects from my network, and won't reconnect, until wireless networking is toggled off and on.

Dmesg shows that I have a rt3290, supported with driver rt2x00.

It may be of use to you to know that **Fedora 19 beta** (you can try a livecd/usb) does not exhibit the instability.

I find it curious that although this machine is certified by Canonical, and OEM-installed by HP, no one seems to have thoroughly tested the wireless connectivity.

---

### Post by cssvb94 on 2013-11-11
Hi,

Had the same problem for 3 days trying different solutions.
None of it worked or was unstable.
That happened after upgrading to Ubuntu 13.10.
At the end I just downloaded the vanilla 13.12 kernel from kernel.org, unpacked it to /usr/src and created dpkgs without modifying or patching anything.
Guess what - it worked as charm!
That actually cost me money, because in my most despaired time during this period I gave up once and went to the computer shop and bought tp-link usb wifi dongle with atheros chipset (ath9k), which also didn't work.
Well, after installing the brand new and shiny 13.12 kernel, crossing fingers and reboot - EVERYTHING worked as expected, I mean everything - wifi, bluetooth, ethernet lan, wifi usb dongle.
No more binary blobs required, no patching and praying.
I decided to put that kernel as held with aptitude to prevent future problems, but still able to update the system.
Hope this will help somebody.

---

