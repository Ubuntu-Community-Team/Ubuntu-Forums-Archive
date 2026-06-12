---
title: "alsa   cannot open audio device hw:1,0  [Input/output error]  question"
date: 2020-05-06
forum: Multimedia Software
---

### Post by shantiq on 2020-05-06
I found out last year an easy way to [convert VHS]("https://ubuntuforums.org/showthread.php?t=2416541") to an mkv file with flac sound
but now I am getting an alsa problem everytime and have no idea why


Nothing I can see has changed


```
cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf220000 irq 130
 1 [Alpha          ]: USB-Audio - Lexicon Alpha
                      Lexicon Lexicon Alpha at usb-0000:00:14.0-6, full speed
 2 [CAMERA         ]: USB-Audio - USB2.0 PC CAMERA
                      ARKMICRO USB2.0 PC CAMERA at usb-0000:00:14.0-3, high speed

```









```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f alsa -thread_queue_size 1024 -i hw:1,0  -c:v libx264  -s 720x576 -b:v 2400k -vf eq=saturation=0.5 -r 25 -aspect 4:3 -c:a flac -channels 2 -ar 48000   outfile.mkv
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
[video4linux2,v4l2 @ 0x5561a6784bc0] This device does not support any standard
[mjpeg @ 0x5561a6785f60] EOI missing, emulating
Input #0, video4linux2,v4l2, from '/dev/video0':
  Duration: N/A, start: 3412.361590, bitrate: N/A
    Stream #0:0: Video: mjpeg, yuvj422p(pc, bt470bg/unknown/unknown), 640x480, 30 fps, 30 tbr, 1000k tbn, 1000k tbc
[COLOR=#800000][alsa @ 0x5561a678ba00] cannot open audio device hw:1,0 (Device or resource busy)    ***BUT IT IS NOT BUSY WITH any process i can see***
hw:1,0: Input/output error[/COLOR]



```

---

### Post by Yellow Pasque on 2020-05-08
> BUT IT IS NOT BUSY WITH any process i can see
So you looked at?:
```
lsof /dev/snd/*
```

Have you considered trying '-f pulse' instead of '-f alsa'?
[https://ffmpeg.org/ffmpeg-devices.html#pulse](https://ffmpeg.org/ffmpeg-devices.html#pulse)

---

### Post by shantiq on 2020-05-09
thanx Pasque 

&#10122; had looked at ```
[COLOR=#000000][FONT=&amp]lsof /dev/snd/*[/FONT][/COLOR]
```   which i take it shows processes still alive? and then to kill them with ```
sudo kill -15 pid
``` or ```
sudo kill -9 pid
``` I suppose?

[COLOR=#000000]&#10123; As regards pulse yes that sounds good but requires a reconfig
[/COLOR][COLOR=#E6E6E6][FONT=&amp]
[/FONT][/COLOR]```
To enable this output device you need to configure FFmpeg with --enable-libpulse.
```

There must a way to reset alsa so it does not glitch like this  maybe [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")  altho a tad loath to try those routes as many say they often worsen matters

**PS =====**

i used same command on an older PC I have got with Slackware installed and it is working with same ffmpeg command and fine there altho once it also gave me the ```
[COLOR=#800000][FONT=&amp](Device or resource busy)[/FONT][/COLOR]
``` runaround


Sound is often a puzzle on Linux :]



Anyway many thanx you have provided food for thought here ...   will play further and see

---

### Post by Yellow Pasque on 2020-05-09
> **shantiq said:**
> To enable this output device you need to configure FFmpeg with --enable-libpulse.

You don't have to worry about that. ffmpeg is already built with  --enable-libpulse

> There must a way to reset alsa so it does not glitch

Well, if something is really using the device, then it is not a "glitch". And no, I wouldn't try random commands to fix it.
As for lsof, you'll probably find that pulseaudio itself is responsible for "grabbing" the hw:x,y device. You don't want to kill that. Are you sure that all applications using/playing audio are stopped before you attempt to use ffmpeg?

---

### Post by shantiq on 2020-05-09
OK

so  ```
[COLOR=#000000]*--enable-libpulse*[/COLOR]
```   does not appear on my ffmpeg installed on my system or do you mean it is there but not spelt out


```
--enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree


```


And as re:   all audio turned off YES emphatically

---

### Post by Yellow Pasque on 2020-05-09
Look at your ffmpeg configuration line:
> configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus **--enable-libpulse** --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared

---

### Post by shantiq on 2020-05-09
hi again if i choose pulse it does  [as you can see in config not installed here]


```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f [COLOR=#a52a2a]**pulse**[/COLOR] -thread_queue_size 1024 -i hw:1,0  -c:v libx264  -s 720x576 -b:v 2400k -vf eq=saturation=0.5 -r 25 -aspect 4:3 -c:a flac -channels 2 -ar 48000  ~/Desktop/floyd.mkvffmpeg version N-91586-g90dc584 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 18.102 / 56. 18.102
  libavcodec     58. 22.101 / 58. 22.101
  libavformat    58. 17.101 / 58. 17.101
  libavdevice    58.  4.101 / 58.  4.101
  libavfilter     7. 26.100 /  7. 26.100
  libswscale      5.  2.100 /  5.  2.100
  libswresample   3.  2.100 /  3.  2.100
  libpostproc    55.  2.100 / 55.  2.100
[video4linux2,v4l2 @ 0x55eefd7f5f00] This device does not support any standard
[mjpeg @ 0x55eefd7f7500] EOI missing, emulating
Input #0, video4linux2,v4l2, from '/dev/video0':
  Duration: N/A, start: 15065.860398, bitrate: N/A
    Stream #0:0: Video: mjpeg, yuvj422p(pc, bt470bg/unknown/unknown), 640x480, 30 fps, 30 tbr, 1000k tbn, 1000k tbc
[COLOR=#800000]**Unknown input format: 'pulse'**[/COLOR]
```


with

```
cat /proc/asound/cards 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf220000 irq 130
 1 [Alpha          ]: USB-Audio - Lexicon Alpha
                      Lexicon Lexicon Alpha at usb-0000:00:14.0-6, full speed
 2 [CAMERA         ]: USB-Audio - USB2.0 PC CAMERA
                      ARKMICRO USB2.0 PC CAMERA at usb-0000:00:14.0-3, high speed



```


and

```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Alpha [Lexicon Alpha], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



```

---

### Post by Yellow Pasque on 2020-05-09
> configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include

You seem to have two copies of ffmpeg installed, and your local/home copy looks like it's missing libpulse (and a bunch of other dependencies) for some reason. I honestly don't know what you're doing there.
Also, if you're going to use '-f pulse', you need to use a pulse device (not hw:x,y).
[https://ffmpeg.org/ffmpeg-devices.html#pulse](https://ffmpeg.org/ffmpeg-devices.html#pulse)

---

### Post by shantiq on 2020-05-09
ok so pulse not an option as no wish to reinstall ffmpeg if avoidable
was really more wanting to get alsa to "behave" :) here as it thinks there is a process going on
so my question really is how to prod deeper into alsa so that it reveals where it thinks it is "busy"
Anyone knows of ways of doing this ?   I have read around a lot and far come up empty as to a way to "see"   what it is doing

Thank you so much for your help thus far

I know the command is fine as is as it used to work and works on my Slackware oldie so the kink is with alsa here

---

### Post by Yellow Pasque on 2020-05-09
> so my question really is how to prod deeper into alsa so that it reveals where it thinks it is "busy"
Again,
```
lsof /dev/snd/*
```
Please give the output!

> ok so pulse not an option as no wish to reinstall ffmpeg if avoidable
There is no need to reinstall ffmpeg to use pulse. However, you do need to make sure you're using the system copy of ffmpeg (like you did in your initial post) and not the copy of ffmpeg you have in your /home.

---

### Post by shantiq on 2020-05-09
hi again


```
lsof /dev/snd/*COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
alsamixer 12204 shan    3u   CHR  116,2      0t0  513 /dev/snd/controlC0
pulseaudi 13335 shan  mem    CHR 116,15           571 /dev/snd/pcmC1D0c
pulseaudi 13335 shan  mem    CHR 116,14           570 /dev/snd/pcmC1D0p
pulseaudi 13335 shan   22u   CHR 116,13      0t0  400 /dev/snd/controlC1
pulseaudi 13335 shan   28u   CHR 116,13      0t0  400 /dev/snd/controlC1
pulseaudi 13335 shan   29u   CHR 116,15      0t0  571 /dev/snd/pcmC1D0c
pulseaudi 13335 shan   30u   CHR  116,2      0t0  513 /dev/snd/controlC0
pulseaudi 13335 shan   35u   CHR 116,14      0t0  570 /dev/snd/pcmC1D0p



```


i have 2 indeed ffmpegs

```
/home/shan/bin/ffmpeg

```   which i now remember i had installed so to have --enable-libfdk-aac  and --enable-libx265 whenever that was

AND

haaaaaaaaaaaaaaaa   i see and i have   and this one indeed has --enable-libpulse   so what is the syntax for that   i have no experience of doing pulse instead of alsa here  and THAT SHOULD swing it bypass alsa altogether here  getting closer

```
***/usr/bin/ffmpeg***
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...



```

---

### Post by Yellow Pasque on 2020-05-09
Well, you already got this part, where you use:
```
-f pulse
```

Now, you need to replace '-i hw:1,0' with '-i <name of the pulse device>'
You can find <name of the pulse device> with:
```
pactl list sources
```
If you're unsure, give the output of that command.

---

### Post by shantiq on 2020-05-09
ok YP

```
pactl list sourcesSource #0
    State: IDLE
    Name: alsa_output.usb-Lexicon_Lexicon_Alpha-00.analog-stereo.monitor
    Description: Monitor of Lexicon Alpha Analogue Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 48000Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: alsa_output.usb-Lexicon_Lexicon_Alpha-00.analog-stereo
    Latency: 0 usec, configured 1837500 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Lexicon Alpha Analogue Stereo"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "Lexicon Alpha"
        alsa.long_card_name = "Lexicon Lexicon Alpha at usb-0000:00:14.0-6, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:6:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/sound/card1"
        udev.id = "usb-Lexicon_Lexicon_Alpha-00"
        device.bus = "usb"
        device.vendor.id = "1210"
        device.vendor.name = "DigiTech"
        device.product.id = "000a"
        device.product.name = "Lexicon Alpha"
        device.serial = "Lexicon_Lexicon_Alpha"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    Formats:
        pcm


Source #1
    State: IDLE
    Name: alsa_input.usb-Lexicon_Lexicon_Alpha-00.analog-stereo
    Description: Lexicon Alpha Analogue Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: n/a
    Latency: 222 usec, configured 2000000 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "Lexicon Alpha"
        alsa.long_card_name = "Lexicon Lexicon Alpha at usb-0000:00:14.0-6, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:6:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/sound/card1"
        udev.id = "usb-Lexicon_Lexicon_Alpha-00"
        device.bus = "usb"
        device.vendor.id = "1210"
        device.vendor.name = "DigiTech"
        device.product.id = "000a"
        device.product.name = "Lexicon Alpha"
        device.serial = "Lexicon_Lexicon_Alpha"
        device.string = "front:1"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analogue Stereo"
        device.description = "Lexicon Alpha Analogue Stereo"
        alsa.mixer_name = "USB Mixer"
        alsa.components = "USB1210:000a"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    Ports:
        analog-input: Analogue Input (priority: 10000)
    Active Port: analog-input
    Formats:
        pcm



```



I tried this with no luck probably entered the wrong bit  then thought would pick the word "default" as i have disabled all other cards and direct hit yippee   THANK U so much   it really bugged me as i love digitizing those old VHS ...   it is a sideway solution and that is fine so far as we get there
Thanx for your patience too


Marked as solved


```
shan@shan-Aspire-XC-780:~$[COLOR=#800000]*** /usr/bin/ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f pulse  -i  default -c:v libx264  -s 720x576 -b:v 2400k -vf eq=saturation=0.5 -r 25 -aspect 4:3 -c:a flac -channels 2 -ar 48000  ~/Desktop/outfile.mkv***[/COLOR]
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
[video4linux2,v4l2 @ 0x55a9c8648b80] This device does not support any standard
[mjpeg @ 0x55a9c8649fc0] EOI missing, emulating
Input #0, video4linux2,v4l2, from '/dev/video0':
  Duration: N/A, start: 32496.580474, bitrate: N/A
    Stream #0:0: Video: mjpeg, yuvj422p(pc, bt470bg/unknown/unknown), 640x480, 30 fps, 30 tbr, 1000k tbn, 1000k tbc
Guessed Channel Layout for Input Stream #1.0 : stereo
Input #1, pulse, from 'default':
  Duration: N/A, start: 1589039002.806428, bitrate: 1536 kb/s
    Stream #1:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg (native) -> h264 (libx264))
  Stream #1:0 -> #0:1 (pcm_s16le (native) -> flac (native))
Press [q] to stop, [?] for help
[swscaler @ 0x55a9c8694d20] deprecated pixel format used, make sure you did set range correctly
[libx264 @ 0x55a9c8669500] using SAR=16/15
[libx264 @ 0x55a9c8669500] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 BMI2 AVX2
[libx264 @ 0x55a9c8669500] profile High 4:2:2, level 3.0, 4:2:2 8-bit
[libx264 @ 0x55a9c8669500] 264 - core 152 r2854 e9a5903 - H.264/MPEG-4 AVC codec - Copyleft 2003-2017 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=abr mbtree=1 bitrate=2400 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to '/home/shan/Desktop/outfile.mkv':
  Metadata:
    encoder         : Lavf57.83.100
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv422p(progressive), 720x576 [SAR 16:15 DAR 4:3], q=-1--1, 2400 kb/s, 25 fps, 1k tbn, 25 tbc
    Metadata:
      encoder         : Lavc57.107.100 libx264
    Side data:
      cpb: bitrate max/min/avg: 0/0/2400000 buffer size: 0 vbv_delay: -1
    Stream #0:1: Audio: flac ([172][241][0][0] / 0xF1AC), 48000 Hz, stereo, s16, 128 kb/s
    Metadata:
      encoder         : Lavc57.107.100 flac
frame=   43 fps=0.0 q=0.0 size=       0kB time=00:00:00.28 bitrate=   0.0kbits/sframe=   55 fps= 54 q=21.0 size=       1kB time=00:00:00.67 bitrate=  11.8kbits/frame=   68 fps= 45 q=20.0 size=       1kB time=00:00:01.24 bitrate=   6.4kbits/frame=   81 fps= 40 q=22.0 size=       1kB time=00:00:01.82 bitrate=   4.3kbits/frame=   93 fps= 37 q=22.0 size=       1kB time=00:00:02.49 bitrate=   3.2kbits/frame=  106 fps= 35 q=22.0 size=       1kB time=00:00:02.88 bitrate=   2.8kbits/frame=  119 fps= 34 q=23.0 size=       1kB time=00:00:03.55 bitrate=   2.2kbits/frame=  131 fps= 32 q=23.0 size=       1kB time=00:00:03.93 bitrate=   2.0kbits/frame=  144 fps= 32 q=23.0 size=       1kB time=00:00:04.32 bitrate=   1.8kbits/frame=  155 fps= 31 q=23.0 size=       1kB time=00:00:04.70 bitrate=   1.7kbits/frame=  168 fps= 30 q=23.0 size=    1895kB time=00:00:05.37 bitrate=2887.3kbits/frame=  181 fps= 30 q=23.0 size=    1895kB time=00:00:05.85 bitrate=2650.6kbits/frame=  193 fps= 29 q=23.0 size=    1895kB time=00:00:06.52 bitrate=2377.4kbits/frame=  206 fps= 29 q=23.0 size=    1895kB time=00:00:06.91 bitrate=2245.3kbits/frame=  218 fps= 29 frame= 3356 fps= 25 q=-1.0 Lsize=   50973kB time=00:02:14.88 bitrate=3095.8kbits/s speed=1.01x    95kB time=00:00:07.96 bitrate=1948.3kbits/s speed=0.987x    
video:40017kB audio:10920kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.068923%
[libx264 @ 0x55a9c8669500] frame I:18    Avg QP:17.13  size: 35244
[libx264 @ 0x55a9c8669500] frame P:845   Avg QP:21.25  size: 18754
[libx264 @ 0x55a9c8669500] frame B:2493  Avg QP:23.38  size:  9826
[libx264 @ 0x55a9c8669500] consecutive B-frames:  0.9%  0.1%  0.2% 98.8%
[libx264 @ 0x55a9c8669500] mb I  I16..4: 13.7% 66.0% 20.2%
[libx264 @ 0x55a9c8669500] mb P  I16..4:  5.0% 13.2%  1.4%  P16..4: 39.5% 24.8% 11.6%  0.0%  0.0%    skip: 4.6%
[libx264 @ 0x55a9c8669500] mb B  I16..4:  1.4%  2.3%  0.1%  B16..8: 41.3% 15.4%  3.3%  direct:17.0%  skip:19.1%  L0:47.4% L1:39.4% BI:13.2%
[libx264 @ 0x55a9c8669500] final ratefactor: 20.43
[libx264 @ 0x55a9c8669500] 8x8 transform intra:64.9% inter:64.0%
[libx264 @ 0x55a9c8669500] coded y,uvDC,uvAC intra: 44.4% 60.3% 22.7% inter: 40.1% 56.6% 3.0%
[libx264 @ 0x55a9c8669500] i16 v,h,dc,p: 39% 41% 12%  8%
[libx264 @ 0x55a9c8669500] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 15% 30% 34%  3%  3%  2%  4%  3%  6%
[libx264 @ 0x55a9c8669500] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 35% 16%  4%  5%  4%  5%  4%  5%
[libx264 @ 0x55a9c8669500] i8c dc,h,v,p: 53% 28% 14%  4%
[libx264 @ 0x55a9c8669500] Weighted P-Frames: Y:14.1% UV:6.7%
[libx264 @ 0x55a9c8669500] ref P L0: 36.4%  9.9% 29.8% 21.1%  2.8%
[libx264 @ 0x55a9c8669500] ref B L0: 66.4% 25.1%  8.5%
[libx264 @ 0x55a9c8669500] ref B L1: 86.1% 13.9%
[libx264 @ 0x55a9c8669500] kb/s:2428.25




```

---

### Post by Yellow Pasque on 2020-05-09
I don't know for sure, but I would try:
```
-f pulse -i alsa_input.usb-Lexicon_Lexicon_Alpha-00.analog-stereo
```
Also, this might help you see available source names:
```
ffmpeg -sources pulse
```

---

### Post by shantiq on 2020-05-09
All sorted Yellow Pasque and marked as solved

Picked

```
-f pulse -i default

```
As i block all other cards
Will try

```
-f pulse -i alsa_input.usb-Lexicon_Lexicon_Alpha-00.analog-stereo

```
Also see if it flies


Much appreciated
You&#8217;re a gent


Shan


EDIT:    did try  ```
-f pulse -i alsa_input.usb-Lexicon_Lexicon_Alpha-00.analog-stereo

```    and  YES spot on

```
ffmpeg -sources pulse
```   BEST way to find correct name


+++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++


TO SUMMARIZE
--------------------


easiest path to rip VHS with ffmpeg using pulse [maybe easier than with alsa]


======================
&#10122;   find name of your device

```
ffmpeg -sources pulse
```


you will find the answer at the bottom under:
Auto-detected sources for pulse:NAMEOFYOURDEVICE




====
&#10123;  The command

```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f pulse -i NAMEOFYOURDEVICE -c:v libx264  -s 720x576 -b:v 2400k  -aspect 4:3 -c:a flac -channels 2 -ar 48000  ~/VIDEOS/YourVHS.mkv

```

====


for the hardware/leads required [typically under $10/£8/&#8364;10] if you have the VHS player   and also fine tunings and post-editing     [see info here]("https://ubuntuforums.org/showthread.php?t=2416541") 

-

---

### Post by Yellow Pasque on 2020-05-09
LOL, I knew I should have suggested trying '-i default'
I thought explicitly specifying device name would be more bulletproof though. (I was overthinking again.)

I'm glad it's working. Enjoy.

---

