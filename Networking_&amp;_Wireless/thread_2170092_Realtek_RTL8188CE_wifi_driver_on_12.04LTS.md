---
title: "Realtek RTL8188CE wifi driver on 12.04LTS"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by asiandub on 2013-08-24
[FONT=arial][SIZE=4][COLOR=#333333]I've set up a fresh 12.04 (64bit, Kernel 3.8.0.29) and have issues with my **wifi card** which **isn't showing any networks / let alone connecting** to any.
[/COLOR]
[COLOR=#333333]I followed [this blogpos]("http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/")t to compile the latest driver from Realtek:[/COLOR]
[/SIZE][/FONT]
[LIST=1]
[*][FONT=arial][SIZE=4](download from realtek)[/SIZE][/FONT]
[*][FONT=arial][SIZE=4](make install)[/SIZE][/FONT]
[*][FONT=arial][SIZE=4](modprobe rtl8192ce)[/SIZE][/FONT]
[*][FONT=arial][SIZE=4](add module to /etc/modules)[/SIZE][/FONT]
[/LIST]
[FONT=arial][SIZE=4][COLOR=#333333]
Immediately after the steps above the Ubuntu network manager **showed wifi networks**. But when I then tried to connect it timed out and after a subsequent reboot I couldn't even see networks anymore (and ever since then).
[/COLOR]
[COLOR=#333333]Tried a lot of things but I guess I fail to see the core of the problem. All output seems as if it actually*should* work - but of course it doesn't...[/COLOR]
[/SIZE][/FONT][COLOR=#333333][FONT=UbuntuRegular][FONT=arial][SIZE=4]
This is how the system looks like:[/SIZE][/FONT]

[/FONT][/COLOR]```
lspci -v -s 02:00.0

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8175
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at e000 [size=256]
    Memory at f7b00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce
```

```
[FONT=Ubuntu Mono]ifconfig wlan0[/FONT]
wlan0     Link encap:Ethernet  HWaddr 64:5a:04:31:09:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000  [FONT=Ubuntu Mono]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
```

```
[FONT=Ubuntu Mono]lsmod[/FONT]
Module                  Size  Used by
joydev                 17613  0 
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_realtek    79916  1 
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20501  1 ghash_clmulni_intel
hid_logitech_dj        18767  0 
arc4                   12573  2 
microcode              23017  0 
rtl8192ce             141806  0 
rtlwifi               123323  1 rtl8192ce
usbhid                 47346  1 hid_logitech_dj
hid                   105549  2 hid_logitech_dj,usbhid
mac80211              630977  2 rtl8192ce,rtlwifi
cfg80211              525244  2 rtlwifi,mac80211
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
lpc_ich                17144  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  620421  3 
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13564  1 i915
mac_hid                13253  0 
mei                    41820  0 
video                  19652  1 i915
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            61749  0 
ahci                   25879  3 
libahci                31606  1 ahci [FONT=Ubuntu Mono]r8169                  68716  0 [/FONT]
```

```
[FONT=Ubuntu Mono]cat /etc/modules[/FONT]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc [FONT=Ubuntu Mono]rtl8192ce.ko[/FONT]
```
```

[FONT=Ubuntu Mono]dmesg | grep -i -e rtl -e wlan -e wif -e 8188[/FONT]
[    2.161737] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000c7a000, 80:ee:73:73:40:77, XID 0c000800 IRQ 44
[    2.173761] r8169 0000:05:00.0 eth1: RTL8168g/8111g at 0xffffc90000c7c000, 80:ee:73:73:40:74, XID 0c000800 IRQ 46
[    3.527480] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.531130] rtlwifi: wireless switch is on
[    4.934306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready [FONT=Ubuntu Mono][    4.934776] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT]
```

[FONT=arial][SIZE=4][COLOR=#333333]I don't see anything that actually points me in any direction.[/COLOR]
[COLOR=#333333]I should also say that dealing with kernel modules is fairly new to me. After hours of fruitless try & error I'd really appreciate if anyone more knowledgeable than me would provide some insights on what to do next.[/COLOR][/SIZE][/FONT]

---

### Post by praseodym on 2013-08-24
Try these module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by asiandub on 2013-08-24
Thanks for answering!

Tried adding these and (after having no success) another option 'fwlps=0' which I found someone else using successfully, but no change. 

```

systools -v -m rtl8192ce

Module = "rtl8192ce"


  Attributes:
    coresize            = "141806"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "0"
    srcversion          = "8371CA3A9E899B11125FFDE"
    taint               = "OF"
    uevent              = <store method only>


  Parameters:
    fwlps               = "N"
    ips                 = "N"
    swenc               = "N"
    swlps               = "N"


  Sections:
    .bss                = "0x0000000000000000"
    .data               = "0x0000000000000000"
    .exit.text          = "0x0000000000000000"
    .gnu.linkonce.this_module= "0x0000000000000000"
    .init.text          = "0x0000000000000000"
    .note.gnu.build-id  = "0x0000000000000000"
    .parainstructions   = "0x0000000000000000"
    .rodata             = "0x0000000000000000"
    .rodata.str1.1      = "0x0000000000000000"
    .rodata.str1.8      = "0x0000000000000000"
    .strtab             = "0x0000000000000000"
    .symtab             = "0x0000000000000000"
    .text               = "0x0000000000000000"
    __mcount_loc        = "0x0000000000000000"
    __param             = "0x0000000000000000"

```

---

### Post by praseodym on 2013-08-25
Lets check:
```

iwconfig
sudo iwlist scan
rfkill list
lsmod
route -n
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by asiandub on 2013-08-25
[COLOR=#333333][FONT=UbuntuRegular]**Update:**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In order to compile the actual Realtek driver against kernel 3.8 I had to comment out a method invocation that didn't seem to be required any longer. After some deeper research I *think* that this might have disabled important driver functionality. Since I actually got the LAN driver working (another exciting Realtek tale) it's probably a good idea to not open another can of worms and postpone work on the wifi driver until Realtek releases a version that's actually *supposed* to compile against 3.8.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks everyone for his help![/FONT][/COLOR]

---

