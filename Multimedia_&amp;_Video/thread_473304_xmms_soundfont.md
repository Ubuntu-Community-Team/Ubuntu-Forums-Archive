---
title: "xmms soundfont"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by n_hendrick on 2007-06-13
okay I have a list of midi files, the only player that will allow playlists and conversion to mp3 is xmms, I can get xmms to play the midis using the freepats library. I can not get xmms to play using any other soundfont. You'd think it would be as easy as getting the configuration file to point to another soundfont but xmms won't play anything except freepats. The reason I need another soundfont is because freepats doesn't sound notes properly in all the musical phrases of the midis I have If I could just get this FluidSynth3 soundfont to load with xmms that would be great.
I've tried to switch between OSS ALSA in the output plugins no go. I've tried loading the soundfont manually before I initialize xmms, xmms just crashes (if I don't manually load the soundfont xmms just sits there, I'm not sure why it would crash after asfxload but it does). I've tried placing the timidity.cfg file in a base of /etc/ I've tried different soundfonts (like unison and fluid) still no go. I placed the changed soundfont into xmms-midi.cfg still won't play.  I've also tried loading different seq modules still no change. Its weird because timidity plays them just fine, but it won't run soundfonts through xmms. There has to be something I'm overlooking.....heres my specs....
Athlon Sempron 3000+ audigy 2 zs 1 gig ram Nvidia 7600 GS Hauppauge Tvcard
Heres the folloring configuration files and lsmod and lspci....

/etc/timidity/timidity.cfg
```

# Instrument configuration file for timidity
# $Id: timidity.cfg,v 1.7 2005/09/03 19:26:03 hmh Exp $

# You can change just about every option in TiMidity++ using
# This config file.  Please refer to the timidity.cfg(5) manpage
# for more details

## If you have a slow CPU, uncomment these:
#opt EFresamp=d		#disable resampling
#opt EFvlpf=d		#disable VLPF
#opt EFreverb=d		#disable reverb
#opt EFchorus=d		#disable chorus
#opt EFdelay=d		#disable delay
#opt anti-alias=d	#disable sample anti-aliasing
#opt EWPVSETOZ		#disable all Midi Controls
#opt p32a		#default to 32 voices with auto reduction
#opt s32kHz		#default sample frequency to 32kHz
#opt fast-decay		#fast decay notes

## If you have a moderate CPU, try these:
#opt EFresamp=l
#opt EFreverb=g,42
#opt EFchorus=s
#opt s32kHz
#opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:
source /usr/local/timidity/timidity_fluid3.cfg
#source /etc/timidity/freepats.cfg

```

/etc/timidity/xmms-midi.cfg
```

#source /etc/timidity/freepats.cfg
source /usr/local/timidity/timidity_fluid3.cfg

```

/etc/timidity/freepats.cfg
```

dir /usr/share/midi/freepats

# Automatically generated on Sun Feb 19 19:22:39 EST 2006
# by http://freepats.opensrc.org/mkcfg.sh.txt

drumset 0

 25	Drum_000/025_Snare_Roll.pat 
 26	Drum_000/026_Snap.pat 
 27	Drum_000/027_High_Q.pat 
 31	Drum_000/031_Sticks.pat 
 32	Drum_000/032_Square_Click.pat 
 33	Drum_000/033_Metronome_Click.pat 
 34	Drum_000/034_Metronome_Bell.pat 
 35	Drum_000/035_Kick_1.pat amp=100
 36	Drum_000/036_Kick_2.pat amp=100
 37	Drum_000/037_Stick_Rim.pat 
 38	Drum_000/038_Snare_1.pat 
 39	Drum_000/039_Clap_Hand.pat amp=100
 40	Drum_000/040_Snare_2.pat 
 41	Drum_000/041_Tom_Low_2.pat amp=100
 42	Drum_000/042_Hi-Hat_Closed.pat 
 43	Drum_000/043_Tom_Low_1.pat amp=100
 44	Drum_000/044_Hi-Hat_Pedal.pat 
 45	Drum_000/045_Tom_Mid_2.pat amp=100
 46	Drum_000/046_Hi-Hat_Open.pat 
 47	Drum_000/047_Tom_Mid_1.pat amp=100
 48	Drum_000/048_Tom_High_2.pat amp=100
 49	Drum_000/049_Cymbal_Crash_1.pat 
 50	Drum_000/050_Tom_High_1.pat amp=100
 51	Drum_000/051_Cymbal_Ride_1.pat 
 52	Drum_000/052_Cymbal_Chinese.pat 
 53	Drum_000/053_Cymbal_Ride_Bell.pat amp=100
 54	Drum_000/054_Tombourine.pat 
 55	Drum_000/055_Cymbal_Splash.pat 
 56	Drum_000/056_Cow_Bell.pat 
 57	Drum_000/057_Cymbal_Crash_2.pat 
 58	Drum_000/058_Vibra-Slap.pat 
 59	Drum_000/059_Cymbal_Ride_2.pat 
 60	Drum_000/060_Bongo_High.pat 
 61	Drum_000/061_Bongo_Low.pat 
 62	Drum_000/062_Conga_High_1_Mute.pat 
 63	Drum_000/063_Conga_High_2_Open.pat 
 64	Drum_000/064_Conga_Low.pat 
 65	Drum_000/065_Timbale_High.pat 
 66	Drum_000/066_Timbale_Low.pat 
 67	Drum_000/067_Agogo_High.pat 
 68	Drum_000/068_Agogo_Low.pat 
 69	Drum_000/069_Cabasa.pat amp=100
 70	Drum_000/070_Maracas.pat 
 71	Drum_000/071_Whistle_1_High_Short.pat 
 72	Drum_000/072_Whistle_2_Low_Long.pat 
 73	Drum_000/073_Guiro_1_Short.pat 
 74	Drum_000/074_Guiro_2_Long.pat 
 75	Drum_000/075_Claves.pat amp=100
 76	Drum_000/076_Wood_Block_1_High.pat 
 77	Drum_000/077_Wood_Block_2_Low.pat 
 78	Drum_000/078_Cuica_1_Mute.pat amp=100
 79	Drum_000/079_Cuica_2_Open.pat amp=100
 80	Drum_000/080_Triangle_1_Mute.pat 
 81	Drum_000/081_Triangle_2_Open.pat 
 82	Drum_000/082_Shaker.pat 
 84	Drum_000/084_Belltree.pat 

bank 0

 0	Tone_000/000_Acoustic_Grand_Piano.pat amp=120 pan=center
 1	Tone_000/001_Acoustic_Brite_Piano.pat 
 2	Tone_000/002_Electric_Grand_Piano.pat 
 4	Tone_000/004_Electric_Piano_1_Rhodes.pat 
 5	Tone_000/005_Electric_Piano_2_Chorused_Yamaha_DX.pat 
 6	Tone_000/006_Harpsichord.pat 
 7	Tone_000/007_Clavinet.pat 
 8	Tone_000/008_Celesta.pat 
 9	Tone_000/009_Glockenspiel.pat 
 13	Tone_000/013_Xylophone.pat 
 14	Tone_000/014_Tubular_Bells.pat 
 15	Tone_000/015_Dulcimer.pat 
 16	Tone_000/016_Hammond_Organ.pat 
 19	Tone_000/019_Church_Organ.pat 
 21	Tone_000/021_Accordion.pat 
 23	Tone_000/023_Tango_Accordion.pat 
 24	Tone_000/024_Nylon_Guitar.pat 
 25	Tone_000/025_Steel_Guitar.pat 
 26	Tone_000/026_Jazz_Guitar.pat 
 27	Tone_000/027_Clean_Electric_Guitar.pat 
 28	Tone_000/028_Muted_Electric_Guitar.pat 
 29	Tone_000/029_Overdriven_Guitar.pat 
 30	Tone_000/030_Distortion_Guitar.pat 
 32	Tone_000/032_Acoustic_Bass.pat 
 33	Tone_000/033_Finger_Bass.pat 
 34	Tone_000/034_Pick_Bass.pat 
 35	Tone_000/035_Fretless_Bass.pat 
 36	Tone_000/036_Slap_Bass_1.pat 
 37	Tone_000/037_Slap_Bass_2.pat 
 38	Tone_000/038_Synth_Bass_1.pat 
 40	Tone_000/040_Violin.pat 
 42	Tone_000/042_Cello.pat 
 44	Tone_000/044_Tremolo_Strings.pat 
 45	Tone_000/045_Pizzicato_Strings.pat 
 46	Tone_000/046_Harp.pat 
 47	Tone_000/047_Timpani.pat 
 48	Tone_000/048_String_Ensemble_1_Marcato.pat 
 53	Tone_000/053_Voice_Oohs.pat 
 56	Tone_000/056_Trumpet.pat 
 57	Tone_000/057_Trombone.pat 
 58	Tone_000/058_Tuba.pat 
 59	Tone_000/059_Muted_Trumpet.pat 
 60	Tone_000/060_French_Horn.pat 
 61	Tone_000/061_Brass_Section.pat 
 64	Tone_000/064_Soprano_Sax.pat 
 65	Tone_000/065_Alto_Sax.pat 
 66	Tone_000/066_Tenor_Sax.pat 
 67	Tone_000/067_Baritone_Sax.pat 
 68	Tone_000/068_Oboe.pat 
 69	Tone_000/069_English_Horn.pat 
 70	Tone_000/070_Bassoon.pat 
 71	Tone_000/071_Clarinet.pat 
 72	Tone_000/072_Piccolo.pat 
 73	Tone_000/073_Flute.pat 
 74	Tone_000/074_Recorder.pat 
 75	Tone_000/075_Pan_Flute.pat 
 76	Tone_000/076_Bottle_Blow.pat 
 79	Tone_000/079_Ocarina.pat 
 80	Tone_000/080_Square_Wave.pat 
 84	Tone_000/084_Charang.pat 
 88	Tone_000/088_New_Age.pat 
 94	Tone_000/094_Halo_Pad.pat 
 95	Tone_000/095_Sweep_Pad.pat 
 98	Tone_000/098_Crystal.pat 
 101	Tone_000/101_Goblins--Unicorn.pat 
 102	Tone_000/102_Echo_Voice.pat 
 104	Tone_000/104_Sitar.pat 
 114	Tone_000/114_Steel_Drums.pat 
 115	Tone_000/115_Wood_Block.pat 
 120	Tone_000/120_Guitar_Fret_Noise.pat 
 122	Tone_000/122_Seashore.pat 
 125	Tone_000/125_Helicopter.pat 

```

/usr/local/timidity/timidity_fluid3.cfg
```

# example of timidity configuration files

# paths

dir "/usr/local/timidity/cfg"	# to *.cfg

dir "/usr/local/timidity/sf2"	# to *.sf2



# fundamental SoundFont bank

source /usr/local/timidity/cfg/fluid3.cfg

```

lsmod:
```

Module                  Size  Used by
snd_rtctimer            3488  1 
binfmt_misc            11272  1 
rfcomm                 37660  0 
l2cap                  22404  5 rfcomm
bluetooth              51300  4 rfcomm,l2cap
vmnet                  36388  13 
vmmon                 111660  0 
xt_limit                2688  8 
xt_tcpudp               3328  7 
iptable_mangle          2816  0 
ipt_LOG                 6528  8 
ipt_MASQUERADE          3456  0 
nf_nat                 17964  1 ipt_MASQUERADE
ipt_TOS                 2304  0 
ipt_REJECT              4608  1 
nf_conntrack_irc        7064  0 
nf_conntrack_ftp        9728  0 
nf_conntrack_ipv4      17932  7 
xt_state                2560  6 
nf_conntrack           59864  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               6680  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3072  1 
ip_tables              12232  2 iptable_mangle,iptable_filter
x_tables               15108  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
ppdev                   9220  0 
cpufreq_powersave       1792  0 
cpufreq_conservative     6560  0 
cpufreq_ondemand        7676  0 
cpufreq_userspace       4116  0 
cpufreq_stats           5508  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats
dev_acpi               11140  0 
tc1100_wmi              7172  0 
sony_acpi               5388  0 
pcc_acpi               12160  0 
asus_acpi              16412  0 
button                  7696  0 
sbs                    14752  0 
i2c_ec                  5120  1 sbs
video                  15492  0 
ac                      5124  0 
container               4352  0 
dock                    9216  0 
battery                 9860  0 
backlight               6016  1 asus_acpi
ipv6                  252768  12 
sbp2                   23044  0 
parport_pc             34980  0 
lp                     11332  0 
parport                35272  3 ppdev,parport_pc,lp
fuse                   44436  0 
snd_emu10k1_synth       7296  0 
snd_emux_synth         34688  1 snd_emu10k1_synth
snd_seq_virmidi         6784  1 snd_emux_synth
snd_seq_midi_emul       6784  1 snd_emux_synth
snd_emu10k1           120352  2 snd_emu10k1_synth
snd_ac97_codec         97312  1 snd_emu10k1
snd_bt87x              15012  0 
ac97_bus                2304  1 snd_ac97_codec
snd_util_mem            4864  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_hwdep               9092  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_pcm                76680  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_page_alloc          9992  3 snd_emu10k1,snd_bt87x,snd_pcm
bt878                  10920  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                49648  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  4 snd_rtctimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tuner                  60840  0 
tvaudio                23196  0 
bttv                  170356  1 bt878
video_buf              25348  1 bttv
ir_common              30340  1 bttv
nvidia               6834708  22 
joydev                  9920  0 
snd                    51716  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          1408  1 bttv
i2c_algo_bit            7816  1 bttv
sg                     35484  0 
btcx_risc               5000  1 bttv
rtc                    13232  1 snd_rtctimer
soundcore               7520  1 snd
emu10k1_gp              3840  0 
gameport               15112  2 emu10k1_gp
tveeprom               14992  1 bttv
videodev               27136  1 bttv
v4l2_common            24192  3 tuner,bttv,videodev
v4l1_compat            14340  1 videodev
pcspkr                  3072  0 
psmouse                37640  0 
sd_mod                 22292  0 
xpad                    8964  0 
usbhid                 25056  0 
hid                    25728  1 usbhid
serio_raw               6916  0 
shpchp                 33300  0 
pci_hotplug            31160  1 shpchp
i2c_nforce2             5888  0 
i2c_core               21648  8 i2c_ec,tuner,tvaudio,bttv,nvidia,i2c_algo_bit,tveeprom,i2c_nforce2
nvidia_agp              8604  1 
agpgart                34096  2 nvidia,nvidia_agp
af_packet              20872  2 
tsdev                   7872  0 
evdev                  10112  3 
usb_storage            70976  0 
ext3                  129288  2 
jbd                    53032  1 ext3
mbcache                 8196  1 ext3
libusual               17040  1 usb_storage
ide_cd                 31648  0 
cdrom                  36512  1 ide_cd
ide_disk               16000  5 
amd74xx                14236  0 [permanent]
generic                 4228  0 [permanent]
ata_generic             8196  0 
ohci1394               35376  0 
ieee1394              297656  2 sbp2,ohci1394
sata_nv                19716  0 
libata                125208  2 ata_generic,sata_nv
scsi_mod              141580  5 sbp2,sg,sd_mod,usb_storage,libata
forcedeth              44936  0 
ehci_hcd               32780  0 
ohci_hcd               21252  0 
usbcore               131480  7 xpad,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                13832  0 
processor              22956  1 thermal
fan                     4740  0 
fbcon                  41760  0 
tileblit                2688  1 fbcon
font                    8320  1 fbcon
bitblit                 6016  1 fbcon
softcursor              2304  1 bitblit
vesafb                  8196  0 
capability              5000  0 
commoncap               7296  1 capability

```

lspci:
```

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GS (rev a2)
02:06.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

```

/etc/default/timidity
```

# Defaults for TiMidity++ scripts
# sourced by /etc/init.d/timidity
# installed at /etc/default/timidity by the maintainer scripts
# $Id: timidity.default,v 1.3 2004/08/07 14:33:26 hmh Exp $

#
# This is a POSIX shell fragment
#

# Enable MIDI sequencer (ALSA), default is disabled
TIM_ALSASEQ=true

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="-B2,8 -Os"

```

/etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq

```

My xmms midi plugin is 0.3-4 xmms is the newest cvs and timidity is the newest for the distribution. Oh yeah, I'm running Feisty 7.04 and Alsa 1.0.13.
I would really like to get soundfonts to recognize through xmms, any help is appreciated.

---

### Post by n_hendrick on 2007-06-14
*bump* Anyone know anything about this?

---

