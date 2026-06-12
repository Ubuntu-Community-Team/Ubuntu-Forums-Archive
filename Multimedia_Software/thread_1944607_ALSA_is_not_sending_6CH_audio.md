---
title: "ALSA is not sending 6CH audio"
date: 2012-03-21
forum: Multimedia Software
---

### Post by Drempel on 2012-03-21
Greetings,
 
I'm going slightly mad because of my HTPC machine with Ubuntu won't support 6CH audio. Somehow only stereo is working while 5.1 device (S/PDIF) is present. 
 
General information: [http://www.alsa-project.org/db/?f=cf8925aedbb1d9d1650c31dbb2f393a7e9d9b17e](http://www.alsa-project.org/db/?f=cf8925aedbb1d9d1650c31dbb2f393a7e9d9b17e)
Mixer list: [http://pastebin.com/hVUDbzUx](http://pastebin.com/hVUDbzUx)
Mixer settings: [http://postimage.org/image/cwmc8avch/full](http://postimage.org/image/cwmc8avch/full)
 
Some things I tried:
```
root@klondike:~# aplay -L
Home directory /home/ronald not ours.
null
Discard all samples (playback) or generate zero samples (capture)
default:CARD=PCH
HDA Intel PCH, VT1708S Analog
Default Audio Device
front:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Front speakers
surround40:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
HDA Intel PCH, HDMI 0
HDMI Audio Output
dmix:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct sample mixing device
dmix:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct sample mixing device
dmix:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct sample snooping device
hw:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Hardware device with all software conversions

``` 
```
root@klondike:~# aplay -L
Home directory /home/ronald not ours.
null
Discard all samples (playback) or generate zero samples (capture)
default:CARD=PCH
HDA Intel PCH, VT1708S Analog
Default Audio Device
front:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Front speakers
surround40:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
HDA Intel PCH, HDMI 0
HDMI Audio Output
dmix:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct sample mixing device
dmix:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct sample mixing device
dmix:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct sample snooping device
hw:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
HDA Intel PCH, VT1708S Analog
Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
HDA Intel PCH, VT1708S Digital
Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
HDA Intel PCH, HDMI 0
Hardware device with all software conversions

```
```
root@klondike:~# speaker-test -Dhw:0,1 -c6
speaker-test 1.0.24.2
Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Home directory /home/ronald not ours.
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

``` 
aplay -vv -D hw:0,1 Norrlanda.wav (2CH file/This is somehow upscaled to 5.1)
```
root@klondike:~# aplay  -vv -D hw:0,1 Norrlanda.wav
Home directory /home/ronald not ours.
Playing WAVE 'Norrlanda.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stere                                                                                                 o
Hardware PCM card 0 'HDA Intel PCH' device 1 subdevice 0
Its setup is:
stream       : PLAYBACK
access       : RW_INTERLEAVED
format       : S16_LE
subformat    : STD
channels     : 2
rate         : 44100
exact rate   : 44100 (44100/1)
msbits       : 16
buffer_size  : 22016
period_size  : 5504
period_time  : 124807
tstamp_mode  : NONE
period_step  : 1
avail_min    : 5504
period_event : 0
start_threshold  : 22016
stop_threshold   : 22016
silence_threshold: 0
silence_size : 0
boundary     : 6196953087261802496
appl_ptr     : 0
hw_ptr       : 0
#############+                                     | 25%

``` 
aplay -vv (With or Without -C2/C6) -D hw:0,1 Surround-SDL-testfiles/dolby-enlighten.wav (6CH file)
```
root@klondike:~# aplay  -vv -D hw:0,1 Surround-SDL-testfiles/dolby-enlighten.wav
Home directory /home/ronald not ours.
Playing WAVE 'Surround-SDL-testfiles/dolby-enlighten.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Channels 6
aplay: set_params:1065: Channels count non available
```
speaker-test -Dhw:0,1,0 -c2 -l1 -f75 (works but just stereo)
```
root@klondike:~# speaker-test -Dhw:0,1,0 -c2 -l1 -f75
speaker-test 1.0.24.2
Playback device is hw:0,1,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Home directory /home/ronald not ours.
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.926840
```
speaker-test -Dhw:0,1,0 -c6 -l1 -f75
```
root@klondike:~# speaker-test -Dhw:0,1,0 -c6 -l1 -f75
speaker-test 1.0.24.2
Playback device is hw:0,1,0
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Home directory /home/ronald not ours.
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```
speaker-test -Dplughw:0,1,0 -c6 -l1 -f75 (Only sound on 0 and 1)
```
root@klondike:~# speaker-test -Dplughw:0,1,0 -c6 -l1 -f75
 
speaker-test 1.0.24.2
 
Playback device is plughw:0,1,0
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Home directory /home/ronald not ours.
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 32.798390
```
And i'm kinda out of options. Does someone have an idea ?
Thanks in advance.

Kind regards,
Drempel

---

### Post by Drempel on 2012-03-21
Additional note:
 
When using a 6CH wav sample file with the plughw:0,1 device it will automaticle downgrade to 2CH.
 
```
root@klondike:~# aplay -v -Dplughw:0,1 -c6 Surround-SDL-testfiles/dolby-enlighten.wav
Home directory /home/ronald not ours.
Playing WAVE 'Surround-SDL-testfiles/dolby-enlighten.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Channels 6
Plug PCM: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 1
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 6
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24064
  period_size  : 6016
  period_time  : 125333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6016
  period_event : 0
  start_threshold  : 24064
  stop_threshold   : 24064
  silence_threshold: 0
  silence_size : 0
  boundary     : 6773413839565225984
Slave: Hardware PCM card 0 'HDA Intel PCH' device 1 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24064
  period_size  : 6016
  period_time  : 125333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6016
  period_event : 0
  start_threshold  : 24064
  stop_threshold   : 24064
  silence_threshold: 0
  silence_size : 0
  boundary     : 6773413839565225984
  appl_ptr     : 0
  hw_ptr       : 0
```

---

### Post by BicyclerBoy on 2012-03-21
S/PDIF only supports raw PCM stereo up to 96KHz 24bit, some pro gear accepts 192KHz 24bit.

Multi-channel audio over S/PDIF must be matrix encoded AC3/DTS datastream (not raw audio).
Do this by using any of:
- alsa a52 plugin
- player supports digital pass-thru' & AC3 encoder (VLC mplayer mythtv XBMC)

speaker-test & aplay can not output/test digital pass-thru'.

The alsa a52 plugin must be compiled against libavcodec-extra-unstripped packages.

Multi-channel audio is supported over HDMI as discrete PCM & AC3/DTS & HDA formats.

---

### Post by Drempel on 2012-03-22
Sir, you have made my day. All is working now. 
 
Thank you!

---

