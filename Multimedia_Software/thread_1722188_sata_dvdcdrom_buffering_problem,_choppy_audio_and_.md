---
title: "sata dvd/cdrom buffering problem, choppy audio and video"
date: 2011-04-05
forum: Multimedia Software
---

### Post by Jay Christnach on 2011-04-05
hello dear people,

as the title says. The formats audio or dvd  are correctly recognised but audio and video plays choppy. I tried with  different applications. mplayer cdda://1 gives no error messages but the  audio track skips. I tried with brand new cds and dvds.

uname -a
Linux fermi 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

it runs on a rather recent dual core 64bit amd with nvidia chipset, the dvd unit has not been used much too  

lshw -C disk
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S223C
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready

with inserted audio cd:
     *-medium
          physical id: 0
          logical name: /dev/cdrom

i  get many of the following messages in kern.log when inserting an audio  cd. A dialogue on the desktop pops up asking for the application to play  an audio CD.

Apr  5 21:16:30 fermi kernel: [11549.799786] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  5 21:16:30 fermi kernel: [11549.799793] sr 5:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Apr  5 21:16:30 fermi kernel: [11549.799800] sr 5:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Apr  5 21:16:30 fermi kernel: [11549.799809] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Apr  5 21:16:30 fermi kernel: [11549.799823] end_request: I/O error, dev sr0, sector 0


when inserting a dvd (a Hitchcock movie :-) ) I get these errors:

Apr  5 21:19:29 fermi kernel: [11728.855975] __ratelimit: 116 callbacks suppressed
Apr  5 21:19:29 fermi kernel: [11728.855981] Buffer I/O error on device sr0, logical block 2030175
Apr  5 21:19:29 fermi kernel: [11728.886015] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  5 21:19:29 fermi kernel: [11728.886022] sr 5:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Apr  5 21:19:29 fermi kernel: [11728.886029] sr 5:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Apr  5 21:19:29 fermi kernel: [11728.886039] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 3d f4 be 00 00 02 00
Apr  5 21:19:29 fermi kernel: [11728.886054] end_request: I/O error, dev sr0, sector 16241400
Apr  5 21:19:29 fermi kernel: [11728.886061] Buffer I/O error on device sr0, logical block 2030175
Apr  5 21:19:29 fermi kernel: [11729.278692] UDF-fs: Partition marked readonly; forcing readonly mount
Apr  5 21:19:29 fermi kernel: [11729.312270] UDF-fs INFO UDF: Mounting volume 'VERTIGO_G2', timestamp 2003/04/17 16:56 (1078)

The udf file system seems to get corrrectly mounted and I can list the files.

fsck /dev/sr0
fsck from util-linux-ng 2.17.2
fsck: fsck.udf: not found
fsck: Error 2 while executing fsck.udf for /dev/sr0

error 2 states "system should be rebooted". I'll do that afterwards and see if I can get more info.

lsmod gives:

Module                  Size  Used by
nls_utf8                1421  1 
udf                    85529  1 
crc_itu_t               1715  1 udf
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37367  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
hwmon_vid               3130  0 
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
joydev                 11104  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
usbhid                 41116  0 
max6650                10482  0 
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
hid                    83600  1 usbhid
snd_rawmidi            23420  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                 57481  10  snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device           6888  8  snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                     71251  18  snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usblp                  12407  0 
emu10k1_gp              1964  0 
psmouse                64576  0 
k8temp                  4040  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
nvidia              10832442  42 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
serio_raw               4918  0 
gameport               10966  2 emu10k1_gp
soundcore               8052  1 snd
lp                      9336  0 
parport                37160  2 ppdev,lp
i2c_nforce2             6099  0 
usb_storage            50377  1 
ohci1394               30260  0 
forcedeth              55624  0 
ieee1394               94771  1 ohci1394
pata_amd               11962  0 
ahci                   37870  6 


Well  I already googled for hours and read many forum posts about similar  issues (although always a little different), to no avail. I hope  somebody can help.

kind greetings..

---

### Post by BicyclerBoy on 2011-04-06
Ubuntu 10.04 & the same kernel version as you..

Recently (last 2 months) DVD playback has been unusable & have resorted to using the old DVD player. Similar error messages to you but I don't think your DVD error messages are the real problem..they look normal.

My 10.10 computer plays DVDs fine.

With the latest kernel 2.6.32-31 the problem may have been resolved. (expt with 1 DVD).

---

### Post by Jay Christnach on 2011-04-12
Thanks bycyclerboy for your reply.

A newer kernel didn't solve the issue.

I now discovered the "read of scrambled sector without authentication" error and googled for it. I found a source on linuxquestions stating that one should check for libdvdcss. After installing libdvdcss2 the dvd-videos play allright.

But the problem is only partly solved, because audio cds still play with gaps every few seconds.

best regards

---

### Post by BicyclerBoy on 2011-04-13
Sorry should have asked you if you meant stamped/bought DVDs..
Could have pointed you to css stuff.

Remember that after a distribution upgrade you have to re-activate medibuntu etc..& re-run the script.

There is/was something wrong with 10.04 kernel & mounting DVDs/filesystem.

If you play music (with the same player) from file , do you have gaps/breaks ?

Long shot.. Could be resampling 44.1 to 48KHz problems with audio device.
Try to get mplayer to resample to 48KHz
-af resample=48000

---

