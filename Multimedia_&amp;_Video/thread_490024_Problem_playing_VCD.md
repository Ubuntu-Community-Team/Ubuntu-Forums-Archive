---
title: "Problem playing VCD"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by GRbenji on 2007-07-02
I'm new to Linux and have installed Edubuntu for some kids to use.

Tried to play some cartoon VCD on the Movie Player and get msg "The playback of this movie requires a VCD protocol source plugin which is not installed".  May I know how to resolve it?

Thank you.

---

### Post by mikehipson on 2007-07-11
hello i have that same problem.... can somebody solve it????

Mike

---

### Post by Neo_Me on 2007-07-12
Is There Any Solution for This ??

---

### Post by KRossKoWolf on 2007-07-12
Hi, you have to install the drivers to play Dvd's, as far as I remeber, to do this I would recommend installing a program call Automatix2, get it [here]("http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation"), select the package that corrospoands to your install, the one with the right numbers and processor architecture, when it's done double click it, and use the package manager that should apppear to install, once it finishes, click "Applications", then "System Tools", then "Automatix", it willl ask for a password, use your password for this, then read the warning message and accept, if you wish to, then click "Codec's and Plugins", then select "AUD-DVD Codecs" and "Multimedia Codecs", then click "Start", it should install, and now your VCD should play, good luck :).

---

### Post by Bablefish on 2007-07-12
I did that sometime ago and VCDs still don't work

---

### Post by mikehipson on 2007-07-12
Hi, Im doing the automatix thing, and i downloaded it, and got as far as going into "applications" then "system tools" then "automatix"  I read the note and agreed to the terms and conditions.  It started doing something, but didnt finish.  it says "automatix could not continue because some keys could not be downloaded.  Please try again later"  Should I assume that all i have to do is try again later and everything should work out?  or do i have to download something else?


Mike

---

### Post by david_2001 on 2007-07-12
(S)VCD playback seems to be well broken in feisty.  Mplayer works but totem, vlc and xine-based players do not.  Take a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/43589](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/43589).

---

### Post by Lividity on 2007-07-12
I just got VCD playback to work using VLC 

Step 1: Determine the path to your CDROM  

From the terminal: nano /etc/fstab           
See 1.png

My dvdrw/cdrw is /dev/scd0 
See 2.png

2: Open VLC 

3: ctrl + f or Click File then select "Open File..." 
See 3.png

3: where it says "Open:" Input the path to your CD/DVD drive. Mine is  "/dev/scd0"
See 4.png

4: Click OK and enjoy
See 5.png

The film is playing in photo 5 I just don't know how to take a screenshot showing it. 

P.S. 

I have VCD playback via Mplayer. All I have to do is 

1: Fire up Mplayer

2:  right click the player window

3: Scroll to sub-menu VCD  

4: Select Open Disk...

I get an error message that pops up that says "ioctl dif1: Input/output error"

Then the movie begins playing without issue. So I close the error window and watch the film.

---

### Post by trak87 on 2007-07-12
If you have mplayer installed, playing a vcd disk can be as simple as this (on the command line):

```
mplayer vcd://1
```

---

### Post by Lividity on 2007-07-12
Oh, if you don't have vlc then from the terminal I would:

sudo apt-get update 
enter

sudo apt-cache search vlc
enter

sudo apt-get install vlc vlc-nox vlc-plugin-alsa vlc-plugin-arts vlc-plugin-esd vlc-plugin-ggi vlc-plugin-glide vlc-plugin-sdl vlc-plugin-svgalib 
enter

---

### Post by Lividity on 2007-07-12
> **trak87 said:**
> If you have mplayer installed, playing a vcd disk can be as simple as this (on the command line):

```
mplayer vcd://1
```



lividity@Black-Box:~$ mplayer vcd://1
MPlayer 2:1.0~rc1-0ubuntu12+3v1ubuntu0 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 1
track 02:  adr=1  ctrl=4  format=2  00:08:00  mode: 1
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

---

### Post by Lividity on 2007-07-12
> **trak87 said:**
> If you have mplayer installed, playing a vcd disk can be as simple as this (on the command line):

```
mplayer vcd://1
```

When I typed: mplayer vdc://1
In a terminal I received the 0x56444152 error

I have libdv4 installed so that was not the problem.  

Then I read linuchsan's post here:

[http://ubuntuforums.org/showthread.php?t=314510&highlight=0x56444152](http://ubuntuforums.org/showthread.php?t=314510&highlight=0x56444152)

I got VCD playback from the command line by typing: mplayer vcd://2

No errors no problems : )

---

### Post by trak87 on 2007-07-13
> **Lividity said:**
> I got VCD playback from the command line by typing: mplayer vcd://2

No errors no problems : )


Right. I should have mentioned that it may actually be vcd://1, vcd://2 or vcd://3, etc. The number refers to a track or chapter or something like that.

You can watch a dvd disc the same way:

```
mplayer dvd://n
```

Where 'n' is a number. mplayer is the most capable player of them all. The only problem with it is the interface, but if you learn some of the key commands ('f' for full screen, +/- to adjust a/v sync, etc.) you'll be fine.

There are some hints about mplayer keystrokes here:

/usr/share/doc/mplayer/examples/etc/input.conf

---

### Post by Bablefish on 2007-07-13
After doing all of this I still can't play mine. Does it make a difference that the movies on my VCDs are .dat files?

---

### Post by trak87 on 2007-07-13
> **Bablefish said:**
> After doing all of this I still can't play mine. Does it make a difference that the movies on my VCDs are .dat files?

That shouldn't matter as long as they really are vcd's. But as I recall -- going way back -- mplayer can play dat files directly:

```
mplayer /media/cdrom0/some_dir/filename.dat
```

Does it work?

---

### Post by ShagzModo on 2007-07-14
Hi all!
please help me out on getting vcd play to work.
this is my output in the terminal:

paul@ubun2-pg:~$ mplayer vcd://1
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 1
track 02:  adr=1  ctrl=4  format=2  00:18:72  mode: 1
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: qdv.dll, /usr/lib/win32/qdv.dll, /usr/local/lib/win32/qdv.dll
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=qdv.dll, r=0x8a6c838)
Failed to create DirectShow filter
ERROR: Could not open required DirectShow codec qdv.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdv] vfm: ffmpeg (FFmpeg DV decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0

---

### Post by trak87 on 2007-07-14
For vcd files, use 'mplayer vcd://2' instead of 1. The first track is usually nothing.

I believe the problem is you need to install the proper A/V codecs.  There may be multiple packages you need to install. For starters, do you have the w32codecs package installed? I believe it is a restricted formats package and I don't have the instruction link handy, but basically you have to enable a repository and then you can install it via Synaptic. Once installed try your vcd again and see if it works.

---

### Post by Lividity on 2007-07-18
> **trak87 said:**
> For vcd files, use 'mplayer vcd://2' instead of 1. The first track is usually nothing.

I believe the problem is you need to install the proper A/V codecs.  There may be multiple packages you need to install. For starters, do you have the w32codecs package installed? I believe it is a restricted formats package and I don't have the instruction link handy, but basically you have to enable a repository and then you can install it via Synaptic. Once installed try your vcd again and see if it works.

I had the same error he has. He just needs to switch the track. I had the proper codecs installed.

---

### Post by ignos on 2007-07-24
> For vcd files, use 'mplayer vcd://2' instead of 1. The first track is usually nothing.

Thank you.

---

### Post by ShagzModo on 2007-07-31
mplayer vcd://2 is working fine!

---

### Post by yuanfangcan on 2007-08-12
Yes Mplayer works for me. And I used "vcdxrip --no-ext-psd --cdrom-device=/dev/cdrom --rip" to extract the video to mpeg format.  Everything works great!

---

### Post by ntlam on 2007-08-18
I used the command
mplayer vcd://2
there was only the sound and no image
anyone knows this problem?

---

