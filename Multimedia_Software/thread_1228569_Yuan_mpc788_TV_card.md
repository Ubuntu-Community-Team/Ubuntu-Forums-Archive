---
title: "Yuan mpc788 TV card"
date: 2009-08-01
forum: Multimedia Software
---

### Post by daveglover on 2009-08-01
Hi

I have just given up finally on Windows Vista Media Centre Edition, and replaced it with Ubuntu 9.04. and I am working through getting everything working. I already have 8.04 in use as a LAMP server, but I didn't have to do much to make that work!

I have been struggling for a few days with the TV card fitted into the machine, which is a Yuan MPC788 miniPCI Hybrid. I have read almost everything available on the web about this, but it is very complex for a relative newcomer. Most of the stuff seems from quite a while ago, and I was wondering if there is a definitive write up anywhere on getting this card working in Ubuntu?

Eventually I want to use something like MythTV, but in the meantime I am trying to test the card before I load up MythTV. (I did try MythTV briefly, but blew the whole thing away after tweaking far too much and too many things started not working properly.)

The card is being recognised, lsmod shows CX88xx etc. modules, but  the /dev/dvb directory has not been created. Folowing an instruction on the web to modprobe several modules, eventually I found that when I did a sudo modprobe cx88-dvb, I get    

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.28-14-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

which seems to imply that the firmware is not correct for the card. I could be totally wrong on all of this, but like I say I've spent about 4 days looking at this and this is how far I have got. Extracting firmware from the windows drivers looks a bit beyond my capabilities at this stage.

Anybody any experience in getting this TV card working in Ubuntu?

---

### Post by killerrabbit on 2009-08-17
Hello!

I'm having about the same troubles with an Yuan PG-700 (analog+DVB-T). Is yours also an hybrid card or one DVB-T, DVB-S or DVB-C?

Anyways I've done some investigations myself but am stuck so far. I'll share my info and possibly you can do the same commans to see if its an similar fault and making it easier for someone to help us :-)

enrique@ubuntu:~$ lsmod | grep -i cx88
cx88_alsa              21384  1 
snd_pcm                99464  4 snd_hda_intel,cx88_alsa,snd_pcm_oss
cx8802                 27012  0 
cx8800                 45036  0 
cx88xx                 88104  3 cx88_alsa,cx8802,cx8800
ir_common              56068  1 cx88xx
snd                    78920  19 snd_hda_intel,snd_seq_oss,snd_rawmidi,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           15364  1 cx88xx
videobuf_dvb           16516  2 cx8802,cx88xx
tveeprom               23428  1 cx88xx
compat_ioctl32         18304  1 cx8800
videodev               45184  4 tuner,cx8800,cx88xx,compat_ioctl32
v4l2_common            23296  2 tuner,cx8800
videobuf_dma_sg        22660  4 cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          29828  5 cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
btcx_risc              13960  4 cx88_alsa,cx8802,cx8800,cx88xx
enrique@ubuntu:~$ lspci -nnv -d 14f1:*
04:02.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device [12ab:3700]
    Flags: bus master, medium devsel, latency 20, IRQ 17
    Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

04:02.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device [12ab:3700]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

04:02.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
    Subsystem: Yuan Yuan Enterprise Co., Ltd. Device [12ab:3700]
    Flags: bus master, medium devsel, latency 6, IRQ 9
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel modules: cx8802

enrique@ubuntu:~$ dmesg | grep -i cx88
[   12.659068] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   12.659123] cx8800 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.659988] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   12.659990] cx88[0]: try to pick one of the existing card configs via
[   12.659991] cx88[0]: card=<n> insmod option.  Updating to the latest
[   12.659992] cx88[0]: version might help as well.
[   12.659996] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   12.660008] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   12.660011] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   12.660013] cx88[0]:    card=2 -> GDI Black Gold
[   12.660015] cx88[0]:    card=3 -> PixelView
[   12.660017] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   12.660019] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   12.660021] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   12.660023] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   12.660025] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   12.660027] cx88[0]:    card=9 -> Leadtek PVR 2000
[   12.660029] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   12.660031] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   12.660033] cx88[0]:    card=12 -> ASUS PVR-416
[   12.660035] cx88[0]:    card=13 -> MSI TV-@nywhere
[   12.660037] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   12.660039] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   12.660042] cx88[0]:    card=16 -> KWorld LTV883RF
[   12.660044] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   12.660046] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   12.660048] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   12.660050] cx88[0]:    card=20 -> Provideo PV259
[   12.660052] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   12.660054] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   12.660056] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   12.660058] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   12.660060] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   12.660063] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   12.660065] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   12.660067] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   12.660069] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   12.660071] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   12.660073] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   12.660075] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   12.660078] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   12.660080] cx88[0]:    card=34 -> ATI HDTV Wonder
[   12.660082] cx88[0]:    card=35 -> WinFast DTV1000-T
[   12.660084] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   12.660086] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   12.660088] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   12.660090] cx88[0]:    card=39 -> KWorld DVB-S 100
[   12.660092] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   12.660094] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   12.660096] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   12.660098] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   12.660100] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   12.660103] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   12.660105] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   12.660107] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   12.660109] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   12.660111] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   12.660113] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   12.660115] cx88[0]:    card=51 -> WinFast DTV2000 H ver. I (old)
[   12.660117] cx88[0]:    card=52 -> Geniatech DVB-S
[   12.660119] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   12.660121] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   12.660123] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   12.660126] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   12.660128] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   12.660130] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   12.660132] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   12.660134] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   12.660136] cx88[0]:    card=61 -> Winfast TV2000 XP Global
[   12.660138] cx88[0]:    card=62 -> PowerColor RA330
[   12.660140] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   12.660142] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   12.660144] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   12.660146] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   12.660148] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   12.660151] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
[   12.660153] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
[   12.660155] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
[   12.660157] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
[   12.660159] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
[   12.660161] cx88[0]:    card=73 -> TeVii S420 DVB-S
[   12.660163] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
[   12.660165] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
[   12.660167] cx88[0]:    card=76 -> WinFast DTV2000 H ver. J (new)
[   12.660171] cx88[0]: subsystem: 12ab:3700, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   12.660173] cx88[0]: TV tuner type -1, Radio tuner type -1
[   12.686877] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   12.888966] cx88[0]/0: found at 0000:04:02.0, rev: 5, irq: 17, latency: 20, mmio: 0xf7000000
[   12.889101] cx88[0]/0: registered device video0 [v4l2]
[   12.889131] cx88[0]/0: registered device vbi0
[   12.889385] cx88[0]/2: cx2388x 8802 Driver Manager
[   12.889451] cx88_audio 0000:04:02.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.889458] cx88_audio 0000:04:02.1: setting latency timer to 64
[   12.889485] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[ 3908.598357] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[ 3908.598362] cx88/2: registering cx8802 driver, type: dvb access: shared

And as I've understood it, you already did:

enrique@ubuntu:~$ ls -l /dev/dvb
ls: kan inte komma åt /dev/dvb: Filen eller katalogen finns inte # doesn't exist
enrique@ubuntu:~$ ls -l /dev/video0
crw-rw----+ 1 root video 81, 0 2009-08-17 13:53 /dev/video0

Are you still in limbo on this or did you find any soloution? Anybody else got a suggestion on how to solve this?

---

### Post by avacado on 2009-10-08
I am struggling with the same problems but different hardware.
I wonder if yu have made any progress?

try $ sudo modprobe cx8800 C=<your card number>

My DVICO hybrid card is sometimes recognized, but sometimes the driver does not seem to start.

even when it is recognized, w_scan does not work, just produces empty file rather than the initial scan file which is required to tune to a channel.

---

