---
title: "No HDMI sound in XBMC"
date: 2011-10-02
forum: Multimedia Software
---

### Post by petri on 2011-10-02
On VLC there is sound for 5.1 but no way I succeed with XBMC. I'm out of ideas and seems like even threads via Google. 

My ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
 can be found here: [http://www.alsa-project.org/db/?f=e7d6200a4ae925d6c7a51ea93967c4e534393f8e](http://www.alsa-project.org/db/?f=e7d6200a4ae925d6c7a51ea93967c4e534393f8e)


edit: sound is coming from Nvidia Geforce GT430.

---

### Post by BicyclerBoy on 2011-10-02
Good choice of video card..

You should get your alsa user-space (lib & utils) to 1.0.24.
Try ricotz-unstable ppa.
[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick](https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick)

You need to be running the nVidia driver..probably 260 or later.

Then try
speaker-test -c 2 -r 48000 -D hw:1,9
speaker-test -c 2 -r 48000 -D hw:1,8
speaker-test -c 2 -r 48000 -D hw:1,7
speaker-test -c 2 -r 48000 -D hw:1,3

open & close terminal each time.


It looks like hw:1,9 is connected so try
speaker-test -c 8 -r 192000 -D hw:1,9

---

### Post by petri on 2011-10-03
Thanks for your advice about videocard!


Seems like I got alsa user-space (lib & utils) to 1.0.24 according to: [http://www.alsa-project.org/db/?f=c996a7518187060aac3be57d934b6d1ef4db9f47](http://www.alsa-project.org/db/?f=c996a7518187060aac3be57d934b6d1ef4db9f47) but now I have no sound at all.

```
~$ speaker-test -c 8 -r 192000 -D hw:1,9

speaker-test 1.0.24.2

Playback device is hw:1,9
Stream parameters are 192000Hz, S16_LE, 8 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy

```

and none of the **speaker-test -c 2 -r 48000 -D hw:1,X** gives any sound.


edit:
```
~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)
```

---

### Post by BicyclerBoy on 2011-10-03
Make sure you close/re-open terminal with each speaker-test cmd..
No other program can have the alsa device open/in-use.

Can you post your
aplay -l
dmesg | grep HDMI

maybe something else has changed..

Note:
- you must be using nVidia driver (that supports your GPU)
- X screen must be active
- must have a HDMI receiver attached. (DVI-D-HDMI okay)

---

### Post by petri on 2011-10-03
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
~$ dmesg | grep HDMI
[   18.111796] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[   18.131272] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[   18.151275] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[   18.171289] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   20.100034] HDMI: detected monitor VSX-521
[   20.100037]       at connection type HDMI
[   20.100040] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   20.100045] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   20.100050] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[   20.100054] HDMI: supports coding type AC-3: channels = 6, rates = 44100 48000 88200, max bitrate = 640000
[   20.100058] HDMI: supports coding type DTS: channels = 7, rates = 48000 88200 176400 192000, max bitrate = 1536000
[   20.100061] HDMI: supports coding type DSD (One Bit Audio): channels = 2, rates = 48000 176400 384000
[   20.100064] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[   20.100068] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 176400 192000 384000
[   20.100072] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 176400 192000 384000
[   22.941269] HDMI: ASP channel 0 => slot 0
[   22.970052] HDMI: ASP channel 1 => slot 1
[   22.990032] HDMI: ASP channel 15 => slot 2
[   23.010012] HDMI: ASP channel 15 => slot 3
[   23.030025] HDMI: ASP channel 15 => slot 4
[   23.050045] HDMI: ASP channel 15 => slot 5
[   23.070026] HDMI: ASP channel 15 => slot 6
[   23.082913] HDMI: ASP channel 15 => slot 7
[   23.101280] HDMI: ELD buf size is 95
[   23.121277] HDMI: DIP GP[0] buf size is 23
[   23.141271] HDMI: DIP GP[1] buf size is 23
[   23.161283] HDMI: DIP GP[2] buf size is 23
[   23.181274] HDMI: DIP GP[3] buf size is 23
[   23.201284] HDMI: DIP GP[4] buf size is 0
[   23.221279] HDMI: DIP GP[5] buf size is 0
[   23.241278] HDMI: DIP GP[6] buf size is 0
[   23.261280] HDMI: DIP GP[7] buf size is 0
[  236.661300] ALSA patch_hdmi.c:451: HDMI: select CA 0x13 for 8-channel allocation:  FL/FR LFE FC RL/RR RLC/RRC
[  236.780029] HDMI: ASP channel 0 => slot 0
[  236.800026] HDMI: ASP channel 1 => slot 1
[  236.820030] HDMI: ASP channel 5 => slot 2
[  236.840047] HDMI: ASP channel 4 => slot 3
[  236.860029] HDMI: ASP channel 6 => slot 4
[  236.880028] HDMI: ASP channel 7 => slot 5
[  236.900025] HDMI: ASP channel 2 => slot 6
[  236.920028] HDMI: ASP channel 3 => slot 7
[  236.940020] HDMI: ELD buf size is 95
[  236.960030] HDMI: DIP GP[0] buf size is 23
[  236.980027] HDMI: DIP GP[1] buf size is 23
[  237.000024] HDMI: DIP GP[2] buf size is 23
[  237.021298] HDMI: DIP GP[3] buf size is 23
[  237.041276] HDMI: DIP GP[4] buf size is 0
[  237.061297] HDMI: DIP GP[5] buf size is 0
[  237.081283] HDMI: DIP GP[6] buf size is 0
[  237.101271] HDMI: DIP GP[7] buf size is 0
[  273.841273] HDMI: ASP channel 0 => slot 0
[  273.861273] HDMI: ASP channel 1 => slot 1
[  273.881277] HDMI: ASP channel 15 => slot 2
[  273.901268] HDMI: ASP channel 15 => slot 3
[  273.921269] HDMI: ASP channel 15 => slot 4
[  273.941273] HDMI: ASP channel 15 => slot 5
[  273.961268] HDMI: ASP channel 15 => slot 6
[  273.981277] HDMI: ASP channel 15 => slot 7
[  274.001278] HDMI: ELD buf size is 95
[  274.021278] HDMI: DIP GP[0] buf size is 23
[  274.041268] HDMI: DIP GP[1] buf size is 23
[  274.061276] HDMI: DIP GP[2] buf size is 23
[  274.081279] HDMI: DIP GP[3] buf size is 23
[  274.101274] HDMI: DIP GP[4] buf size is 0
[  274.121269] HDMI: DIP GP[5] buf size is 0
[  274.141268] HDMI: DIP GP[6] buf size is 0
[  274.161274] HDMI: DIP GP[7] buf size is 0
[  275.626077] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  275.640027] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  276.306787] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  276.328563] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  276.350030] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[  276.370025] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[  278.290040] HDMI: detected monitor VSX-521
[  278.290042]       at connection type HDMI
[  278.290045] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[  278.290050] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[  278.290055] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[  278.290059] HDMI: supports coding type AC-3: channels = 6, rates = 44100 48000 88200, max bitrate = 640000
[  278.290062] HDMI: supports coding type DTS: channels = 7, rates = 48000 88200 176400 192000, max bitrate = 1536000
[  278.290066] HDMI: supports coding type DSD (One Bit Audio): channels = 2, rates = 48000 176400 384000
[  278.290069] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[  278.290073] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 176400 192000 384000
[  278.290077] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 176400 192000 384000
[  889.403897] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  889.430025] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  889.482311] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  889.510023] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[  889.530027] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[  889.550053] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[  891.470087] HDMI: detected monitor VSX-521
[  891.470089]       at connection type HDMI
[  891.470093] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[  891.470098] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[  891.470103] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16 20 24
[  891.470106] HDMI: supports coding type AC-3: channels = 6, rates = 44100 48000 88200, max bitrate = 640000
[  891.470110] HDMI: supports coding type DTS: channels = 7, rates = 48000 88200 176400 192000, max bitrate = 1536000
[  891.470114] HDMI: supports coding type DSD (One Bit Audio): channels = 2, rates = 48000 176400 384000
[  891.470117] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[  891.470120] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 176400 192000 384000
[  891.470124] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 88200 176400 192000 384000
[ 1752.531301] ALSA patch_hdmi.c:451: HDMI: select CA 0x13 for 8-channel allocation:  FL/FR LFE FC RL/RR RLC/RRC
[ 1752.650020] HDMI: ASP channel 0 => slot 0
[ 1752.670042] HDMI: ASP channel 1 => slot 1
[ 1752.690026] HDMI: ASP channel 5 => slot 2
[ 1752.710027] HDMI: ASP channel 4 => slot 3
[ 1752.730028] HDMI: ASP channel 6 => slot 4
[ 1752.750025] HDMI: ASP channel 7 => slot 5
[ 1752.770024] HDMI: ASP channel 2 => slot 6
[ 1752.790042] HDMI: ASP channel 3 => slot 7
[ 1752.810028] HDMI: ELD buf size is 95
[ 1752.830025] HDMI: DIP GP[0] buf size is 23
[ 1752.850029] HDMI: DIP GP[1] buf size is 23
[ 1752.870030] HDMI: DIP GP[2] buf size is 23
[ 1752.890027] HDMI: DIP GP[3] buf size is 23
[ 1752.910030] HDMI: DIP GP[4] buf size is 0
[ 1752.930027] HDMI: DIP GP[5] buf size is 0
[ 1752.950021] HDMI: DIP GP[6] buf size is 0
[ 1752.970013] HDMI: DIP GP[7] buf size is 0
[ 1785.390023] HDMI: ASP channel 0 => slot 0
[ 1785.410023] HDMI: ASP channel 1 => slot 1
[ 1785.430039] HDMI: ASP channel 15 => slot 2
[ 1785.450027] HDMI: ASP channel 15 => slot 3
[ 1785.470026] HDMI: ASP channel 15 => slot 4
[ 1785.490041] HDMI: ASP channel 15 => slot 5
[ 1785.510019] HDMI: ASP channel 15 => slot 6
[ 1785.530028] HDMI: ASP channel 15 => slot 7
[ 1785.550016] HDMI: ELD buf size is 95
[ 1785.570028] HDMI: DIP GP[0] buf size is 23
[ 1785.590028] HDMI: DIP GP[1] buf size is 23
[ 1785.610027] HDMI: DIP GP[2] buf size is 23
[ 1785.630018] HDMI: DIP GP[3] buf size is 23
[ 1785.650026] HDMI: DIP GP[4] buf size is 0
[ 1785.670027] HDMI: DIP GP[5] buf size is 0
[ 1785.690027] HDMI: DIP GP[6] buf size is 0
[ 1785.710022] HDMI: DIP GP[7] buf size is 0


```



edit:
> **BicyclerBoy said:**
> ...

Note:
- you must be using nVidia driver (that supports your GPU)
- X screen must be active
- must have a HDMI receiver attached. (DVI-D-HDMI okay)

I have all of those. I edited my previous post with Nvidias driver version a minute after you posted.

---

### Post by BicyclerBoy on 2011-10-03
looks fine ..but the dmesg messages at 1752 secs look a bit weird..

cat /proc/asound/card1/eld#3.0

or maybe your hdmi device needs something real basic
speaker-test -c2 -r 44100 -F S16_LE -D hw:1,9

---

### Post by petri on 2011-10-03
```
~$ cat /proc/asound/card1/eld#3.0
monitor_present		1
eld_valid		1
monitor_name		VSX-521
     
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x2f41
product_id		0x0
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count		8
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0x1] LPCM
sad1_channels		8
sad1_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad1_bits		[0xe0000] 16 20 24
sad2_coding_type	[0x2] AC-3
sad2_channels		6
sad2_rates		[0xe0] 44100 48000 88200
sad2_max_bitrate	640000
sad3_coding_type	[0x7] DTS
sad3_channels		7
sad3_rates		[0x6c0] 48000 88200 176400 192000
sad3_max_bitrate	1536000
sad4_coding_type	[0x9] DSD (One Bit Audio)
sad4_channels		2
sad4_rates		[0xa40] 48000 176400 384000
sad5_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels		8
sad5_rates		[0xc0] 48000 88200
sad6_coding_type	[0xb] DTS-HD
sad6_channels		8
sad6_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad7_coding_type	[0xc] MLP (Dolby TrueHD)
sad7_channels		8
sad7_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
```




edit:

```
~$ speaker-test -c2 -r 44100 -F S16_LE -D hw:1,9

speaker-test 1.0.24.2

Playback device is hw:1,9
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
```

---

### Post by BicyclerBoy on 2011-10-03
That means hw:1,9 is connected to hdmi receiver (eld#3.0)..

Does the TV/DFP/receiver have a volume control/mute fn  ?

The device or resource busy suggests another program running taking over the alsa device..

---

### Post by petri on 2011-10-03
Yes receiver has mute function but it is not on. Sound worked before I updated alsa to 1.0.24.

---

### Post by BicyclerBoy on 2011-10-03
That kind of implicates the ricotz ppa as the problem..
Sorry I suggested it now..

I use alsa 1.0.24 from iQuik ppa (10.04 only).

You could rewind the alsa lib & utilies back to an earlier version with the force version in synaptic..

---

### Post by petri on 2011-10-03
I rebooted and now **speaker-test -c2 -r 44100 -F S16_LE -D hw:1,9** works but there is no sound.


edit: I haven't changed back to 1.0.23 yet.

---

### Post by petri on 2011-10-03
Now I have changed back to 1.0.23 and now the speaker icon has disappeared and there is no sound with VLC or the earlier commands on this thread.

---

### Post by petri on 2011-10-03
Patience is a virtue which I have have less and less for every year. Well I had nothing to lose so I made a clean install and updated it. But I have not installed Nvidia drivers because I am not sure if it is from nvidia.com or Ubuntus drivers I should use. This time I want to do everything right or at least the way somebody who knows more than I do tells me to.

My new **wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh** looks like this: [http://www.alsa-project.org/db/?f=2556dca6978c8f1d3680485d7c381bb08c65199d](http://www.alsa-project.org/db/?f=2556dca6978c8f1d3680485d7c381bb08c65199d) 

Surely a clean install must be easiest to get HDMI sound to?

Commands earlier in this thread doesn't produce any sound.

---

### Post by petri on 2011-10-03
Installed the newest drivers from nvidia.com and with the posts #3 in this thread [http://ubuntuforums.org/showthread.php?t=1668173](http://ubuntuforums.org/showthread.php?t=1668173) I got the sound back in VLC with 5.1 but the video in VLC is too jerky so I want to get the sound to XBMC too. Anyone?

---

### Post by petri on 2011-10-05
and bump

---

### Post by petri on 2011-10-13
Believe it or not but I did it all by myself. Or almost. Now I have sound not only in VLC but Movie Player and XBMC too.
Here's how I did it.


First I removed Nouveau drivers from my fresh installation with help of [this]("http://whyareyoureadingthisurl.wordpress.com/2011/09/17/nvidia-geforce-210-on-ubuntu-11-04/") which I found from [here]("http://ubuntuforums.org/showpost.php?p=11321991&postcount=2"). The command was

```
sudo apt-get --purge remove xserver-xorg-video-nouveau

```
and reboot. Although this was a fresh install it did found something to remove. I'm no expert so I'm not sure was it necessary.


Then I istalled Nvidia drivers with 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

and reboot.

The the X didn't show up right meaning sreen resolution was still wrong but 

```
sudo nvidia-xconfig
```

in terminal fixed it. Rebooted again. Then I used

```
alsamixer
```

to unmute all Nvidias SPDIF channels and rebooted.


After that reboot I checked Sound preferences to make sure if Hardware and Output tabs had right sound card, Nvidia and 
not the internal one. Finally

```
aplay -l
```

showed Nvidia was with me and with

```
speaker-test -c **6** -r 48000 -D hw:**1,9**
```

(bold digit 6 because I have 5.1 system and bold 1,9 is my sound card) I got nice buzzing on right speakers. Now I got 5.1 sound 
on VLC after configuring it to use output **ALSA**, use **S/PDIF** and choosing my soundcard number **1,9**.


I even got right sound out of Movie player and Ubuntu sound theme working  (from Sound preferences - tab Sound Effects, not on 
logging in though (no drums) but when Desktop arrives it does make it's sound) thanks to with [this post]("http://ubuntuforums.org/showpost.php?p=10242739&postcount=1").

Open file with

```
gksu gedit /etc/asound.conf
```

Mine looks like this, card 1 and device 9 aka 1,9

```
pcm.!default {
type hw
card 1
device 9
}
```

and saved it. And reboot.

Now the original problem, XBMC sound. Thanks to [this post]("http://ubuntuforums.org/showpost.php?p=11086057&postcount=15") I finally did it: I used a **Custom device** called **hw:1,9** in both [B]Audio 
output device[/B] and **Passthrough output device** and got 5.1 sound through HDMI in XBMC working including XBMC menusounds! 

I am not so sure if so many reboots is necessary but after spending far far more than 50 hours to this I didn't want to take any risks. 
Bookmarking this post to myself for the future need.

---

### Post by petri on 2012-04-14
Note to myself: 
Custom device called **plughw:1,9** in both [B]Audio
output device[/B] and **Passthrough output device**

---

