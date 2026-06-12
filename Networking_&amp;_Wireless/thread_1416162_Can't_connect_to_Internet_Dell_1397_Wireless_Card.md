---
title: "Can't connect to Internet: Dell 1397 Wireless Card"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by thomas144 on 2010-02-25
I have a Dell Inspiron 1545 computer. I boot into Ubuntu with a flash drive. When I boot, I cannot connect to a wireless network. No available networks are displayed (and I know my router is on) and the Network Manager icon displays no bars. I suspect that the Dell Wireless card (having a Broadcom BCM-4312 chipset) needs a driver. I have tried to intstall both of the restricted drivers (BCM STA and 43xx drivers), but with no success. I have run lspci in Terminal, and got many lines of text. Here are the lines that look relevant to me:
 
```
 
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
 
```
 
In Windows 7, everything is just fine. In Ubuntu, my wired connection works like a charm, but is not really accessible. Basically, I have to connect to wireless in Ubuntu or I have no reason for having it. Please help.

---

### Post by jpl888 on 2010-02-25
I have the very same wireless card as you the bcm4312 rev 01 and the Broadcom STA driver works for me. 

I have also got the card working using the open source driver as per [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620).

Could you post output of ```
lsmod
``` and ```
dmesg
```

and I will see if I can help.

---

### Post by thomas144 on 2010-02-25
THANK YOU! :D I'm so glad that you have replied to me.
I'm going to run those commands tomorrow and post the outputs here. I'll probably do that sometime tomorrow.

---

### Post by thomas144 on 2010-02-26
I'm sorry that I said, "sometime tomorrow," since you are in Ireland and I am in the eastern United States. That means that when I said that I would post the outputs in the afternoon, in Ireland, it would be at night. Anyway, I got to running those commands earlier than I expected. I got a lot of output for each command. Here is the output of lsmod:
 
```

[FONT=Courier New][FONT=Courier New]Module                  Size  Used by[/FONT]
[FONT=Courier New]binfmt_misc            10220  1 [/FONT]
[FONT=Courier New]ppdev                   8232  0 [/FONT]
[FONT=Courier New]lp                     11908  0 [/FONT]
[FONT=Courier New]parport                40528  2 ppdev,lp[/FONT]
[FONT=Courier New]snd_hda_codec_idt      72976  1 [/FONT]
[FONT=Courier New]snd_hda_intel          31880  2 [/FONT]
[FONT=Courier New]snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel[/FONT]
[FONT=Courier New]snd_hwdep               9352  1 snd_hda_codec[/FONT]
[FONT=Courier New]snd_pcm_oss            44704  0 [/FONT]
[FONT=Courier New]snd_mixer_oss          18976  1 snd_pcm_oss[/FONT]
[FONT=Courier New]snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/FONT]
[FONT=Courier New]joydev                 13088  0 [/FONT]
[FONT=Courier New]snd_seq_dummy           3460  0 [/FONT]
[FONT=Courier New]snd_seq_oss            33440  0 [/FONT]
[FONT=Courier New]snd_seq_midi            8192  0 [/FONT]
[FONT=Courier New]snd_rawmidi            27360  1 snd_seq_midi[/FONT]
[FONT=Courier New]iptable_filter          3872  0 [/FONT]
[FONT=Courier New]snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi[/FONT]
[FONT=Courier New]ip_tables              21200  1 iptable_filter[/FONT]
[FONT=Courier New]x_tables               25832  1 ip_tables[/FONT]
[FONT=Courier New]b43                   136552  0 [/FONT]
[FONT=Courier New]snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/FONT]
[FONT=Courier New]mac80211              210104  1 b43[/FONT]
[FONT=Courier New]snd_timer              26992  2 snd_pcm,snd_seq[/FONT]
[FONT=Courier New]snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
[FONT=Courier New]psmouse                57124  0 [/FONT]
[FONT=Courier New]uvcvideo               65260  0 [/FONT]
[FONT=Courier New]videodev               43360  1 uvcvideo[/FONT]
[FONT=Courier New]cfg80211              109144  2 b43,mac80211[/FONT]
[FONT=Courier New]v4l1_compat            16804  2 uvcvideo,videodev[/FONT]
[FONT=Courier New]v4l2_compat_ioctl32    13344  1 videodev[/FONT]
[FONT=Courier New]dell_wmi                3216  0 [/FONT]
[FONT=Courier New]led_class               5256  1 b43[/FONT]
[FONT=Courier New]serio_raw               6596  0 [/FONT]
[FONT=Courier New]snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
[FONT=Courier New]dell_laptop             9692  0 [/FONT]
[FONT=Courier New]soundcore               9088  1 snd[/FONT]
[FONT=Courier New]dm_crypt               14888  0 [/FONT]
[FONT=Courier New]snd_page_alloc         10928  2 snd_hda_intel,snd_pcm[/FONT]
[FONT=Courier New]dcdbas                  9136  1 dell_laptop[/FONT]
[FONT=Courier New]squashfs               24520  1 [/FONT]
[FONT=Courier New]aufs                  176208  1 [/FONT]
[FONT=Courier New]nls_iso8859_1           5280  1 [/FONT]
[FONT=Courier New]nls_cp437               6976  1 [/FONT]
[FONT=Courier New]vfat                   13184  1 [/FONT]
[FONT=Courier New]fat                    59832  1 vfat[/FONT]
[FONT=Courier New]dm_raid45              78504  0 [/FONT]
[FONT=Courier New]xor                     5456  1 dm_raid45[/FONT]
[FONT=Courier New]fbcon                  41344  72 [/FONT]
[FONT=Courier New]tileblit                3136  1 fbcon[/FONT]
[FONT=Courier New]font                    8832  1 fbcon[/FONT]
[FONT=Courier New]bitblit                 6688  1 fbcon[/FONT]
[FONT=Courier New]softcursor              2336  1 bitblit[/FONT]
[FONT=Courier New]i915                  246984  3 [/FONT]
[FONT=Courier New]drm                   193856  3 i915[/FONT]
[FONT=Courier New]i2c_algo_bit            7076  1 i915[/FONT]
[FONT=Courier New]usb_storage            65952  1 [/FONT]
[FONT=Courier New]sky2                   55556  0 [/FONT]
[FONT=Courier New]ssb                    40944  1 b43[/FONT]
[FONT=Courier New]video                  23612  1 i915[/FONT]
[FONT=Courier New]output                  3680  1 video[/FONT]
[FONT=Courier New]intel_agp              32816  2 i915[/FONT]
[FONT=Courier New]ubuntu@ubuntu:~$ clear[/FONT]
 
[FONT=Courier New]ubuntu@ubuntu:~$ lsmod[/FONT]
[FONT=Courier New]Module                  Size  Used by[/FONT]
[FONT=Courier New]binfmt_misc            10220  1 [/FONT]
[FONT=Courier New]ppdev                   8232  0 [/FONT]
[FONT=Courier New]lp                     11908  0 [/FONT]
[FONT=Courier New]parport                40528  2 ppdev,lp[/FONT]
[FONT=Courier New]snd_hda_codec_idt      72976  1 [/FONT]
[FONT=Courier New]snd_hda_intel          31880  2 [/FONT]
[FONT=Courier New]snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel[/FONT]
[FONT=Courier New]snd_hwdep               9352  1 snd_hda_codec[/FONT]
[FONT=Courier New]snd_pcm_oss            44704  0 [/FONT]
[FONT=Courier New]snd_mixer_oss          18976  1 snd_pcm_oss[/FONT]
[FONT=Courier New]snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/FONT]
[FONT=Courier New]joydev                 13088  0 [/FONT]
[FONT=Courier New]snd_seq_dummy           3460  0 [/FONT]
[FONT=Courier New]snd_seq_oss            33440  0 [/FONT]
[FONT=Courier New]snd_seq_midi            8192  0 [/FONT]
[FONT=Courier New]snd_rawmidi            27360  1 snd_seq_midi[/FONT]
[FONT=Courier New]iptable_filter          3872  0 [/FONT]
[FONT=Courier New]snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi[/FONT]
[FONT=Courier New]ip_tables              21200  1 iptable_filter[/FONT]
[FONT=Courier New]x_tables               25832  1 ip_tables[/FONT]
[FONT=Courier New]b43                   136552  0 [/FONT]
[FONT=Courier New]snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/FONT]
[FONT=Courier New]mac80211              210104  1 b43[/FONT]
[FONT=Courier New]snd_timer              26992  2 snd_pcm,snd_seq[/FONT]
[FONT=Courier New]snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
[FONT=Courier New]psmouse                57124  0 [/FONT]
[FONT=Courier New]uvcvideo               65260  0 [/FONT]
[FONT=Courier New]videodev               43360  1 uvcvideo[/FONT]
[FONT=Courier New]cfg80211              109144  2 b43,mac80211[/FONT]
[FONT=Courier New]v4l1_compat            16804  2 uvcvideo,videodev[/FONT]
[FONT=Courier New]v4l2_compat_ioctl32    13344  1 videodev[/FONT]
[FONT=Courier New]dell_wmi                3216  0 [/FONT]
[FONT=Courier New]led_class               5256  1 b43[/FONT]
[FONT=Courier New]serio_raw               6596  0 [/FONT]
[FONT=Courier New]snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
[FONT=Courier New]dell_laptop             9692  0 [/FONT]
[FONT=Courier New]soundcore               9088  1 snd[/FONT]
[FONT=Courier New]dm_crypt               14888  0 [/FONT]
[FONT=Courier New]snd_page_alloc         10928  2 snd_hda_intel,snd_pcm[/FONT]
[FONT=Courier New]dcdbas                  9136  1 dell_laptop[/FONT]
[FONT=Courier New]squashfs               24520  1 [/FONT]
[FONT=Courier New]aufs                  176208  1 [/FONT]
[FONT=Courier New]nls_iso8859_1           5280  1 [/FONT]
[FONT=Courier New]nls_cp437               6976  1 [/FONT]
[FONT=Courier New]vfat                   13184  1 [/FONT]
[FONT=Courier New]fat                    59832  1 vfat[/FONT]
[FONT=Courier New]dm_raid45              78504  0 [/FONT]
[FONT=Courier New]xor                     5456  1 dm_raid45[/FONT]
[FONT=Courier New]fbcon                  41344  72 [/FONT]
[FONT=Courier New]tileblit                3136  1 fbcon[/FONT]
[FONT=Courier New]font                    8832  1 fbcon[/FONT]
[FONT=Courier New]bitblit                 6688  1 fbcon[/FONT]
[FONT=Courier New]softcursor              2336  1 bitblit[/FONT]
[FONT=Courier New]i915                  246984  3 [/FONT]
[FONT=Courier New]drm                   193856  3 i915[/FONT]
[FONT=Courier New]i2c_algo_bit            7076  1 i915[/FONT]
[FONT=Courier New]usb_storage            65952  1 [/FONT]
[FONT=Courier New]sky2                   55556  0 [/FONT]
[FONT=Courier New]ssb                    40944  1 b43[/FONT]
[FONT=Courier New]video                  23612  1 i915[/FONT]
[FONT=Courier New]output                  3680  1 video[/FONT]
[FONT=Courier New]intel_agp              32816  2 i915[/FONT]
 
[/FONT]
```[FONT=Courier New]
 
The output of dmesg may be so long that Terminal cut off the output, or maybe not. I'm not an expert on this. Anyway, here is the output of dmesg:
 
[FONT=Courier New]```
[FONT=Courier New][    0.438601] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff][/FONT]
[FONT=Courier New][    0.438605] pci 0000:00:02.0: reg 20 io port: [0xefe8-0xefef][/FONT]
[FONT=Courier New][    0.438645] pci 0000:00:02.1: reg 10 64bit mmio: [0xf6b00000-0xf6bfffff][/FONT]
[FONT=Courier New][    0.438774] pci 0000:00:1a.0: reg 20 io port: [0x6f60-0x6f7f][/FONT]
[FONT=Courier New][    0.438871] pci 0000:00:1a.1: reg 20 io port: [0x6f80-0x6f9f][/FONT]
[FONT=Courier New][    0.438970] pci 0000:00:1a.2: reg 20 io port: [0x6fa0-0x6fbf][/FONT]
[FONT=Courier New][    0.439068] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff][/FONT]
[FONT=Courier New][    0.439139] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439145] pci 0000:00:1a.7: PME# disabled[/FONT]
[FONT=Courier New][    0.439203] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6afc000-0xf6afffff][/FONT]
[FONT=Courier New][    0.439266] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439271] pci 0000:00:1b.0: PME# disabled[/FONT]
[FONT=Courier New][    0.439360] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439365] pci 0000:00:1c.0: PME# disabled[/FONT]
[FONT=Courier New][    0.439456] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439461] pci 0000:00:1c.1: PME# disabled[/FONT]
[FONT=Courier New][    0.439553] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439558] pci 0000:00:1c.2: PME# disabled[/FONT]
[FONT=Courier New][    0.439651] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.439656] pci 0000:00:1c.4: PME# disabled[/FONT]
[FONT=Courier New][    0.439736] pci 0000:00:1d.0: reg 20 io port: [0x6f00-0x6f1f][/FONT]
[FONT=Courier New][    0.439832] pci 0000:00:1d.1: reg 20 io port: [0x6f20-0x6f3f][/FONT]
[FONT=Courier New][    0.439929] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f][/FONT]
[FONT=Courier New][    0.440047] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff][/FONT]
[FONT=Courier New][    0.440118] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.440123] pci 0000:00:1d.7: PME# disabled[/FONT]
[FONT=Courier New][    0.440388] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77][/FONT]
[FONT=Courier New][    0.440396] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b][/FONT]
[FONT=Courier New][    0.440404] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87][/FONT]
[FONT=Courier New][    0.440412] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b][/FONT]
[FONT=Courier New][    0.440420] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf][/FONT]
[FONT=Courier New][    0.440428] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfed1c800-0xfed1cfff][/FONT]
[FONT=Courier New][    0.440478] pci 0000:00:1f.2: PME# supported from D3hot[/FONT]
[FONT=Courier New][    0.440483] pci 0000:00:1f.2: PME# disabled[/FONT]
[FONT=Courier New][    0.440526] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf6afbf00-0xf6afbfff][/FONT]
[FONT=Courier New][    0.440546] pci 0000:00:1f.3: reg 20 io port: [0x1100-0x111f][/FONT]
[FONT=Courier New][    0.441005] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf69fc000-0xf69fffff][/FONT]
[FONT=Courier New][    0.441225] pci 0000:0c:00.0: supports D1 D2[/FONT]
[FONT=Courier New][    0.441227] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold[/FONT]
[FONT=Courier New][    0.441239] pci 0000:0c:00.0: PME# disabled[/FONT]
[FONT=Courier New][    0.441380] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6900000-0xf69fffff][/FONT]
[FONT=Courier New][    0.441468] pci 0000:09:00.0: reg 10 64bit mmio: [0xf68fc000-0xf68fffff][/FONT]
[FONT=Courier New][    0.441480] pci 0000:09:00.0: reg 18 io port: [0xde00-0xdeff][/FONT]
[FONT=Courier New][    0.441569] pci 0000:09:00.0: supports D1 D2[/FONT]
[FONT=Courier New][    0.441571] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT]
[FONT=Courier New][    0.441578] pci 0000:09:00.0: PME# disabled[/FONT]
[FONT=Courier New][    0.441659] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff][/FONT]
[FONT=Courier New][    0.441664] pci 0000:00:1c.2: bridge 32bit mmio: [0xf6800000-0xf68fffff][/FONT]
[FONT=Courier New][    0.441734] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff][/FONT]
[FONT=Courier New][    0.441739] pci 0000:00:1c.4: bridge 32bit mmio: [0xf6600000-0xf67fffff][/FONT]
[FONT=Courier New][    0.441747] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf0000000-0xf01fffff][/FONT]
[FONT=Courier New][    0.441819] pci 0000:00:1e.0: transparent bridge[/FONT]
[FONT=Courier New][    0.441867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT][/FONT]
[FONT=Courier New][    0.442131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT][/FONT]
[FONT=Courier New][    0.442265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT][/FONT]
[FONT=Courier New][    0.442336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT][/FONT]
[FONT=Courier New][    0.442410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT][/FONT]
[FONT=Courier New][    0.442484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT][/FONT]
[FONT=Courier New][    0.454954] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)[/FONT]
[FONT=Courier New][    0.455076] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4[/FONT]
[FONT=Courier New][    0.455195] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)[/FONT]
[FONT=Courier New][    0.455301] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.[/FONT]
[FONT=Courier New][    0.455422] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)[/FONT]
[FONT=Courier New][    0.455544] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)[/FONT]
[FONT=Courier New][    0.455667] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)[/FONT]
[FONT=Courier New][    0.455776] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.[/FONT]
[FONT=Courier New][    0.455974] SCSI subsystem initialized[/FONT]
[FONT=Courier New][    0.456020] libata version 3.00 loaded.[/FONT]
[FONT=Courier New][    0.456020] usbcore: registered new interface driver usbfs[/FONT]
[FONT=Courier New][    0.456020] usbcore: registered new interface driver hub[/FONT]
[FONT=Courier New][    0.456020] usbcore: registered new device driver usb[/FONT]
[FONT=Courier New][    0.456020] ACPI: WMI: Mapper loaded[/FONT]
[FONT=Courier New][    0.456020] PCI: Using ACPI for IRQ routing[/FONT]
[FONT=Courier New][    0.480007] Bluetooth: Core ver 2.15[/FONT]
[FONT=Courier New][    0.480025] NET: Registered protocol family 31[/FONT]
[FONT=Courier New][    0.480025] Bluetooth: HCI device and connection manager initialized[/FONT]
[FONT=Courier New][    0.480025] Bluetooth: HCI socket layer initialized[/FONT]
[FONT=Courier New][    0.480025] NetLabel: Initializing[/FONT]
[FONT=Courier New][    0.480025] NetLabel:  domain hash size = 128[/FONT]
[FONT=Courier New][    0.480025] NetLabel:  protocols = UNLABELED CIPSOv4[/FONT]
[FONT=Courier New][    0.480034] NetLabel:  unlabeled traffic allowed by default[/FONT]
[FONT=Courier New][    0.480081] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0[/FONT]
[FONT=Courier New][    0.480086] hpet0: 4 comparators, 64-bit 14.318180 MHz counter[/FONT]
[FONT=Courier New][    0.501307] Switched to high resolution mode on CPU 1[/FONT]
[FONT=Courier New][    0.509999] Switched to high resolution mode on CPU 0[/FONT]
[FONT=Courier New][    0.510017] pnp: PnP ACPI init[/FONT]
[FONT=Courier New][    0.510037] ACPI: bus type pnp registered[/FONT]
[FONT=Courier New][    0.561592] pnp: PnP ACPI: found 13 devices[/FONT]
[FONT=Courier New][    0.561594] ACPI: ACPI bus type pnp unregistered[/FONT]
[FONT=Courier New][    0.561606] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved[/FONT]
[FONT=Courier New][    0.561609] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved[/FONT]
[FONT=Courier New][    0.561619] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved[/FONT]
[FONT=Courier New][    0.561625] system 00:0a: ioport range 0x900-0x97f has been reserved[/FONT]
[FONT=Courier New][    0.561628] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved[/FONT]
[FONT=Courier New][    0.561631] system 00:0a: ioport range 0x1000-0x1005 has been reserved[/FONT]
[FONT=Courier New][    0.561633] system 00:0a: ioport range 0x1008-0x100f has been reserved[/FONT]
[FONT=Courier New][    0.561639] system 00:0b: ioport range 0xf400-0xf4fe has been reserved[/FONT]
[FONT=Courier New][    0.561641] system 00:0b: ioport range 0x1006-0x1007 has been reserved[/FONT]
[FONT=Courier New][    0.561644] system 00:0b: ioport range 0x100a-0x1059 could not be reserved[/FONT]
[FONT=Courier New][    0.561647] system 00:0b: ioport range 0x1060-0x107f has been reserved[/FONT]
[FONT=Courier New][    0.561650] system 00:0b: ioport range 0x1080-0x10bf has been reserved[/FONT]
[FONT=Courier New][    0.561653] system 00:0b: ioport range 0x1100-0x111f has been reserved[/FONT]
[FONT=Courier New][    0.561655] system 00:0b: ioport range 0x1010-0x102f has been reserved[/FONT]
[FONT=Courier New][    0.561658] system 00:0b: ioport range 0x809-0x809 has been reserved[/FONT]
[FONT=Courier New][    0.561664] system 00:0c: iomem range 0x0-0x9efff could not be reserved[/FONT]
[FONT=Courier New][    0.561666] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved[/FONT]
[FONT=Courier New][    0.561669] system 00:0c: iomem range 0xc0000-0xcffff has been reserved[/FONT]
[FONT=Courier New][    0.561672] system 00:0c: iomem range 0xe0000-0xfffff has been reserved[/FONT]
[FONT=Courier New][    0.561674] system 00:0c: iomem range 0x100000-0xbd8bf3ff could not be reserved[/FONT]
[FONT=Courier New][    0.561677] system 00:0c: iomem range 0xbd8bf400-0xbdafffff could not be reserved[/FONT]
[FONT=Courier New][    0.561680] system 00:0c: iomem range 0xbdb00000-0xbdbfffff has been reserved[/FONT]
[FONT=Courier New][    0.561683] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved[/FONT]
[FONT=Courier New][    0.561686] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved[/FONT]
[FONT=Courier New][    0.561689] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved[/FONT]
[FONT=Courier New][    0.561691] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved[/FONT]
[FONT=Courier New][    0.561694] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved[/FONT]
[FONT=Courier New][    0.561697] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved[/FONT]
[FONT=Courier New][    0.561700] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved[/FONT]
[FONT=Courier New][    0.561705] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved[/FONT]
[FONT=Courier New][    0.561708] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved[/FONT]
[FONT=Courier New][    0.561711] system 00:0c: iomem range 0xfed1c800-0xfed1cfff has been reserved[/FONT]
[FONT=Courier New][    0.561714] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved[/FONT]
[FONT=Courier New][    0.561717] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved[/FONT]
[FONT=Courier New][    0.566400] AppArmor: AppArmor Filesystem Enabled[/FONT]
[FONT=Courier New][    0.566468] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b[/FONT]
[FONT=Courier New][    0.566470] pci 0000:00:1c.0:   IO window: disabled[/FONT]
[FONT=Courier New][    0.566477] pci 0000:00:1c.0:   MEM window: disabled[/FONT]
[FONT=Courier New][    0.566481] pci 0000:00:1c.0:   PREFETCH window: disabled[/FONT]
[FONT=Courier New][    0.566486] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c[/FONT]
[FONT=Courier New][    0.566488] pci 0000:00:1c.1:   IO window: disabled[/FONT]
[FONT=Courier New][    0.566495] pci 0000:00:1c.1:   MEM window: 0xf6900000-0xf69fffff[/FONT]
[FONT=Courier New][    0.566499] pci 0000:00:1c.1:   PREFETCH window: disabled[/FONT]
[FONT=Courier New][    0.566505] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:09[/FONT]
[FONT=Courier New][    0.566508] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff[/FONT]
[FONT=Courier New][    0.566514] pci 0000:00:1c.2:   MEM window: 0xf6800000-0xf68fffff[/FONT]
[FONT=Courier New][    0.566519] pci 0000:00:1c.2:   PREFETCH window: disabled[/FONT]
[FONT=Courier New][    0.566524] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d[/FONT]
[FONT=Courier New][    0.566528] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff[/FONT]
[FONT=Courier New][    0.566534] pci 0000:00:1c.4:   MEM window: 0xf6600000-0xf67fffff[/FONT]
[FONT=Courier New][    0.566539] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff[/FONT]
[FONT=Courier New][    0.566547] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03[/FONT]
[FONT=Courier New][    0.566549] pci 0000:00:1e.0:   IO window: disabled[/FONT]
[FONT=Courier New][    0.566555] pci 0000:00:1e.0:   MEM window: disabled[/FONT]
[FONT=Courier New][    0.566559] pci 0000:00:1e.0:   PREFETCH window: disabled[/FONT]
[FONT=Courier New][    0.566576]   alloc irq_desc for 16 on node 0[/FONT]
[FONT=Courier New][    0.566578]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    0.566584] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT]
[FONT=Courier New][    0.566590] pci 0000:00:1c.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    0.566599]   alloc irq_desc for 17 on node 0[/FONT]
[FONT=Courier New][    0.566600]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    0.566604] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17[/FONT]
[FONT=Courier New][    0.566609] pci 0000:00:1c.1: setting latency timer to 64[/FONT]
[FONT=Courier New][    0.566617]   alloc irq_desc for 18 on node 0[/FONT]
[FONT=Courier New][    0.566619]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    0.566622] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18[/FONT]
[FONT=Courier New][    0.566627] pci 0000:00:1c.2: setting latency timer to 64[/FONT]
[FONT=Courier New][    0.566636] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT]
[FONT=Courier New][    0.566641] pci 0000:00:1c.4: setting latency timer to 64[/FONT]
[FONT=Courier New][    0.566649] pci 0000:00:1e.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    0.566654] pci_bus 0000:00: resource 0 io:  [0x00-0xffff][/FONT]
[FONT=Courier New][    0.566656] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff][/FONT]
[FONT=Courier New][    0.566659] pci_bus 0000:0c: resource 1 mem: [0xf6900000-0xf69fffff][/FONT]
[FONT=Courier New][    0.566661] pci_bus 0000:09: resource 0 io:  [0xd000-0xdfff][/FONT]
[FONT=Courier New][    0.566664] pci_bus 0000:09: resource 1 mem: [0xf6800000-0xf68fffff][/FONT]
[FONT=Courier New][    0.566666] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff][/FONT]
[FONT=Courier New][    0.566668] pci_bus 0000:0d: resource 1 mem: [0xf6600000-0xf67fffff][/FONT]
[FONT=Courier New][    0.566670] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff][/FONT]
[FONT=Courier New][    0.566673] pci_bus 0000:03: resource 3 io:  [0x00-0xffff][/FONT]
[FONT=Courier New][    0.566675] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff][/FONT]
[FONT=Courier New][    0.566710] NET: Registered protocol family 2[/FONT]
[FONT=Courier New][    0.566879] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)[/FONT]
[FONT=Courier New][    0.568161] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)[/FONT]
[FONT=Courier New][    0.572483] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)[/FONT]
[FONT=Courier New][    0.573003] TCP: Hash tables configured (established 524288 bind 65536)[/FONT]
[FONT=Courier New][    0.573006] TCP reno registered[/FONT]
[FONT=Courier New][    0.573133] NET: Registered protocol family 1[/FONT]
[FONT=Courier New][    0.573207] Trying to unpack rootfs image as initramfs...[/FONT]
[FONT=Courier New][    1.949625] Freeing initrd memory: 5699k freed[/FONT]
[FONT=Courier New][    1.952559] Scanning for low memory corruption every 60 seconds[/FONT]
[FONT=Courier New][    1.952701] audit: initializing netlink socket (disabled)[/FONT]
[FONT=Courier New][    1.952721] type=2000 audit(1267176270.950:1): initialized[/FONT]
[FONT=Courier New][    1.962711] HugeTLB registered 2 MB page size, pre-allocated 0 pages[/FONT]
[FONT=Courier New][    1.964125] VFS: Disk quotas dquot_6.5.2[/FONT]
[FONT=Courier New][    1.964182] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)[/FONT]
[FONT=Courier New][    1.964735] fuse init (API version 7.12)[/FONT]
[FONT=Courier New][    1.964814] msgmni has been set to 5960[/FONT]
[FONT=Courier New][    1.965023] alg: No test for stdrng (krng)[/FONT]
[FONT=Courier New][    1.965037] io scheduler noop registered[/FONT]
[FONT=Courier New][    1.965039] io scheduler anticipatory registered[/FONT]
[FONT=Courier New][    1.965041] io scheduler deadline registered[/FONT]
[FONT=Courier New][    1.965082] io scheduler cfq registered (default)[/FONT]
[FONT=Courier New][    1.965093] pci 0000:00:02.0: Boot video device[/FONT]
[FONT=Courier New][    1.965405]   alloc irq_desc for 24 on node 0[/FONT]
[FONT=Courier New][    1.965407]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    1.965419] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X[/FONT]
[FONT=Courier New][    1.965430] pcieport-driver 0000:00:1c.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    1.965614]   alloc irq_desc for 25 on node 0[/FONT]
[FONT=Courier New][    1.965616]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    1.965626] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X[/FONT]
[FONT=Courier New][    1.965637] pcieport-driver 0000:00:1c.1: setting latency timer to 64[/FONT]
[FONT=Courier New][    1.965814]   alloc irq_desc for 26 on node 0[/FONT]
[FONT=Courier New][    1.965816]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    1.965826] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X[/FONT]
[FONT=Courier New][    1.965836] pcieport-driver 0000:00:1c.2: setting latency timer to 64[/FONT]
[FONT=Courier New][    1.966019]   alloc irq_desc for 27 on node 0[/FONT]
[FONT=Courier New][    1.966021]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    1.966030] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X[/FONT]
[FONT=Courier New][    1.966041] pcieport-driver 0000:00:1c.4: setting latency timer to 64[/FONT]
[FONT=Courier New][    1.966151] pci_hotplug: PCI Hot Plug PCI Core version: 0.5[/FONT]
[FONT=Courier New][    1.966266] pciehp: PCI Express Hot Plug Controller Driver version: 0.4[/FONT]
[FONT=Courier New][    1.966427] ACPI: AC Adapter [AC] (on-line)[/FONT]
[FONT=Courier New][    1.966496] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0[/FONT]
[FONT=Courier New][    1.967430] ACPI: Lid Switch [LID][/FONT]
[FONT=Courier New][    1.967472] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1[/FONT]
[FONT=Courier New][    1.967479] ACPI: Power Button [PBTN][/FONT]
[FONT=Courier New][    1.967520] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2[/FONT]
[FONT=Courier New][    1.967522] ACPI: Sleep Button [SBTN][/FONT]
[FONT=Courier New][    1.968241] ACPI: SSDT 00000000bdac29cf 0023F (v01  PmRef   BspIst 00003000 INTL 20050624)[/FONT]
[FONT=Courier New][    1.968667] ACPI: SSDT 00000000bdac2de5 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)[/FONT]
[FONT=Courier New][    1.968992] Monitor-Mwait will be used to enter C-1 state[/FONT]
[FONT=Courier New][    1.969025] Monitor-Mwait will be used to enter C-2 state[/FONT]
[FONT=Courier New][    1.969032] Marking TSC unstable due to TSC halts in idle[/FONT]
[FONT=Courier New][    1.969046] ACPI: CPU0 (power states: C1[C1] C2[C2])[/FONT]
[FONT=Courier New][    1.969069] processor LNXCPU:00: registered as cooling_device0[/FONT]
[FONT=Courier New][    1.969073] ACPI: Processor [CPU0] (supports 8 throttling states)[/FONT]
[FONT=Courier New][    1.969512] ACPI: SSDT 00000000bdac2c0e 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)[/FONT]
[FONT=Courier New][    1.969827] ACPI: SSDT 00000000bdac33ab 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)[/FONT]
[FONT=Courier New][    1.970280] ACPI: CPU1 (power states: C1[C1] C2[C2])[/FONT]
[FONT=Courier New][    1.970301] processor LNXCPU:01: registered as cooling_device1[/FONT]
[FONT=Courier New][    1.970304] ACPI: Processor [CPU1] (supports 8 throttling states)[/FONT]
[FONT=Courier New][    1.982288] thermal LNXTHERM:01: registered as thermal_zone0[/FONT]
[FONT=Courier New][    1.982296] ACPI: Thermal Zone [THM] (45 C)[/FONT]
[FONT=Courier New][    1.983447] Linux agpgart interface v0.103[/FONT]
[FONT=Courier New][    1.983457] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled[/FONT]
[FONT=Courier New][    1.984650] brd: module loaded[/FONT]
[FONT=Courier New][    1.985076] loop: module loaded[/FONT]
[FONT=Courier New][    1.985150] input: Macintosh mouse button emulation as /devices/virtual/input/input3[/FONT]
[FONT=Courier New][    2.000546] ahci 0000:00:1f.2: version 3.0[/FONT]
[FONT=Courier New][    2.000562] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18[/FONT]
[FONT=Courier New][    2.000607]   alloc irq_desc for 28 on node 0[/FONT]
[FONT=Courier New][    2.000609]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    2.000621] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X[/FONT]
[FONT=Courier New][    2.000669] ahci: SSS flag set, parallel bus scan disabled[/FONT]
[FONT=Courier New][    2.000707] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode[/FONT]
[FONT=Courier New][    2.000711] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems [/FONT]
[FONT=Courier New][    2.000716] ahci 0000:00:1f.2: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.041328] ACPI: Battery Slot [BAT0] (battery present)[/FONT]
[FONT=Courier New][    2.070084] scsi0 : ahci[/FONT]
[FONT=Courier New][    2.070187] scsi1 : ahci[/FONT]
[FONT=Courier New][    2.070241] scsi2 : ahci[/FONT]
[FONT=Courier New][    2.070298] scsi3 : ahci[/FONT]
[FONT=Courier New][    2.070352] scsi4 : ahci[/FONT]
[FONT=Courier New][    2.070410] scsi5 : ahci[/FONT]
[FONT=Courier New][    2.070808] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 28[/FONT]
[FONT=Courier New][    2.070812] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 28[/FONT]
[FONT=Courier New][    2.070814] ata3: DUMMY[/FONT]
[FONT=Courier New][    2.070816] ata4: DUMMY[/FONT]
[FONT=Courier New][    2.070818] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 28[/FONT]
[FONT=Courier New][    2.070822] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 28[/FONT]
[FONT=Courier New][    2.071648] Fixed MDIO Bus: probed[/FONT]
[FONT=Courier New][    2.071683] PPP generic driver version 2.4.2[/FONT]
[FONT=Courier New][    2.071788] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/FONT]
[FONT=Courier New][    2.071847]   alloc irq_desc for 22 on node 0[/FONT]
[FONT=Courier New][    2.071849]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    2.071856] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22[/FONT]
[FONT=Courier New][    2.071875] ehci_hcd 0000:00:1a.7: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.071879] ehci_hcd 0000:00:1a.7: EHCI Host Controller[/FONT]
[FONT=Courier New][    2.071932] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1[/FONT]
[FONT=Courier New][    2.075834] ehci_hcd 0000:00:1a.7: debug port 1[/FONT]
[FONT=Courier New][    2.075841] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported[/FONT]
[FONT=Courier New][    2.075855] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400[/FONT]
[FONT=Courier New][    2.090015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00[/FONT]
[FONT=Courier New][    2.090104] usb usb1: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.090131] hub 1-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.090139] hub 1-0:1.0: 6 ports detected[/FONT]
[FONT=Courier New][    2.090234]   alloc irq_desc for 20 on node 0[/FONT]
[FONT=Courier New][    2.090236]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    2.090240] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20[/FONT]
[FONT=Courier New][    2.090252] ehci_hcd 0000:00:1d.7: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.090255] ehci_hcd 0000:00:1d.7: EHCI Host Controller[/FONT]
[FONT=Courier New][    2.090292] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2[/FONT]
[FONT=Courier New][    2.094204] ehci_hcd 0000:00:1d.7: debug port 1[/FONT]
[FONT=Courier New][    2.094211] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported[/FONT]
[FONT=Courier New][    2.094225] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000[/FONT]
[FONT=Courier New][    2.110016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00[/FONT]
[FONT=Courier New][    2.110070] usb usb2: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.110098] hub 2-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.110105] hub 2-0:1.0: 6 ports detected[/FONT]
[FONT=Courier New][    2.110175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/FONT]
[FONT=Courier New][    2.110194] uhci_hcd: USB Universal Host Controller Interface driver[/FONT]
[FONT=Courier New][    2.110285] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20[/FONT]
[FONT=Courier New][    2.110293] uhci_hcd 0000:00:1a.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.110297] uhci_hcd 0000:00:1a.0: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.110331] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3[/FONT]
[FONT=Courier New][    2.110361] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60[/FONT]
[FONT=Courier New][    2.110441] usb usb3: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.110468] hub 3-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.110474] hub 3-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.110550]   alloc irq_desc for 21 on node 0[/FONT]
[FONT=Courier New][    2.110552]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    2.110558] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21[/FONT]
[FONT=Courier New][    2.110564] uhci_hcd 0000:00:1a.1: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.110568] uhci_hcd 0000:00:1a.1: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.110599] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4[/FONT]
[FONT=Courier New][    2.110633] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80[/FONT]
[FONT=Courier New][    2.110714] usb usb4: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.110738] hub 4-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.110745] hub 4-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.110824] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22[/FONT]
[FONT=Courier New][    2.110831] uhci_hcd 0000:00:1a.2: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.110835] uhci_hcd 0000:00:1a.2: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.110880] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5[/FONT]
[FONT=Courier New][    2.110909] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0[/FONT]
[FONT=Courier New][    2.110987] usb usb5: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.111011] hub 5-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.111017] hub 5-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.111094] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20[/FONT]
[FONT=Courier New][    2.111101] uhci_hcd 0000:00:1d.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.111105] uhci_hcd 0000:00:1d.0: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.111135] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6[/FONT]
[FONT=Courier New][    2.111164] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00[/FONT]
[FONT=Courier New][    2.111240] usb usb6: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.111264] hub 6-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.111270] hub 6-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.111346] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21[/FONT]
[FONT=Courier New][    2.111353] uhci_hcd 0000:00:1d.1: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.111356] uhci_hcd 0000:00:1d.1: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.111391] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7[/FONT]
[FONT=Courier New][    2.111419] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20[/FONT]
[FONT=Courier New][    2.111493] usb usb7: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.111520] hub 7-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.111526] hub 7-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.111603] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22[/FONT]
[FONT=Courier New][    2.111610] uhci_hcd 0000:00:1d.2: setting latency timer to 64[/FONT]
[FONT=Courier New][    2.111614] uhci_hcd 0000:00:1d.2: UHCI Host Controller[/FONT]
[FONT=Courier New][    2.111653] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8[/FONT]
[FONT=Courier New][    2.111683] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40[/FONT]
[FONT=Courier New][    2.111759] usb usb8: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.111783] hub 8-0:1.0: USB hub found[/FONT]
[FONT=Courier New][    2.111789] hub 8-0:1.0: 2 ports detected[/FONT]
[FONT=Courier New][    2.111894] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12[/FONT]
[FONT=Courier New][    2.131452] i8042.c: Detected active multiplexing controller, rev 1.1.[/FONT]
[FONT=Courier New][    2.144514] serio: i8042 KBD port at 0x60,0x64 irq 1[/FONT]
[FONT=Courier New][    2.144519] serio: i8042 AUX0 port at 0x60,0x64 irq 12[/FONT]
[FONT=Courier New][    2.144522] serio: i8042 AUX1 port at 0x60,0x64 irq 12[/FONT]
[FONT=Courier New][    2.144524] serio: i8042 AUX2 port at 0x60,0x64 irq 12[/FONT]
[FONT=Courier New][    2.144527] serio: i8042 AUX3 port at 0x60,0x64 irq 12[/FONT]
[FONT=Courier New][    2.144587] mice: PS/2 mouse device common for all mice[/FONT]
[FONT=Courier New][    2.144701] rtc_cmos 00:04: RTC can wake from S4[/FONT]
[FONT=Courier New][    2.144737] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0[/FONT]
[FONT=Courier New][    2.144768] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs[/FONT]
[FONT=Courier New][    2.144881] device-mapper: uevent: version 1.0.3[/FONT]
[FONT=Courier New][    2.144969] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com[/FONT]
[FONT=Courier New][    2.145026] device-mapper: multipath: version 1.1.0 loaded[/FONT]
[FONT=Courier New][    2.145030] device-mapper: multipath round-robin: version 1.0.0 loaded[/FONT]
[FONT=Courier New][    2.145214] cpuidle: using governor ladder[/FONT]
[FONT=Courier New][    2.145702] cpuidle: using governor menu[/FONT]
[FONT=Courier New][    2.146094] TCP cubic registered[/FONT]
[FONT=Courier New][    2.146213] NET: Registered protocol family 10[/FONT]
[FONT=Courier New][    2.146629] lo: Disabled Privacy Extensions[/FONT]
[FONT=Courier New][    2.146905] NET: Registered protocol family 17[/FONT]
[FONT=Courier New][    2.146926] Bluetooth: L2CAP ver 2.13[/FONT]
[FONT=Courier New][    2.146928] Bluetooth: L2CAP socket layer initialized[/FONT]
[FONT=Courier New][    2.146932] Bluetooth: SCO (Voice Link) ver 0.6[/FONT]
[FONT=Courier New][    2.146934] Bluetooth: SCO socket layer initialized[/FONT]
[FONT=Courier New][    2.146985] Bluetooth: RFCOMM TTY layer initialized[/FONT]
[FONT=Courier New][    2.146988] Bluetooth: RFCOMM socket layer initialized[/FONT]
[FONT=Courier New][    2.146990] Bluetooth: RFCOMM ver 1.11[/FONT]
[FONT=Courier New][    2.147813] PM: Resume from disk failed.[/FONT]
[FONT=Courier New][    2.147826] registered taskstats version 1[/FONT]
[FONT=Courier New][    2.147934]   Magic number: 14:256:425[/FONT]
[FONT=Courier New][    2.148051] rtc_cmos 00:04: setting system clock to 2010-02-26 09:24:31 UTC (1267176271)[/FONT]
[FONT=Courier New][    2.148054] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found[/FONT]
[FONT=Courier New][    2.148055] EDD information not available.[/FONT]
[FONT=Courier New][    2.170687] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4[/FONT]
[FONT=Courier New][    2.420067] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/FONT]
[FONT=Courier New][    2.420084] usb 1-5: new high speed USB device using ehci_hcd and address 2[/FONT]
[FONT=Courier New][    2.429565] ata1.00: ATA-8: SAMSUNG HM250HI, 2AC101C4, max UDMA/133[/FONT]
[FONT=Courier New][    2.429568] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)[/FONT]
[FONT=Courier New][    2.439091] ata1.00: configured for UDMA/133[/FONT]
[FONT=Courier New][    2.450125] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250HI  2AC1 PQ: 0 ANSI: 5[/FONT]
[FONT=Courier New][    2.450241] sd 0:0:0:0: Attached scsi generic sg0 type 0[/FONT]
[FONT=Courier New][    2.450277] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)[/FONT]
[FONT=Courier New][    2.450317] sd 0:0:0:0: [sda] Write Protect is off[/FONT]
[FONT=Courier New][    2.450320] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00[/FONT]
[FONT=Courier New][    2.450341] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/FONT]
[FONT=Courier New][    2.450459]  sda:[/FONT]
[FONT=Courier New][    2.500039] Clocksource tsc unstable (delta = -185187558 ns)[/FONT]
[FONT=Courier New][    2.583597] usb 1-5: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.700036] usb 1-6: new high speed USB device using ehci_hcd and address 3[/FONT]
[FONT=Courier New][    2.859207] usb 1-6: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    2.876946]  sda1 sda2 sda3[/FONT]
[FONT=Courier New][    2.877194] sd 0:0:0:0: [sda] Attached SCSI disk[/FONT]
[FONT=Courier New][    2.970064] usb 2-1: new high speed USB device using ehci_hcd and address 2[/FONT]
[FONT=Courier New][    3.131842] usb 2-1: configuration #1 chosen from 1 choice[/FONT]
[FONT=Courier New][    3.200052] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/FONT]
[FONT=Courier New][    3.202177] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GT10N, A108, max UDMA/100, ATAPI AN[/FONT]
[FONT=Courier New][    3.206125] ata2.00: configured for UDMA/100[/FONT]
[FONT=Courier New][    3.222465] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT10N    A108 PQ: 0 ANSI: 5[/FONT]
[FONT=Courier New][    3.230072] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray[/FONT]
[FONT=Courier New][    3.230075] Uniform CD-ROM driver Revision: 3.20[/FONT]
[FONT=Courier New][    3.230149] sr 1:0:0:0: Attached scsi CD-ROM sr0[/FONT]
[FONT=Courier New][    3.230190] sr 1:0:0:0: Attached scsi generic sg1 type 5[/FONT]
[FONT=Courier New][    3.580063] ata5: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=Courier New][    3.952565] ata6: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=Courier New][    3.970097] Freeing unused kernel memory: 660k freed[/FONT]
[FONT=Courier New][    3.970292] Write protecting the kernel read-only data: 7580k[/FONT]
[FONT=Courier New][    4.091027] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset[/FONT]
[FONT=Courier New][    4.091423] agpgart-intel 0000:00:00.0: detected 32764K stolen memory[/FONT]
[FONT=Courier New][    4.094806] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000[/FONT]
[FONT=Courier New][    4.163325] sky2 driver version 1.23[/FONT]
[FONT=Courier New][    4.163793] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18[/FONT]
[FONT=Courier New][    4.163810] sky2 0000:09:00.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    4.163844] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0[/FONT]
[FONT=Courier New][    4.163950]   alloc irq_desc for 29 on node 0[/FONT]
[FONT=Courier New][    4.163952]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    4.163971] sky2 0000:09:00.0: irq 29 for MSI/MSI-X[/FONT]
[FONT=Courier New][    4.164593] sky2 eth0: addr 00:25:64:76:6a:06[/FONT]
[FONT=Courier New][    4.169101] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17[/FONT]
[FONT=Courier New][    4.169118] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    4.183892] Initializing USB Mass Storage driver...[/FONT]
[FONT=Courier New][    4.184024] scsi6 : SCSI emulation for USB Mass Storage devices[/FONT]
[FONT=Courier New][    4.184201] usb-storage: device found at 2[/FONT]
[FONT=Courier New][    4.184202] usb-storage: waiting for device to settle before scanning[/FONT]
[FONT=Courier New][    4.184241] scsi7 : SCSI emulation for USB Mass Storage devices[/FONT]
[FONT=Courier New][    4.184324] usbcore: registered new interface driver usb-storage[/FONT]
[FONT=Courier New][    4.184327] USB Mass Storage support registered.[/FONT]
[FONT=Courier New][    4.186716] usb-storage: device found at 2[/FONT]
[FONT=Courier New][    4.186719] usb-storage: waiting for device to settle before scanning[/FONT]
[FONT=Courier New][    4.209488] [drm] Initialized drm 1.1.0 20060810[/FONT]
[FONT=Courier New][    4.220029] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT]
[FONT=Courier New][    4.220035] i915 0000:00:02.0: setting latency timer to 64[/FONT]
[FONT=Courier New][    4.227289] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining[/FONT]
[FONT=Courier New][    4.227293] [drm] MTRR allocation failed.  Graphics performance may suffer.[/FONT]
[FONT=Courier New][    4.227456]   alloc irq_desc for 30 on node 0[/FONT]
[FONT=Courier New][    4.227458]   alloc kstat_irqs on node 0[/FONT]
[FONT=Courier New][    4.227467] i915 0000:00:02.0: irq 30 for MSI/MSI-X[/FONT]
[FONT=Courier New][    4.330249] [drm] i2c_init DPDDC-D[/FONT]
[FONT=Courier New][    4.469444] [drm] fb0: inteldrmfb frame buffer device[/FONT]
[FONT=Courier New][    4.482216] acpi device:3e: registered as cooling_device2[/FONT]
[FONT=Courier New][    4.482914] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3c/input/input5[/FONT]
[FONT=Courier New][    4.482951] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)[/FONT]
[FONT=Courier New][    4.483010] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434[/FONT]
[FONT=Courier New][    4.483085] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43/input/input6[/FONT]
[FONT=Courier New][    4.483113] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)[/FONT]
[FONT=Courier New][    4.483142] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0[/FONT]
[FONT=Courier New][    4.483432] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0[/FONT]
[FONT=Courier New][    4.882448] [drm] LVDS-8: set mode 1366x768 c[/FONT]
[FONT=Courier New][    5.373574] Console: switching to colour frame buffer device 170x48[/FONT]
[FONT=Courier New][    5.567928] xor: automatically using best checksumming function: generic_sse[/FONT]
[FONT=Courier New][    5.610008]    generic_sse:  7972.800 MB/sec[/FONT]
[FONT=Courier New][    5.610010] xor: using function: generic_sse (7972.800 MB/sec)[/FONT]
[FONT=Courier New][    5.612146] device-mapper: dm-raid45: initialized v0.2594b[/FONT]
[FONT=Courier New][    9.182838] usb-storage: device scan complete[/FONT]
[FONT=Courier New][    9.182906] usb-storage: device scan complete[/FONT]
[FONT=Courier New][    9.183807] scsi 7:0:0:0: Direct-Access     HP       v125w            PMAP PQ: 0 ANSI: 0 CCS[/FONT]
[FONT=Courier New][    9.184937] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS[/FONT]
[FONT=Courier New][    9.185479] sd 6:0:0:0: Attached scsi generic sg2 type 0[/FONT]
[FONT=Courier New][    9.185614] sd 7:0:0:0: Attached scsi generic sg3 type 0[/FONT]
[FONT=Courier New][    9.186809] sd 7:0:0:0: [sdc] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)[/FONT]
[FONT=Courier New][    9.187295] sd 7:0:0:0: [sdc] Write Protect is off[/FONT]
[FONT=Courier New][    9.187298] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00[/FONT]
[FONT=Courier New][    9.187300] sd 7:0:0:0: [sdc] Assuming drive cache: write through[/FONT]
[FONT=Courier New][    9.189428] sd 6:0:0:0: [sdb] Attached SCSI removable disk[/FONT]
[FONT=Courier New][    9.190427] sd 7:0:0:0: [sdc] Assuming drive cache: write through[/FONT]
[FONT=Courier New][    9.190436]  sdc: sdc1[/FONT]
[FONT=Courier New][    9.192439] sd 7:0:0:0: [sdc] Assuming drive cache: write through[/FONT]
[FONT=Courier New][    9.192445] sd 7:0:0:0: [sdc] Attached SCSI removable disk[/FONT]
[FONT=Courier New][   11.899183] aufs 2-standalone.tree-30-20090727[/FONT]
[FONT=Courier New][   11.913245] squashfs: version 4.0 (2009/01/31) Phillip Lougher[/FONT]
[FONT=Courier New][   15.036238] kjournald starting.  Commit interval 5 seconds[/FONT]
[FONT=Courier New][   15.036287] EXT3 FS on loop1, internal journal[/FONT]
[FONT=Courier New][   15.036326] ext3_orphan_cleanup: deleting unreferenced inode 16[/FONT]
[FONT=Courier New][   15.037288] ext3_orphan_cleanup: deleting unreferenced inode 15[/FONT]
[FONT=Courier New][   15.037962] ext3_orphan_cleanup: deleting unreferenced inode 14[/FONT]
[FONT=Courier New][   15.037970] EXT3-fs: loop1: 3 orphan inodes deleted[/FONT]
[FONT=Courier New][   15.037972] EXT3-fs: recovery complete.[/FONT]
[FONT=Courier New][   15.038239] EXT3-fs: mounted filesystem with writeback data mode.[/FONT]
[FONT=Courier New][   15.041215] aufs test_add:242:exe[1124]: uid/gid/perm //filesystem.squashfs 0/0/0755, 999/999/0755[/FONT]
[FONT=Courier New][   39.582254] udev: starting version 147[/FONT]
[FONT=Courier New][   39.881993] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)[/FONT]
[FONT=Courier New][   40.078410] input: Dell WMI hotkeys as /devices/virtual/input/input7[/FONT]
[FONT=Courier New][   40.225525] Linux video capture interface: v2.00[/FONT]
[FONT=Courier New][   40.235011] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:180a)[/FONT]
[FONT=Courier New][   40.237015] input: Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8[/FONT]
[FONT=Courier New][   40.237069] usbcore: registered new interface driver uvcvideo[/FONT]
[FONT=Courier New][   40.237073] USB Video Class driver (v0.1.0)[/FONT]
[FONT=Courier New][   40.292681] cfg80211: Calling CRDA to update world regulatory domain[/FONT]
[FONT=Courier New][   40.442171] sky2 eth0: enabling interface[/FONT]
[FONT=Courier New][   40.444141] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
[FONT=Courier New][   40.456772] b43-phy0: Broadcom 4312 WLAN found (core revision 15)[/FONT]
[FONT=Courier New][   40.543197] ip_tables: (C) 2000-2006 Netfilter Core Team[/FONT]
[FONT=Courier New][   40.560465] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)[/FONT]
[FONT=Courier New][   40.560513] b43: probe of ssb0:0 failed with error -95[/FONT]
[FONT=Courier New][   40.560562] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ][/FONT]
[FONT=Courier New][   40.568739] cfg80211: World regulatory domain updated:[/FONT]
[FONT=Courier New][   40.568743]    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)[/FONT]
[FONT=Courier New][   40.568746]    (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT]
[FONT=Courier New][   40.568749]    (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/FONT]
[FONT=Courier New][   40.568751]    (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/FONT]
[FONT=Courier New][   40.568753]    (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT]
[FONT=Courier New][   40.568756]    (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT]
[FONT=Courier New][   40.745991] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input9[/FONT]
[FONT=Courier New][   40.773262] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input10[/FONT]
[FONT=Courier New][   41.266659] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21[/FONT]
[FONT=Courier New][   41.266691] HDA Intel 0000:00:1b.0: setting latency timer to 64[/FONT]
[FONT=Courier New][   42.342791] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11[/FONT]
[FONT=Courier New][   42.361189] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12[/FONT]
[FONT=Courier New][   42.361265] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13[/FONT]
[FONT=Courier New][   47.012625] lp: driver loaded but no devices found[/FONT]
[FONT=Courier New][   47.033731] ppdev: user-space parallel port driver[/FONT]
```
[/FONT]

[FONT=Courier New]I[FONT=Verdana] do see some thing that look relevant in dmesg. It does say that the driver is loaded. I'm just guessing here, but maybe we should see which position the rfkill switch is in. I'm not sure which command we would need to find that out and/or turn the wireless card on.[/FONT][/FONT]
[/FONT]

---

### Post by bkratz on 2010-02-26
some Dells seem to have a problem with rfkill. I just wanted to make you aware of this thread in case you need it.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

### Post by thomas144 on 2010-02-26
Thanks for the rfkill suggestion. I'll run the command to remove the dell-laptop thing. Since I'm using a flash drive, if I mess anything up, I could just start over. That would be no big deal. I'm connected wirelessly in Windows 7 right now. I'll boot into Ubuntu, run that command, and get back to you with the results. The command that I am going to run is
```
 
sudo rmmod -f dell-laptop

```
Thanks for the command. See you soon.

---

### Post by thomas144 on 2010-02-26
After some poking around, I don't think that I need to remove dell-laptop. However, I have found two important pieces of data:
     The first piece of data that I have learned is that I think the rfkill is unblocked on my computer. I ran the command
```
rfkill list
```
and got
```
 
0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

```
That eliminates one possible problem.
 
     The second important fact is that neither of the restricted wireless drivers are installed. I must have tried them before I screwed up my flash drive and put Ubuntu on it again, overwriting all of my settings. I would try installing a restricted driver again, but which restricted driver should I install, the Broadcom B43 wireless driver of the Broadcom STA wireless driver?

---

### Post by bkratz on 2010-02-26
To be honest I have seen either or and both used and the open source version too!  The majority of documentation such as

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Says that STA is the correct one.

---

### Post by thomas144 on 2010-02-26
Thanks! I'll try to install the STA driver and I'll probably post the results to here within an hour or so. If it doesn't work, we can go from there. Here's to hoping that it works::)

---

### Post by thomas144 on 2010-02-26
Bad news. I went to System>Administration>Hardware Drivers. I installed the STA driver and it told me that I had to reboot. I don't think that you can restart from a flash drive (it just shuts off and the boots into Windows 7). I shut down the computer and powered it back up. I went back to the restricted drivers screen and it said that the STA driver was activated but not actively in use (?!). I clicked on the Network Manager Icon and it still said that my wired connection was disconnected and "Configure VPN." I booted into Windows, shut down, and then back into Ubuntu Live. Same results .](*,)I think that the smiley illustrates that. There is a little sign that the driver may be somehow doing something. Twice, I got a thing that said that I was off of the network, and it had signal bars with an X instead of a port with an X.

---

### Post by bkratz on 2010-02-26
Here a pretty good thread, pay particular attention to posts 5 and 12.

[http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483)

---

### Post by thomas144 on 2010-02-26
The light bulb icon next to the title means we are making progress :D.
I didn't read all of the thread, but I saw post #12. Now, I'm going to follow his directions, which are:
 
1. sudo rmmod b43 ssb wl

2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source

3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
blacklist ssb
blacklist b43
blacklist wl

4. Open /etc/modules and make sure that these aren't there:
b43
ssb
wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.
 
I have a few possible issues, though. Since I have a bootable flash drive, I am not sure if I could get to /etc, which may be stored in the file casper-rl. Second, what is Jockey, and how would I use it? Or, maybe I could use bcmwl-kernel-source. The command to get that would be
```
sudo apt-get bcmwl-kernal-source
```
right? I think that I may need some additional help with following the directions. I might try to follow them, anyway.

---

### Post by bkratz on 2010-02-26
Yes just use

sudo apt-get bcmwl-kernel-source

---

### Post by bkratz on 2010-02-26
Oh forgot here is the definition of Jockey

[https://wiki.ubuntu.com/Testing/Includes/Jockey](https://wiki.ubuntu.com/Testing/Includes/Jockey)

---

### Post by thomas144 on 2010-02-27
Oh. Jockey is just fancy for System>Administration>Hardware Drivers. And now that I have the command worked out, I will try to carry out those instructions. The problem is that I can't restart--just shut down and turn back on. That shouldn't make a significant difference, I hope. OK, then. I'll go run those commands.

---

### Post by thomas144 on 2010-02-27
We have a problem. I saw something that had b43xx in it on the blacklist, but all of the documents in the folder opened as read-only. To circumvent this problem, I am just guessing that we might have to use graphical sudo.

---

### Post by efflandt on 2010-02-27
Note that once you "activate" Broadcom STA on bootable USB iso with persistent data, and reboot, if you go back to Hardware Drivers you will see that it says "activated, but not in use".

Just do **sudo modprobe wl**, and if you already (properly) set up a wireless connection in Network Connections, the network icon should start swirling and attempt to connect.

That is not necessary for a "regular installation" on hard drive or USB, but I found it necessary on bootable USB iso.  Or to automate that you could insert following in /home/ubuntu/.profile (default user) to load it automatically if not already loaded:

# load Broadcom wireless module if Dell laptop (BCM4311 or BCM4312)
if lspci | grep -q BCM431; then
        lsmod | grep -qw wl - || sudo modprobe wl
fi

I don't think you can do that in initscripts because I think those run before persistent data is mounted.

---

### Post by thomas144 on 2010-02-27
I've decided that it would probably be easier to just start over. I'll reinstall Ubuntu to my flash drive, and follow the directions that I have. I might not get around to doing this for a few days, though. I'll see you when I make that new startup disc.

---

### Post by bkratz on 2010-02-27
> **thomas144 said:**
> I've decided that it would probably be easier to just start over. I'll reinstall Ubuntu to my flash drive, and follow the directions that I have. I might not get around to doing this for a few days, though. I'll see you when I make that new startup disc.


Well we will be looking for the posting, good luck, I think you have all the answers you need and shouldn't have any problems.
( I hope )

---

### Post by thomas144 on 2010-03-01
I booted from the CD and made a startup disk. I shut down the computer and booted off of the flash drive with no trouble. I got to step 3 with no problems. Now, I have to weed through /etc/modprobe.d. I opened gedit with graphical sudo, but I came to /etc/modprobe.d/blacklist.conf. It has a set of two lines and I'm not sure if I should delete it or not. Here is the text in question:
# replaced by b43 and ssb.
blacklist bcm43xx
 
Should I delete it or leave it alone?

---

### Post by bkratz on 2010-03-01
> **thomas144 said:**
> I booted from the CD and made a startup disk. I shut down the computer and booted off of the flash drive with no trouble. I got to step 3 with no problems. Now, I have to weed through /etc/modprobe.d. I opened gedit with graphical sudo, but I came to /etc/modprobe.d/blacklist.conf. It has a set of two lines and I'm not sure if I should delete it or not. Here is the text in question:
# replaced by b43 and ssb.
blacklist bcm43xx
 
Should I delete it or leave it alone?

Just leave it alone.  It is simply saying that BCM43xx was replaced by b43 and ssb so it is blacklisted and not used.

---

### Post by thomas144 on 2010-03-04
Sorry for the long time between posts. Anyway, I'll leave that line alone, and go ahead with the intrustructions.

---

### Post by thomas144 on 2010-03-05
I am going to boot into Ubuntu, but after the 9-step process, I have saved someone's instructions that say this:
>  
Note that once you "activate" Broadcom STA on bootable USB iso with persistent data, and reboot, if you go back to Hardware Drivers you will see that it says "activated, but not in use".
Just do sudo modprobe wl, and if you already (properly) set up a wireless connection in Network Connections, the network icon should start swirling and attempt to connect.
That is not necessary for a "regular installation" on hard drive or USB, but I found it necessary on bootable USB iso. Or to automate that you could insert following in /home/ubuntu/.profile (default user) to load it automatically if not already loaded:
# load Broadcom wireless module if Dell laptop (BCM4311 or BCM4312)
if lspci | grep -q BCM431; then
lsmod | grep -qw wl - || sudo modprobe wl
fi
I don't think you can do that in initscripts because I think those run before persistent data is mounted.

How to I configure a wireless connection? Do I just go to the wireless tab and then add a connection, then enter all the information?

---

### Post by bkratz on 2010-03-05
Yes, just right click on the icon and select the wireless tab and enter the data.  If you can, I would temporarily remove encryption on the AP just to make sure you can connect, you can alway add it back after verification.

---

### Post by thomas144 on 2010-03-05
The encryption on the router is WPA-2 PSK. I just turned it off by typing my gateway IP address into my URL bar. I went into the settings and turned off the security. Now, it's slightly scary that in theory, anyone could eavesdrop on my Internet connection. But then, in practice, probably no one knows that my Internet connection is unencrypted.
Now, I'll go into Ubuntu, go to System>Administration>Network Connections. I'll also try to finish all those directions.

---

### Post by thomas144 on 2010-03-05
I clicked on the Network Manager icon, went to VPN Connections and configure VPN. I went to the Wireless tab and set up a connection with all the defaults except the SSID. I set up Infrastructure Mode, MTU as automatic, security: none, IPv4: automatic, IPv6: Ignore. Do I need to enter any other data?

---

### Post by thomas144 on 2010-03-05
I went through all of these steps:
1. sudo rmmod b43 ssb wl
2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source
3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
blacklist ssb
blacklist b43
blacklist wl
4. Open /etc/modules and make sure that these aren't there:
b43
ssb
wl
5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.
6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.
7. Reboot your computer.
8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"
9. Reboot your computer.
 
My computer still doesn't seem to know that I have a wireless card. I don't think that this approach will work. I'm not sure if I configured the network connection properly, but the wireless card is not under Network Tools and interface devices. I'm not sure where to go from here.

---

### Post by thomas144 on 2010-03-07
Hello? Is there anybody who can help?

---

### Post by migs73 on 2010-05-24
Thomas,

Quote;
'The encryption on the router is WPA-2 PSK. I just turned it off by typing my gateway IP address into my URL bar. '

Did you do this wirelessly or connected??

---

### Post by thomas144 on 2010-08-07
Migs73, I see that you've discovered my old thread long after it became inactive. While I was searching the forums, I discovered my old thread and decided to read through it. I saw your post on the end. In late May of this year (2010), I installed Ubuntu to my hard drive alongside Windows 7, which was already there. Less than 24 hours after that, I got my wireless card working. Now I have been using Ubuntu 10.04 for over two months, and I'm very satisfied with it. Thanks for offering your help, but I would like to say that everything is working. I'm going to mark this thread as solved, even if it never really solved my problems. I got my wireless card working after installing Ubuntu. A lot having to do with me and Ubuntu has changed since March.

[SIZE=3]Bottom Line: My problem is solved, or at least no longer relevant.[/SIZE]

---

