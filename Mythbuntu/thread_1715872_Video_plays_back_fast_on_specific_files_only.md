---
title: "Video plays back fast on specific files only"
date: 2011-03-27
forum: Mythbuntu
---

### Post by arriflex on 2011-03-27
The problem is that recordings from a specific channel that are encoded with 256k bitrate do not play back properly. They play at two to three times normal speed, very jittery and stuttering, with no audio sync. In other words, playback of these files (recorded off my local CBS affiliate) is fast, like they're being fast forwarded through. 

The problem I had happens both while using hdmi audio and the regular analog output. I suspect the problem is audio related though, because it occurs only while attempting to playback files that are encoded as the folloiwng:
```
scan: audio 0x1: AC-3, rate=48000Hz, bitrate=256000 English (AC3) (2.0 ch)
```

Unfortunately, Alsa reports only supporting up to sample rate 192000. 

I have tried practically every Nvidia driver, and am currently using 270.29 with every possible v-sync box checked in every dialog I can find. I have tried playback using all three vdpau profiles as well as having tried expanding the buffer.

Attached is an excerpted table of mythfrontend logs during two video files playing back, the first column is a bad file, the following plays fine. I shifted the row positions to maintain approximate parity.

I'm lost. This worked fine before 10.10, hasn't worked since. Where do I start?

Here's the bad file:

```
#CBS Criminal Minds, plays back at around triple speed, no sync audio

TV: Attempting to change from None to WatchingPreRecorded
AFD: Opened codec 0xb1cb8f10, id(MPEG2VIDEO) type(Video)
AFD: codec AC3 has 2 channels
AFD: Opened codec 0xad77fc20, id(AC3) type(Audio)
Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
Opening ALSA audio device 'default'.
Mixer unable to find control Master 1
mixer unable to find control Master 1
VDPAU: Created 2 output surfaces.
VDPAU: Created VDPAU render device 1266x705
NVP(6): Forcing decode extra audio option on (Video method requires it).
OSD Theme Dimensions W: 1280 H: 720
Realtime priority would require SUID as root.
TV: Changing from None to WatchingPreRecorded
OpenGLVideoSync()
mythbackend version: branches/release-0-23-fixes [26437] www.mythtv.org
Using runtime prefix = /usr
Using configuration directory = /home/edgar/.mythtv
Empty LocalHostName.
Using localhost value of mythtv
Testing network connectivity to '192.168.0.8'
New DB connection, total: 1
Connected to database 'mythconverg' at host: 192.168.0.8
Closing DB connection named 'DBManager0'
Connected to database 'mythconverg' at host: 192.168.0.8
Video timing method: SGI OpenGL
Current MythTV Schema Version (DBSchemaVer): 1254
ProgramInfo(): Updated pathname '':'' -> '2291_20110327000500.mpg'
AFD: Opened codec 0xb4454000, id(MPEG2VIDEO) type(Video)
AFD: codec AC3 has 2 channels
AFD: Opened codec 0xb4453610, id(AC3) type(Audio)
VDPAU: Added 2 output surfaces (total 4, max 4)
Preview: Grabbed preview '/var/lib/mythtv/recordings/2291_20110327000500.mpg' 1920x1088@64s
~MythContext waiting for threads to exit.
```

And the following is a good one:
```
#NBC nightly news, HD, playback fine

TV: Attempting to change from None to WatchingPreRecorded
[mpeg2video @ 0x3cdd120]mpeg_decode_postinit() failure
[mpeg2video @ 0x3cdd120]mpeg_decode_postinit() failure
AFD: Opened codec 0xafe9a10, id(MPEG2VIDEO) type(Video)
AFD: codec AC3 has 2 channels
AFD: Opened codec 0xafe9f90, id(AC3) type(Audio)
Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
Opening ALSA audio device 'default'.
Mixer unable to find control Master 1
mixer unable to find control Master 1
VDPAU: Created 2 output surfaces.
VDPAU: Created VDPAU render device 1266x705
NVP(8): Forcing decode extra audio option on (Video method requires it).
OSD Theme Dimensions W: 1280 H: 720
Realtime priority would require SUID as root.
TV: Changing from None to WatchingPreRecorded
OpenGLVideoSync()
WriteAudio: buffer underrun
Video timing method: SGI OpenGL
VDPAU: Added 2 output surfaces (total 4, max 4)

```

And for reference, here's lspci:
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by nickrout on 2011-03-30
what does mediainfo tell you about the files?

what about playback with other players? (mplayer, xine, vlc etc)

---

### Post by arriflex on 2011-03-31
The CBS files play ok Gnome Mplayer and gxine, although I have not experimented with various de-interlacing options there, but not in VLC, and not in the native Mythbuntu player inside mythtv.

Thanks for looking at this with me. I guess I could set up an Mplayer profile in the playback for everything recorded on that channel. I just can't believe I'm the only one with this problem, I still wonder if my CBS affiliate even knows they're pushing out the audio stream at 256kbps!

Mediainfo reports this for a CBS recording:
```
General
ID                               : 239 (0xEF)
Complete name                    : /var/lib/mythtv/recordings/2291_20110330210000.mpg
Format                           : MPEG-TS
File size                        : 6.83 GiB
Duration                         : 59mn 53s
Overall bit rate                 : 16.3 Mbps

Video
ID                               : 49 (0x31)
Menu ID                          : 1 (0x1)
Format                           : MPEG Video
Format version                   : Version 2
Format profile                   : Main@High
Format settings, BVOP            : No
Format settings, Matrix          : Default
Format settings, GOP             : M=1, N=9
Codec ID                         : 2
Duration                         : 59mn 53s
Bit rate mode                    : Constant
Bit rate                         : 15.6 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
Frame rate                       : 29.970 fps
Standard                         : Component
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Interlaced
Scan order                       : Top Field First
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.251
Stream size                      : 6.38 GiB (93%)

Audio
ID                               : 52 (0x34)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : 129
Duration                         : 59mn 53s
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Compression mode                 : Lossy
Delay relative to video          : -307ms
Stream size                      : 110 MiB (2%)
Language                         : English

```


And this for an NBC recording (the NBC recordings playback fine):
```
General
ID                               : 235 (0xEB)
Complete name                    : /var/lib/mythtv/recordings/2171_20110330210000.mpg
Format                           : MPEG-TS
File size                        : 5.20 GiB
Duration                         : 59mn 55s
Overall bit rate                 : 12.4 Mbps

Video
ID                               : 49 (0x31)
Menu ID                          : 1 (0x1)
Format                           : MPEG Video
Format version                   : Version 2
Format profile                   : Main@High
Format settings, BVOP            : Yes
Format settings, Matrix          : Default
Format settings, GOP             : M=3, N=15
Codec ID                         : 2
Duration                         : 59mn 54s
Bit rate mode                    : Constant
Bit rate                         : 11.6 Mbps
Nominal bit rate                 : 18.1 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
ActiveFormatDescription          : Full frame 16:9 image
Frame rate                       : 29.970 fps
Standard                         : Component
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Interlaced
Scan order                       : Top Field First
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.187
Stream size                      : 4.86 GiB (93%)

Audio
ID                               : 52 (0x34)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : 129
Duration                         : 59mn 55s
Bit rate mode                    : Constant
Bit rate                         : 192 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Compression mode                 : Lossy
Delay relative to video          : -160ms
Stream size                      : 82.3 MiB (2%)
Language                         : English
Name                             : en:Primary Audio

Text #1
ID                               : 49 (0x31)608-1
Menu ID                          : 1 (0x1)
Format                           : EIA-608
Muxing mode                      : A/53 / DTVCC Transport
Muxing mode, more info           : Muxed in Video #1
Duration                         : 59mn 54s
Stream size                      : 0.00 Byte (0%)

Text #2
ID                               : 49 (0x31)1
Menu ID                          : 1 (0x1)
Format                           : EIA-708
Muxing mode                      : A/53 / DTVCC Transport
Muxing mode, more info           : Muxed in Video #1
Duration                         : 59mn 54s
Stream size                      : 0.00 Byte (0%)


```

---

### Post by arriflex on 2011-05-19
Upgrading to .24 did the trick for me. No other changes. Followed the brilliant advice from: [http://ubuntuforums.org/showpost.php?p=10755199&postcount=2](http://ubuntuforums.org/showpost.php?p=10755199&postcount=2)

Hope this helps someone else.

---

