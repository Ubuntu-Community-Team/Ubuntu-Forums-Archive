---
title: "No Wireless on Ubuntu 10.10"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by insanekat on 2011-04-27
Hello,
Just got a new HP Pavilion g series laptop and dual booted Ubuntu 10.10 and Windows 7. However, on Ubuntu 10.10 I cannot get wireless. Wireless router is a Linksys WRT54G, works fine with my current computer also running Ubuntu 10.10

Wireless button won't turn on/activate, but all is fine in Windows 7.

Tried the various troubleshooting articles, Google searches, other forum posts with no luck. This includes the rfkill as well as the b43 removal bcmwl installation options.

Really not too sure where to go from here so any help is greatly appreciated.

---

### Post by chili555 on 2011-04-27
Chili the Jedi is going to attempt to jump all the way to the end in one or two posts. Please open Applications > Accessories > Terminal and run and post:```
rfkill list all
sudo rmmod -f hp-wmi
sudo rfkill unblock all
```Any improvement?

---

### Post by josephmills on 2011-04-27
> **chili555 said:**
> Chili the Jedi is going to attempt to jump all the way to the end in one or two posts. Please open Applications > Accessories > Terminal and run and post:```
rfkill list all
sudo rmmod -f hp-wmi
sudo rfkill unblock all
```Any improvement?

I look forward to see it

---

### Post by insanekat on 2011-04-27
> 1: hp-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
Nothing, except for now pushing my wireless button turns my bluetooth on and off...

---

### Post by chili555 on 2011-04-27
Hey, I took a shot...now let's do it the hard way. Please post:```
lspci -nn
```Feel free to strip away all the lines that are obviously not a wireless card.

---

### Post by josephmills on 2011-04-27
take out all ipaddress and hw address lets see a ```
sudo lshw -C network
```

---

### Post by insanekat on 2011-04-27
```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
03:00.0 Network controller [0280]: RaLink Device [1814:539f]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

```

---

### Post by insanekat on 2011-04-27
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 64:31:50:8a:ef:7e
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f020ffff

```

---

### Post by chili555 on 2011-04-27
> Network controller [0280]: RaLink Device [1814:539f]This is the very new rt5390. It's so new that no native built-in driver exists. Here is most of the procedure:  [http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

You can safely ignore the 64-bit part; it should work equally well in 32-bit. Before you start, hook up the ethernet cable and do:```
sudo apt-get install linux-headers-generic build-essential
```This is a fairly advanced process, but if you follow each step carefully, you should be successful. josephmills and I have subscribed to the thread, so, if you get stuck, shout and we'll help you.

---

### Post by insanekat on 2011-04-27
Thank you very much for your time in helping me! GREATLY appreciated! I will give that a try right now.

---

### Post by chili555 on 2011-04-27
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

The 5390 is the second item from the top. You should be able to right-click it and select 'Extract Here.'

---

### Post by insanekat on 2011-04-27
I followed the steps from that thread and it appeared to go through fine, however still no wireless. The r5390sta is showing up in my Additional Drivers though, so it did something...

---

### Post by josephmills on 2011-04-27
> **insanekat said:**
> I followed the steps from that thread and it appeared to go through fine, however still no wireless. The r5390sta is showing up in my Additional Drivers though, so it did something...

did you activate it?

---

### Post by chili555 on 2011-04-27
> **insanekat said:**
> I followed the steps from that thread and it appeared to go through fine, however still no wireless. The r5390sta is showing up in my Additional Drivers though, so it did something...Please do:```
sudo modprobe r5390sta
dmesg | grep 539
iwconfig
```We're close!

---

### Post by insanekat on 2011-04-28
At "sudo modprobe r5390sta"

I get:

```
FATAL: r5390sta not found
```

---

### Post by josephmills on 2011-04-28
could we see 
```

dmesg | grep 539

```
Thanks

---

### Post by insanekat on 2011-04-28
```
[    0.000000]   HighMem zone: 5391 pages used for memmap
[    0.353967] ACPI: EC: Look up EC in DSDT
[   10.446367] rt5390sta: disagrees about version of symbol cfg80211_scan_done
[   10.446374] rt5390sta: Unknown symbol cfg80211_scan_done (err -22)
[   10.446485] rt5390sta: disagrees about version of symbol cfg80211_scan_done
[   10.446492] rt5390sta: Unknown symbol cfg80211_scan_done (err -22)
[   10.447228] rt5390sta: disagrees about version of symbol regulatory_hint
[   10.447231] rt5390sta: Unknown symbol regulatory_hint (err -22)
[   10.447329] rt5390sta: disagrees about version of symbol regulatory_hint
[   10.447333] rt5390sta: Unknown symbol regulatory_hint (err -22)
[   10.447891] rt5390sta: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   10.447895] rt5390sta: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   10.447988] rt5390sta: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   10.447991] rt5390sta: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   10.448113] rt5390sta: disagrees about version of symbol wiphy_register
[   10.448116] rt5390sta: Unknown symbol wiphy_register (err -22)
[   10.448216] rt5390sta: disagrees about version of symbol wiphy_register
[   10.448219] rt5390sta: Unknown symbol wiphy_register (err -22)
[   10.448384] rt5390sta: disagrees about version of symbol wiphy_new
[   10.448387] rt5390sta: Unknown symbol wiphy_new (err -22)
[   10.448480] rt5390sta: disagrees about version of symbol wiphy_new
[   10.448483] rt5390sta: Unknown symbol wiphy_new (err -22)
[   10.449313] rt5390sta: disagrees about version of symbol wiphy_rfkill_stop_polling
[   10.449316] rt5390sta: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[   10.449571] rt5390sta: disagrees about version of symbol wiphy_rfkill_stop_polling
[   10.449574] rt5390sta: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[   10.449901] rt5390sta: disagrees about version of symbol cfg80211_connect_result
[   10.449904] rt5390sta: Unknown symbol cfg80211_connect_result (err -22)
[   10.450142] rt5390sta: disagrees about version of symbol cfg80211_connect_result
[   10.450146] rt5390sta: Unknown symbol cfg80211_connect_result (err -22)
[   10.450659] rt5390sta: disagrees about version of symbol wiphy_unregister
[   10.450662] rt5390sta: Unknown symbol wiphy_unregister (err -22)
[   10.450917] rt5390sta: disagrees about version of symbol wiphy_unregister
[   10.450920] rt5390sta: Unknown symbol wiphy_unregister (err -22)
[   10.451799] rt5390sta: disagrees about version of symbol wiphy_rfkill_start_polling
[   10.451802] rt5390sta: Unknown symbol wiphy_rfkill_start_polling (err -22)
[   10.452211] rt5390sta: disagrees about version of symbol wiphy_rfkill_start_polling
[   10.452214] rt5390sta: Unknown symbol wiphy_rfkill_start_polling (err -22)
[   10.452993] rt5390sta: disagrees about version of symbol cfg80211_inform_bss_frame
[   10.452996] rt5390sta: Unknown symbol cfg80211_inform_bss_frame (err -22)
[   10.453546] rt5390sta: disagrees about version of symbol cfg80211_inform_bss_frame
[   10.453549] rt5390sta: Unknown symbol cfg80211_inform_bss_frame (err -22)
[   10.453828] rt5390sta: disagrees about version of symbol wiphy_free
[   10.453831] rt5390sta: Unknown symbol wiphy_free (err -22)
[   10.454211] rt5390sta: disagrees about version of symbol wiphy_free
[   10.454213] rt5390sta: Unknown symbol wiphy_free (err -22)
[   16.539340] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

---

### Post by chili555 on 2011-04-28
Let's see:```
sudo modprobe rt5390sta
iwconfig
```Thanks.

---

### Post by insanekat on 2011-04-28
```
~$ sudo modprobe rt5390sta

FATAL: Error inserting rt5390sta (/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt5390sta.ko): Invalid argument

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by chili555 on 2011-04-28
That suggests that the compile did not go at all well. Please redo:```
cd Downloads/2010wherever
sudo su
make clean
make
exit
```Note any errors and post them here.

---

### Post by insanekat on 2011-04-28
The first make I did seemed fine but still nothing after a restart, so I tried again and then it came up with:

```
/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make

make -C tools
make[1]: Entering directory `/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1356 bytes is larger than 1024 bytes
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1356 bytes is larger than 1024 bytes
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘InitLookupTable’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635: warning: missing braces around initializer
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635: warning: (near initialization for ‘WordStruct.field’)
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:6380: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/action.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c:1558: warning: unused variable ‘EfuseData’
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/spectrum.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.c: In function ‘RTMPSetProfileParameters’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.c:1436: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘ULONG’
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicSwitchChannel’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1243: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1384: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1392: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1403: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicAdjustTxPower’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4977: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4984: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4990: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5055: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5060: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5064: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5071: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5076: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5080: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5087: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5092: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5096: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1755: warning: the frame size of 1320 bytes is larger than 1024 bytes
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:755: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1085: warning: the frame size of 1304 bytes is larger than 1024 bytes
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:571: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c:314: warning: the frame size of 1756 bytes is larger than 1024 bytes
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.c: In function ‘Set_Antenna_Proc’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.c:1387: warning: ‘UsedAnt’ may be used uninitialized in this function
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c: In function ‘FrequencyCalibration’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:214: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:227: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:242: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:264: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:277: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:292: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:463: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:734: note: expected ‘u16 *’ but argument is of type ‘INT *’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:482: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:734: note: expected ‘u16 *’ but argument is of type ‘INT *’
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt33xx.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3390.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt5390.o
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:1802: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘ATEAsicSwitchChannel’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5076: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5230: warning: comparison of distinct pointer types lacks a cast
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5007: warning: unused variable ‘RFValue2’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5002: warning: unused variable ‘RFRegTable’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001: warning: unused variable ‘R4’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001: warning: unused variable ‘R3’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001: warning: unused variable ‘R2’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7564: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477: warning: unused variable ‘ChannelPower’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7649: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘GetPowerDeltaFromTssiRatio’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7801: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘LONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7830: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘LONG’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_READ_EXTERNAL_TSSI_Proc’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:8011: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7965: warning: unused variable ‘EEPTemp’
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7964: warning: ‘BbpData’ may be used uninitialized in this function
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘RTATEGetTssiByChannel’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7708: warning: ‘BbpData’ may be used uninitialized in this function
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7480: warning: ‘BBPR47’ may be used uninitialized in this function
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477: warning: ‘BbpData’ may be used uninitialized in this function
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7584: warning: ‘BbpData’ may be used uninitialized in this function
  CC [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.o
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c: In function ‘TxPowerDown’:
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:618: warning: ' ' flag used with ‘%p’ gnu_printf format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:618: warning: too few arguments for format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:627: warning: ' ' flag used with ‘%p’ gnu_printf format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:627: warning: too few arguments for format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:632: warning: ' ' flag used with ‘%p’ gnu_printf format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:632: warning: too few arguments for format
/home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/misc.c:636: warning: too few arguments for format
  LD [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
cp -f /home/kat/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/rt5390sta.ko /tftpboot

```

Thanks again for all your continued help! I really hope we can get this.

---

### Post by insanekat on 2011-04-28
Also, would upgrading to 11.04 help or hinder the process?

---

### Post by chili555 on 2011-04-28
> **insanekat said:**
> Also, would upgrading to 11.04 help or hinder the process?Hinder. I downloaded it and tried to compile it on my 11.04 machine and it errors out.

I'm studying all this now.

---

### Post by chili555 on 2011-04-28
I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system, from errored out to warnings but installs and modprobes without error. I don't have the device, so I don't know if it works properly. Let's try it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patches except the x64_86 patch (I assume you have installed a 32-bit system). Move them to your 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed!

---

### Post by insanekat on 2011-04-28
Yaaay it works!!! Thanks so much, that was amazing! Tons of good vibes to you! Thank you!

---

### Post by chili555 on 2011-04-28
Woo hoo! You will have helped the searchers, too. Would you please use the thread tools at the top to mark the thread Solved?

Have fun!

---

### Post by insanekat on 2011-04-28
If I upgrade to 11.04 do you think that'll mess it up?

---

### Post by chili555 on 2011-04-28
Probably not, except you'll have to recompile: sudo su, make clean, make, make install, modprobe rt5390sta, exit.

---

### Post by port86 on 2011-04-29
> **chili555 said:**
> I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system, from errored out to warnings but installs and modprobes without error. I don't have the device, so I don't know if it works properly. Let's try it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patches except the x64_86 patch (I assume you have installed a 32-bit system). Move them to your 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed!

Thank you for the excellent information. Problem solved!!

---

### Post by Psychs on 2011-04-29
> **chili555 said:**
> I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system, from errored out to warnings but installs and modprobes without error. I don't have the device, so I don't know if it works properly. Let's try it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patches except the x64_86 patch (I assume you have installed a 32-bit system). Move them to your 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed!


I tried the method. It does not work for me.

[LIST=1]
[*]I see the RT5390 driver in the 'add new drivers window' is active and in use.
[*]Network-manager shows wireless network is disabled (though it is enabled).
[*]ifconfig does not  wireless details.
[*]iwconfig shows wlan0 and details.
[/LIST]

---

### Post by chili555 on 2011-04-29
> I tried the method. It does not work for me.

    I see the RT5390 driver in the 'add new drivers window' is active and in use.
    Network-manager shows wireless network is disabled (though it is enabled).
    ifconfig does not wireless details.
    iwconfig shows wlan0 and details.
Please post:```
sudo iwlist wlan0 scan
rfkill list all
```Thanks.

---

### Post by seebs on 2011-04-29
I followed the instructions, including applying the patches from the SuSE version.  Driver builds okay.  Comes up totally dead and not working.

# iwlist wlan0 scan
wlan0     No scan results
# rfkill list all
0: hci0: Bluetooth
       Soft blocked: no
       Hard blocked: no

On modprobe rt5390sta, I get a bunch of error messages in dmesg:

# dmesg
[...]
[ 2571.584670] rt5390 0000:02:00.0: setting latency timer to 64
[ 2571.585245] <-- RTMPAllocAdapterBlock, Status=0
[ 2571.611602] KH: Use High Memory for Beacon
[ 2571.615789] <-- RTMPAllocTxRxRingMemory, Status=0
[ 2571.621606] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[ 2571.629104] KH: Use High Memory for Beacon
[ 2571.632907] <-- RTMPAllocTxRxRingMemory, Status=0
[ 2571.636397] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]

Under 10.x I was able to get the device to come up, as I recall.  I am using 11.x because I have slightly better luck getting the clickpad on my hp dm1 to ALMOST work there.  :)

---

### Post by seebs on 2011-04-29
UTSL reveals:  It's failing to read a config file.  Another thread had instructions which referred to a file named RT5390STA.dat.  Sure enough, the driver source installed one named RTA2860STA.dat, installed in a similarly-named directory.  Created the right directory, copied the file from a modified archive into that directory, reprobed the driver, and it comes up.

---

### Post by winchendonsprings on 2011-04-30
Worked for me as well.

Also I included -  rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch

Thanks a lot. Especially @chili555

Do you think that this driver will be included by default soon?

---

### Post by Psychs on 2011-04-30
> **chili555 said:**
> Please post:```
sudo iwlist wlan0 scan
rfkill list all
```Thanks.

Here are the results
```

$ sudo iwlist wlan0 scan
wlan0     No scan results

$ rfkill list all
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```One more thing to note is that the network-manager now says - wireless networks disconnected.

---

### Post by chili555 on 2011-04-30
> **Psychs said:**
> Here are the results
```

$ sudo iwlist wlan0 scan
wlan0     No scan results

$ rfkill list all
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```One more thing to note is that the network-manager now says - wireless networks disconnected.Let's have a look at:```
dmesg | grep 539
```Thanks.

---

### Post by Psychs on 2011-04-30
> **chili555 said:**
> Let's have a look at:```
dmesg | grep 539
```Thanks.

```
dmesg | grep 539
[    0.312223] pci 0000:02:00.0: [1814:539f] type 0 class 0x000280
[    1.305391] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.305398] EISA: Probing bus 0 at eisa.0
[   10.005111] rt5390 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.005190] rt5390 0000:02:00.0: setting latency timer to 64
[   14.691539] [fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
```

---

### Post by gilnear on 2011-05-19
I know this is two weeks old but I'd like to thank chili555 and seebs for all their hard work on this!

I have an HP DM1Z running Ubuntu 11.04. I had the same problems as others here: The drivers wouldn't compile until I applied the patches, then the card seemed unusable (iwconfig showed the device but nothing else would), and then I read seebs's post.. The RT5390STA.dat file was missing!

The final steps that worked for me:
```

cd /etc/Wireless
sudo su
mkdir RT5390STA
cp RT2860STA/RT2860STA.dat RT5390STA/RT5390STA.dat
rmmod RT5390STA
modprobe RT5390STA
exit

```

---

### Post by Psychs on 2011-05-20
> **gilnear said:**
> I know this is two weeks old but I'd like to thank chili555 and seebs for all their hard work on this!

I have an HP DM1Z running Ubuntu 11.04. I had the same problems as others here: The drivers wouldn't compile until I applied the patches, then the card seemed unusable (iwconfig showed the device but nothing else would), and then I read seebs's post.. The RT5390STA.dat file was missing!

The final steps that worked for me:
```

cd /etc/Wireless
sudo su
mkdir RT5390STA
cp RT2860STA/RT2860STA.dat RT5390STA/RT5390STA.dat
rmmod RT5390STA
modprobe RT5390STA
exit

```

Thanks **gilnear**. Actually **chilli555**'s post #24 has all the points that you have mentioned. I had done exactly what he has mentioned there. But even then wi-fi did not work. 

Later I made the change in the config.mk file as mentioned in the following post by **akshay.guleria@gmail.com**                 :
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

[LIST]
[*]*HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)*
[/LIST]
After this I followed the instructions given in post #24. 
Rebooted the computer and life is good now.

Thanks.

---

### Post by Tulip on 2011-06-06
> **chili555 said:**
> I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system, from errored out to warnings but installs and modprobes without error. I don't have the device, so I don't know if it works properly. Let's try it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patches except the x64_86 patch (I assume you have installed a 32-bit system). Move them to your 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed!

I can confirm this works on an Asus K73E and 11.04. Thank you for the help.

---

### Post by theswirlingparabol on 2011-06-20
> **Tulip said:**
> I can confirm this works on an Asus K73E and 11.04. Thank you for the help.
 
 
Hi, i'm pretty much a newbie to ubuntu, i've got the 5390 wireless card and i'm runnin 11.04 (64 bit).  I downloaded the drivers from ralink and the patches from opensuse.
 
when i try patch -p0 < rt5390sta-2.4.0.4-config.patch...or any other patch, i get a fail message.  they all fail to patch to config or makefile.  please help, i'm really stuck.

---

### Post by chili555 on 2011-06-20
> **theswirlingparabol said:**
> Hi, i'm pretty much a newbie to ubuntu, i've got the 5390 wireless card and i'm runnin 11.04 (64 bit).  I downloaded the drivers from ralink and the patches from opensuse.
 
when i try patch -p0 < rt5390sta-2.4.0.4-config.patch...or any other patch, i get a fail message.  they all fail to patch to config or makefile.  please help, i'm really stuck.In the terminal, did you change directories to the location of the patches and Makefile?```
cd Downloads/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
patch, etc.
```Substitute the location you downloaded the file you extracted; Downloads, Desktop, or wherever.

---

### Post by fishin4guitars on 2011-06-23
> **chili555 said:**
> In the terminal, did you change directories to the location of the patches and Makefile?```
cd Downloads/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
patch, etc.
```Substitute the location you downloaded the file you extracted; Downloads, Desktop, or wherever.

Don't forget to do 
```

patch -p0 < ../patch-name

```

---

### Post by Dafydd on 2011-07-26
> **chili555 said:**
> I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system, from errored out to warnings but installs and modprobes without error. I don't have the device, so I don't know if it works properly. Let's try it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patches except the x64_86 patch (I assume you have installed a 32-bit system). Move them to your 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed!

Thanks. This worked for me!

Cheers

Dafydd

---

### Post by insanekat on 2011-10-15
I just upgraded to 11.10 and no wireless again :( I tried following the steps as before but there were errors/it didn't work. You guys still there for help haha?

---

### Post by chili555 on 2011-10-16
@insanekat--

I just downloaded a fresh copy; i.e. not patched and the latest available version and it makes and installs with many warnings but no errors. I don't have the device, so I don't know if it connects.

Please try so we'll know.

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by insanekat on 2011-10-16
Used the instructions here again: [http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

There was no
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
in the config.mk file.

I tried make anyway and got:
```
make -C tools
make[1]: Entering directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/3.0.0-12-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2011-10-16
Do you have the linux-headers-generic and build-essential installed?

---

### Post by insanekat on 2011-10-17
Yep.

---

### Post by chili555 on 2011-10-17
Please post:```
uname -r
ls /lib/modules/`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by Oneiric N00b on 2011-10-17
I have the same problem, to me the message was 
```
cp -f /home/amy/Documents/wifi/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1

```


```
uname -r 
3.0.0-0300-generic
```
 and finally,
```
ls /lib/modules/`uname -r`

build   modules.alias      modules.builtin.bin  modules.dep.bin      modules.inputmap   modules.order     modules.softdep      modules.usbmap
initrd  modules.alias.bin  modules.ccwmap       modules.devname      modules.isapnpmap  modules.pcimap    modules.symbols      updates
kernel  modules.builtin    modules.dep          modules.ieee1394map  modules.ofmap      modules.seriomap  modules.symbols.bin

```

any idea??

---

### Post by chili555 on 2011-10-17
> **Oneiric N00b said:**
> I have the same problem, to me the message was 
```
cp -f /home/amy/Documents/wifi/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1

```


```
uname -r 
3.0.0-0300-generic
```
 and finally,
```
ls /lib/modules/`uname -r`

build   modules.alias      modules.builtin.bin  modules.dep.bin      modules.inputmap   modules.order     modules.softdep      modules.usbmap
initrd  modules.alias.bin  modules.ccwmap       modules.devname      modules.isapnpmap  modules.pcimap    modules.symbols      updates
kernel  modules.builtin    modules.dep          modules.ieee1394map  modules.ofmap      modules.seriomap  modules.symbols.bin

```

any idea??Sure. Precede your 'make' command with sudo su:```
sudo su
make clean
make
sudo make install
modprobe rt5390sta
exit
```

---

### Post by Oneiric N00b on 2011-10-17
I tried as you said but when I enable the wireless a black screen appears with several commands/lines and freeze all the activities of my computer, even the ethernet connection. I restarted it several times to make it even connect with ethernet.

---

### Post by Judson J on 2011-10-17
HI all, not sure if I have a similar problem as above. I have two laptops, Dell 1525 and Inspion 9100. Both have XP and 10.10 installed. 1525 connects wirelessy on both systems, howeverthe 9100 only connects wirelesly on XP. Something in the Network Manager is saying firmware missing, hardware not ready, but I dont know what, or where to look..
Any ideas?
thanks!

---

### Post by insanekat on 2011-10-17
```
3.0.0-12-generic-pae
```

```
initrd               modules.dep          modules.order
kernel               modules.dep.bin      modules.pcimap
modules.alias        modules.devname      modules.seriomap
modules.alias.bin    modules.ieee1394map  modules.softdep
modules.builtin      modules.inputmap     modules.symbols
modules.builtin.bin  modules.isapnpmap    modules.symbols.bin
modules.ccwmap       modules.ofmap        modules.usbmap

```

---

### Post by Judson J on 2011-10-18
Hi, thanks for the reply, but, not sure what to do what this? Type it into terminal? Entered the 1st line but command not found..
Thanks  all the same!

---

### Post by insanekat on 2011-10-18
> **Judson J said:**
> Hi, thanks for the reply, but, not sure what to do what this? Type it into terminal? Entered the 1st line but command not found..
Thanks  all the same!
Oh sorry, this was in response to the previous page, it was my output, not what you should input haha. Ignore my posts in relation to your problem! As I am also having trouble getting the wireless going...

---

### Post by chili555 on 2011-10-18
> **Judson J said:**
> HI all, not sure if I have a similar problem as above. I have two laptops, Dell 1525 and Inspion 9100. Both have XP and 10.10 installed. 1525 connects wirelessy on both systems, howeverthe 9100 only connects wirelesly on XP. Something in the Network Manager is saying firmware missing, hardware not ready, but I dont know what, or where to look..
Any ideas?
thanks!This thread is getting a bit long and there are several different wireless chipsets discussed. Some or none may be identical to yours! Please start your own new thread and run and post the result of this command in the terminal:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Leave a link to your new thread here and I'll respond as soon as I can.

---

### Post by chili555 on 2011-10-18
> **insanekat said:**
> ```
3.0.0-12-generic-pae
```

```
initrd               modules.dep          modules.order
kernel               modules.dep.bin      modules.pcimap
modules.alias        modules.devname      modules.seriomap
modules.alias.bin    modules.ieee1394map  modules.softdep
modules.builtin      modules.inputmap     modules.symbols
modules.builtin.bin  modules.isapnpmap    modules.symbols.bin
modules.ccwmap       modules.ofmap        modules.usbmap

```I still wonder if the appropriate linux-headers are correctly installed. Please post:```
ls /usr/src | grep `uname -r`
```

---

### Post by insanekat on 2011-10-19
Thank you again for your continued help chilli :) 

Okay so I put that into the terminal and literally nothing happens... That seems very not right! So looking in that folder, I have a bunch of other folders with various linux-headers-# and linux-headers-#-generic, where the #s are versions I'd assume. I have no idea what this means.

---

### Post by chili555 on 2011-10-19
It means that you do *not* have the linux-headers installed matching your running kernel version which are needed to do the compilation referred to in post #47.> uname -r 
3.0.0-0300-generic> ls /usr/src | grep `uname -r`> Okay so I put that into the terminal and literally nothing happens... That seems very not right! 'Literally nothing happens' means it doesn't exist, despite that you asserted that they *were* installed. Please get an ethernet connection and do:```
sudo apt-get install linux-headers-generic linux-headers-`uname -r`
```Then try the compile again.

---

### Post by insanekat on 2011-10-19
I apologize, earlier I did run the installation and it told me they were already installed. They also showed up as installed in Synaptic. Guess I messed up, sorry to waste your time.

Okay, still nothing:

```
root@kat-HP-Pavilion-g6-Notebook-PC:/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf os/linux/Makefile
root@kat-HP-Pavilion-g6-Notebook-PC:/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make
make -C tools
make[1]: Entering directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic-pae'
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/action.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicGetAutoAgcOffset’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:882:10: warning: unused variable ‘bTempSuccess’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:881:6: warning: unused variable ‘LookupTableIndex’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:880:6: warning: unused variable ‘CurrentTemp’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:879:8: warning: unused variable ‘BbpValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:878:32: warning: unused variable ‘pTxPowerTuningEntry2’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:875:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:874:32: warning: unused variable ‘pTxPowerTuningEntry’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicAdjustTxPower’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1575:16: warning: unused variable ‘flags’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1562:20: warning: unused variable ‘pFinalTxPwr’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1560:11: warning: unused variable ‘bAutoTxAgc’ [-Wunused-variable]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c: In function ‘LinkUp’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c:1446:35: warning: unused variable ‘pCurrEntry’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c:1445:28: warning: unused variable ‘HashIdx’ [-Wunused-variable]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
In file included from /usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/uaccess.h:570:0,
                 from /usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:351,
                 from /usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/os/rt_linux.h:40,
                 from /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_os.h:44,
                 from /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_comm.h:60,
                 from /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rt_config.h:33,
                 from /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:28:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:1709:28:
/usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.c:2189:28:
/usr/src/linux-headers-3.0.0-12-generic-pae/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c: In function ‘RtmpDrvPciMapSingle’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c:2420:60: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibration’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:202:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:215:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:230:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:136:10: warning: unused variable ‘bUpdateRFR’ [-Wunused-variable]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:481:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [enabled by default]
include/linux/pci.h:741:19: note: expected ‘u16 *’ but argument is of type ‘ULONG *’
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:500:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [enabled by default]
include/linux/pci.h:741:19: note: expected ‘u16 *’ but argument is of type ‘ULONG *’
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG’ [-Wformat]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.o
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.c: In function ‘NICInitRT3390RFRegisters’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.c:42:7: warning: unused variable ‘bbpreg’ [-Wunused-variable]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_Init’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:490:25: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390LoadRFSleepModeSetup’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:910:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390ReverseRFSleepModeSetup’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:986:8: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_ChipSwitchChannel’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1631:17: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1642:17: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1656:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1526:17: warning: unused variable ‘BbpR110’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1525:23: warning: unused variable ‘BbpR109’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘GetDesiredTssiAndCurrentTssi’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3120:2: warning: missing braces around initializer [-Wmissing-braces]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3120:2: warning: (near initialization for ‘htTssiInfo.PartA.field’) [-Wmissing-braces]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_ATETssiCalibration’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3391:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3480:4: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp.h:5742:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3392:42: warning: unused variable ‘ChannelPower’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘GetPowerDeltaFromTssiRatio’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3622:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘LONG’ [-Wformat]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3651:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘LONG’ [-Wformat]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_AsicResetBbpAgent’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3929:8: warning: unused variable ‘BBPValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3928:8: warning: unused variable ‘loop’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function ‘RT5390_ATETssiCalibration’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3446:16: warning: ‘BbpData’ may be used uninitialized in this function [-Wuninitialized]
  CC [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.o
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘DefaultATEAsicSwitchChannel’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1248:16: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1034:21: warning: unused variable ‘RFValue2’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:5162:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TX_FREQOFFSET_Proc’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:7623:13: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_EX_Proc’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9373:9: warning: unused variable ‘CurrentChannel’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9372:9: warning: unused variable ‘BSSID_ADDR’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9371:10: warning: unused variable ‘ChannelPower’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9370:10: warning: unused variable ‘EEPData’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369:31: warning: unused variable ‘TssiDeltaPerChannel’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369:8: warning: unused variable ‘TssiRefPerChannel’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:53: warning: unused variable ‘BBP49Value’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:42: warning: unused variable ‘RF28Value’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:31: warning: unused variable ‘RF27Value’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:22: warning: unused variable ‘RFValue’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:9: warning: unused variable ‘BbpData’ [-Wunused-variable]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9376:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9360:1: warning: control reaches end of non-void function [-Wreturn-type]
  LD [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  LD [M]  /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic-pae'
cp -f /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
root@kat-HP-Pavilion-g6-Notebook-PC:/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# sudo make install
make -C /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-12-generic-pae
make[1]: Leaving directory `/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
root@kat-HP-Pavilion-g6-Notebook-PC:/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# modprobe rt5390sta
root@kat-HP-Pavilion-g6-Notebook-PC:/home/kat/Documents/Linux/Wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# exit
exit

```

---

### Post by chili555 on 2011-10-19
No problem.

Lots of warnings but no error. Most importantly, does it work?

---

### Post by insanekat on 2011-10-19
Nope, still just turns my Bluetooth on or off.

---

### Post by chili555 on 2011-10-19
What??? Are you saying that when you modprobe rt5390sta it turns your bluetooth off?? Let's see:```
sudo modprobe rt5390sta
dmesg | grep 539
```Thanks.

---

### Post by insanekat on 2011-10-19
```
[    0.408160] pci 0000:03:00.0: [1814:539f] type 0 class 0x000280
[    0.456539] pnp 00:06: [io  0x0c6c]
[    0.495393] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[   14.589216] rt5390sta: module license 'unspecified' taints kernel.
[   14.589224] rt5390sta: module license 'unspecified' taints kernel.

```

I also tried again today and got:

```
[    0.408158] pci 0000:03:00.0: [1814:539f] type 0 class 0x000280
[    1.005393] thermal LNXTHERM:01: registered as thermal_zone1
[    1.005397] ACPI: Thermal Zone [TZ1] (0 C)
[   18.029833] rt5390sta: module license 'unspecified' taints kernel.

```

---

### Post by insanekat on 2011-10-24
OR
```
[    0.408158] pci 0000:03:00.0: [1814:539f] type 0 class 0x000280
[    0.456539] pnp 00:06: [io  0x0010-0x001f]
[    1.638539] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.704688] rt5390sta: module license 'unspecified' taints kernel.
[   33.665390] ata3.00: error: { UNC }

```

---

### Post by chili555 on 2011-10-24
Let's try a temporary experiment. Please do:```
sudo modprobe rt2800pci
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by insanekat on 2011-10-25
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

---

### Post by chili555 on 2011-10-25
> ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
Hmmmm, the interface ra0 would be created by a compiled Ralink module, not the built-in rt2800pci. In fact RT539x devices are now claimed by rt2800pci in Ubuntu 11.10. Let's dig a lot deeper. Please do:```
sudo rmmod -f rt5390sta
sudo modprobe rt2800pci
dmesg > insanekat.txt
lsmod >> insanekat.txt
rfkill list all >> insanekat.txt
zip insanekat.zip insanekat.txt
```You will find the file insanekat.zip in your user directory. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by insanekat on 2011-10-26
Attached. Also, when I run: 
```
sudo rmmod -f rt5390sta
sudo modprobe rt2800pci
```
My wireless button works. Good sign? However, if I restart the computer it goes back to how it was (won't turn on through the wireless button).

---

### Post by chili555 on 2011-10-26
Could you please let me see:```
md5sum /lib/firmware/rt2860.bin
```I am studying this but need to be away from my computer for a few hours: [http://lists.debian.org/debian-kernel/2011/02/msg00460.html](http://lists.debian.org/debian-kernel/2011/02/msg00460.html)> rt2800pci/ rt2800usb are fine, but the firmware images shipped as 
rt2860.bin (v11) and rt2870.bin (v12) in firmware-ralink appear to be 
too old for reliable operations, especially for rt30x0 (>> v17/ v19 
required) and rt35xx. Using the the plain versions shipped in 
firmware-ralink I notice the same problems, scanning works, even auth 
succeeds, but there is no actual traffic passing through. However 
updating rt2860.bin and rt2870.bin to the current versions offered by
RaLink at [http://www.ralink.com.tw/support.php?s=2:](http://www.ralink.com.tw/support.php?s=2:)
- Firmware RT28XX/RT30XX PCI/mPCI/PCIe/CardBus series 
  (RT2760/RT2790/RT2860/RT2890/RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790/RT3090)
  03/31/2010, v26
- Firmware RT28XX/RT30XX USB series (RT2870/RT2770/RT3572/RT3070)
  03/31/2010, v22
allows reliable operations using rt2800pci/ rt2800usb for me, both 
firmware images also work with plain 2.6.32 [1].More later.

---

### Post by insanekat on 2011-10-26
```
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin
```

---

### Post by chili555 on 2011-10-26
Download the firmware file I attached above to your desktop. Right-click it and select 'Extract Here.' Now open a terminal and do:```
sudo su
mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.old
cp Desktop/RT2860_Firmware_V26/rt2860.bin  /lib/firmware
rmmod -f rt2800pci
modprobe rt2800pci
dmesg | grep rt2
exit
```Have we resolved this complaint from previously?> [ 2401.287715] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareIf you have not rebooted the computer, you may still see the line from timestamp 2401.xx.

---

### Post by insanekat on 2011-10-26
```
[   20.596744] register rt2860
[   20.596806] rt2860 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.596863] rt2860 0000:03:00.0: setting latency timer to 64

```

---

### Post by chili555 on 2011-10-27
> **insanekat said:**
> ```
[   20.596744] register rt2860
[   20.596806] rt2860 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.596863] rt2860 0000:03:00.0: setting latency timer to 64

```That looks pretty solid, no errors or warnings are reported. Was a wireless interface wlan0 created?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Does it try to connect?

---

### Post by insanekat on 2011-10-27
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

```
wlan0     Interface doesn't support scanning.

```

---

### Post by insanekat on 2011-11-23
Long story short, I had to do a reinstall, and now it works. Thank you for the help though!

---

