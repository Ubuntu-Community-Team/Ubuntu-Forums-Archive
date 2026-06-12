---
title: "Winfast Leadtek Xpert 2000XP Deluxe and BTTV"
date: 2009-06-15
forum: Multimedia Software
---

### Post by blaqhawk2k on 2009-06-15
I am running Ubuntu 9.04 64 Bit and Vista 64 Bit on my Gigabyte P35-DS3R
I am using an Intel Core 2 Quad CPU
Have 8GB of Ram and over 500GB of hard drive space(multiple drives)

My issue is the Winfast Leadtek Xpert 2000XP Deluxe I have is not working in any of the O/S I have. I gave up on Vista 64 bit because the drivers would not load due to driver certificates being unsigned. Not enough info on the web to get around it yet.

Decided to get the card to work in Ubuntu.

First thing I needed to understand is what the card is doing when loading Ubuntu

Checked 'dmesg' log by launching **System => Administration => Log File Viewer**

```
[   10.613188] Linux video capture interface: v2.00
[   10.626308] bttv: driver version 0.9.17 loaded
[   10.626310] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.626364] bttv: Bt8xx card found (0).
[   10.626375] bttv 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.626383] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 18, latency: 32, mmio: 0xea100000
[   10.626433] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   10.626435] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   10.626458] bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
[   10.626500] bttv0: tuner type=5
[   10.626502] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   10.627104] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   10.627700] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   10.641724] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   10.683767] tuner-simple 0-0061: creating new instance
[   10.683770] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   10.692972] bttv0: registered device video0
[   10.692999] bttv0: registered device vbi0
[   10.693020] bttv0: registered device radio0
[   10.693047] bttv0: PLL: 28636363 => 35468950 .. ok
[   10.728776] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:05:02.0/input/input6
[   10.766500] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.766569] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.777148] Bt87x 0000:05:02.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.777277] bt87x0: Using board 1, analog, digital (rate 32000 Hz)

```The logging showed the card type is correct but the tuner was detected incorrectly. I need a tuner type 2 for North America(Canada/USA). Bttv is the default driver the system is using so I need to work within the limits of it.

Question is how do I configure my card to load this tuner type on startup.

The best answer I could find after searching the web is /etc/modprobe.d/bttv. I needed to create this file and put the configuration I want in there.

Most of the references I found said to use:

> **options bttv card=34 tuner=2 gbuffers=8 lumafilter=1 combfilter=1 chroma_agc=1**
I gave this a try.

> [B]ALT+F2

gksudo gedit /etc/modprobe.d/bttv[/B]```
[COLOR=Blue]**bttv card=34 tuner=2 radio=0 gbuffers=8 debug=1 lumafilter=1 combfilter=1 chroma_agc=1**[/COLOR]
```When I restarted Ubuntu I checked dmesg after the system was loaded successfully. The tuner type was loaded successfully as 2. I launched tvtime and was able to get sound but no video.

I checked /dev for video and could see /dev/video0

> **ls -al /dev/video***I was not sure if the bttv drive was pointing to /dev/video0 so I checked for more parameters to configured the video.

> 
**/sbin/modprobe bttv**```
filename:       /lib/modules/2.6.28-13-generic/kernel/drivers/media/video/bt8xx/bttv.ko
license:        GPL
author:         Ralph Metzler & Marcus Metzler & Gerd Knorr
description:    bttv - v4l/v4l2 driver module for bt848/878 based cards
srcversion:     97A8FA06F360905675E7702
alias:          pci:v0000109Ed0000036Fsv*sd*bc*sc*i*
alias:          pci:v0000109Ed0000036Esv*sd*bc*sc*i*
alias:          pci:v0000109Ed00000351sv*sd*bc*sc*i*
alias:          pci:v0000109Ed00000350sv*sd*bc*sc*i*
depends:        videobuf-core,videobuf-dma-sg,ir-common,videodev,tveeprom,v4l2-common,btcx-risc,i2c-algo-bit,compat_ioctl32
vermagic:       2.6.28-13-generic SMP mod_unload modversions 
parm:           ir_debug:int
parm:           repeat_delay:int
parm:           repeat_period:int
parm:           ir_rc5_remote_gap:int
parm:           ir_rc5_key_timeout:int
parm:           i2c_debug:int
parm:           i2c_hw:configure i2c debug level (int)
parm:           i2c_scan:scan i2c bus at insmod time (int)
parm:           i2c_udelay:soft i2c delay at insmod time, in usecs (should be 5 or higher). Lower value means higher bus speed. (int)
parm:           vbibufs:number of vbi buffers, range 2-32, default 4 (int)
parm:           vbi_debug:vbi code debug messages, default is 0 (no) (int)
parm:           gpiomask:int
parm:           audioall:int
parm:           svhs:array of int
parm:           remote:array of int
parm:           audiomux:array of int
parm:           triton1:set ETBF pci config bit [enable bug compatibility for triton1 + others] (int)
parm:           vsfx:set VSFX pci config bit [yet another chipset flaw workaround] (int)
parm:           latency:pci latency timer (int)
parm:           card:specify TV/grabber card model, see CARDLIST file for a list (array of int)
parm:           pll:specify installed crystal (0=none, 28=28 MHz, 35=35 MHz) (array of int)
parm:           tuner:specify installed tuner type (array of int)
parm:           autoload:automatically load i2c modules like tuner.o, default is 1 (yes) (int)
parm:           no_overlay:allow override overlay default (0 disables, 1 enables) [some VIA/SIS chipsets are known to have problem with overlay] (int)
parm:           debug_latency:int
parm:           fdsr:int
parm:           v4l2:int
parm:           combfilter:int
parm:           lumafilter:int
parm:           radio:The TV card supports radio, default is 0 (no) (array of int)
parm:           bigendian:byte order of the framebuffer, default is native endian (int)
parm:           bttv_verbose:verbose startup messages, default is 1 (yes) (int)
parm:           bttv_gpio:log gpio changes, default is 0 (no) (int)
parm:           bttv_debug:debug messages, default is 0 (no) (int)
parm:           irq_debug:irq handler debug messages, default is 0 (no) (int)
parm:           gbuffers:number of capture buffers. range 2-32, default 8 (int)
parm:           gbufsize:size of the capture buffers, default is 0x208000 (int)
parm:           reset_crop:reset cropping parameters at open(), default is 1 (yes) for compatibility with older applications (int)
parm:           automute:mute audio on bad/missing video signal, default is 1 (yes) (int)
parm:           chroma_agc:enables the AGC of chroma signal, default is 0 (no) (int)
parm:           adc_crush:enables the luminance ADC crush, default is 1 (yes) (int)
parm:           whitecrush_upper:sets the white crush upper value, default is 207 (int)
parm:           whitecrush_lower:sets the white crush lower value, default is 127 (int)
parm:           vcr_hack:enables the VCR hack (improves synch on poor VCR tapes), default is 0 (no) (int)
parm:           irq_iswitch:switch inputs in irq handler (int)
parm:           uv_ratio:ratio between u and v gains, default is 50 (int)
parm:           full_luma_range:use the full luma range, default is 0 (no) (int)
parm:           coring:set the luma coring level, default is 0 (no) (int)
parm:           video_nr:video device numbers (array of int)
parm:           vbi_nr:vbi device numbers (array of int)
parm:           radio_nr:radio device numbers (array of int)

```> **ALT+F2**

[B]gksudo gedit /etc/modprobe.d/bttv 
[/B]```
[COLOR=Blue][B]options bttv card=34 tuner=2 radio=1 gbuffers=16 bttv_debug=1 video_nr=0 lumafilter=1 combfilter=1 chroma_agc=1 automute=0
[/B][/COLOR]
```restart Ubuntu to confirm dmesg is logging the new configuration

dmesg

```
[   10.703030] Linux video capture interface: v2.00
[   10.733382] bttv: driver version 0.9.17 loaded
[   10.733384] bttv: using 16 buffers with 2080k (520 pages) each for capture
[   10.733436] bttv: Bt8xx card found (0).
[   10.733447] bttv 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.733456] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 18, latency: 32, mmio: 0xea100000
[   10.733504] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   10.733505] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[   10.733513] bttv0: risc main @ 37843000
[   10.733530] bttv0: gpio: en=00000000, out=00000000 in=00b37707 [init]
[   10.733531] bttv0: BT878A ARESET
[   10.733585] bttv0: tuner type=2
[   10.733587] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   10.734189] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   10.734785] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   10.799089] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   10.799103] bttv0: tuner' i2c attach [addr=0x61,client=tuner']
[   10.849163] tuner-simple 0-0061: creating new instance
[   10.849165] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   10.858510] bttv0: registered device video0
[   10.858529] bttv0: registered device vbi0
[   10.858546] bttv0: registered device radio0
[   10.858563] bttv0: video mux: input=0 mux=2
[   10.858570] bttv0: PLL: 28636363 => 35468950 .. ok
[   10.892783] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:05:02.0/input/input6
[   10.907371] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.907433] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.967734] Bt87x 0000:05:02.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.967851] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   16.655560] bttv: open minor=1
[   16.655563] bttv0: open called (type=vbi-cap)
[   16.655569] bttv0: PLL: no change required
[   16.656212] bttv0: video mux: input=0 mux=2
[   16.656218] bttv0: PLL: no change required
[   16.656855] BT878 vbi (Leadtek WinFast 2000: VIDIOC_QUERYCAP
[   16.659540] bttv: open minor=0
[   16.659543] bttv0: open called (type=vid-cap)
[   16.659550] bttv0: PLL: no change required
[   16.660211] bttv0: video mux: input=0 mux=2
[   16.660220] bttv0: PLL: no change required
[   16.661375] BT878 video (Leadtek WinFast 20: VIDIOC_QUERYCAP
[   16.663149] bttv: open minor=2
[   16.663152] bttv0: open called (radio)
```Looks like that was the configuration I was looking for as tv is working with sound in video in tvtime and xawtv. I need to get the remote to work as I have to key in the channel when using tvtime. I'll do that sometime later. I spent the day trying to figure this out, time for a break. Tvtime is really nice, I'm used to xawtv but tvtime seems simple to configure. Xawtv is also crashing when I try to change the default configuration. Good bye Xawtv and hello tvtime!

It would be nice to have a GUI to configure bttv. That could of made this easier considering there is confusing suggestions to use:[INDENT]/etc/modules
/etc/modules.conf
/etc/modprobe.d/bttv
/etc/modprobe.d/options. 
[/INDENT]Which one is the best choice? Which one is legacy so avoid using it?

Well at least the tv card is working in 64 bit Ubuntu now, that's more then I got out of 64 bit Vista.

I need to get my Epson Stylus CX5800 to work as well. This is another device not working properly in Vista. Maybe I will get lucky and get it to work in Ubuntu.

---

### Post by azuosd on 2010-05-15
Wanted to thank you for this, been searching all over the place,  and finaly got my Winfast tv2000 xp deluxe working in 10.04 by adding

[B][COLOR=Blue][B]options bttv card=34 tuner=2 radio=1 gbuffers=16 bttv_debug=1 video_nr=0 lumafilter=1 combfilter=1 chroma_agc=1 automute=0
[/B][/COLOR][/B]
to /etc/modprobe.d/bttv

really apprecate it!!
thanks

---

