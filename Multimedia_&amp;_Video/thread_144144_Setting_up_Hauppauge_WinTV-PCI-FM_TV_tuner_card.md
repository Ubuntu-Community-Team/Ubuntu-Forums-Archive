---
title: "Setting up Hauppauge WinTV-PCI-FM TV tuner card"
date: 2006-03-13
forum: Multimedia &amp; Video
---

### Post by mycroft on 2006-03-13
Hi! I just installed a Hauppauge card in my computer, but it seems to need a bit of fine tuning in Linux. I have installed tvtime, but it (the program OR the card) isn't working very well (weird colours, no channel scanning possible etc). However, I think I should first establish if the card is even recognized properly and if the correct drivers etc are loaded.

Output of *lspci -v* concerning the TV card:

```
0000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3401
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

0000:00:0a.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3401
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2
```


Output of *lsmod*:

```
Module                  Size  Used by
nvidia               3711364  12
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
analog                 10528  0
snd_mpu401              6344  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  2 analog,snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  2 snd_mpu401,snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  14 snd_mpu401,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_viapro              7696  0
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
tda9887                13208  0
cx8800                 28812  0
cx88xx                 50976  1 cx8800
ir_common               7428  1 cx88xx
v4l1_compat            12420  1 cx8800
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  2 nvidia,via_agp
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
bttv                  141456  0
video_buf              19844  3 cx8800,cx88xx,bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  2 cx88xx,bttv
v4l2_common             5888  2 cx8800,bttv
btcx_risc               4872  3 cx8800,cx88xx,bttv
tveeprom               12568  2 cx88xx,bttv
i2c_core               19728  7 i2c_acpi_ec,i2c_viapro,tda9887,cx88xx,bttv,i2c_algo_bit,tveeprom
videodev                9344  3 cx8800,cx88xx,bttv
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  366
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

These are the details returned by the info program from Hauppauge (executed in Windows):

```
Model 34519 Rev. J189
Serial #8201332
Tuner Model: TCL MFPE05_2
Tuner Formats: (B/G/I/D/K/L/L')
Tuner Audio: Stereo (CX881)
Video Formats: NTSC ( M 443 ) PAL ( B G H I D K M N NCOMBO ) SECAM ( L L' )
Audio Outputs: External
External Inputs: 2
S-Video Inputs: 1
Teletext: Yes (Software)
Radio: FM
Decoder: CX881
IR: Yes
```

As you may notice, the model number indicates ([http://www.hauppauge.com/pages/support/support.html]("http://www.hauppauge.com/pages/support/support.html")) that the card uses the 88x chip, which appears to be corroborated by the "Decoder: CX881" entry.


Any suggestions as to what I should do next?

---

### Post by pneaveill on 2007-02-22
Ever get it going?

I just got one of these also.

Here is my output, if that helps any:

lspci -v 

```

00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: Dell Unknown device 00b4
        Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 00b4
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at ff000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd000000-feffffff
        Prefetchable memory behind bridge: f8000000-f80fffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ff80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 10
        I/O ports at dcd0 [size=16]

01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
        Subsystem: Creative Labs CT4850 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at ece0 [size=32]
        Capabilities: <access denied>

01:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 05)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at ecd8 [size=8]
        Capabilities: <access denied>

01:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at f8001000 (32-bit, prefetchable) [size=4K]

01:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at f8000000 (32-bit, prefetchable) [size=4K]

01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell Unknown device 00b4
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at ec00 [size=128]
        Memory at fdfffc00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at f8020000 [disabled] [size=128K]
        Capabilities: <access denied>

``` lsmod

```

Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
vmnet                  41900  0 
vmmon                 118636  0 
ipv6                  272288  8 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  2 
lp                     12964  0 
tsdev                   9152  0 
bt878                  12472  0 
tuner                  54828  0 
tvaudio                26012  0 
msp3400                32928  0 
bttv                  176116  1 bt878
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
v4l2_common            17280  3 tuner,msp3400,bttv
btcx_risc               6280  1 bttv
tveeprom               16144  1 bttv
3c59x                  47912  0 
videodev               10752  1 bttv
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  2 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  1 snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_bt87x              16932  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
mii                     6912  1 3c59x
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
emu10k1_gp              4992  0 
gameport               17160  2 emu10k1_gp
snd_page_alloc         11400  3 snd_emu10k1,snd_bt87x,snd_pcm
snd                    58372  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_hwdep,snd_timer
soundcore              11232  1 snd
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
serio_raw               8452  0 
evdev                  11392  1 
psmouse                41352  0 
floppy                 63044  0 
i2c_i810                6276  0 
hw_random               7320  0 
i2c_algo_bit           10376  2 bttv,i2c_i810
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
i2c_core               23424  7 i2c_ec,tuner,tvaudio,msp3400,bttv,tveeprom,i2c_algo_bit
intel_agp              26012  1 
agpgart                34888  2 intel_agp
pcspkr                  4352  0 
ext3                  142856  3 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  6 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


```

---

### Post by dennis m king on 2007-03-04
i have a pvr 350 and i can watch it doing a mplayer  /dev/video0 and see great looking tv
but no other program works tvtime will not open the device and says no signel if i get this working to capture stuff from the input (i make dvds from vhs tapes a lot i will not need to boot in windows)  and the  tvtime seems to have settings to do this. 
on the mplayer i can not do anything but watch the channel it gives and it is always 4

---

### Post by williammanda on 2007-03-05
I,m still new at linux but I'm not sure linux supports your cards. Here are a couple of websites you can review:

[https://help.ubuntu.com/community/MythTV_Edgy_hardware](https://help.ubuntu.com/community/MythTV_Edgy_hardware)

[http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page)

Good luck!

---

### Post by panch0 on 2007-03-05
Since MPlayer works, I would recommend KPlayer as the frontend. It now has support for TV devices, so it will list the device under the Devices subtree, let you choose the list of channels, add channels to the playlist, and so on.

---

