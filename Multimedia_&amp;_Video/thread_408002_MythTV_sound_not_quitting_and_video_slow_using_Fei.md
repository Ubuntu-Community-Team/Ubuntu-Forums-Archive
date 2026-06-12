---
title: "MythTV sound not quitting and video slow using Feisty Fawn (7.0.4)"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by michwill on 2007-04-12
Hi all,

I'm having trouble with my MythTV setup.  My setup is as follows:

1) I have a vanilla install of Ubuntu Feisty Fawn 7.0.4 Alternate Install
2) using on-board sound
3) Motherboard:  [http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?DetailID=387&MenuID=92&LanID=0](http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?DetailID=387&MenuID=92&LanID=0)
4) TV Tuner: [http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=321](http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=321)


My issues are as follows:

1) Video is slow using Ubuntu (Although Fedora is acceptable)
2) Sound doesn't quit after leaving MythTV (this is very very very annoying)

. . .any help would be appreciated.

Regards,
Michael

---

### Post by majoridiot on 2007-04-13
did you install the firmware for that card?

```
$ wget http://pchdtv.com/downloads/firmware.tar.gz
$ tar xzzf firmware.tar.gz firmware
$ sudo cp firmware/* /lib/firmware
$ rm firmware firmware.tar.gz
```

a reboot may be required.

---

### Post by michwill on 2007-04-14
Well, I don't have a DVB or HDTV card so I didn't think that this would apply.  Should I still install it?

---

### Post by majoridiot on 2007-04-14
no... i misread your card, sorry.

what is the output of:

```
$ lspci -vn
```

and 

```
$ dmesg | grep bttv
```

and

```
$ cat /etc/modprobe.d/bttv
```

---

### Post by michwill on 2007-04-14
$lspci -vn   says this:
```
00:00.0 0600: 1106:0314
	Subsystem: 1019:1623
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:00.1 0600: 1106:1314
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 0

00:00.2 0600: 1106:2314
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 0

00:00.3 0600: 1106:3208
	Flags: bus master, medium devsel, latency 0

00:00.4 0600: 1106:4314
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 0

00:00.7 0600: 1106:7314
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 0

00:01.0 0604: 1106:b198 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fca00000-feafffff
	Prefetchable memory behind bridge: e7f00000-f7efffff
	Capabilities: <access denied>

00:0a.0 0400: 109e:036e (rev 11)
	Subsystem: 107d:6606
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f7fff000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

00:0a.1 0480: 109e:0878 (rev 11)
	Subsystem: 107d:6606
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f7ffe000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 0101: 1106:3149 (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e000 [size=256]
	Capabilities: <access denied>

00:0f.1 0101: 1106:0571 (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 32, IRQ 16
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 0c03: 1106:3038 (rev 81) (prog-if 00 [UHCI])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

00:10.1 0c03: 1106:3038 (rev 81) (prog-if 00 [UHCI])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at d880 [size=32]
	Capabilities: <access denied>

00:10.2 0c03: 1106:3038 (rev 81) (prog-if 00 [UHCI])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

00:10.3 0c03: 1106:3038 (rev 81) (prog-if 00 [UHCI])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at d480 [size=32]
	Capabilities: <access denied>

00:10.4 0c03: 1106:3104 (rev 86) (prog-if 20 [EHCI])
	Subsystem: 1019:1623
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 0601: 1106:3227
	Subsystem: 1019:1623
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 0401: 1106:3059 (rev 60)
	Subsystem: 1019:aa51
	Flags: medium devsel, IRQ 20
	I/O ports at d000 [size=256]
	Capabilities: <access denied>

00:12.0 0200: 1106:3065 (rev 78)
	Subsystem: 1019:0102
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at ee00 [size=256]
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
	Subsystem: 270f:1942
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: <access denied>

```


$dmesg | grep bttv   says this:

```

[   52.277404] bttv: driver version 0.9.16 loaded
[   52.277409] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   52.277515] bttv: Bt8xx card found (0).
[   52.277560] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 19, latency: 64, mmio: 0xf7fff000
[   52.277580] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   52.277583] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   52.277618] bttv0: gpio: en=00000000, out=00000000 in=00bff507 [init]
[   52.278116] bttv0: using tuner=5
[   52.278120] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   52.278832] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   52.279569] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   52.280285] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   52.313464] bttv0: registered device video0
[   52.313497] bttv0: registered device vbi0
[   52.313527] bttv0: registered device radio0
[   52.313547] bttv0: PLL: 28636363 => 35468950 .. ok
[   52.346937] input: bttv IR (card=34) as /class/input/input7
[   81.793267] bttv0: PLL can sleep, using XTAL (28636363).

```


. . .and there is no /etc/modprobe.d/bttv file

/etc/modprobe.d/ contains the following:
```

aliases
alsa-base
arch
arch-aliases
blacklist
blacklist-framebuffer
blacklist-modem
blacklist-oss
blacklist-scanner
blacklist-watchdog
bluez
ibm_acpi.modprobe
ipw3945
isapnp
libpisock9
lrm-video
nvidia-kernel-nkc
options
toshiba_acpi.modprobe
```

---

### Post by majoridiot on 2007-04-14
if you do a test capture with:

```
$ cat /dev/video0 > test.mpg 
```

does it play back correctly?

also, please define "video is slow"- does it skip, hesitate or lag behind the sound?

---

### Post by michwill on 2007-04-14
No, video output fails.  Neither Totem nor VLC can play back what's captured.  By slow, I mean all of the above.  It skips frames, plays in what seems like slow motion (a tiny tiny bit of ghosting), and the sound is out of sync.  It definitely seems to be a driver issue considering that I don't have nearly these issues in Fedora.

---

### Post by michwill on 2007-04-17
. . .any ideas?

---

### Post by majoridiot on 2007-04-17
what is the result of:

```
$ sudo sh -c "dmesg | egrep '(bttv|bt87?|tveeprom)'"
```

---

### Post by michwill on 2007-04-17
```
[   54.045117] bttv: driver version 0.9.16 loaded
[   54.045122] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   54.045188] bttv: Bt8xx card found (0).
[   54.045236] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 19, latency: 64, mmio: 0xf7fff000
[   54.045247] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   54.045251] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   54.045285] bttv0: gpio: en=00000000, out=00000000 in=00bff107 [init]
[   54.045736] bttv0: using tuner=5
[   54.045740] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   54.046471] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   54.047287] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   54.048023] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   54.074387] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   54.084661] bttv0: registered device video0
[   54.084692] bttv0: registered device vbi0
[   54.084743] bttv0: registered device radio0
[   54.084763] bttv0: PLL: 28636363 => 35468950 .. ok
[   54.119340] input: bttv IR (card=34) as /class/input/input7
[   54.379213] bt878: AUDIO driver version 0.0.0 loaded
[   83.921084] bttv0: PLL can sleep, using XTAL (28636363).
```

---

### Post by michwill on 2007-04-18
Any ideas? Do we think this is just a Feisty issue?  Should I work with 6.10 instead?

---

### Post by majoridiot on 2007-04-18
one more... the output of:

```
$ lsmod 
```

and then we'll take a run at it. :)

---

### Post by michwill on 2007-04-18
it reads as follows:


```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
button                  8720  0 
video                  16388  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
container               5248  0 
ipv6                  268704  14 
xfs                   562008  1 
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
bt878                  11960  0 
snd_bt87x              16292  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
parport_pc             36388  1 
xpad                    9988  0 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tuner                  61864  0 
bttv                  173684  1 bt878
parport                36936  3 ppdev,lp,parport_pc
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_bt87x,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9472  1 snd_via82xx
psmouse                38920  0 
i2c_viapro             10132  0 
snd_timer              23684  2 snd_seq,snd_pcm
video_buf              26116  1 bttv
ir_common              31236  1 bttv
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
pcspkr                  4224  0 
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
i2c_core               22784  6 i2c_ec,tuner,bttv,i2c_viapro,i2c_algo_bit,tveeprom
videodev               28160  1 bttv
v4l2_common            25216  3 tuner,bttv,videodev
v4l1_compat            15236  1 videodev
snd                    54020  14 snd_bt87x,snd_seq_oss,snd_via82xx,snd_seq,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_bt87x,snd_via82xx,snd_pcm
via_agp                11264  1 
agpgart                35400  1 via_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  8 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
usbhid                 26592  0 
hid                    27392  1 usbhid
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
via82cxxx              10372  0 [permanent]
generic                 5124  0 [permanent]
floppy                 59524  0 
ehci_hcd               34188  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
uhci_hcd               25360  0 
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
ata_generic             9092  0 
sata_via               12548  0 
libata                125336  2 ata_generic,sata_via
scsi_mod              142348  1 libata
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
```

---

### Post by majoridiot on 2007-04-18
it might be trying to use the wrong tuner... try:

```
sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv
```

then

```
sudo modprobe bttv card=34 tuner=43
```

see if that helps... or if it tunes anything at all.

---

### Post by michwill on 2007-04-18
. . .actually I did that on installs 3,4, and 5.  Didn't affect anything.  I'll try it again though.

---

### Post by michwill on 2007-04-18
. . .nope, still slow video (low FPS, and sound lags).


This makes no sense. XawTV works fine.  I'd simply use it if it were even as remotely full featured as Myth.  FYI, I appreciate your input thusfar.

---

### Post by majoridiot on 2007-04-18
well, if it works fine in xawtv, then we should be able to get it running in mythtv. :) 
get it back to the point that it works in xawtv, so it is in a known "good" state.  

what are your tuner settings for that card in mythtv-setup?

---

### Post by michwill on 2007-04-18
Analog V4L capture card

/dev/video0

BT878 video (Leadtek Winfast 20 [bttv])

/dev/vbi0

/dev/dsp

---

### Post by michwill on 2007-04-18
. . .just tried XawTV again.  It works fine.

---

### Post by majoridiot on 2007-04-18
ok... now you have me wondering.  xawtv plays fine, but you can't do a cat /dev/video0 > test.mpg and get a playable file?

---

### Post by michwill on 2007-04-18
Correct.  It captures data from video0, but the file isn't playable.  Not even VLC would play it.

---

### Post by michwill on 2007-04-19
. . .even tried Cinelerra (video editing program) and it couldn't properly play it.  The video output was completely garbled, regular intervals of static sound (every 2 seconds or so), and the occasional flicker.

---

### Post by edmondt on 2007-04-20
I have the same card with the same video slow down with mythtv... I was impressed on how easy the mythtv install was tho, just sudo apt-get install mythtv :)

TV is fine on XawTV, but mythTV is really slow....

---

### Post by majoridiot on 2007-04-20
not to slough this off or anything... but have you tried asking at the mythtv forums to see if anyone there has seen
the same thing?

it's a puzzler...

---

### Post by michwill on 2007-04-20
Yup, I have, but it was poopooed (I'm sure that's a word) off as "well wait until Feisty is officially released before complaining".  Since it's released I suppose I'll post again ;)  Thanks!

---

### Post by majoridiot on 2007-04-20
yeah, they can be that way sometimes.  did you try this at all with edgy or was feisty your first shot at ubuntu mythtv?

i'll talk to superm1 about this and see if he has any thoughts.  i've pretty much exhausted google on this one.

---

### Post by michwill on 2007-04-22
ok. . .wow. . .I installed Xubuntu and the majority of my problems simply went away.  Now the only issue I see is that of sound lag, or rather, video lag.  This in the sense of only being a second or so behind, not low framerate.  The video speed is now near perfect, simply out of sync with the sound.  Any suggestions?

---

### Post by michwill on 2007-04-22
. . .moving right along.  I've got the sound sync issue solved, but now the sound is static.  I can't increase or decrease the volume and there is an odd droning noise in the background as if something is turned up too loud and producing odd feedback.  *shrug*

---

### Post by majoridiot on 2007-04-23
run alsamixer and make sure that all capture inputs *except* the input you are using for mythtv are muted and then try so
strike a good balance between the capture input you are using and the master volume.

also, make sure you are using the correct input for audio in mythtv-setup.  the new feisty packages now default to ALSA driver PCM-
that may need to be changed, depending on your configuration.

---

### Post by michwill on 2007-04-23
Yeah, I went through about a bajillion (give or take) combinations before realizing I shouldn't use the LINEIN.  I installed "alsamixer-gui" and muted the LINEIN, but placed the two red dots over LINEIN and all worked.

As a side question, what exactly do those red/white dots mean anyway?  I know that clicking the speaker icons mutes or unmutes the channel, but the dots are a bit of an enigma.

Now my only problems are getting a properly set up lircrc file (for remote control use) and getting that confounded high pitched drone noise to stop.

The drone noise sounds like feedback as if i've got the volume cranked despite it's low output volume.

As for changing the Audio in Myth, I've tried every  "dsp" option to no avail.  *shrug*

---

### Post by majoridiot on 2007-04-23
if you are using alsa try (settings for frontend- playback-->general):

audio output device ALSA:default
mixer device: default
mixer controls: PCM (or your preference)

your feedback may be related to the settings on line-in.  you want it **set** to capture with the appropriate levels
and you likely want the playback **muted** on line-in. you can launch alsamixer with the -v capture option to show
capture settings as opposed to playback.

for a beter understanding of alsamixer:

```
man alsamixer
```

---

### Post by michwill on 2007-04-24
I twiddled around with the settings there and adjusting the capture values did decrease the volume of the drone, but it's still there.  Also I'm having static artifacts that make it sound people are talking through a kazoo.

---

### Post by michwill on 2007-04-24
Is it perhaps a problem with xine?

---

### Post by josesanders on 2007-04-24
> $ cat /dev/video0 > test.mpg

This only works when the stream is mpg.  Correct me if I'm wrong, but isn't your card a capture card, not an encoder card?  It that's the case, the stream is raw video, not mpeg encoded, which might not be playable with most media players.

---

### Post by michwill on 2007-04-24
Thanks josesanders, you may be right.  I've actually gotten past that issue however.  I installed Xubuntu and all video issues pretty much went away.

Now I'm dealing with weird sound artifacts that only occur in MythTV and not TVTime or XawTV.  I'm guessing it's because with MythTV I'm using processed sound, and with the others I'm using the sound directly from LINEIN.  Still I don't know how to fix this issue.

---

### Post by majoridiot on 2007-04-24
> **michwill said:**
> Thanks josesanders, you may be right.  I've actually gotten past that issue however.  I installed Xubuntu and all video issues pretty much went away.

Now I'm dealing with weird sound artifacts that only occur in MythTV and not TVTime or XawTV.  I'm guessing it's because with MythTV I'm using processed sound, and with the others I'm using the sound directly from LINEIN.  Still I don't know how to fix this issue.

since that is a capcard (never realized it, duh!) have you tried changing the audio settings for capture?

setup-->tv settings-->recording profiles-->software encoders-->live tv

if it is set to cap at 32Khz, first try boosting it to 48K and see if that helps any in livetv.

---

### Post by michwill on 2007-04-24
Hrm, there is no option there.  Perhaps it's under another menu?

---

### Post by majoridiot on 2007-04-24
see if there is a setting for the tuner card in mythtv-setup.  it's there for other cards.

---

### Post by michwill on 2007-04-24
yeah, just tried. . .mythtv-setup has 32k, 44k, and 48k.  None of them made a difference.  Gimme a sec while I go pull out a bit of my hair.  ;)

---

### Post by majoridiot on 2007-04-24
at this point, you might try subscribing to the mythtv-users mailing list and asking there... 

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

---

### Post by michwill on 2007-04-24
Done.  Thanks for your help.

---

### Post by michwill on 2007-04-25
Got it figured out!  Thanks to majoridiot and superm1!  Basically the final part was fixing the Transcoder(s) in the Mythfrontend.  Changing to MPEG instead of RTJPEG and adjusting the MP3 encoding fixed my problems.

---

### Post by majoridiot on 2007-04-25
glad you finally got it working! :D

you might want to post a follow-up to your mythv-users list and let folks know it is resolved and how, so that others
can learn from your pain.  LOL

---

### Post by michwill on 2007-04-25
Done.  Thanks again!

---

### Post by lowebb on 2007-10-21
Awaking this thread again because I'm having similar problems and was hoping you could specify what you've done to fix this.

I have an analogue card (hauppage) which uses a line-out from the card to line-in and works fine with tvtime, but with mythtv the audio is about 3 sec's behind the video. Additionally, the audio continues even after I leave the channel, so if I switch mythtv off, the audio continues.

I've tried looking at everything mentioned in this thread but have had no luck. Any help would be appreciated

---

### Post by bboons on 2007-10-21
I'm having a similar problem with audio. I have an ATI TV Wonder card with it's audio out plugged into the sound card audio in. Myth appears to start fine with audio and all but after I close the MythTv application the audio continues. Also, when I pause and rewind etc. the picture does the right things but the audio is always live.
Please help. BTW, I'm running Gusty.

---

### Post by lowebb on 2007-10-22
This has to be a common problem with analogue cards. Come on guys whats the secret!

---

### Post by applegrew on 2007-10-25
Hi just came-by to say that I too encountered the "slow video" problem with MythTV. This happens everytime the audio capture device (in The capture device section of mythtv-setup) is set to /dev/dsp. If I set this to /dev/dsp then it works properly.

---

