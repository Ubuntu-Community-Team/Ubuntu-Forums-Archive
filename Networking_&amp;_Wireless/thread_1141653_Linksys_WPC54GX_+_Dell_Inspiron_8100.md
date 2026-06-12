---
title: "Linksys WPC54GX + Dell Inspiron 8100"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by tymbrwlf on 2009-04-28
I have a fresh install of Ubuntu 9.04 on an older Dell Inspiron 8100 Laptop. I have tried everything I can find to get my Linksys WPC54GX, v.2 wireless card (Airgo chipset) to work (ndiswrapper, linuxant, etc). I have been able to get Ubuntu to do everything I need this laptop to do EXCEPT get the wirelss working. This is now my only obstacle to making the switch to Linux on it.

Please help if possible.

ETA:
~$ lspci | grep 'Airgo'
0d:00.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)

~$ lspci -nn | grep 'Airgo'
0d:00.0 Ethernet controller [0200]: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 03)

~$ ifconfig
Does not list wireless connection; only eth0 and lo interfaces

~$ iwconfig
Again, "no wireless extensions" listed for the above two mentioned interfaces

~$~$ lsmod
Module                  Size  Used by
ndiswrapper           193436  0
isofs                  39844  0
udf                    87716  0
crc_itu_t              10112  1 udf
binfmt_misc            16776  1
input_polldev          11912  0
lp                     17156  0
pcmcia                 44748  0
ppdev                  15620  0
snd_maestro3           27268  3
snd_ac97_codec        112292  1 snd_maestro3
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  1 snd_pcm
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               19108  0
psmouse                61972  0
dcdbas                 15264  0
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13316  0
pcspkr                 10496  0
soundcore              15200  1 snd
nvidia               4712596  26
yenta_socket           32396  3
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 40212  0
video                  25360  0
output                 11008  1 video
parport_pc             40100  1
parport                42220  3 lp,ppdev,parport_pc
intel_agp              34108  1
agpgart                42696  2 nvidia,intel_agp
ohci1394               38576  0
ieee1394               94660  1 ohci1394
e100                   41740  0
mii                    13312  1 e100
floppy                 64324  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

I can provide more info if needed. I'm relatively new to linux so any help is greatly appreciated. This particular issue is just way beyond my knowledge

---

### Post by t0mppa on 2009-04-28
Well, since you can't see wireless interface on iwconfig or ifconfig, one thing to check would be running 'lshw -C network' on a terminal. It will show the status of your drivers, if it says network UNCLAIMED, it means no drivers are associated with the interface and if it's network DISABLED, then you've probably switched the interface off.

---

### Post by tymbrwlf on 2009-04-28
Output of lshw -C network

```
  *-network
       description: AG100 Wireless Lan Adapter
       vendor: Airgo
       physical id: 0
       slot: Socket 1
       resources: irq:10
  *-network UNCLAIMED
       description: Ethernet controller
       product: AGN100 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 1
       bus info: pci@0000:0d:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=248 maxlatency=255 mingnt=24
```
I've installed ndiswrapper and it sees the card and the driver. 

```
~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netani : driver installed
        device (17CB:0001) present

```

---

### Post by t0mppa on 2009-04-28
It still isn't being applied to the wireless interface though, so something's amiss.

I'm no expert on linksys chips, but off the top of my head: did you by any chance try installing some other drivers before NDISwrapper? Or maybe you have proprietary driver at System / Hardware Drivers enabled? Sometimes the old drivers can create conflicts, where neither driver is working, if they're still loaded to kernel while you install the new ones.

---

### Post by tymbrwlf on 2009-04-28
Nope. The Linksys drivers were the only ones I loaded. The only additional, proprietary drivers loaded are the Nvidia ones. How can I find out if something is being loaded that conflicts? And additionally, how can I stop something from conflicting if that is the case? Thanks in advance.

---

### Post by t0mppa on 2009-04-29
You could check 'lspci -vv' (vv for very verbose, will give a LOT of data) from a terminal and in the wireless config there, should find kernel modules loaded along the last lines. When you don't know where or how a module gets loaded (so you can't uninstall it), there's always the blacklisting option. Blacklisting goes through the blacklist*.conf files at /etc/modprobe.d/, but you really shouldn't go there unless you know what you're doing. Linux is a bit easy to break up by hand editing configuration files and doing something silly.

What you should do though, is grab a hold of someone who knows more about these things, specifically the ins and outs of linksys cards & NDISwrapper. I've never used either one, so I can only guess what might be wrong. And a quick search only provided one guy who found a working solution, which was to compile a custom kernel. Sounds a little extreme way of solving the issue.

---

### Post by tymbrwlf on 2009-04-29
I'll try that and see if I can trace this down. I'm going to install Fedora to determine if this issue is Ubuntu specific or just a general Linux problem. This is very frustrating because the wireless card is the only thing I'm having trouble with. Everything else works great. I really don't want to have to put Windows back on this laptop

---

### Post by tymbrwlf on 2009-04-29
After a little investigating, I suspect that the issue make be the fact that the kernel has the 4k stack size option enabled. The installation for ndiswrapper states that MOST Windows drivers will NOT work unless this is disabled and the kernel recompiled/installed. Sure does seem like a lot of trouble for one device from a major vendor.

:(

Is there a quick link for this process? Recompiling a kernel is WAY above my level of expertise

---

### Post by tymbrwlf on 2009-04-29
That's not the problem. Ubuntu has that option disabled in the kernel by default. Here's the output of lspci -vv:

```

0d:00.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)
        Subsystem: Linksys Device 0037
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at 3c080000 (32-bit, non-prefetchable) [disabled] [size=128K]
        Region 1: Memory at 3c000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

---

### Post by tymbrwlf on 2009-04-30
Anyone have any other ideas?

---

### Post by tymbrwlf on 2009-05-01
Obviously, I'm wasting my time with this particular wireless adapter (it doesn't seem to like ANY flavor of Linux; CentOS, Fedora, OpenSuSE, Knoppix, Ubuntu, etc). Can someone recommend one that will work that is readily available at a major retailer? I have to have this working before Monday so I can't wait for something I ordered online to show up in the mail.

---

### Post by tymbrwlf on 2009-05-03
Here's the output from dmesg. Could this hold a clue as to why it's not working? Perhaps an IRQ conflict?

```
[   17.117924] psmouse serio1: ID: 10 00 64<6>ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   18.092453] ndiswrapper: driver netani (Linksys,02/04/2005, 1.4.4.183) loaded
[   18.093053] ndiswrapper 0000:0d:00.0: enabling device (0000 -> 0002)
[   18.093080] ndiswrapper 0000:0d:00.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   18.094379] ndiswrapper: using IRQ 10
[   18.351536] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[   18.351549] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43767264
[   18.351555] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69466779
[   18.351560] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6341646e
[   18.351566] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65766974
[   18.351571] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69616843
[   18.351576] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a736e
[   18.351581] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206f4e
[   18.351587] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x696168
[   18.351603] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[   18.351610] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x536d696e
[   18.351615] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65527379
[   18.351621] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x52746573
[   18.351626] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a7165
[   18.351631] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x73616552
[   18.351636] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206e6f
[   18.351642] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x2065646f
[   18.351647] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x30203d
[   18.379735] ndiswrapper (mp_init:219): couldn't initialize device: C0010007
[   18.379752] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   18.379774] ndiswrapper (mp_halt:262): device df91b500 is not initialized - not halting
[   18.379781] ndiswrapper: device eth%d removed
[   18.379813] ndiswrapper 0000:0d:00.0: PCI INT A disabled
[   18.379844] ndiswrapper: probe of 0000:0d:00.0 failed with error -22
[   18.382310] usbcore: registered new interface driver ndiswrapper
[ 1193.141057] ndiswrapper 0000:09:00.0: enabling device (0000 -> 0002)
[ 1193.141083] ndiswrapper 0000:09:00.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[ 1193.142110] ndiswrapper: using IRQ 10
[ 1193.416128] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[ 1193.416141] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43767264
[ 1193.416146] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69466779
[ 1193.416152] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6341646e
[ 1193.416157] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65766974
[ 1193.416162] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69616843
[ 1193.416168] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a736e
[ 1193.416173] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206f4e
[ 1193.416178] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x696168
[ 1193.416194] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[ 1193.416201] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x536d696e
[ 1193.416206] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65527379
[ 1193.416211] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x52746573
[ 1193.416217] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a7165
[ 1193.416222] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x73616552
[ 1193.416227] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206e6f
[ 1193.416233] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x2065646f
[ 1193.416238] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x30203d
[ 1193.448901] ndiswrapper (mp_init:219): couldn't initialize device: C0010007
[ 1193.448918] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 1193.448940] ndiswrapper (mp_halt:262): device c0e12500 is not initialized - not halting
[ 1193.448947] ndiswrapper: device eth%d removed
[ 1193.448982] ndiswrapper 0000:09:00.0: PCI INT A disabled
[ 1193.449026] ndiswrapper: probe of 0000:09:00.0 failed with error -22
[ 1220.705841] ndiswrapper 0000:0d:00.0: enabling device (0000 -> 0002)
[ 1220.705866] ndiswrapper 0000:0d:00.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[ 1220.706889] ndiswrapper: using IRQ 10
[ 1221.001828] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[ 1221.001839] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43767264
[ 1221.001845] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69466779
[ 1221.001850] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6341646e
[ 1221.001855] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65766974
[ 1221.001861] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x69616843
[ 1221.001866] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a736e
[ 1221.001871] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206f4e
[ 1221.001876] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x696168
[ 1221.001892] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 8, return_address: e147e20a
[ 1221.001898] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x536d696e
[ 1221.001904] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x65527379
[ 1221.001909] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x52746573
[ 1221.001914] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x203a7165
[ 1221.001919] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x73616552
[ 1221.001925] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x43206e6f
[ 1221.001930] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x2065646f
[ 1221.001935] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x30203d
[ 1221.033625] ndiswrapper (mp_init:219): couldn't initialize device: C0010007
[ 1221.033641] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 1221.033663] ndiswrapper (mp_halt:262): device d7851500 is not initialized - not halting
[ 1221.033670] ndiswrapper: device eth%d removed
[ 1221.033704] ndiswrapper 0000:0d:00.0: PCI INT A disabled
[ 1221.033745] ndiswrapper: probe of 0000:0d:00.0 failed with error -22

```The ndiswrapper module is loading and it "sees" the pcmcia card but lshw -C network shows the device as unclaimed.

```
  *-network
       description: AG100 Wireless Lan Adapter
       vendor: Airgo
       physical id: 0
       slot: Socket 1
       resources: irq:10
  *-network UNCLAIMED
       description: Ethernet controller
       product: AGN100 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 1
       bus info: pci@0000:0d:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=248 maxlatency=255 mingnt=24
```

Any ideas would be greatly appreciated. I'm stumped

---

### Post by joslinar on 2009-05-12
Hello there,
I apologize I'm not writing here with a solution but just to say thanks. I was on my way to buying this adapter for a dell latitude d620 when I stumbled onto this post. I guess I will not buy it now. 

[COLOR="Blue"][SIZE="5"]Anybody knows about an easy to obtain (mayor retailer) pcmcia 802.11 card?[/SIZE][/COLOR]

---

### Post by tymbrwlf on 2009-05-26
I have an update to this issue. Perhaps this will give the more savvy Ubuntu/linux users a clue that could help me. If I power on the laptop with a wired connection and leave it for a little while, then insert the wireless card, sometimes it will start working and pick up a connection. Sometimes. It's intermittent. When it does work, it works great. Is there some log I can look at to see what's different about when it's working and when it's not?

---

