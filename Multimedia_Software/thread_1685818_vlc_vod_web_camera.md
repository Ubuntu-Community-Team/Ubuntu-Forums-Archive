---
title: "vlc vod web camera"
date: 2011-02-11
forum: Multimedia Software
---

### Post by bulsoft on 2011-02-11
vlc 1.1.4 ubuntu 10.10 Linux bulsoft-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

```

vlc -vvv --color -I telnet --telnet-password video --telnet-host 181.4.1.16 --telnet-port 8000 --rtsp-host 0.0.0.0:5000
telnet 181.4.1.16 8000
```
     load test.conf:
```
# VLC media player VLM command batch
# http://www.videolan.org/vlc/
new test vod
setup test input "/home/bulsoft/test.avi"
setup test enabled

```

```
vlc rtsp://181.4.1.16:5000/test
``` working ok.

I`m having web camera /dev/video0 and ```
vlc v4l2:///dev/video0
``` working ok.

I want to make VoD /dev/video0.

load test.conf:
```
# VLC media player VLM command batch
# http://www.videolan.org/vlc/
new test vod
setup test input "v4l2:///dev/video0"
setup test enabled

```


Log vlc telnet console:
```
[0x8250a94] main vlm daemon debug: creating access '' path='test.conf'
[0x8252f8c] main access debug: looking for access module: 7 candidates
[0x8252f8c] vcd access debug: trying .cue file: test.cue
[0x8252f8c] vcd access debug: could not find .cue file
[0x8252f8c] filesystem access debug: opening file `test.conf'
[0x8252f8c] main access debug: using access module "filesystem"
[0x8252f8c] main access debug: TIMER module_need() : 77.055 ms - Total 77.055 ms / 1 intvls (Avg 77.055 ms)
[0x825380c] main stream debug: Using AStream*Stream
[0x825380c] main stream debug: pre buffering
[0x825380c] main stream debug: received first data after 0 ms
[0x825380c] main stream debug: pre-buffering done 184 bytes in 0s - 8984 KiB/s
[0x8252f8c] main access debug: removing module "filesystem"
[0x8255044] main vod server debug: looking for vod server module: 1 candidate
[0x8255044] vod_rtsp vod server debug: allowing up to 0 connections
[0x8255044] main vod server: creating httpd
[0x8255044] main vod server debug: net: listening to 0.0.0.0 port 5000
[0x8255044] main vod server debug: thread (rtsp vod thread) created at priority 0 (rtsp.c:311)
[0x8255044] main vod server debug: thread started
[0x8255044] main vod server debug: using vod server module "vod_rtsp"
[0x8255044] main vod server debug: TIMER module_need() : 11.312 ms - Total 11.312 ms / 1 intvls (Avg 11.312 ms)
[0x8255224] main input debug: Creating an input for 'test'
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: thread (input) created at priority 10 (input/input.c:214)
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: thread started
[0xb7200814] main stream output debug: using sout chain=`description'
[0xb7200814] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main stream output debug: stream=`description'
[0xb72009dc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main stream out debug: looking for sout stream module: 1 candidate
[0xb72009dc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main stream out debug: using sout stream module "stream_out_description"
[0xb72009dc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main stream out debug: TIMER module_need() : 7.304 ms - Total 7.304 ms / 1 intvls (Avg 7.304 ms)
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: using timeshift granularity of 50 MiB
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: using timeshift path '/tmp'
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: `v4l2:///dev/video0' gives access `v4l2' demux `' path `/dev/video0'
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: creating demux: access='v4l2' demux='' path='/dev/video0'
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux debug: looking for access_demux module: 1 candidate
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Trying direct kernel v4l2
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: opening device '/dev/video0'
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: V4L2 device: USB2.0_Camera using driver: uvcvideo (version: 0.1.0) on usb-0000:00:1d.7-3
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: the device has the capabilities: (X) Video Capture, ( ) Audio, ( ) Tuner, ( ) Radio
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: supported I/O methods are: ( ) Read/Write, (X) Streaming, ( ) Asynchronous
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: video input 0 (Camera 1) has type: External analog input *
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: device supports chroma YUY2 [YUV 4:2:2 (YUYV), YUYV]
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     device supports size 640x480
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     device supports size 320x240
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     device supports size 160x120
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     device supports size 176x144
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     device supports size 352x288
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: '/dev/video0' is a video device
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Extended control API supported by v4l2 driver
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Brightness (980900)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 255 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 125
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 125
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Contrast (980901)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 100 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 65
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 65
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Saturation (980902)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 200 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 168
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 168
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Hue (980903)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: -180 to 180 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Gamma (980910)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 40 to 100 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 50
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 50
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Power Line Frequency (980918)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     menu control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:         0: Disabled
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:         1: 50 Hz
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:         2: 60 Hz
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 2
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: White Balance Temperature (98091a)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 2800 to 6500 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 4800
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 4800
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Sharpness (98091b)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 10 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 8
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 8
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available control: Backlight Compensation (98091c)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 5 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Available private control: Zoom, Absolute (9a090d)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     integer control
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     valid values: 0 to 50 by steps of 1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     default value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     current value: 0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: using streaming i/o (mmap)
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: found default width and height of 640x480
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: will try to find optimal width and height.
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Found maximum framerate of 30.000000
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Found optimal dimensions for framerate 30.000000 of 640x480
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Driver requires at most 614400 bytes to store a complete image
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: Interlacing setting: progressive
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: supported frame intervals for YUY2, 640x480:
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/30
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/20
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/15
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/10
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/5
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug:     supported frame interval: 1/1
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: added new video es YUY2 640x480
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: selecting program id=0
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] v4l2 demux debug: User set fps=30.000000
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux debug: using access_demux module "v4l2"
[0x825910c] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux debug: TIMER module_need() : 160.837 ms - Total 160.837 ms / 1 intvls (Avg 160.837 ms)
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main decoder debug: looking for packetizer module: 21 candidates
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] rawvideo decoder warning: invalid frame rate 0/0, using 25 fps instead
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main decoder debug: using packetizer module "rawvideo"
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main decoder debug: TIMER module_need() : 1.574 ms - Total 1.574 ms / 1 intvls (Avg 1.574 ms)
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0x82598fc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main decoder debug: thread started
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: starting in sync mode
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux meta debug: looking for meta reader module: 2 candidates
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] lua demux meta debug: Trying Lua scripts in /home/bulsoft/.local/share/vlc/lua/meta/reader
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux meta debug: no meta reader module matching "any" could be loaded
[0x825f7ac] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main demux meta debug: TIMER module_need() : 1.015 ms - Total 1.015 ms / 1 intvls (Avg 1.015 ms)
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: `v4l2:///dev/video0' successfully opened
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: Buffering 0%
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: switching to async mode
[0xb7200814] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main stream output debug: adding a new sout input (sout_input:0xb7200578)
[0xb72009dc] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] stream_out_description stream out debug: Adding a stream
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: Stream buffering done (59 ms in 59 ms)
[0x8255224] [&#1055;&#1086;&#1090;&#1086;&#1082;: test] main input debug: Decoder buffering done in 0 ms

```

telnet console ```
>load test.conf
``` without returning

and ```
vlc rtsp://181.4.1.16:5000/test
``` not working.

but light diod on web camera is on, it is indicationg that web camera in capture mode

help me please to solve this ......

---

