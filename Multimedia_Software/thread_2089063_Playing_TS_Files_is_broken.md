---
title: "Playing TS Files is broken"
date: 2012-11-28
forum: Multimedia Software
---

### Post by THolz11 on 2012-11-28
My recorded Films in *.TS format  dont play in Ubuntu 12.04.

Some sd films do play but almost all hd-Recordings dont start.

I tried a clean install with all codecs aand it didnt work.

Ubuntu 10.04 plays all ts files without a Problem.

---

### Post by BicyclerBoy on 2012-11-28
What are you trying to play them in ?

There is/was a gstreamer bug with h264 (in 12.04)..
That should not stop VLC mythtv or XBMC working..

By all codecs do you mean "restricted extras" etc & unstripped libav* ?

---

### Post by THolz11 on 2012-11-28
Videoplayer, Gnome Mplayer and  Banshee 

All codecs, means all i could find in Softwarecenter.

Restricted bad ugly and so.

VLC is the only player that works for all recorded *ts Files in Ubuntu 12.04.

XBMC is not working on Network with *ts or Live-TV (*TS Stream) since i switched to 12.04.

When i try to play files from a smb share on a w7 Host, Ubuntu also not shows  a thumbnail.

When i copy this File to an local drive, Ubuntu shows an Icon and  plays some of the Files.

Playing from SMB -> NO
Playing from Local Drive -> some HD and most SD

---

### Post by BicyclerBoy on 2012-11-28
I would install/use synaptic to manage all installed software. The SW centre is inadequate.

I would check the libav* packages are the unstripped "extras" versions.

gnome mplayer, banshee will be using gstreamer & distro shared libs.
I believe gstreamer-ffmpeg is required for H264 video decoder.
Like I said, there are/were problems ts parsing &/or h264 & 12.04..

VLC, the "real" mplayer, MythTV & XBMC are self-contained.

Your TS files is not an exact definition..there are mpeg(2)-ts container & may contain mpeg2 or mpeg4/10 SD or HD ..

mediainfo is purported to be best info tool. 

Was your live-tv ts streams from a HDHomerun device?
What do you record them with?

You might want to add a 3rd party ppa with a gstreamer bugfix:
[http://ubuntuforums.org/showpost.php?p=12334954&postcount=5](http://ubuntuforums.org/showpost.php?p=12334954&postcount=5)

---

### Post by THolz11 on 2012-11-29
HD TS Recording
General
ID : 	2 (0x2)
Complete name : 	Die Brücke - Transit in den Tod_ZDF HD_2012-03-18_22-05.ts
Format : 	MPEG-TS
File size : 	125 MiB
Duration : 	1mn 18s
Overall bit rate : 	13.3 Mbps

Video
ID : 	511 (0x1FF)
Menu ID : 	3 (0x3)
Format : 	AVC
Format/Info : 	Advanced Video Codec
Format profile : 	Main@L4.0
Format settings, CABAC : 	Yes
Format settings, ReFrames : 	5 frames
Codec ID : 	27
Duration : 	1mn 18s
Bit rate : 	11.5 Mbps
Width : 	1 280 pixels
Height : 	720 pixels
Display aspect ratio : 	16:9
Frame rate : 	50.000 fps
Color space : 	YUV
Chroma subsampling : 	4:2:0
Bit depth : 	8 bits
Scan type : 	Progressive
Bits/(Pixel*Frame) : 	0.249
Stream size : 	107 MiB (86%)
Color primaries : 	BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics : 	BT.709-5, BT.1361
Matrix coefficients : 	BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio #1
ID : 	288 (0x120)
Menu ID : 	3 (0x3)
Format : 	MPEG Audio
Format version : 	Version 1
Format profile : 	Layer 2
Codec ID : 	3
Duration : 	1mn 18s
Bit rate mode : 	Constant
Bit rate : 	256 Kbps
Channel(s) : 	2 channels
Sampling rate : 	48.0 KHz
Compression mode : 	Lossy
Delay relative to video : 	-1s 52ms
Stream size : 	2.40 MiB (2%)
Language : 	German

Audio #2
ID : 	289 (0x121)
Menu ID : 	3 (0x3)
Format : 	MPEG Audio
Format version : 	Version 1
Format profile : 	Layer 2
Codec ID : 	3
Duration : 	1mn 18s
Bit rate mode : 	Constant
Bit rate : 	192 Kbps
Channel(s) : 	2 channels
Sampling rate : 	48.0 KHz
Compression mode : 	Lossy
Delay relative to video : 	-1s 73ms
Stream size : 	1.80 MiB (1%)

Audio #3
ID : 	290 (0x122)
Menu ID : 	3 (0x3)
Format : 	MPEG Audio
Format version : 	Version 1
Format profile : 	Layer 2
Codec ID : 	3
Duration : 	1mn 18s
Bit rate mode : 	Constant
Bit rate : 	192 Kbps
Channel(s) : 	2 channels
Sampling rate : 	48.0 KHz
Compression mode : 	Lossy
Delay relative to video : 	-1s 94ms
Stream size : 	1.80 MiB (1%)
Language : 	qaa

Audio #4
ID : 	320 (0x140)
Menu ID : 	3 (0x3)
Format : 	AC-3
Format/Info : 	Audio Coding 3
Mode extension : 	CM (complete main)
Codec ID : 	6
Duration : 	1mn 18s
Bit rate mode : 	Constant
Bit rate : 	448 Kbps
Channel(s) : 	6 channels
Channel positions : 	Front: L C R, Side: L R, LFE
Sampling rate : 	48.0 KHz
Bit depth : 	16 bits
Compression mode : 	Lossy
Delay relative to video : 	-1s 114ms
Stream size : 	4.21 MiB (3%)
Language : 	German

Text #1
ID : 	352 (0x160)-100
Menu ID : 	3 (0x3)
Format : 	Teletext
Language : 	German

Text #2
ID : 	384 (0x180)
Menu ID : 	3 (0x3)
Format : 	DVB Subtitle
Codec ID : 	6
Duration : 	1mn 14s
Delay relative to video : 	3s 791ms
Language : 	German

Installed :libav* packages are the unstripped "extras" versions.

Now Playing Local with with Mplayer works but there is for seconds no audio then it plays Audio then no audio again.

Playing from SMB dont works Player does nothing wenn trying to open.


VLC work on both Lan and local.

---

### Post by BicyclerBoy on 2012-11-29
Those files are not so different from mine..except that LATM/AAC is normally used with H264 mpeg4/10AVC.

Similar files play okay on atom netbook (576i) in mplayer (real mplayer).
The Gnome totem movie player does not work..

I've long since given up on std distro packages & now build the important ones from source.
I would find/use a recent build of (real) mplayer &/or SMplayer (GUI).

Try an up-to-date XBMC from a 3rd party ppa.

IMO VLC has been the only consistent reliable std distro multimedia package.

---

### Post by THolz11 on 2012-11-29
what i cant understand.

why is it playing from local drive and not from SMB/Share ?

XMBC is now working again.

Gave Frodo a try but now my Nvidia 9400 at  Mediacenter (Mac Mini) works no more with hardware decoding.

I will try eden again.

---

