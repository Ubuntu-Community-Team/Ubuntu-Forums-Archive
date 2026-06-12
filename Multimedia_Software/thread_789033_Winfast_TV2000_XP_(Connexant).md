---
title: "Winfast TV2000 XP (Connexant)"
date: 2008-05-10
forum: Multimedia Software
---

### Post by TransplantedCanuck on 2008-05-10
I know there are a million threads on this card, I've read them all, and followed about a dozen linked guides, etc. All without success.

I know that I need the cx8800 and cx88xx drivers loaded with the correct options (but that never seems to work). 

I seem to be learning something throughout my "Ubuntu Claw your hair out to get things working" process, since many commands just are making sense and I've started to learn whats where in the file system. :p Design? Or Chance?

So, the basic INFO:
It's a WINFAST TV2000 XP Expert  (card=5) in dmesg
I'm in germany, so PAL (tuner=5)

Right now I'd be happy to get video input, since I hear sound is another problem, but I've seen even more guides on that then just getting it to work.

TVtime keeps saying it can't find the device. If you need more info, I'll me keeping a close eye on this thread, so I'll get to you ASAP. (unless I'm sleeping).

Much love and kissies (oh the friendly sort) to whoever can help me out here. My wife loves ubuntu except for some of the things I've had to fix, the TVcard seems to be last on the list. :)


Anyway, heres the outputs I think I need...

dmesg:
```

[   54.912097] Linux video capture interface: v2.00
[   54.994510] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0xb400, speed 1169kHz
[   55.059801] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.137642] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.477430] cx2388x alsa driver version 0.0.6 loaded
[   55.524343] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 16 (level, low) -> IRQ 18
[   55.571412] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   55.571413] cx88[0]: try to pick one of the existing card configs via
[   55.571415] cx88[0]: card=<n> insmod option.  Updating to the latest
[   55.571416] cx88[0]: version might help as well.
[   55.754187] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   55.798821] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   55.843072] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   55.886840] cx88[0]:    card=2 -> GDI Black Gold
[   55.929813] cx88[0]:    card=3 -> PixelView
[   55.971957] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   56.013448] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   56.054779] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   56.095417] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   56.135366] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   56.175567] cx88[0]:    card=9 -> Leadtek PVR 2000
[   56.215295] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   56.254228] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   56.292169] cx88[0]:    card=12 -> ASUS PVR-416
[   56.329281] cx88[0]:    card=13 -> MSI TV-@nywhere
[   56.365692] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   56.401632] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   56.436788] cx88[0]:    card=16 -> KWorld LTV883RF
[   56.471032] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   56.505151] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   56.538500] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   56.571352] cx88[0]:    card=20 -> Provideo PV259
[   56.603789] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   56.636168] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   56.668283] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   56.700870] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   56.733594] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   56.766676] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   56.799630] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   56.832378] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   56.865331] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   56.897929] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   56.930446] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   56.962835] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   56.995433] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   57.027743] cx88[0]:    card=34 -> ATI HDTV Wonder
[   57.059949] cx88[0]:    card=35 -> WinFast DTV1000-T
[   57.092084] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   57.124093] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   57.156241] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   57.188296] cx88[0]:    card=39 -> KWorld DVB-S 100
[   57.220177] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   57.251979] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   57.283412] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   57.314533] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   57.345562] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   57.376349] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   57.406789] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   57.436953] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   57.466666] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   57.496103] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   57.525368] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   57.554552] cx88[0]:    card=51 -> WinFast DTV2000 H
[   57.583598] cx88[0]:    card=52 -> Geniatech DVB-S
[   57.612343] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   57.641275] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   57.669677] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   57.698425] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   57.727127] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   57.755416] cx88[0]: subsystem: 107d:6618, board: UNKNOWN/GENERIC [card=0,autodetected]
[   57.784016] cx88[0]: TV tuner type -1, Radio tuner type -1
[   57.815195] cx8800: Unknown parameter `card'

```


lspci
```

00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:09.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0e.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:0e.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```

lsmod | grep cx88
```

cx88_alsa              14216  1 
cx88xx                 66088  1 cx88_alsa
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx
snd_pcm                78596  6 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,cx88_alsa
tveeprom               16656  1 cx88xx
videodev               29440  1 cx88xx
v4l2_common            18304  2 cx88xx,videodev
videobuf_dma_sg        14980  2 cx88_alsa,cx88xx
videobuf_core          18820  2 cx88xx,videobuf_dma_sg
snd                    56996  30 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_via82xx,snd_via82xx_modem,snd_seq_dummy,snd_ac97_codec,snd_mpu401_uart,snd_seq_oss,snd_pcm_oss,cx88_alsa,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btcx_risc               5896  2 cx88_alsa,cx88xx
i2c_core               24832  5 nvidia,cx88xx,i2c_algo_bit,i2c_viapro,tveeprom

```

---

### Post by TransplantedCanuck on 2008-05-10
anyone?

---

### Post by xc3RnbFO8P on 2008-05-10
Analog is not suppoted, just the dvb:
[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek)

---

### Post by qrees on 2008-05-10
> **Ringi said:**
> Analog is not suppoted, just the dvb:
[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek)

I have this card and is working fine with MythTV. It's detected without problems. Other programs have problems with sound (they don't detect CD audio...). I didn't recompile kernel, nor add any special things, so try MythTV.

---

### Post by TransplantedCanuck on 2008-05-11
Tried mythTV and TVtime and none of them work, the problem is the card isn't recognized at boot.

---

### Post by samichx on 2008-05-17
I tried tvtime and that program did the job for me. This card is not the best I've owned in terms of quality or the other problem - power draw. Apparently every now and then it was spiking and causing my system to freeze or die out at random intervals. Picked up a USB device from the same and it works great (after learning about the nuances of USB devices in ubuntu) and I will likely buy another when the ATSC changeover hits North America.

Meow.

---

### Post by steefjeqv on 2008-05-17
Hi,

Have you tried updating your dvb drivers ?

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

You'll have to use "Case 2", mentioned on this webpage.

If you want to view DVB TV on your PC, use Kaffeine. It's available in Synaptic.

If you want a media center use VDR. It's also available in Synaptic and it's well supported by lots of (mostly German) enthusiasts.

[http://www.vdr-wiki.de/wiki/index.php/Hauptseite]("http://www.vdr-wiki.de/wiki/index.php/Hauptseite")

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

Greetings,
Steven

---

### Post by enyckma on 2008-05-30
try to change the /etc/tvtime/tvtime.xml with gedit as a root:

for volume to work with cd line input:

<!-- This sets the mixer device and channel to use.  The format is device
    name:channel name.  Valid channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor-->
<option name="MixerDevice" value="/dev/mixer:cd"/>


for video to work I think this is the line:

<!-- This sets the default capture device to use. -->
<option name="V4LDevice" value="/dev/video0"/>


excuse my english! just trying to help!!:):popcorn:

---

