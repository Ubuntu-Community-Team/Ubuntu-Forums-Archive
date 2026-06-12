---
title: "Help with an old wireless card"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by kenshen on 2012-03-13
Hey i need some help with an old wireless card zonnet zew 1602a i cant get it to work i use ubuntu 12 beta ndiswrapper -l gives WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
mrv8335 : driver installed
    device (11AB:1FAA) present
as well dmesg gives 

[  362.282706] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  362.375900] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  362.375905] ndiswrapper (load_sys_files:199): couldn't prepare driver 'mrv8335'
[  362.376201] ndiswrapper (load_wrap_driver:102): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[  362.376282] usbcore: registered new interface driver ndiswrapper
[ 3567.808032] Modules linked in: binfmt_misc ndiswrapper(O) parport_pc ppdev vesafb snd_hda_codec_hdmi rfcomm snd_hda_codec_analog bnep bluetooth nvidia(P) snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm snd_hwdep snd_usbmidi_lib snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq joydev snd_timer snd_seq_device uvcvideo videodev v4l2_compat_ioctl32 asus_atk0110 snd mac_hid soundcore snd_page_alloc lp parport hid_microsoft firewire_ohci firewire_core usbhid hid skge crc_itu_t pata_jmicron sky2

help please...

---

### Post by kenshen on 2012-03-13
Help?

---

### Post by bkratz on 2012-03-14
> **kenshen said:**
> Help?


This suggests the wrong driver, and that you used the 32 bit version and should have used the 64 bit (bad magic is not good!)

```
[  362.375900] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

```

---

### Post by kenshen on 2012-03-14
Whoops wrong log i redid it with the current driver here it is 
[    8.748058] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.273116] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[    9.273123] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[    9.273128] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    9.273133] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    9.273137] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[    9.273142] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    9.273147] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    9.273151] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    9.273156] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    9.273163] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    9.273168] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[    9.273173] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    9.273184] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    9.273188] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    9.273200] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[    9.273205] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[    9.273211] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[    9.273220] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[    9.273228] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[    9.273233] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[    9.273238] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[    9.273243] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    9.273250] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    9.273254] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    9.273259] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    9.273263] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[    9.273267] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netmw13c'
[    9.273620] ndiswrapper (load_wrap_driver:102): couldn't load driver netmw13c; check system log for messages from 'loadndisdriver'
[    9.276244] usbcore: registered new interface driver ndiswrapper

---

### Post by kenshen on 2012-03-14
bump?

---

### Post by kenshen on 2012-03-14
so after awhile i did an lspci and i found out my card is a mrv8k or Marvell Libertas Wireless Card following this guide [https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k) i disabled the bad driver and reinstalled my 64bit win xp driver same problem any one? heres the new dmesg [    9.800274] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   10.132331] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   10.132398] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   10.132403] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   10.132408] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   10.132413] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   10.132418] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   10.132422] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   10.132427] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   10.132432] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   10.132440] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   10.132445] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   10.132449] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   10.132461] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   10.132466] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   10.132537] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   10.132542] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   10.132549] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   10.132559] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   10.132568] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   10.132572] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   10.132577] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   10.132583] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   10.132590] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   10.132595] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   10.132600] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   10.132604] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   10.132667] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netmw13c'
[   10.133240] ndiswrapper (load_wrap_driver:102): couldn't load driver netmw13c; check system log for messages from 'loadndisdriver'
[   10.134691] usbcore: registered new interface driver ndiswrapper

---

### Post by praseodym on 2012-03-14
Check:

```
cat /etc/modules.conf
cat /etc/modprobe.d/ndiswrapper.conf
ndiswrapper -l
cd /etc/modprobe.d/
ls -l
```

---

### Post by kenshen on 2012-03-14
cat: /etc/modprobe.d/ndiswrapper.conf: No such file or directory

---

### Post by kenshen on 2012-03-14
ls -l
total 44
-rw-r--r-- 1 root root 2507 Feb 15 20:03 alsa-base.conf
-rw-r--r-- 1 root root  132 Mar 13 17:48 blacklist
-rw-r--r-- 1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1619 Mar 14 10:49 blacklist.conf
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20 10:44 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 15 20:03 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Mar 13 16:31 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root  127 Mar  1 13:29 dkms.conf
-rw-r--r-- 1 root root  157 Feb 18 02:46 nvidia-current_hybrid.conf
lrwxrwxrwx 1 root root   49 Mar 13 16:49 nvidia-graphics-drivers.conf -> /etc/alternatives/x86_64-linux-gnu_nvidia_modconf

---

### Post by praseodym on 2012-03-14
> -rw-r--r-- 1 root root 132 Mar 13 17:48 blacklist
What a file is that?

```
cat /etc/modprobe.d/blacklist
```
? (without ".conf"!) Was there an output for "modules.conf"?

---

### Post by kenshen on 2012-03-14
> **praseodym said:**
> What a file is that?

```
cat /etc/modprobe.d/blacklist
```
? (without ".conf"!) Was there an output for "modules.conf"?

cat /etc/modules.conf
alias wlan0 ndiswrapper

---

### Post by praseodym on 2012-03-14
Try

> sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf

---

### Post by kenshen on 2012-03-14
kinda came for a sec till i restarted my computer forcefully it was running slow dmesg | grep -e ndis -e wlan gives me

[    9.908643] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   10.029167] ndiswrapper: driver netmw126 (Marvell,12/30/2005,3.2.3.2) loaded
[   10.030027] ndiswrapper 0000:05:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   10.031934] ndiswrapper: using IRQ 23
[   10.128563] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   10.128571] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   10.128581] ndiswrapper (mp_halt:254): device ffff880036564780 is not initialized - not halting
[   10.128583] ndiswrapper: device eth%d removed
[   10.128601] ndiswrapper 0000:05:02.0: PCI INT A disabled
[   10.128642] ndiswrapper: probe of 0000:05:02.0 failed with error -22
[   10.238408] usbcore: registered new interface driver ndiswrapper
[   17.459537] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead

---

### Post by kenshen on 2012-03-14
restarting fixed it

---

### Post by praseodym on 2012-03-15
:popcorn::guitar:

---

