---
title: "cx23880 based tv cards."
date: 2008-12-16
forum: Multimedia Software
---

### Post by soxs on 2008-12-16
Hey all, I own an cx23880 based tv card (WinTV NOVA-S-PLUS).

I have serious problems to find my mistake, as I don't get any channels when scanning with tvtime, kdetv, kaffeine.

SOme info:

lsmod
```
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16256  1 
fat                    60592  1 vfat
usb_storage            82496  1 
libusual               23520  1 usb_storage
udf                    91048  0 
vmnet                  52052  13 
vsock                  27664  0 
vmci                   59088  1 vsock
vmmon                  79984  0 
binfmt_misc            14860  1 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
ipv6                  311720  27 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  4 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
container               6656  0 
video                  23444  0 
output                  5632  1 video
dock                   12960  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ext2                   80400  1 
ac                      8328  0 
w83627ehf              27272  0 
hwmon_vid               5120  1 w83627ehf
powernow_k8            16608  0 
freq_table              6464  3 cpufreq_stats,cpufreq_ondemand,powernow_k8
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
loop                   21508  0 
isl6421                 3840  1 
cx24123                15496  1 
cx88_dvb               16388  0 
snd_hda_intel         440536  4 
cx88_vp3054_i2c         4864  1 cx88_dvb
videobuf_dvb            8708  1 cx88_dvb
dvb_core               94380  1 videobuf_dvb
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
cx88_alsa              16648  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                92168  4 snd_hda_intel,cx88_alsa,snd_pcm_oss
fglrx                2231832  28 
snd_timer              27912  3 snd_seq,snd_pcm
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
cx8800                 42628  0 
snd                    70856  18 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,cx88_alsa,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
cx8802                 22276  1 cx88_dvb
cx88xx                 72744  4 cx88_dvb,cx88_alsa,cx8800,cx8802
evdev                  14976  4 
ir_common              39812  1 cx88xx
irtty_sir              10880  0 
i2c_algo_bit            8452  2 cx88_vp3054_i2c,cx88xx
serio_raw               9092  0 
psmouse                46236  0 
tveeprom               20624  1 cx88xx
compat_ioctl32         11136  1 cx8800
sir_dev                19592  1 irtty_sir
videodev               30720  2 cx8800,cx88xx
v4l2_common            21888  4 cx8800,cx88xx,compat_ioctl32,videodev
v4l1_compat            15492  1 videodev
videobuf_dma_sg        17028  6 cx88_dvb,videobuf_dvb,cx88_alsa,cx8800,cx8802,cx88xx
videobuf_core          22020  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
btcx_risc               6792  4 cx88_alsa,cx8800,cx8802,cx88xx
i2c_piix4              11148  0 
pcspkr                  4992  0 
irda                  222956  2 irtty_sir,sir_dev
i2c_core               28544  7 isl6421,cx24123,cx88_vp3054_i2c,cx88xx,i2c_algo_bit,tveeprom,i2c_piix4
wmi_acer               11076  0 
button                 10912  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
crc_ccitt               3584  1 irda
ext3                  149264  4 
jbd                    57000  1 ext3
mbcache                11392  2 ext2,ext3
ide_cd                 35488  0 
cdrom                  41512  1 ide_cd
ata_generic             9988  0 
sg                     41880  0 
sd_mod                 33280  9 
pata_acpi               9856  0 
usbhid                 35680  0 
hid                    44992  1 usbhid
pata_atiixp            10496  0 
ohci1394               36532  0 
floppy                 69096  0 
ahci                   33284  6 
ehci_hcd               41996  0 
libata                176432  4 ata_generic,pata_acpi,pata_atiixp,ahci
ohci_hcd               28956  0 
ieee1394              106968  2 sbp2,ohci1394
atiixp                  6672  0 [permanent]
scsi_mod              178488  5 usb_storage,sbp2,sg,sd_mod,libata
ide_core              136600  2 ide_cd,atiixp
r8169                  36868  0 
usbcore               170288  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41832  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```lspci
```
...
03:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:06.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:06.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

...
```thx for any info

EDIT:
/dev/video0 exists

EDIT:
aswell as /dev/vbi0 and /dev/dvb

so the video4linux2 seems to be satisfied, and does obvously NOT lack any info.

May it be a corrupted channels.conf? Where can I get a good DVB_S channel list for kdetv or kaffeine from?

---

### Post by steefjeqv on 2008-12-17
Hi,

Can you check dmesg and see if the DVB frontend is correctly loaded ?

Greetings,
Steven

---

### Post by soxs on 2008-12-18
```
[   37.691778] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   37.691884] cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37,autodetected]
[   37.691886] cx88[0]: TV tuner type 4, Radio tuner type -1
[   37.700101] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   37.771557] cx2388x alsa driver version 0.0.6 loaded
[   37.853424] tveeprom 1-0050: Hauppauge model 92001, rev C1B1, serial# 928658
[   37.853431] tveeprom 1-0050: MAC address is 00-0D-FE-0E-2B-92
[   37.853433] tveeprom 1-0050: tuner model is Conexant_CX24109 (idx 111, type 4)
[   37.853435] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   37.853437] tveeprom 1-0050: audio processor is CX883 (idx 32)
[   37.853439] tveeprom 1-0050: decoder processor is CX883 (idx 22)
[   37.853441] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   37.853443] cx88[0]: hauppauge eeprom: model=92001
[   37.856853] input: cx88 IR (Hauppauge Nova-S-Plus  as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/input/input6
[   37.904066] cx88[0]/2: cx2388x 8802 Driver Manager
[   37.904099] ACPI: PCI Interrupt 0000:03:06.2[A] -> GSI 21 (level, low) -> IRQ 21
[   37.904112] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 21, latency: 32, mmio: 0xfb000000
[   37.904246] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
[   37.904270] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 21, latency: 32, mmio: 0xfd000000
[   37.904273] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   37.904743] cx88[0]/0: registered device video0 [v4l2]
[   37.904766] cx88[0]/0: registered device vbi0
[   37.905032] ACPI: PCI Interrupt 0000:03:06.1[A] -> GSI 21 (level, low) -> IRQ 21
[   37.905078] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   37.947019] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   37.959576] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   37.959582] cx88/2: registering cx8802 driver, type: dvb access: shared
[   37.959587] cx88[0]/2: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[   37.959591] cx88[0]/2: cx2388x based DVB/ATSC card
[   37.982172] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 19 (level, low) -> IRQ 19
[   37.982808] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   38.015488] DVB: registering new adapter (cx88[0])
[   38.015497] DVB: registering frontend 0 (Conexant CX24123/CX24109)...
[   40.084603] loop: module loaded
[   40.131239] lp: driver loaded but no devices found


```

I hope this is the correct part you require

---

### Post by soxs on 2008-12-19
- bump -

---

### Post by steefjeqv on 2008-12-23
Hi,

The dmesg output looks good.

Is the card recognized (do you have the digital tv icon) when you start up Kaffeine ?

Which satellite are you scanning (astra, hotbird ....) ?

Greetings,
Steven

---

### Post by soxs on 2008-12-24
> **steefjeqv said:**
> Hi,

The dmesg output looks good.

Is the card recognized (do you have the digital tv icon) when you start up Kaffeine ?

Which satellite are you scanning (astra, hotbird ....) ?

Greetings,
Steven

Yes I see a digital TV icon. But when I start scanning [astra 19.2, living in Germany, Karlsruhe] the channels no channel is found.

Edit: Did you read the last line? There it says driver loaded, but NO devices found!

---

### Post by steefjeqv on 2008-12-24
Hi,

I think this last line is referring to your parallel port. It shouldn't influence your DVB card.

You can try scanning with dvb-utils.

sudo apt-get install dvb-utils

sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E 

Greetings + a nice Christmas,
Steven

---

### Post by soxs on 2008-12-24
> **steefjeqv said:**
> Hi,

I think this last line is referring to your parallel port. It shouldn't influence your DVB card.

You can try scanning with dvb-utils.

sudo apt-get install dvb-utils

sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E 

Greetings + a nice Christmas,
Steven

I ll do this as soon as I get back home at about 4th of January.
have nice Christmas too

---

### Post by soxs on 2009-01-05
```
 sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
WARNING: >>> tuning failed!!!
>>> tune to: 12551:v:0:22000 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```This is the not so awesome result... :-(

EDIT: Now it's prooved, it seems to be a generic problem with my TV card...
[http://www.mail-archive.com/linux-dvb@linuxtv.org/msg30199.html](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg30199.html)

EDIT:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-S-Plus](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-S-Plus)

---

### Post by wolfen69 on 2009-01-05
[This]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)") may help.

---

### Post by steefjeqv on 2009-01-05
Hi,

You can try installing the newest v4l DVB driver (Case 2 - Debian instructions) :

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

Greetings,
Steven

---

### Post by soxs on 2009-01-06
Successfully recompiled and installed, but no chnage for sudo scan ...


I did some other tests, e.g. this one. I don't get a picture nor sound (all black, no noise) but I don't either get evil errors..

 ```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:input=1:normid=2
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) 9500 Quad-Core Processor (Family: 16, Model: 2, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge Nova-S-Plus DVB-S
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC-M; 1 = NTSC-M-JP; 2 = NTSC-443; 3 = PAL-BG; 4 = PAL-I; 5 = PAL-DK; 6 = PAL-M; 7 = PAL-N; 8 = PAL-Nc; 9 = PAL-60; 10 = SECAM-B; 11 = SECAM-G; 12 = SECAM-H; 13 = SECAM-DK; 14 = SECAM-L;
 inputs: 0 = DVB; 1 = Composite1; 2 = S-Video;
 Current input: 8
 Current format: BGR24
v4l2: current audio mode is : MONO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed UYVY 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
TV input is not seekable! (Seeking will probably be for changing channels ;)
No bind found for key 'MOUSE_BTN3'.-MOUSE_BTN3_DBL                         
No bind found for key 'MOUSE_BTN3_DBL'.                         
TV input is not seekable! (Seeking will probably be for changing channels ;)
No bind found for key 'MOUSE_BTN3'.-MOUSE_BTN3_DBL                         
No bind found for key 'MOUSE_BTN3_DBL'.                         
No bind found for key 'MOUSE_BTN2'.                         
v4l2: 2087 frames successfully processed, 15 frames dropped.
GNOME screensaver enabled

Exiting... (Quit)
```

---

### Post by soxs on 2009-01-06
I now at least know about my cardnumber: 
 > 37 -> Hauppauge Nova-S-Plus DVB-S                         [0070:9201,0070:9202]and it being supported...

but do I need a firmware? If so, plx tell me which one: [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

---

### Post by wolfen69 on 2009-01-06
> **soxs said:**
> I now at least know about my cardnumber: 
 and it being supported...

but do I need a firmware? If so, plx tell me which one: [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

all those firmware files are very small size. download them all and put them in /lib/firmware
then
```
rmmod cx88-dvb && modprobe cx88-dvb
```
then open vlc, media>open capture device>play

hope it works for you.

[www.linuxtv.org](www.linuxtv.org) is also a great place for info.

---

### Post by cb951303 on 2009-01-06
I have the exact same card. I got the latest v4l-dvb drivers from mercuriel and compiled/installed.

I still get the "tuning failed" error with scan but kaffeine scans 90 channels successfully and they work great. Needless to say it should be 350+ channels with my satellite (Eutelsat)

---

### Post by wolfen69 on 2009-01-06
[Here]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)#cx88_and_associated_kernel_driver_modules") ia another page for you.

---

### Post by cb951303 on 2009-01-06
> **soxs said:**
> I now at least know about my cardnumber: 
 and it being supported...

but do I need a firmware? If so, plx tell me which one: [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

You don't need a firmware. The firmware is already installed on your computer (integrated to v4l-dvb driver) it's called ttpci I think...

---

### Post by steefjeqv on 2009-01-06
Hi,

@cb951303 : Are you using Hardy or Intrepid ?

Greetings,
Steven

---

### Post by wolfen69 on 2009-01-06
and [here]("http://www.linuxtv.org/repo/") is the mercurial repo how to.

---

### Post by cb951303 on 2009-01-06
> **steefjeqv said:**
> Hi,

@cb951303 : Are you using Hardy or Intrepid ?

Greetings,
Steven

intrepid but it doesn't matter. Necessary firmware (ttpci) is last modified in 2006 and is included in every kernel since then...

---

### Post by cb951303 on 2009-01-06
here is how my lsmod lspci output looks like with current v4l-dvb drivers: [http://pastebin.com/f4de6d78f](http://pastebin.com/f4de6d78f)

And a screenshot from kaffeine

---

### Post by soxs on 2009-01-06
The only difference from my output is that I get no nvidia, but this should be cause by my itegrated ati gpu rather than anything else. The rest is the EXACT same output as yours...

---

### Post by cb951303 on 2009-01-06
> **soxs said:**
> The only difference from my output is that I get no nvidia, but this should be cause by my itegrated ati gpu rather than anything else. The rest is the EXACT same output as yours...

did you install kaffeine and tried scanning channels with it?

---

### Post by soxs on 2009-01-06
I did, but neither the default Astra19.2 nor Astra28.2 didn't get any channel at all...

---

### Post by cb951303 on 2009-01-06
> **soxs said:**
> I did, but neither the default Astra19.2 nor Astra28.2 didn't get any channel at all...

I guess it's the new drivers that I compiled/installed that makes the difference. 
I bought the card a week ago just because I read it was supported oob in linux but internet can be misleading.

---

### Post by soxs on 2009-01-06
What new dirvers?? I installed mercurial main dvb v4l stuff but it still didn't work.. Moving some fw files int /lib/firmware didn't help either...

Fedora 10 doesn't like it either...

---

### Post by cb951303 on 2009-01-06
> **soxs said:**
> What new dirvers?? I installed mercurial main dvb v4l stuff but it still didn't work.. Moving some fw files int /lib/firmware didn't help either...

Fedora 10 doesn't like it either...

so you did compiled v4l from mercurial, hmm
are you sure your card is getting signal form dish/lnb?

---

### Post by soxs on 2009-01-06
> **cb951303 said:**
> so you did compiled v4l from mercurial, hmm
are you sure your card is getting signal form dish/lnb?

Ok, I compiled it on ubuntu 8.04 and wohoo.. suprise suprise.. NO CHANGE!

I compiled it on Fedora 10, system through with stack traces at boot time at me, all connected to cx88* , I had to remove it, in order to keep my boot time below 360 seconds..
EDIT: 
And caffeine now doesn't show any icon for TV anymore... -.-

EDIT: /dev/video0 argh and the other related devices are gone .. f***!

---

### Post by soxs on 2009-01-07
Ok, I again started allover with a fresh install...

---

### Post by soxs on 2009-01-07
> **cb951303 said:**
> so you did compiled v4l from mercurial, hmm
are you sure your card is getting signal form dish/lnb?

Going to check that out...

---

### Post by cb951303 on 2009-01-07
> **soxs said:**
> Going to check that out...

I forgot to tell that in order to scan channels from a stellite in kaffeine first you need to adjust your LNB settings.

---

### Post by soxs on 2009-01-07
> **cb951303 said:**
> I forgot to tell that in order to scan channels from a stellite in kaffeine first you need to adjust your LNB settings.

Where do I get these values fpr Astra19.2 and Astra28.2 from?

---

### Post by cb951303 on 2009-01-07
> **soxs said:**
> Where do I get these values fpr Astra19.2 and Astra28.2 from?

I'm not sure but I think these number are related to your specific LNB rather than your satellite.

Are you the only one using the dish? Anyone else in your building maybe? If so, you can ask them or better you can check the number from their receivers' settings menu...

---

### Post by steefjeqv on 2009-01-07
Hi, 

My settings for Astra 28.2 are :

11700
lo 9750
hi 10600

@ sox : did you try Ubuntu 8.10 ? The 2.28 kernel may resolve your problems.

Greetings,
Steven

---

### Post by soxs on 2009-01-07
> **steefjeqv said:**
> Hi, 

My settings for Astra 28.2 are :

11700
lo 9750
hi 10600

@ sox : did you try Ubuntu 8.10 ? The 2.28 kernel may resolve your problems.

Greetings,
Steven
I am currently setting up ubuntu 8.10, and will check that out..

---

### Post by soxs on 2009-01-08
Ok, I tested these LNB values, but no luck so far, not a single channel appears :-S

---

### Post by cb951303 on 2009-01-08
> **soxs said:**
> Ok, I tested these LNB values, but no luck so far, not a single channel appears :-S

Try the mercuriel drivers again in 8.10 if still no channels appear then it means you have a problem with your signal line. (considering that I have the exact same card and 8.10 on my computer)

---

### Post by soxs on 2009-01-08
The latest changes don't seem to like my PC... again the TV icon vanished from kaffeine -.-

---

### Post by soxs on 2009-01-08
Clone Post

---

### Post by soxs on 2009-01-09
Removing and reinstalling seems to fix that issue of vanished TV icon in kaffeine. So I will proably need some time, to check out wether input works or not...

---

### Post by cb951303 on 2009-01-09
remember tv icon also vanishes when your card is on use. so if you try to use 'scan' and open the kaffeine at the same time you won't see tv icon.

:popcorn:

---

