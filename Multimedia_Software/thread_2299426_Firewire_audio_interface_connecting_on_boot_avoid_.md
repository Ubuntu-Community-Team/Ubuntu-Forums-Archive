---
title: "Firewire audio interface connecting on boot avoid jack working"
date: 2015-10-18
forum: Multimedia Software
---

### Post by zanox on 2015-10-18
Hi! as the title says, I have a TC Electronics firewire audio interface, it always worked fine with previous versions than 14.04, with jack. What I get now is that the blue led (that indicates firewire connection/audiostream) is turning on during boot and not at jack's start as usual.. I tried everything on the net before writing here so don't give to me link to official firewire configuration please. From ffado it seems the system sees no firewire interface but lspci sees texas instruments adapter. Modprobe can turn on and off that led and I can hear the "pop" of audio interface connection, but no pulseaudio jack sink shows on pulseaudio managing software... can anyone help me?

---

### Post by tgalati4 on 2015-10-19
Post the output of:

```
lsmod
```

What version of Ubuntu did it work previously?

---

### Post by zanox on 2015-10-19
12.04

giuliano@giuliano-desktop:~$ lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
rfcomm                 69632  0 
bnep                   20480  2 
bluetooth             491520  10 bnep,rfcomm
snd_hda_codec_hdmi     53248  4 
snd_hda_intel          36864  1 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
arc4                   16384  2 
gpio_ich               16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
ppdev                  20480  0 
snd                    86016  9 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     20480  0 
coretemp               16384  0 
nouveau              1368064  4 
kvm_intel             151552  0 
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
kvm                   479232  1 kvm_intel
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mxm_wmi                16384  1 nouveau
mac80211              708608  1 ath9k
wmi                    20480  2 mxm_wmi,nouveau
ttm                    94208  1 nouveau
serio_raw              16384  0 
drm_kms_helper        126976  1 nouveau
i7core_edac            24576  0 
edac_core              53248  2 i7core_edac
lpc_ich                24576  0 
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
drm                   344064  7 ttm,drm_kms_helper,nouveau
mei_me                 20480  0 
mei                    90112  1 mei_me
i2c_algo_bit           16384  1 nouveau
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
8250_fintek            16384  0 
parport_pc             32768  0 
parport                45056  3 lp,ppdev,parport_pc
video                  20480  1 nouveau
mac_hid                16384  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
psmouse               114688  0 
firewire_ohci          40960  0 
ahci                   36864  4 
firewire_core          69632  1 firewire_ohci
libahci                32768  1 ahci
crc_itu_t              16384  1 firewire_core
pata_acpi              16384  0

thank you ;)

---

### Post by tgalati4 on 2015-10-19
Output of:

```
aplay -l
```

Boot a 12.04 USB stick and post:

```
lsmod
```

---

### Post by zanox on 2015-10-20
```
giuliano@giuliano-desktop:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: Konnekt8 [Konnekt8], dispositivo 0: DICE [Konnekt8]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

12.04 lsmod arriving...

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  4 
ath9k                 132390  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_hdmi,snd_hda_intel
mac80211              506816  1 ath9k
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
parport_pc             32866  0 
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
shpchp                 37277  0 
lp                     17799  0 
snd_timer              29990  2 snd_pcm,snd_seq
cfg80211              205544  3 ath9k,mac80211,ath
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
bnep                   18281  2 
i7core_edac            28102  0 
snd                    78855  13 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
edac_core              53746  3 i7core_edac
mei                    41616  0 
rfcomm                 47604  0 
dm_multipath           23230  0 
soundcore              15091  1 snd
bluetooth             180104  10 bnep,rfcomm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
squashfs               36799  1 
overlayfs              28305  1 
nls_utf8               12557  1 
isofs                  40257  1 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 652957  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
nouveau               774641  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau

ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by tgalati4 on 2015-10-20
So it looks like the firewire sound device is being detected and added at boot by 14.04.  Your *aplay* list confirms this.

So now we need to look through the change list for the following libraries between 12.04 and 14.04:

[qu9ote]tgalati4@Mint17 ~ $ apt-cache search ffado
libffado-dev - FFADO API - development files
libffado2 - FFADO API
ffado-dbus-server - FFADO D-Bus server
ffado-mixer-qt4 - FFADO D-Bus mixer applets (QT4)
ffado-tools - FFADO debugging and firmware tools
jackd1-firewire - JACK Audio Connection Kit (FFADO backend)
jackd2-firewire - JACK Audio Connection Kit (FFADO and FreeBoB backends)
multimedia-firewire - Packages for your firewire audiocard / interface
[/quote]

I see two issues here.  Automatic detection of your firewire hardware.  How was it detected in 12.04?  Did you manually *modprobe* the driver?  The second issue is the change in sound frameworks from 12.04 to 14.04.  Could be changes in pulseaudio, jack, or both.

Try blacklisting the firewire module in 14.04 and see if it behaves the way it did in 12.04.

---

### Post by zanox on 2015-10-20
giuliano@giuliano-desktop:~$ apt-cache search ffado
libffado-dev - API FFADO - file di sviluppo
libffado2 - API FFADO
multimedia-firewire - Packages for your firewire audiocard / interface
ffado-dbus-server - server D-Bus FFADO
ffado-mixer-qt4 - applet e mixer per FFAD0 D-Bus (QT4)
ffado-tools - FFADO debugging and firmware tools
jackd1-firewire - JACK Audio Connection Kit (FFADO backend)
jackd2-firewire - JACK Audio Connection Kit (FFADO and FreeBoB backends)

in 12.04 after booting the soundcard was connected only if I started jack (qjackctl), otherwise it wasn't recognised (no pulseaudio sink, the sink showed up after jack start)
blacklisting results in no connection at boot, but I cannot connect it through jack, I'll paste some errors if it helps

pulseaudio volume control doesn't work, through vlc or youtube sometimes works, ffado mixer let me set the sample frequency, I don't know what happened.. O.o
[IMG]https://dl.dropboxusercontent.com/u/14269970/Schermata%20del%202015-10-20%2019%3A04%3A15.png[/IMG]

I'll keep trying different things and I'll let you know...

giuliano@giuliano-desktop:~$ sudo killall -KILL ffado-mixer
ffado-mixer: nessun processo trovato
giuliano@giuliano-desktop:~$ ffado-mixer
ffado-mixer instance is already running

I installed jack sink and it seems to work.. I'll update you

There was audio but after a while it went away.. audio volume cannot connect to pulseaudio.. It seems there's something mismatching

---

### Post by tgalati4 on 2015-10-21
I have seen this type of problem before.  Something to do with the default decoding frequency of 44.1 kHz vs 48 kHz.  When there is a mismatch the device doesn't show up.  Try hardcoding everything to 48 kHz.

Some tips:

[https://bbs.archlinux.org/viewtopic.php?id=75895](https://bbs.archlinux.org/viewtopic.php?id=75895)

[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#High_quality_resampling](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#High_quality_resampling)

This issue might explain why your ffadao mixer worked for a while.  It was performing the 44.1 to 48 kHz conversion until some other process interrupted it.  

jack needs a low-latency kernel to run correctly.  Perhaps you were running Ubuntu Studio 12.04 in the past and now you are not?

---

### Post by zanox on 2015-10-21
no, it was the normal ubuntu release.. maybe should I try reinstalling jack in realtime kernel?

---

### Post by tgalati4 on 2015-10-22
Yes, it's possble that there is a problem with jack.  What are your typical xruns?  Run a Live Session of Ubuntu Studio and see if your hardware works.

---

### Post by zanox on 2015-10-22
I don't have the files quoted in those articles.. What do you mean with my typical xruns?

---

### Post by tgalati4 on 2015-10-22
When you run *jack*, you get xruns, which are delays due to lack of processing power.  When xruns get too high, you get interrupts, glitches, resets, etc.

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

### Post by zanox on 2015-10-24
```
giuliano@giuliano-desktop:~$ jackdbus auto
no message buffer overruns
no message buffer overruns
no message buffer overruns

 Sat Oct 24 13:32:02 2015: Starting jack server...
 Sat Oct 24 13:32:02 2015: JACK server starting in non-realtime mode
 Sat Oct 24 13:32:02 2015: ERROR: firewire ERR: Could not prepare streaming device!
 Sat Oct 24 13:32:02 2015: ERROR: Cannot attach audio driver
 Sat Oct 24 13:32:02 2015: ERROR: JackServer::Open failed with -1
 Sat Oct 24 13:32:02 2015: ERROR: Failed to open server
 Sat Oct 24 13:32:02 2015: ERROR: Segmentation Fault!
 Sat Oct 24 13:32:02 2015: ERROR: info.si_signo = 11
 Sat Oct 24 13:32:02 2015: ERROR: Segmentation Fault!
 Sat Oct 24 13:32:02 2015: ERROR: info.si_signo = 11
 Sat Oct 24 13:32:02 2015: ERROR: info.si_errno = 0
 Sat Oct 24 13:32:02 2015: ERROR: info.si_errno = 0
 Sat Oct 24 13:32:02 2015: ERROR: info.si_code  = 1 (SEGV_MAPERR)
 Sat Oct 24 13:32:02 2015: ERROR: info.si_code  = 1 (SEGV_MAPERR)
 Sat Oct 24 13:32:02 2015: ERROR: info.si_addr  = 0x7f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: info.si_addr  = 0x7f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: reg[00]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[01]       = 0x00007f44f00008c0
 Sat Oct 24 13:32:02 2015: ERROR: reg[00]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[01]       = 0x00007f44ec0008c0
 Sat Oct 24 13:32:02 2015: ERROR: reg[02]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[03]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[02]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[03]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[04]       = 0x00007f45027fbea0
 Sat Oct 24 13:32:02 2015: ERROR: reg[04]       = 0x00007f4501ffaea0
 Sat Oct 24 13:32:02 2015: ERROR: reg[05]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[05]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[06]       = 0x00000000021bd200
 Sat Oct 24 13:32:02 2015: ERROR: reg[07]       = 0x00007f4501ffb700
 Sat Oct 24 13:32:02 2015: ERROR: reg[08]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[06]       = 0x00000000021bd000
 Sat Oct 24 13:32:02 2015: ERROR: reg[07]       = 0x00007f45027fc700
 Sat Oct 24 13:32:02 2015: ERROR: reg[09]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[10]       = 0x00007f451d45b3c0
 Sat Oct 24 13:32:02 2015: ERROR: reg[08]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[09]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[10]       = 0x00007f451d45b3c0
 Sat Oct 24 13:32:02 2015: ERROR: reg[11]       = 0x00000000021bd200
 Sat Oct 24 13:32:02 2015: ERROR: reg[12]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[11]       = 0x00000000021bd000
 Sat Oct 24 13:32:02 2015: ERROR: reg[12]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[13]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[14]       = 0x00007f451ce53f3d
 Sat Oct 24 13:32:02 2015: ERROR: reg[13]       = 0x0000000000000000
 Sat Oct 24 13:32:02 2015: ERROR: reg[14]       = 0x00007f451ce53f3d
 Sat Oct 24 13:32:02 2015: ERROR: reg[15]       = 0x00007f45027fbe00
 Sat Oct 24 13:32:02 2015: ERROR: reg[16]       = 0x00007f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: reg[17]       = 0x0000000000010202
 Sat Oct 24 13:32:02 2015: ERROR: reg[18]       = 0x0000000000000033
 Sat Oct 24 13:32:02 2015: ERROR: reg[15]       = 0x00007f4501ffae00
 Sat Oct 24 13:32:02 2015: ERROR: reg[16]       = 0x00007f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: reg[17]       = 0x0000000000010202
 Sat Oct 24 13:32:02 2015: ERROR: reg[19]       = 0x0000000000000014
 Sat Oct 24 13:32:02 2015: ERROR: reg[20]       = 0x000000000000000e
 Sat Oct 24 13:32:02 2015: ERROR: reg[21]       = 0x0000000000005a07
 Sat Oct 24 13:32:02 2015: ERROR: reg[22]       = 0x00007f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: Stack trace:
 Sat Oct 24 13:32:02 2015: ERROR: End of stack trace
 Sat Oct 24 13:32:02 2015: ERROR: reg[18]       = 0x0000000000000033
 Sat Oct 24 13:32:02 2015: ERROR: reg[19]       = 0x0000000000000014
 Sat Oct 24 13:32:02 2015: ERROR: reg[20]       = 0x000000000000000e
 Sat Oct 24 13:32:02 2015: ERROR: reg[21]       = 0x0000000000005a07
 Sat Oct 24 13:32:02 2015: ERROR: reg[22]       = 0x00007f45195452ea
 Sat Oct 24 13:32:02 2015: ERROR: Stack trace:
 Sat Oct 24 13:32:02 2015: ERROR: End of stack trace
 13:32:04.236 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni.
 Cannot connect to server socket err = File o directory non esistente
 Cannot connect to server request channel
 jack server is not running or cannot be started
```

do you think maybe IRQ priorities may help?

---

### Post by tgalati4 on 2015-10-24
Perhaps a permissions problem.  Open them up:

```
sudo chmod 777 /dev/fddao
```

Your device will be named differently.

Reboot.

---

### Post by zanox on 2015-10-25
After your suggestion I opened ffado-mixer and pavucontrol
[IMG]https://dl.dropboxusercontent.com/u/14269970/1.png[/IMG]

by gnome-system-monitor I can see 4 pulseaudio processes starting and termining continuosly..

giuliano@giuliano-desktop:~$ start-pulseaudio-x11
Connessione non riuscita: Connessione rifiutata
pa_context_connect() non riuscita: Connessione rifiutata

(meaning "refused connection")

Ok, I tried something hard: purging pulseaudio and jack.. Actually audio  is working but I cannot hear from youtube because I have also a HDMI  port that ubuntu sees as audio device (that I need too), I tried  alsamixer for selecting default audio output but:
giuliano@giuliano-desktop:~$ alsamixer
impossibile aprire il mixer: File o directory non esistente

"no such file or directory "

I search for that error without result

---

### Post by tgalati4 on 2015-10-25
Did you delete ALSA as well?

> tgalati4@Mint17 ~ $ which alsamixer
/usr/bin/alsamixer


---

### Post by zanox on 2015-10-25
giuliano@giuliano-desktop:~$ which alsamixer
/usr/bin/alsamixer

audio works but I have no way to select devices :(

---

### Post by tgalati4 on 2015-10-25
Reinstall *pulseaudio*.

---

### Post by zanox on 2015-10-26
I did, but for selecting the device in pavucontrol I need jack sink and that's the original configuration that works and doesn't work, it's a a dog chasing its own tail.. Very weird anyway

It seems there's something missing in the chain

ok I reinstalled pulseaudio but alsamixer isn't working yet

Installed only ffado-dbus and alsamixer is working but even selecting audio card by F6 I cannot hear youtube audio (the only missing, other software works)

---

### Post by tgalati4 on 2015-10-26
Try different browsers for youtube audio.  Each browser has different settings to get sound to work.  For Google Chrome:  [https://www.youtube.com/watch?v=GNJDO4Qppv4](https://www.youtube.com/watch?v=GNJDO4Qppv4)

---

### Post by zanox on 2015-10-26
How can vlc play sound through pulseaudio since I uninstalled it and also alsa-base ffado jackd?

Remains libasound

I'm thinking of trying 15.10 or coming back to 12.04

---

### Post by tgalati4 on 2015-10-26
Simple, *vlc* will use ALSA if *pulseaudio* is not running.  It is a simple fallback.  Spend some time going through [basic sound troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting").

---

### Post by zanox on 2015-10-27
Interesting, I'll take a look asap! thank you

---

