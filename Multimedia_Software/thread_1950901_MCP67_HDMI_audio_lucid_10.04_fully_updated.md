---
title: "MCP67 HDMI audio lucid 10.04 fully updated"
date: 2012-04-01
forum: Multimedia Software
---

### Post by alazare619 on 2012-04-01
A little info: Im using the stock video driver atm not proprietary drivers fresh install but I did apt-get purge pulseaudio to eliminate some issues video works flawlesslyI have checked alsamixer and made sure everything was not MM and was/is at 100 on volume

The tv is a vizio 42 inch and if it makes a diffrence this was a headless install then apt-get installed xubuntu-desktop

**LSPCI info**

```
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
```
[B]
aplay -l[/B]

```
alazare619@Voidd-Server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by BicyclerBoy on 2012-04-01
So what..
Do you have a problem with no audio over HDMI ?

I suspect that full HDMI audio capabilities is only possible when using nVidia driver but not sure with chipset HDMI audio..

dmesg | HDA
ls -al /proc/asound/card0/eld#*

if eld#0.0 etc files exist then post contents
i.e. 
cat /proc/asound/card0/eld#1.0

---

### Post by alazare619 on 2012-04-01
yes the issue is in fact that I have 0 audio what so ever over hdmi My only means to transmit audio is over the hdmi cable Ive never looked into this before as I always had a standalone home theather system that I ran headphone to rca cable converter and played soudn through there well now I no longer have that option so I must transmit the audio over hdmi

do you want me to run those commands btw?

---

### Post by alazare619 on 2012-04-01
Just installed the newest driver off the nvidia website and now aplay -l lists nothing

---

### Post by BicyclerBoy on 2012-04-02
You don't need the latest nVidia driver..
Installing from nVidia directly is a bad idea, recipe for problems later..
Much better to use launchpad ppa & use package management.

HDMI audio:
What you have to have is alsa-1.0.24 (or later) userspace (libraries utils) v& proprietary video driver.

With lucid 10.04 you need to add the iQuik audio ppa to upgrade alsa user-space to 1.0.24.

---

### Post by alazare619 on 2012-04-02
ok I added ubuntu x swat team update ppa, but how do i get the whole iquik ppa? and where can i find userspace?

---

### Post by alazare619 on 2012-04-02
[SIZE=2]Ok quick update, Fresh installed Headless

#apt-get update [/SIZE][SIZE=2]
#add-apt-repository **ppa:team-iquik/alsa**
#add-apt-repository [B]ppa:ubuntu-x-swat/x-updates
[/B][/SIZE][SIZE=1][SIZE=2]#[/SIZE][SIZE=2]apt-get update
#apt-get install xubuntu-desktop nvidia-current
#apt-get dist-upgrade

Dist-upgrade upgraded alsa to 1.0.24, thats where im at atm let me know where to continue and since I fresh installed pulse audio is back on it again[/SIZE]
[/SIZE]

---

### Post by BicyclerBoy on 2012-04-02
pulse-audio is not a problem..
You didn't need to make a fresh install just to remove the nVidia driver..

aplay -l
dmesg | grep HDA
speaker-test   (reports the alsa user version)

The eld# stuff posted earlier is likely pointless as I think your chipset HDA audio does not support ELD reporting.

---

### Post by alazare619 on 2012-04-02
aplay -l
```
alazare619@Voidd-Server:~$ aplay -l
aplay: device_list:240: no soundcards found...

```sudo aplay -l 

```
alazare619@Voidd-Server:~$ sudo aplay -l
[sudo] password for alazare619:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```dmesg | grep HDA

```
alazare619@Voidd-Server:~$ dmesg | grep HDA
[    9.852966] HDA Intel 0000:00:07.0: PCI->APIC IRQ transform: INT A -> IRQ 11
[    9.853002] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.780131] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input3
```speaker-test

```
alazare619@Voidd-Server:~$ speaker-test

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
```

ls -al /proc/asound/card0/

```
ls -al /proc/asound/card0/
total 0
dr-xr-xr-x 8 root root 0 2012-04-02 21:03 .
dr-xr-xr-x 5 root root 0 2012-04-02 21:03 ..
-r--r--r-- 1 root root 0 2012-04-02 21:03 codec#0
-r--r--r-- 1 root root 0 2012-04-02 21:03 codec#3
-r--r--r-- 1 root root 0 2012-04-02 21:03 id
-rw-r--r-- 1 root root 0 2012-04-02 21:03 oss_mixer
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm0c
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm0p
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm1c
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm1p
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm2c
dr-xr-xr-x 3 root root 0 2012-04-02 21:03 pcm3p

```

---

### Post by alazare619 on 2012-04-03
ttt

---

### Post by BicyclerBoy on 2012-04-03
You need to add your user to the audio group..

You have to be able to run aplay -l as a user & not sudo..

speaker-test -c 2 -r 48000 -D hw:0,3

---

### Post by alazare619 on 2012-04-10
> **BicyclerBoy said:**
> You need to add your user to the audio group..

You have to be able to run aplay -l as a user & not sudo..

speaker-test -c 2 -r 48000 -D hw:0,3
Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.964682
 0 - Front Left
 1 - Front Right
Time per period = 10.960683
 0 - Front Left
 1 - Front Right
Time per period = 10.960682
 0 - Front Left
 1 - Front Right
Time per period = 10.960683
 0 - Front Left
 1 - Front Right
Time per period = 10.960683
 0 - Front Left
 1 - Front Right
 

no sound tho

---

### Post by BicyclerBoy on 2012-04-10
But there are no errors & you ran speaker-test as a user (good).

Is possible your connected HDMI receiver has very limited capability..

speaker-test -c 2 -r 44100 -D hw:0,3

and again...
dmesg | grep HDA
ls -al /proc/asound/card0/

---

### Post by alazare619 on 2012-04-11
> **BicyclerBoy said:**
> But there are no errors & you ran speaker-test as a user (good).

Is possible your connected HDMI receiver has very limited capability..

speaker-test -c 2 -r 44100 -D hw:0,3

and again...
dmesg | grep HDA
ls -al /proc/asound/card0/
well i know audio works over hdmi as I've had a ps3 connected and audio works fine 

```
alazare619@Voidd-Server:~$ speaker-test -c 2 -r 44100 -D hw:0,3

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 11.944747

```

```
alazare619@Voidd-Server:~$ dmesg | grep HDA
[   11.881590] HDA Intel 0000:00:07.0: PCI->APIC IRQ transform: INT A -> IRQ 9
[   11.881622] HDA Intel 0000:00:07.0: setting latency timer to 64
[   12.952144] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input3

```
```
alazare619@Voidd-Server:~$ ls -al /proc/asound/card0/
total 0
dr-xr-xr-x 8 root root 0 2012-04-11 13:28 .
dr-xr-xr-x 5 root root 0 2012-04-11 13:28 ..
-r--r--r-- 1 root root 0 2012-04-11 13:28 codec#0
-r--r--r-- 1 root root 0 2012-04-11 13:28 codec#3
-r--r--r-- 1 root root 0 2012-04-11 13:28 id
-rw-r--r-- 1 root root 0 2012-04-11 13:28 oss_mixer
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm0c
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm0p
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm1c
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm1p
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm2c
dr-xr-xr-x 3 root root 0 2012-04-11 13:28 pcm3p

```

---

### Post by BicyclerBoy on 2012-04-11
Could post your /var/log/Xorg.0.log .. to see if nVidia graphics driver is loaded okay.
Never had a mobo with on-board HDMI with audio so not sure what is required to get it to work..

lsmod | grep snd

The files /proc/asound/card0/codec#0 & codec#3 should not be zero length..

Do you have folders ?
ls -al /proc/asound/NVidia/*

---

### Post by alazare619 on 2012-04-11
> **BicyclerBoy said:**
> Could post your /var/log/Xorg.0.log .. to see if nVidia graphics driver is loaded okay.
Never had a mobo with on-board HDMI with audio so not sure what is required to get it to work..

lsmod | grep snd

The files /proc/asound/card0/codec#0 & codec#3 should not be zero length..

Do you have folders ?
ls -al /proc/asound/NVidia/*

var/log/Xorg.0.log = [http://pastebin.com/qv3EGmg6](http://pastebin.com/qv3EGmg6)

```
alazare619@Voidd-Server:~$ lsmod | grep snd
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22165  4 
snd_hda_codec          74297  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  3 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  3 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm

```


as far as the files in /proc/asound/card0/ THEY ARE 0 BYTE files, however there is text inside of those files

```
alazare619@Voidd-Server:~$ ls -all /proc/asound/card0/
total 0
dr-xr-xr-x 8 root root 0 2012-04-11 15:40 .
dr-xr-xr-x 5 root root 0 2012-04-11 15:40 ..
-r--r--r-- 1 root root 0 2012-04-11 15:40 codec#0
-r--r--r-- 1 root root 0 2012-04-11 15:40 codec#3
-r--r--r-- 1 root root 0 2012-04-11 15:40 id
-rw-r--r-- 1 root root 0 2012-04-11 15:40 oss_mixer
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm0c
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm0p
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm1c
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm1p
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm2c
dr-xr-xr-x 3 root root 0 2012-04-11 15:40 pcm3p

```

The NVidia folder appears to be a symlink to card0
```
alazare619@Voidd-Server:~$ ls -all /proc/asound/NVidia
lrwxrwxrwx 1 root root 5 2012-04-11 15:41 /proc/asound/NVidia -> card0

```

---

### Post by BicyclerBoy on 2012-04-11
Likely have to use
sudo ls -al /proc/asound/card0/...    to get the file sizes etc because of the crazy alsa permissions.


The lsmod looks okay to me.. 

What's the contents of /proc/asound/card0/codec#3 ?

You haven't changed RAM (number slots or size) or the GPU memory allocated ?

---

### Post by alazare619 on 2012-04-11
> **BicyclerBoy said:**
> Likely have to use
sudo ls -al /proc/asound/card0/...    to get the file sizes etc because of the crazy alsa permissions.


The lsmod looks okay to me.. 

What's the contents of /proc/asound/card0/codec#3 ?

You haven't changed RAM (number slots or size) or the GPU memory allocated ?

```

alazare619@Voidd-Server:/mnt$ sudo cat /proc/asound/card0/codec#3
[sudo] password for alazare619:
Codec: Nvidia MCP67 HDMI
Address: 3
Function Id: 0x1
Vendor Id: 0x10de0067
Subsystem Id: 0x00670000
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x185601f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
```
```

alazare619@Voidd-Server:/mnt$ sudo ls -all /proc/asound/card0
total 0
dr-xr-xr-x 8 root root 0 2012-04-11 20:35 .
dr-xr-xr-x 5 root root 0 2012-04-11 20:35 ..
-r--r--r-- 1 root root 0 2012-04-11 20:35 codec#0
-r--r--r-- 1 root root 0 2012-04-11 20:35 codec#3
-r--r--r-- 1 root root 0 2012-04-11 20:35 id
-rw-r--r-- 1 root root 0 2012-04-11 20:35 oss_mixer
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm0c
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm0p
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm1c
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm1p
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm2c
dr-xr-xr-x 3 root root 0 2012-04-11 20:35 pcm3p

```

funny thing when i move codec#3 to a win box it shows a size of 900bytes

---

### Post by BicyclerBoy on 2012-04-12
The results in the last few posts are with :
- local HDMI display connected/turned on?
- local X server active on local display ?

The file size thing maybe because of file owner/group is root:root.

Alsa /proc/asound/ folder/file permissions are strange..
I change this (in lucid) for obscure reasons..

RAM I have read reports (maybe be nonsense) that suggest HDMI audio did not work on ION without >=512MB for GPU..VDPAU on ION did require >=512MB in the past..

---

### Post by alazare619 on 2012-04-13
> **BicyclerBoy said:**
> The results in the last few posts are with :
- local HDMI display connected/turned on?
- local X server active on local display ?

The file size thing maybe because of file owner/group is root:root.

Alsa /proc/asound/ folder/file permissions are strange..
I change this (in lucid) for obscure reasons..

RAM I have read reports (maybe be nonsense) that suggest HDMI audio did not work on ION without >=512MB for GPU..VDPAU on ION did require >=512MB in the past..

so what do you suggest i go from here as far as ram wise i can raise it up to 256 at highest i belive want me to change owner of /proc/asoudn to owner/user alazare619?

---

### Post by BicyclerBoy on 2012-04-13
The ownership & permissions only seems to be a problem with MythTV setting alsa buffer size..This doesn't cause real problems with 0.24 unless using HDA audio formats.
It is always possible to raise the buffer size with sudo or to 'fix' the permissions in a start-up file.

I believe that ION (all vdpau cards) needed >=512MB for VDPAU.
For some mobos this requires 2 RAM modules of some minimum size (2x1GB ?).
You may need to set the BIOS to AUTO GPU memory aperture/shared to get to 512MB..

Forget all this ION VDPAU talk...your 7050PV chipset has **NO** VDPAU processor.
I was confusing this chipset with another model..

---

### Post by alazare619 on 2012-04-15
well going to try a new hdmi cable if this doesnt work im going to try fedora 16 (live) or something to see if i get audio in there if so i think im going to go the route of reloading from headless but this time have the alsa ppa in it so i dont pull any bad / old packages that dont support my chipset

---

### Post by BicyclerBoy on 2012-04-16
You can get a new PCI-express video card for less money than a HDMI cable..
[http://www.phoronix.com/scan.php?page=article&item=nvidia_9600gso_nouveau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_9600gso_nouveau&num=1)

But a cheap video card I would recommend is GT520 for **non**-interlaced material. Typical broadcast (via tuner cards) is interlaced.
The GT520 has very good VDPAU decode capability but weak shaders.

GT430 is a good price/performance point.
Both GT430 & GT520 have HDA HDMI audio.

---

