---
title: "Unable to compile RT3090 /ralink driver"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by mma8x on 2013-03-02
Ok, so I have the following:

```
mythuser@MythBox:~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:40:be:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-26-generic firmware=0.34 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbef0000-fbefffff
  *-network

```

I am suffering with the low d/l speeds and erratic disconnects with the native rt2800pci driver.  I'm running kernel 3.5.0-26, but have also tried the latest mainline 3.8.x kernel.  It actually isn't unbearable, and when d/l from the internet I approach my 25 Mbps throttle (although I haven't tried for prolonged periods).  Since this is meant to be a media server though, I need higher speeds on my home network.  I've tried a couple of ppa's with the ralink rt3090sta driver, but I get "link not ready" errors and am unable to connect.  I'm trying to compile the rt3090sta driver myself, but keep error'ing out.

```
ythuser@MythBox:~/RT3090$ sudo make
make -C tools
make[1]: Entering directory `/home/mythuser/RT3090/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/mythuser/RT3090/tools'
/home/mythuser/RT3090/tools/bin2h
cp -f os/linux/Makefile.6 /home/mythuser/RT3090/os/linux/Makefile
make -C /lib/modules/3.5.0-26-generic/build SUBDIRS=/home/mythuser/RT3090/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/crypt_md5.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/crypt_aes.o
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1408 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1408 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1616 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/mythuser/RT3090/os/linux/../../common/crypt_aes.c:2348:1: warning: the frame size of 1152 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/mlme.o
/home/mythuser/RT3090/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/mythuser/RT3090/os/linux/../../common/mlme.c:870:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/mythuser/RT3090/os/linux/../../common/mlme.c:870:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/mythuser/RT3090/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/mythuser/RT3090/os/linux/../../common/mlme.c:5822:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/mythuser/RT3090/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/mythuser/RT3090/os/linux/../../common/mlme.c:6183:1: warning: the frame size of 1744 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_wep.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/action.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_data.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rtmp_init.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_aes.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_sync.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/eeprom.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_info.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/dfs.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/spectrum.o
/home/mythuser/RT3090/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/mythuser/RT3090/os/linux/../../common/spectrum.c:1966:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rt_channel.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_profile.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_asic.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/assoc.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/auth.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/sync.o
/home/mythuser/RT3090/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/mythuser/RT3090/os/linux/../../sta/sync.c:1085:1: warning: the frame size of 1328 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/mythuser/RT3090/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/mythuser/RT3090/os/linux/../../sta/sync.c:755:1: warning: the frame size of 1296 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/mythuser/RT3090/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/mythuser/RT3090/os/linux/../../sta/sync.c:1756:1: warning: the frame size of 1392 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/sanity.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/connect.o
/home/mythuser/RT3090/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/mythuser/RT3090/os/linux/../../sta/connect.c:314:1: warning: the frame size of 1776 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/wpa.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/ags.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/ba_action.o
/home/mythuser/RT3090/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/mythuser/RT3090/os/linux/../../common/ba_action.c:1568:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/ee_prom.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/ee_efuse.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.o
/home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicLoadFirmware’:
/home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.c:352:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.c:355:2: warning: passing argument 1 of ‘writel’ makes integer from pointer without a cast [enabled by default]
In file included from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/realmode.h:5:0,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/acpi.h:32,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/fixmap.h:19,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/apic.h:12,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/smp.h:13,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/mmzone_64.h:10,
                 from /usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/mmzone.h:4,
                 from include/linux/mmzone.h:866,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/mythuser/RT3090/include/os/rt_linux.h:31,
                 from /home/mythuser/RT3090/include/rtmp_os.h:32,
                 from /home/mythuser/RT3090/include/rt_config.h:62,
                 from /home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.c:28:
/usr/src/linux-headers-3.5.0-26-generic/arch/x86/include/asm/io.h:63:1: note: expected ‘unsigned int’ but argument is of type ‘ULONG *’
/home/mythuser/RT3090/os/linux/../../common/rtmp_mcu.c:356:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
  CC [M]  /home/mythuser/RT3090/os/linux/../../chips/rt30xx.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../common/rt_rf.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../chips/rt3090.o
  CC [M]  /home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.o
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:679:2: warning: ‘enum tx_power_setting’ declared inside parameter list [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:679:2: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:678:29: error: parameter 2 (‘Type’) has incomplete type
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:676:12: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1355:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1355:2: warning: (near initialization for ‘CFG80211_Ops.set_channel’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1378:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1378:2: warning: (near initialization for ‘CFG80211_Ops.add_key’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1379:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1379:2: warning: (near initialization for ‘CFG80211_Ops.get_key’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1380:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1380:2: warning: (near initialization for ‘CFG80211_Ops.del_key’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1381:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1381:2: warning: (near initialization for ‘CFG80211_Ops.set_default_key’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1388:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:1388:2: warning: (near initialization for ‘CFG80211_Ops.rfkill_poll’) [enabled by default]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c: In function ‘CFG80211_Scaning’:
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:2062:2: error: too few arguments to function ‘ieee80211_channel_to_frequency’
In file included from include/net/mac80211.h:21:0,
                 from /home/mythuser/RT3090/include/os/rt_linux.h:82,
                 from /home/mythuser/RT3090/include/rtmp_os.h:32,
                 from /home/mythuser/RT3090/include/rt_config.h:62,
                 from /home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:28:
include/net/cfg80211.h:2366:12: note: declared here
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c: In function ‘CFG80211_SupBandInit’:
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:2594:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:2622:3: error: too few arguments to function ‘ieee80211_channel_to_frequency’
In file included from include/net/mac80211.h:21:0,
                 from /home/mythuser/RT3090/include/os/rt_linux.h:82,
                 from /home/mythuser/RT3090/include/rtmp_os.h:32,
                 from /home/mythuser/RT3090/include/rt_config.h:62,
                 from /home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.c:28:
include/net/cfg80211.h:2366:12: note: declared here
make[2]: *** [/home/mythuser/RT3090/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/mythuser/RT3090/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make: *** [LINUX] Error 2

```

Just about to give up here...

---

### Post by praseodym on 2013-03-02
Try the driver rt3290 from the Ralink-homepage. Do not forget to copy the firmware **~/DPO_RT3290_LinuxSTA_V2600_20120508/common/rt3290.bin** to **/lib/firmware**

---

### Post by mma8x on 2013-03-02
Yeah, I had tried that earlier (forgot about the firmware though).  Also tried with the 2860 driver.  Forgot what happened with 2860, but rt3290sta gives me nothing from dmesg, and I don't have wlan0 listed as an available interface.

---

### Post by praseodym on 2013-03-02
Is there a "ra0" interface?

---

### Post by mma8x on 2013-03-02
no, only lo and eth0.  Like i said, no dmesg output.  it doesn't look like the driver is recognizing the card.  is using the 3290 driver known to work with the 3090 card?

---

### Post by praseodym on 2013-03-02
Did you manipulate the file **/os/linux/config.mk** before compiling? Check here:

[http://wiki.ubuntuusers.de/wlan/ralink#RT28xx](http://wiki.ubuntuusers.de/wlan/ralink#RT28xx)
```

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

---

### Post by mma8x on 2013-03-02
Yup.

---

### Post by aliqasemi on 2013-07-03
this increased my wireless spead by a factor of at least 5, compared to the default rt2800 driver in Ubuntu 12.04, I was leaving with the slow driver for more than a year now, thank you very much.

---

