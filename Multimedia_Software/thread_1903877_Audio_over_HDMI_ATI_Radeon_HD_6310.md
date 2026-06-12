---
title: "Audio over HDMI ATI Radeon HD 6310"
date: 2012-01-03
forum: Multimedia Software
---

### Post by HuckBerry on 2012-01-03
This is a re-post from the Hardware Support Forums.

I recently got an ASRock E350M1/USB3 Mini-ITX motherboard. I was super excited about using the board for a HTPC given its low power consumption. 

I installed 10.04.3 LTS because I had it handy and because I prefer LTS versions. Most things worked out-of-the-box, except I can't seem to get any audio over the HDMI port.

I've been searching around the net for a few days but haven't found anything promising. I did poke around ALSA's website, but their lists seem focused only on soundcards and not graphics cards with audio over HDMI. (EDIT: also check out [this]("http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO") ubuntu.org page) I've included some information on the hardware being used:

Motherboard:
[NewEgg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157247")

lspci:
```

me@GAMMA:~$ sudo lspci -vv -n
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
	Subsystem: ASRock Incorporation Device [1849:9802]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at f000 [size=256]
	Region 2: Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Vendor Specific Information <?>

00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1314]
	Subsystem: ASRock Incorporation Device [1849:1314]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: ASRock Incorporation Device [1849:1892]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

lshw:
```

me@GAMMA:~$ sudo lshw -class multimedia
  *-multimedia:0          
       description: Audio device
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:feb44000-feb47fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:feb40000-feb43fff

```

modprobe:
```

me@GAMMA:/etc/X11$ lsmod
Module                  Size  Used by
radeon                678831  0 
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
drm                   163747  3 radeon,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          22069  6 
snd_hda_codec          74201  3 snd_hda_codec_realtek,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54244  22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
psmouse                63677  0 
serio_raw               3978  0 
xhci                   37160  0 
joydev                  8740  0 
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
hid_logitech            7388  0 
ff_memless              4093  1 hid_logitech
usbhid                 36110  1 hid_logitech
hid                    67288  2 hid_logitech,usbhid
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169
pata_atiixp             3148  0 

```

---

### Post by bryanl on 2012-01-03
in the sound preferences, check the hardware tab and make sure that the HDMI is there and that it is selected. There is a profile and a 'test speakers' button there as well that you can use to see if the hardware is set. (if HDMI isn't there, then the lspci and drivers and whatnot become a significant hassle IMHO)

The second thing to check is on the output tab where the device for sound output needs to have HDMI selected.

After that, run alsamixer (install it if need be, it's a nice console app) and make sure that the input and output levels are set for what you need.

---

### Post by PeterTaps on 2012-01-03
Also, make sure that you install AMD/ATI drivers (and the updates). Without this, sound will not work.

I used the following command:

[I]$sudo apt-get install fglrx fglrx-updates fglrx-updates fglrx-amdcccle-updates 

However, a recent post suggested that just fglrx-updates will update everything:

[/I]$ sudo apt-get install fglrx-updates

Regards,
Peter

---

### Post by HuckBerry on 2012-01-05
I forgot to mention in my OP that I had gone to sound preferences and set the onboard sound card's profile to 'off' and double checked that the HDMI was selected in the output tab. I also checked alsa mixer. The alsa mixer descriptions didn't match what I had been seeing in lshw and lspci, but i unmuted everything just in case.

I booted up a mint live CD because someone in another forum reported success with a different motherboard that also had the 6310. In mint, the HDMI audio appears as [Radeon HD 6250/6310] instead of [Radeon 6310]. From that information I found this site:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

which lists compatibility with my card specifically. Sadly, in mint the HDMI audio did not work. However the onboard southbridge audio did work. That's using the HDA Intel driver (same as ubuntu). Very odd.

Here is all the same commands from above, but from a mint 12 live CD and lsmod instead of modprobe.

lspci:
```

mint@mint ~ $ sudo lspci -vv -n
00:01.0 0300: 1002:9802 (prog-if 00 [VGA controller])
    Subsystem: 1849:9802
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at f000 [size=256]
    Region 2: Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0200c  Data: 4169
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 0403: 1002:1314
    Subsystem: 1849:1314
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 43
    Region 0: Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0100c  Data: 4171
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.2 0403: 1002:4383 (rev 40)
    Subsystem: 1849:1892
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```lshw:

```

mint@mint ~ $ sudo lshw -class multimedia
  *-multimedia:0          
       description: Audio device
       product: Wrestler HDMI Audio [Radeon HD 6250/6310]
       vendor: ATI Technologies Inc
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:43 memory:feb44000-feb47fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:feb40000-feb43fff

```lsmod (I'll go back and edit my OP to show lsmod too)

```

mint@mint ~ $ sudo lsmod
Module                  Size  Used by
joydev                 17393  0 
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
snd_hda_codec_realtek   254125  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  1 
snd_hda_codec          91754  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
k10temp                12990  0 
snd                    55902  12 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
radeon                925020  3 
usbhid                 41905  1 hid_logitech
usb_storage            44173  1 
hid                    77367  2 hid_logitech,usbhid
uas                    17699  0 
xhci_hcd               72915  0 
r8169                  43104  0 
ahci                   21634  1 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
libahci                25727  1 ahci
pata_atiixp            12967  0 
i2c_algo_bit           13199  1 radeon

```

---

### Post by HuckBerry on 2012-01-08
UPDATE:
I installed Mint 12 on a Whim and it detected a non-free driver for my hardware. It is possible that 10.04 didn't have this driver in its repos (even though it's LTS) so I installed it. The driver (fglrx) caused Mint's composed desktop to go crazy, but audio over HDMI worked. A little research yielded that there is a specific compatibility issue with ATI's non-free driver and GNOME3. I installed Mint 11 and things seem to be better. 

Everything appears to work now under Mint 11 w/ ATI's driver, so I'll see if I can't replicate it under Maverick (Mint 11's foundation). ATI's driver fails to handle 1080p very well, and still stumbles on 720p. I'm going to try it under windows with ATI's windows driver to see if it is the driver or the hardware and report back.

---

