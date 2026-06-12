---
title: "A TV Card that will $#%#$% work?!"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by netboy541 on 2007-05-19
Hello Folks.

I have battled a tv card I purchased for months (since march) and have finally given up.  It works in under 3 minutes in Windows, and here we are in May, and I still can't get it to work.  

The TV card thread:
[http://ubuntuforums.org/showthread.php?t=386651](http://ubuntuforums.org/showthread.php?t=386651)


Anyway, since I have thrown in the towel (unless someone knows how to make it work), I still have no TV card, and would like to correct this, but before I buy yet another TV card, I wanted to ask the ubuntu community what TV card for a LAPTOP will work with minimal aggravation...

A few things to know:

#1 - I am in the United States.  We use NTSC here.  Please don't suggest PAL only cards!
#2 - I do not want to spend an arm and a leg.
#3 - remotes and other fancy whistles are not a big deal to me.  This is for my laptop! 
#4 - I run Kubuntu Fiesty 7.04 on a Toshiba a45-s120 laptop.
#5 - I prefer PCMCIA, but USB will do if that's all there really is.

Thanks a bunch for all your help! :)

---

### Post by fenian on 2007-05-19
I don't think the saa7134 module is loaded at boot in feisty,to get it to load at boot run this command (if you haven't done so already)

                  > sudo sh -c "echo "saa7134" >> /etc/modules"

PCMCIA tv tuners don't work really well under windows (too slow for framegrabber)  and getting them to work at all in linux seems like a huge pain.I think USB is the best option for a laptop tuner this[Hauppauge USB stick]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") looks nice and appears to work with Feisty and Edgy.

---

### Post by netboy541 on 2007-05-20
I ordered one.  Found it for like 65 dollars.  W0rd. :)

Looks like it's pretty dog-gone simple to get to go.  I don't mind working a little bit, but that one I had I still can't get to go, so I'm shipping it to Dad Tuesday.  He runs XP, and it'll work in under 3 minutes.  lol


Thanks for your help!

---

### Post by netboy541 on 2007-05-25
So, i received this tv card.

got a killer picture, but can't get sound to save my life.

anyone got any ideas how to make the sound work?

I hooked it up to my cable tv, and was quite pleased with the picture, but if I have no sound, it does me no good.


Thanks in advanced!

---

### Post by fenian on 2007-05-25
Open up TVTime then open a terminal and run...
> 
sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

if that doesn't work try running...
> 
sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp 

---

### Post by netboy541 on 2007-05-25
BRILLIANT! :D

Second line worked like a charm.

Thanks a million!!

---

### Post by bliffle on 2007-07-17
Well, I've got the Hauppage 950 as well as the Diamond HDTV100, and it doesn't work either.

In fact, I think it's not recognized in the IO layer at all, tho the dmesg says:

[ 5295.356000] EEPROM ID= 0x9567eb1a
[ 5295.356000] Vendor/Product ID= 2040:6513
[ 5295.356000] AC97 audio (5 sample rates)
[ 5295.356000] 500mA max power
[ 5295.356000] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[ 5295.356000] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 1908334
[ 5295.356000] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[ 5295.356000] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[ 5295.356000] tveeprom 0-0050: audio processor is None (idx 0)
[ 5295.356000] tveeprom 0-0050: has radio
[ 5295.360000] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[ 5295.360000] attach inform (default): detected I2C address c2
[ 5295.360000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 5295.360000] tuner 0x61: Configuration acknowledged
[ 5295.360000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 5295.360000] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[ 5295.360000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: xc3028 tuner successfully loaded
[ 5295.364000] attach_inform: tvp5150 detected.
[ 5295.432000] tvp5150 0-005c: tvp5150am1 detected.
[ 5295.520000] Loading base firmware: xc3028_init0.i2c.fw
[ 5296.556000] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[ 5296.580000] xc3028-tuner.c: firmware 2.7
[ 5296.580000] ANALOG TV REQUEST
[ 5296.588000] em28xx #0: V4L2 device registered as /dev/video0
[ 5296.588000] em2880-dvb.c: DVB Init
[ 5296.588000] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[ 5297.816000] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw
[ 5297.840000] xc3028-tuner.c: firmware 2.7
[ 5297.840000] Sending extra call for Digital TV!
[ 5297.944000] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[ 5297.944000] DVB: registering new adapter (em2880 DVB-T)
[ 5297.944000] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 5297.944000] em28xx-audio.c: probing for em28x1 non standard usbaudio
[ 5297.944000] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[ 5297.944000] em28xx #0: Found Hauppauge WinTV HVR 950

And the lsmod:

Module                  Size  Used by
lgdt330x               10244  1 
em28xx_audio            7940  0 
tvp5150                20752  0 
qt1010                  7812  0 
mt2060                  6532  0 
xc3028_tuner            9984  2 
mt352                   8328  0 
zl10353                 7816  0 
tuner                  68008  0 
em2880_dvb             14980  0 
em28xx                 96180  2 em28xx_audio,em2880_dvb
compat_ioctl32          2304  1 em28xx
ir_common              40068  1 em28xx
videodev               29312  1 em28xx
v4l2_common            18432  4 tvp5150,tuner,em28xx,videodev
v4l1_compat            15236  2 em28xx,videodev
tveeprom               16784  1 em28xx
dvb_core               82600  2 lgdt330x,em2880_dvb
michael_mic             3584  4 
arc4                    2944  4 
ecb                     4480  4 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  2 
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nvram                   9992  1 
uinput                 10240  1 
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_centrino      9920  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
button                  8720  0 
container               5248  0 
battery                10756  0 
asus_acpi              17308  0 
sbs                    15652  0 
dock                   10268  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  11 lgdt330x,tvp5150,qt1010,mt2060,xc3028_tuner,mt352,zl10353,tuner,em28xx,tveeprom,i2c_ec
ibm_acpi               31512  0 
backlight               7040  2 asus_acpi,ibm_acpi
video                  16388  0 
ac                      6020  0 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nsc_ircc               24208  0 
ipw2100                72244  0 
irda                  201276  3 irtty_sir,sir_dev,nsc_ircc
snd                    54020  13 em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
ieee80211              34760  1 ipw2100
serio_raw               7940  0 
soundcore               8672  1 snd
psmouse                38920  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
pcspkr                  4224  0 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
agpgart                35400  2 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  6 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  3 sg,sd_mod,libata
floppy                 59524  0 
e1000                 126016  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 em28xx_audio,em2880_dvb,em28xx,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

Nothing in lspci:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: IBM Unknown device 0529
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
	I/O behind bridge: 00004000-00008fff
	Memory behind bridge: c0200000-cfffffff
	Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: medium devsel, IRQ 11
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: IBM Unknown device 0537
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at c0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
	Subsystem: IBM Unknown device 0524
	Flags: medium devsel, IRQ 11
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
	Subsystem: IBM Unknown device 0530
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
	Subsystem: IBM Unknown device 0552
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: e8000000-ebfff000 (prefetchable)
	Memory window 1: c4000000-c7fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
	Subsystem: IBM Unknown device 0552
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: ec000000-effff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
	Subsystem: IBM PRO/1000 MT Mobile Connection
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at c0220000 (32-bit, non-prefetchable) [size=128K]
	Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 8000 [size=64]
	[virtual] Expansion ROM at c0240000 [disabled] [size=64K]
	Capabilities: <access denied>

02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Unknown device 2551
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

And bringing up "tvtime" is just a bluescreen, no source, no signal.

---

### Post by gmc on 2007-07-18
Hi bliffle,

> **bliffle said:**
> Well, I've got the Hauppage 950 as well as the Diamond HDTV100, and it doesn't work either.

[lots deleted]

And bringing up "tvtime" is just a bluescreen, no source, no signal.


Uhm, TVTime doesn't support mpeg2 devices. If your Hauppage is anything like mine, you should be able to issue 'cat /dev/video0 > test.mpeg' and then play that file from mplayer or vlc.

Gord

---

### Post by netboy541 on 2007-07-18
Howdy!

I had to install a few drivers to make my usb stick work.  After I did that, it worked like a champ, and still does!  I use TV Time, as I have no need to record the shows, I just want to watch TV when I'm bored or something.... and play PS2. :)

I went to [this site]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") to install the drivers, and it worked the first time.

You do have USB 2.0 right?  Using 1.1 with this device seems to cause weird things to happen....
Also, if I install the module for my modem, then my TV card sound will not work no matter what I do... 
Just thought I'd throw that in there too.... 


HTH

You Said:

Well, I've got the Hauppage 950 as well as the Diamond HDTV100, and it doesn't work either.

In fact, I think it's not recognized in the IO layer at all, tho the dmesg says:

<SNIP>

And bringing up "tvtime" is just a bluescreen, no source, no signal.


--------------------------

---

### Post by LeGollemux on 2007-07-18
Hi all, I am hoping someone can help. I have a saa7134 chipset card. Got it working with the help of previous posts in this forum. I can see video in both TVtime and VLC. the sox command line gets me sound in TVtime but I am unable to get sound in VLC.

The command line I am running VLC with is: "vlc -vvv --color v4l:/dev/video0:norm=0:channel=1:size=320x240”

any ideas??

---

### Post by david_2001 on 2007-07-18
> **LeGollemux said:**
> Hi all, I am hoping someone can help. I have a saa7134 chipset card. Got it working with the help of previous posts in this forum. I can see video in both TVtime and VLC. the sox command line gets me sound in TVtime but I am unable to get sound in VLC.

The command line I am running VLC with is: "vlc -vvv --color v4l:/dev/video0:norm=0:channel=1:size=320x240&#8221;

any ideas??

Assuming that you have the saa7134_alsa module loaded (lsmod | grep saa7134_alsa to check) then open Gnome Volume Control, change device to SAA7134 (ALSA Mixer) and then on the Switches tab check Video Capture.  (If the Video Capture switch is missing, add it from Edit | Preferences.)  Note that sound output isn't completely reliable (you'll find out if you try to move the Video Playback mixers!) and a fix involves installing the latest V4L from Mercurial.

---

### Post by LeGollemux on 2007-07-18
Thank you for the quick reply. And I do think you have something there. I have noticed that there are 3 different sound settings on the settings tab. One of them is saa7134 alsa so its definately listed.

What Ill do is install/re-install the alsa side of things and come back to you with a reply.

---

### Post by bliffle on 2007-07-18
> **gmc said:**
> Hi bliffle,


Uhm, TVTime doesn't support mpeg2 devices. If your Hauppage is anything like mine, you should be able to issue 'cat /dev/video0 > test.mpeg' and then play that file from mplayer or vlc.

Gord

I did the "cat /dev/video0 > test.mpeg" and it started making a huge file, so I ctl-c'ed it to stop then ran "vlc test.mpeg"  and got a pixillating picture for a few seconds. I don't want/need to record, just to view live. vlc seems to be my most reliable video player. But I'm guessing I've gotta play the TV stick from something that can set the channels, like TVtime. Or is there a way to get tvtime to use /dev/video0 as input?

---

### Post by bliffle on 2007-07-18
> **david_2001 said:**
> Assuming that you have the saa7134_alsa module loaded (lsmod | grep saa7134_alsa to check) then open Gnome Volume Control, change device to SAA7134 (ALSA Mixer) and then on the Switches tab check Video Capture.  (If the Video Capture switch is missing, add it from Edit | Preferences.)  Note that sound output isn't completely reliable (you'll find out if you try to move the Video Playback mixers!) and a fix involves installing the latest V4L from Mercurial.

OK, I tried the lsmod | grep saa7134_alsa

and got:

root@JHT40UUU:/home/john# lsmod | grep saa7134_alsa
saa7134_alsa           15392  0 
saa7134               130764  1 saa7134_alsa
video_buf              26116  2 saa7134_alsa,saa7134
snd_pcm                79876  5 saa7134_alsa,em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  14 saa7134_alsa,em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Does that confirm the 7134 is OK?

How do I open the Gnome Volume Control? Is that from the <System...preferences...sound> menubar?

Anyhow, I'm not getting video anyhow.

---

### Post by bliffle on 2007-07-18
Well, at last I've got analog TV going in tvtime, that's a first. No sound, of course, but I'm not surprised since I even have sound problems playing MP3s, which I can usually solve by diddling "alsamixer". And I know I've pulled up a GUI version of alsamixer, somehow, in the past, but I can't seem to do it now.

Anyway, I'm still searching for a way to view the live Digital feed from the 950 thru the USB. If TVTIME doesn't/won't do it, what will? If 'vlc' (an old fave for reliability) then how do I select channel?

---

### Post by bliffle on 2007-07-18
When I run the vlc command mentioned earlier in this thread:

vlc -vvv --color v4l:/dev/video0:norm=0:channel=1:size=320x240

vlc comes up and stuff appears in the statusbar but no audible sound and no video. The 'video' menuitem is gray but the 'audio' menuitem is enabled. the system stats show audio as being decoded but no video.

---

### Post by bliffle on 2007-07-18
the vlc doc at sourceforge doesn't say anything about the "-vvv" parameter.

lsusb yields:

root@JHT40UUU:/home/john# lsusb
Bus 004 Device 004: ID 2040:6513 Hauppauge 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by david_2001 on 2007-07-19
> **bliffle said:**
> OK, I tried the lsmod | grep saa7134_alsa

and got:

root@JHT40UUU:/home/john# lsmod | grep saa7134_alsa
saa7134_alsa           15392  0 
saa7134               130764  1 saa7134_alsa
video_buf              26116  2 saa7134_alsa,saa7134
snd_pcm                79876  5 saa7134_alsa,em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  14 saa7134_alsa,em28xx_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Does that confirm the 7134 is OK?

Yes.  You only need to know that it's there.
> How do I open the Gnome Volume Control? Is that from the <System...preferences...sound> menubar

If you have a normal Gnome installation then right click the speaker icon in the system tray (top right).  Otherwise, run gnome-volume-control in a terminal.
> 
Anyhow, I'm not getting video anyhow.
The saa7134 modules aren't relevant to the Hauppauge 950, though you do seem to have the em28xx_audio module loaded, which will help.

---

### Post by bliffle on 2007-07-19
I knew I'd seen that GUI volume control before. Seems to be a subset of the 'alsamixer' text volume display.

Still, I have no digital video.

---

### Post by LeGollemux on 2007-07-20
ok, Im not getting anywhere here. I have video, no problem. but!! no matter what I try I am unable to get sound. I know the sound is working, ubuntu system sounds play.

I have tried the sox option, and various other things. 

The command line Im using is " vlc -vvv v4l:/video0:dev/dsp1:norm=0:channel=1:size=320x240

video0 = my TV card (philips saa7134 chipset)
dsp1    = Alsa7134 (dsp is normal alsa)
norm  = buggered if I know (wont display without it)
channel = (0-television, 1 composite, 3 s-video)
size = duh

is there anyone that can give an opinion on why the sound wont work? at this point Im being told that it would have taken 5 minutes to get it working in that other OS. 

Something I noticed. If you put an extra space in the command line you get a chroma error message. hows that for wierd!!!!

---

### Post by david_2001 on 2007-07-20
> **LeGollemux said:**
> ok, Im not getting anywhere here. I have video, no problem. but!! no matter what I try I am unable to get sound. I know the sound is working, ubuntu system sounds play.

I have tried the sox option, and various other things. 

The command line Im using is " vlc -vvv v4l:/video0:dev/dsp1:norm=0:channel=1:size=320x240

video0 = my TV card (philips saa7134 chipset)
dsp1    = Alsa7134 (dsp is normal alsa)
norm  = buggered if I know (wont display without it)
channel = (0-television, 1 composite, 3 s-video)
size = duh

is there anyone that can give an opinion on why the sound wont work? at this point Im being told that it would have taken 5 minutes to get it working in that other OS. 

Something I noticed. If you put an extra space in the command line you get a chroma error message. hows that for wierd!!!!
Ok, I don't normally use vlc to play TV but I worked on the command line a little and came up with the following that plays with sound here:
```
vlc -vvv v4l:/dev/video2:norm=0:channel=0:size=320x240:adev=/dev/dsp1:samplerate=32000:frequency=543250
```
Note that my analogue TV card is /dev/video2, "norm" is the TV norm (0 is PAL), "adev" is the oss audio device associated with the card by the saa7134_alsa module (if alsa-oss is installed), "samplerate" is the usual audio output sample rate for a saa7134 card (32kHz) and frequency is the TV channel to tune (UK Channel 4 from Crystal Palace in this example).  To make the console output a little less verbose, take out the "-vvv".

---

### Post by LeGollemux on 2007-07-23
Ok, I have had a measure of success, I did the following:

rmmod saa7134_alsa
rmmod saa7134. 
sudo modprobe tuner (the different card numbers were having no effect.)
sudo modprobe saa7134
sudo modprobe saa7134_alsa.

Then I installed tvtime and sox. 

type : tvtime | arecord -D hw:1,0 -r 32000 -c 2 S16_LE | sox -q -c 2 -r 32000 -w -t wav hw:0,0

( I am only running composite into the card) keep this in mind, your going to love the next part.

TVtime runs fine, set to composite, great picture...no sound...wait for it.....change to Svideo, great sound, no picture. AAAAAARGH!!!!! 

so close..... *sob*

---

### Post by david_2001 on 2007-07-23
> **LeGollemux said:**
> TVtime runs fine, set to composite, great picture...no sound...wait for it.....change to Svideo, great sound, no picture. AAAAAARGH!!!!! 

so close..... *sob*

In general, support for saa7134 cards is very good.  Can you let us know the exact make/model of your TV card - it might help - and post the console output from running "dmesg | grep saa".

---

### Post by LeGollemux on 2007-07-24
ok, the card is a Gigabyte: **Global TV Card part**[/B]# GT-PTV-AF-RH.

the label on the back also mentions that it is a Philips SAA7131E solution.

The output for dmesg | grep saa is :

dcmedia@dcmedia-tv:~$ dmesg | grep saa
[   12.296010] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.296105] saa7133[0]: found at 0000:01:01.0, rev: 209, irq: 16, latency: 96, mmio: 0xe1004000
[   12.296114] saa7133[0]: subsystem: 1458:9003, board: AVerMedia Cardbus TV/Radio (E500) [card=46,insmod option]
[   12.296124] saa7133[0]: board init: gpio is c000000
[   12.438747] saa7133[0]: i2c eeprom 00: 58 14 03 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   12.438764] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   12.438779] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c2 ff ff ff ff
[   12.438793] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.438808] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 50 ff ff ff ff ff ff
[   12.438823] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.438838] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.438853] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.526747] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   12.833224] saa7133[0]: registered device video0 [v4l2]
[   12.833252] saa7133[0]: registered device vbi0
[   12.833281] saa7133[0]: registered device radio0
[   12.855490] saa7134 ALSA driver for DMA sound loaded
[   12.855525] saa7133[0]/alsa: saa7133[0] at 0xe1004000 irq 16 registered as card -2
[  915.901327] saa7134 ALSA driver for DMA sound unloaded
[  962.775284] saa7134: `' invalid for parameter `tuner'
[ 1004.713859] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 1004.713934] saa7133[0]: found at 0000:01:01.0, rev: 209, irq: 16, latency: 96, mmio: 0xe1004000
[ 1004.713947] saa7133[0]: subsystem: 1458:9003, board: AVerMedia Cardbus TV/Radio (E500) [card=46,insmod option]
[ 1004.713960] saa7133[0]: board init: gpio is effffff
[ 1004.896943] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 1005.232451] saa7133[0]: i2c eeprom 00: 58 14 03 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 1005.232473] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[ 1005.232497] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c2 ff ff ff ff
[ 1005.232521] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1005.232544] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 50 ff ff ff ff ff ff
[ 1005.232598] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1005.232622] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1005.232646] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1007.695305] saa7133[0]: registered device video0 [v4l2]
[ 1007.695495] saa7133[0]: registered device vbi0
[ 1007.695656] saa7133[0]: registered device radio0
[ 1007.722265] saa7134 ALSA driver for DMA sound loaded
[ 1007.722646] saa7133[0]/alsa: saa7133[0] at 0xe1004000 irq 16 registered as card -2


Any help is appreciated.

---

### Post by david_2001 on 2007-07-24
Finding information about running this card under Linux in a language that I can comprehend turns out to be not easy.  Card number 46 is probably not going to be the one to use and my searches indicate that passing card number 81 to the saa7134 driver may bring better results (as a fall-back position, try card number 69).

---

### Post by starfleetcaptainrob on 2007-07-24
I have the Hauppauge WinTV-HVR-950 as well and can't seem to get it to work.  I think I saw in this thread that Biffle was having problems getting TVtime to use it and was just getting a blue screen.  I'm having the same issue and can't seem to figure it out.  I followed the instructions from this site:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")

when I do lsusb it shows that the card is being recognized:

```
fredbear@megatron:~$ lsusb
Bus 006 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 2040:6513 Hauppauge 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

when I type in lsmod | grep saa7134_alsa it gives me this:

```
fredbear@megatron:~$ lsmod | grep saa7134_alsa
saa7134_alsa           15392  0 
saa7134               130764  2 saa7134_dvb,saa7134_alsa
video_buf              26116  4 saa7134_dvb,saa7134_alsa,saa7134,video_buf_dvb
snd_pcm                79876  6 saa7134_alsa,em28xx_audio,snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd                    54020  20 saa7134_alsa,em28xx_audio,snd_usb_audio,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep

```

Under my dev folder i've got /dvb/adapter0/dvr0 and I've tried editing the XML file for TVtime to make it point to that, but that doesn't seem to work either.  I'm completely out of ideas and am hoping someone can help!  I know this card has worked for other people, I just don't understand why I can't get it to work.  Anyhow, any help would be appreciated.

---

### Post by david_2001 on 2007-07-25
> **starfleetcaptainrob said:**
> I have the Hauppauge WinTV-HVR-950 as well and can't seem to get it to work.  I think I saw in this thread that Biffle was having problems getting TVtime to use it and was just getting a blue screen.  I'm having the same issue and can't seem to figure it out.  I followed the instructions from this site:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")

[Cut]

Under my dev folder i've got /dvb/adapter0/dvr0 and I've tried editing the XML file for TVtime to make it point to that, but that doesn't seem to work either.  I'm completely out of ideas and am hoping someone can help!  I know this card has worked for other people, I just don't understand why I can't get it to work.  Anyhow, any help would be appreciated.
Your WinTV-HVR-950 is not an saa7134 device, so if you have the saa7134 driver loaded then it must be for something else.  In the meantime, the information on that website you reference is that only the the DVB tuner works under Linux (that would be the /dev/dvb/adapter0 device), so if DVB is broadcast where you are try kaffeine rather than TVTime, which is analogue only.

---

### Post by bliffle on 2007-07-26
Yeah, tvtime is analog only. But I can't seem to get vlc or kaffeine working with the 950 in order to get digital.

---

### Post by LeGollemux on 2007-07-27
I have TV and sound! 

After getting only video on Composite and sound on S-video (both share a sound source), I made a small adapterfrom dual RCA to 3.5mm mini-jack. inserted that into my line in and ! sounds with pictures. I'm so happy.

So this is what I did to get my card working. 

sudo apt-get install  tvtime 

rmmod saa7134_alsa
rmmod saa7134

modprobe saa7134 (the tuner and card numbers did not seem to have an effect)
modprobe saa7134_alsa

tvtime 

That's it, of course none of the above is any of my own doing, thanks for all the great help from everyone.

---

### Post by bliffle on 2007-08-01
> **LeGollemux said:**
> ok, Im not getting anywhere here. I have video, no problem. but!! no matter what I try I am unable to get sound. I know the sound is working, ubuntu system sounds play....


Are you getting HDTV? Or just analog?

---

### Post by bliffle on 2007-08-01
> **starfleetcaptainrob said:**
> I have the Hauppauge WinTV-HVR-950 as well and can't seem to get it to work.  I think I saw in this thread that Biffle was having problems getting TVtime to use it and was just getting a blue screen.  I'm having the same issue and can't seem to figure it out.  I followed the instructions from this site:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")

when I do lsusb it shows that the card is being recognized:

```
fredbear@megatron:~$ lsusb
Bus 006 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 2040:6513 Hauppauge 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

when I type in lsmod | grep saa7134_alsa it gives me this:

```
fredbear@megatron:~$ lsmod | grep saa7134_alsa
saa7134_alsa           15392  0 
saa7134               130764  2 saa7134_dvb,saa7134_alsa
video_buf              26116  4 saa7134_dvb,saa7134_alsa,saa7134,video_buf_dvb
snd_pcm                79876  6 saa7134_alsa,em28xx_audio,snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd                    54020  20 saa7134_alsa,em28xx_audio,snd_usb_audio,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep

```

Under my dev folder i've got /dvb/adapter0/dvr0 and I've tried editing the XML file for TVtime to make it point to that, but that doesn't seem to work either.  I'm completely out of ideas and am hoping someone can help!  I know this card has worked for other people, I just don't understand why I can't get it to work.  Anyhow, any help would be appreciated.

Yeah, we know it's worked for somebody else. So tantalizing. I'm gonna return that card to the store pretty soon and bailout. Too bad.

I also have a Diamond HDTV100 which has an xc3028 in place of the 7134, so maybe I'll keep trying with that.

I'd like to get setup so I can watch HDTV while traveling in the USA, and also while in Europe.

---

### Post by LeGollemux on 2007-08-01
I dont have access to HD-TV where I am. So its just analogue is taken via RCA (Yellow,Red & White) off a Satelite decoder. 

I decided to try and re-create the whole thing. I took a new machine and installed feisty on it. Then I put the TV card in. LSPCI told me it was being picked up on the PCI bus. 

Then I typed:

1. sudo apt-get install tvtime
2. sudo modprobe saa7134_alsa
3. sudo modprobe saa7134
4. sudo sh –c  ‘echo “options saa7134 card=46 alsa=1” > /etc/modprobe.d/saa7134’
5. sudo nano /etc/modules (added **saa7134** as the last line)
6. tvtme

if you just get a blue screen (ha!) with tvtime and no writing at all then tvtime is not picking up your card.

this is all I did to get the video working, and it works very well. the tvtime guys are doing some great stuff when it comes to deinterlacing.

The sound!

I connect the RCA (white&red) from the satelite decoder into the line in on the sound card. This sorts out the sound problem. 

I hope this helps.

---

### Post by starfleetcaptainrob on 2007-08-02
I think I've figured out my problem, now if I could just figure out how to solve it.  I think tvtime is trying to import video from my webcam rather than the tv card.  When I open up tvtime via terminal it gives me this output:

```
fredbear@megatron:~$ tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
arecord: set_params:909: Channels count non available
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/fredbear/.tvtime/tvtime.xml
aplay: playback:2021: read error
videoinput: Driver refuses to set norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: pwc [Logitech QuickCam Pro 4000/usb-0000:00:02.1-1/655372]
    does not support studio-quality colour images required by tvtime.
    This is a hardware limitation of some cards including many
    low-quality webcams.  Please select a different video device to use
    with the command line option --device.

    Message from the card was: Invalid argument

Thank you for using tvtime.

```

Anyone have any ideas on how I get it to point to my tv card rather than my webcam?

---

### Post by starfleetcaptainrob on 2007-08-04
Bumpity...anyone...Bueller?

EDIT:  Okay, nevermind.  I got the video working but no audio yet.  I had to go in and edit the tvtime XML file to use /dev/video1.  I didn't even know there was a video1 file otherwise I probably would have done that long ago.  Anyhow, anyone have any ideas on how to get the audio working?

---

### Post by bliffle on 2007-08-06
Since it's "TVTime" I assume you're doing analog TV only?

Where is that TVTime XML file?

---

### Post by starfleetcaptainrob on 2007-08-06
> **bliffle said:**
> Since it's "TVTime" I assume you're doing analog TV only?

Where is that TVTime XML file?

Hey Bliffle, I believe it's under /etc/tvtime.  I'm at work right  now so I don't know for sure.  There should be a record within the file that talks about the source and the default should read /dev/video0.  Change it to /dev/video1 and you should get analog video.  I don't get any audio, but let me know if you do.  I've tried both the sox commands that have been suggested in this forum and other forums with no success.  So close!!  What's frusterating (at least for me) is that the video comes in nice and clear on this card.  If I could only get some sound...

---

### Post by bliffle on 2007-08-17
I returned the Hauppage HVR-950 (I only need one HDTV stick that doesn't work).

SO now I have to solve the Diamond HDTV100 problem.

---

### Post by starfleetcaptainrob on 2007-08-20
Wish I could return mine at this point.  I'm still soundless.  I've lost the receipt at this point too.  Good luck with your other card.

---

### Post by bliffle on 2007-08-21
I'm going to try running the Diamond Video display software under Wine, VMware and Virtualbox to see if I can succeed that way.

VMware documents are so full of promotional talk I can't figure out how to install and operate it, so I'll try Wine next.

Talking about obtuse, I can't find the Diamond CD for their software so I gotta get it from their website and they don't even state it's name, nor do they provide a download.

What he hell is wrong with people?

---

### Post by narcisgarcia on 2008-03-19
To specify anorher source, you can run:
tvtime --device=/dev/video0
tvtime --device=/dev/video1
tvtime --device=/dev/video2

For more parameters:
tvtime --help
(in a console)

---

### Post by netboy541 on 2008-03-19
I use the Happuage HVR-950 and it works like a champ using these instructions...........

```

How to install the modules for the Happuage WinTV HVR950 tv card ---



For Ubuntu&#8217;s Feisty Fawn : )this works for gutsy too....
sudo su
apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential
cd /lib/firmware
wget http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz
tar xvzf firmware_v4.tgz
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
cd v4l-dvb-experimental
make 
make install
reboot
sudo modprobe em2880-dvb
If on the next reboot, the card stops working the em2880-dvb module is not being loaded properly in Feisty. To fix this :
cd /etc/modprobe.d
sudo gedit dvbstick
then add this line to the new dvbstick file :
install em28xx /sbin/modprobe --ignore-install em28xx; /bin/sleep 2; /sbin/modprobe em2880-dvb
reboot and it should be back up and running.


```

for sound, i start tv time, then open a console and issue:

```

sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp 

```

The tv card is an ATSC tv card.  I felt it was not so smart to get a analog tv card since that will be dead soon, and the reception here sucks anyway...


It is my experience that the SAA cards suck, getting them to work is a nightmare, and the one card I had working in under fifteen minutes was the happauge usb stick.  I spent weeks trying to get the saa based card to work, and i finally got so pissed off over it, i sent the card to my dad so he could use it under windows and i took the loss on it and got a different card.

Take it from me, if you follow my instructions, the happuage stick WILL WORK. 

hope that helps!

---

### Post by Chibi-Tatsu on 2008-03-27
Well, I have no sound and when I tried the line:

sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

I got an error: sox stio: Can't open input file `/dev/dsp1': No such file or directory

when I run the command:

sudo modprobe saa7134_alsa

I get: FATAL: Error inserting saa7134_alsa (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by netboy541 on 2008-03-27
ok, i'm lost.


what kind of TV card are you using?

the happauge does not use a SAA chipset, so I don't understand where that's coming from...

it uses the em2880-dvb module.

if you are indeed using the Happuage HVR-950, make sure you follow my instructions closely.  It has worked for me on all my laptops and my desktops, and all are running kubuntu fiesty or gutsy.

the SOX command works, but sometimes it's a bit hard-headed.  I've had to close tvtime and restart it a time or two to get the sound to work.  also changing channels and then throwing the command at it works as well.

check your logs and make sure it's setting it as DSP1 and not something else...

---

### Post by msrinath80 on 2008-03-27
netboy, it seems you've successfully got the 950 stick to work. I have two questions for you:

1. Does the sound lag from the video or vice versa?
2. Have you been able to get Analog TV working with sound?

Thanks in advance for your reply.

---

### Post by netboy541 on 2008-03-27
There have been a few instances where the sound gets a little out of whack.  I usually just close TV Time, kill the sound, and start it again and issue the sox command.  About the only time that happens is when I'm working the processor really hard (like encoding on the fly)


I have sucessfully got the analog TV portion to work fine..

When I did hook my PS2 up to my stick, there was a little lag, but nothing too bad.
I could still play games no sweat.

---

### Post by msrinath80 on 2008-03-27
Dude, you rule! Bought it today and got it working in under 10 minutes using the above instructions. No sound lag. Decent picture! I'll update this post after experimenting more with it. Love this USB stick!!!

---

### Post by netboy541 on 2008-03-27
I do what I can.  I about ripped my hair out of my head trying to find a TV Card that works.

For those of you that want to know, I have parked the instructions on  [my blog]("http://flat-broke.org/rminick/b2evolution/blogs/index.php?blog=10&title=how_to_install_the_modules_for_the_happu&more=1&c=1&tb=1&pb=1").


If it works for you, post a message! I'd sure like to know how many I've helped! :)

Thanks!

---

### Post by msrinath80 on 2008-03-28
Firstly, thanks for the instructions. Just like to add some comments:

1. I did not have to go beyond the reboot stage (i.e. no need to sudo modprobe em2880-dvb and so on). On the next reboot everything was found!

2. My webcam which was working perfectly before I installed the HVR-950 suddenly stopped working! If I remove the HVR-950, then it works fine. Not a big issue for me, but I just thought others should know.

3. sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

enabled the sound for me without any lag!

The first time I ran the above sox command, I got the dsp device busy message. I then terminated esd through System -> Preferences -> Sound (Sounds Tab) -> Deselect Enable software sound mixing (ESD) and sox ran without any problems.

4. I don't have cable TV at home (presently) and neither are ATSC OTA (Over-The-Air) signals present in my area. As a result, I simply used the portable antenna provided with the HVR-950 to watch analog TV.


For the record, I run Gutsy (i386) on a Fujitsu S7110 (2 GB RAM, 2 GHz dual-core centrino). I would love to know whether the installation procedure works well with Hardy Heron, the next release of Ubuntu if and when you test it.

Once again, thanks a lot!

---

### Post by Chibi-Tatsu on 2008-03-29
> **netboy541 said:**
> ok, i'm lost.


what kind of TV card are you using?

the happauge does not use a SAA chipset, so I don't understand where that's coming from...

it uses the em2880-dvb module.

if you are indeed using the Happuage HVR-950, make sure you follow my instructions closely.  It has worked for me on all my laptops and my desktops, and all are running kubuntu fiesty or gutsy.

the SOX command works, but sometimes it's a bit hard-headed.  I've had to close tvtime and restart it a time or two to get the sound to work.  also changing channels and then throwing the command at it works as well.

check your logs and make sure it's setting it as DSP1 and not something else...

Apologies; yes, using the HVR-950.  Ran your instructions line-by-line, but got the sox error I mentioned.  Which logs do I check to see if it's (which, TVtime?) setting it as DSP1?

PS: 64-bit system, gnome gutsy.

---

### Post by netboy541 on 2008-03-29
i bet it has something to do with it being a 64 bit o/s.

i only know 32 bit o/ses, so i'm not of much help for you there.

I'd check the messages at bootup where it detects everything...
look for where it detects the TV card and assigns it's id (/dev/dsp or /dev/dsp1)

---

### Post by Chibi-Tatsu on 2008-03-29
Oh, I have dsp; just no dsp1.

An interesting (and possibly relevant) snippet from dmesg:

> [   41.744168] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 1158585
[   41.744172] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   41.744177] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   41.744181] tveeprom 0-0050: audio processor is None (idx 0)
[   41.744184] tveeprom 0-0050: has radio

> [   43.054965] ANALOG TV REQUEST
[   43.061574] em28xx #0: V4L2 device registered as /dev/video0
[   43.061578] em28xx #0: Found Hauppauge WinTV HVR 950
[   43.061599] usbcore: registered new interface driver em28xx
[   43.111546] em28xx_audio: disagrees about version of symbol snd_pcm_new
[   43.111550] em28xx_audio: Unknown symbol snd_pcm_new
[   43.111588] em28xx_audio: disagrees about version of symbol snd_card_register
[   43.111597] em28xx_audio: Unknown symbol snd_card_register
[   43.111616] em28xx_audio: disagrees about version of symbol snd_card_free
[   43.111617] em28xx_audio: Unknown symbol snd_card_free
[   43.111664] em28xx_audio: disagrees about version of symbol snd_card_new
[   43.111666] em28xx_audio: Unknown symbol snd_card_new
[   43.111682] em28xx_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[   43.111684] em28xx_audio: Unknown symbol snd_pcm_lib_ioctl
[   43.111716] em28xx_audio: disagrees about version of symbol snd_pcm_set_ops
[   43.111717] em28xx_audio: Unknown symbol snd_pcm_set_ops
[   43.111735] em28xx_audio: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   43.111737] em28xx_audio: Unknown symbol snd_pcm_hw_constraint_integer
[   43.111789] em28xx_audio: disagrees about version of symbol snd_pcm_period_elapsed
[   43.111790] em28xx_audio: Unknown symbol snd_pcm_period_elapsed

---

### Post by netboy541 on 2008-03-30
yeah that looks bad.  If I was a gamblin' man, I'd be willing to bet the modules that are out there aren't for 64 bit.  Give me some time and let me see what I can find.  I know there isn't a whole lot of main-stream support for 64 bit anything right now, so you may be hosed.

More to come..

---

### Post by msrinath80 on 2008-03-30
Chibi, I know a surefire way to determine if 64-bit OS is causing the problem. Just download a 32-bit Gutsy live CD and follow the installation instructions as posted earlier (i.e. the same ones as on the lunapark6 website). If the tuner works, then you know where the problem was. Remember, after installing the modules, there is no need to reboot, just unplug the USB stick and put it back in! Everything is detected!!

For the record, I was able to get the tuner to work on Hardy (beta) Live CD (again 32-bit). Only the sound isn't working. Sound is working on Gutsy though (through sox)!

---

### Post by Chibi-Tatsu on 2008-03-30
Yeah, I figure that I'll just wait until Hardy gets out of beta (I'll be too busy to watch TV for a while... and best to avoid temptation) and start off with a 32-bit install.  The 64-bit has been noticably faster, but I don't need the extra speed all that much, and some of the workarounds for flash, video and the like are a bit irksome.

Gracias for your instructions, though; they definitely helped me get the video working.  And yeah, there's probably some missing drivers.

---

### Post by msrinath80 on 2008-04-04
How to play TV using mplayer:

[http://ubuntuforums.org/showthread.php?p=4653073#post4653073](http://ubuntuforums.org/showthread.php?p=4653073#post4653073)

---

