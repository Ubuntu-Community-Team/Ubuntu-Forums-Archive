---
title: "Apple ProRes Codec Support in Ubuntu?"
date: 2010-07-06
forum: Multimedia Software
---

### Post by seventhsamurai on 2010-07-06
I do a lot of video encoding as part of my work and have been using Ubuntu extensively for my needs. I have found a simple, open source encoder like Handbrake to give far superior results than other encoders costing several hundred dollars. With MPEG-4 and x264 universally accepted as the best distribution codec for video, Handbrake is godsent. It reads everything, well, almost.

Handbrake does not read mov files with the Apple ProRes codec and after doing some google searches, I haven't found anyone who has been able to really rig any support for it in Ubuntu.

I was wondering if anyone had successfully been able to read ProRes quicktimes in Ubuntu or encode from them.

My current fix is to run the ProRes quicktimes through Sorenson Squeeze on a Windows machine and encode with a lossless codec without further compression, then take it to Handbrake and encode to MP4. Obviously this takes double the amount of time.

With almost all codecs being supported in Linux, I wonder why one of the most popular codecs today is left out.

---

### Post by andrew.46 on 2010-09-11
Hi seventhsamurai,

> **seventhsamurai said:**
> I was wondering if anyone had successfully been able to read ProRes quicktimes in Ubuntu or encode from them.

It is possible for a 32 bit system to at least play these files by using the svn MPlayer according to this guide:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

and then manually adding the following codec to the codecs installed with w32codecs:

[http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx](http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx)

All the best,

Andrew

---

### Post by seventhsamurai on 2010-09-12
Thanks andrew. I installed the player. I cannot figure out how to add the codec manually. Can you please help? Thanks.

---

### Post by andrew.46 on 2010-09-12
Hi seventhsmurai,

I will admit that I did not spell that out in great detail as your post was unanswered for a couple of months and I did not know if you would receive this answer :).

As long as you have installed the latest svn MPlayer according to the guide I linked to, and you are running a 32 bit installation, the following single command should place the required codec in the correct location:

```

sudo wget \
     'http://samples.mplayerhq.hu/drivers32/new/AppleProResDecoder.qtx' \
     -O /usr/lib/codecs/AppleProResDecoder.qtx

```

I attach a screenshot of SMPlayer playing [a sample Apple ProRes file]("http://samples.mplayerhq.hu/V-codecs/HCPA/Boar__Apple_ProRes_422-partial.mov").

Andrew

---

### Post by seventhsamurai on 2010-09-12
I did as you asked, hoping against hope that it would work, because I am running a 64bit installation.

So I guess there is no way to really get this to work in a 64 bit system huh?

---

### Post by andrew.46 on 2010-09-12
Hi seventhsamurai,

> **seventhsamurai said:**
> I did as you asked, hoping against hope that it would work, because I am running a 64bit installation.

So I guess there is no way to really get this to work in a 64 bit system huh?

Unfortunately at the moment access to this codec only comes with the 32 bit MPlayer. Having said that I believe it is possible to compile the 32 bit MPlayer on a 64 bit system and thus use AppleProResDecoder.qtx but I have had no experience with this. Hopefully others can guide on this one?

Andrew

---

### Post by mc4man on 2010-09-12
> compile the 32 bit MPlayer on a 64 bit system
pretty simple, see here (could be refined but does work
[http://ubuntuforums.org/showthread.php?p=9338517](http://ubuntuforums.org/showthread.php?p=9338517)

Edit:
you might be able to install a pre-built 32 bit mplayer, though probably better to build

---

### Post by andrew.46 on 2011-02-27
And the definitive test of the 32 bit MPlayer is as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i appleprores[/COLOR]**

qtprores    qtvideo   working   Apple ProRes 422 (HQ) decoder  [AppleProResDecoder.qtx]

```

Andrew

---

### Post by carbon512 on 2011-03-24
Hello -- jumping in to this helpful thread; I had been looking for the same thing.

I installed mplayer (and gnome mplayer since the gui stuff helps this linux newbie). I did this from the repository since it is now 2011 and I hoped that would work by now; simpler.

Then I got the codec, put it in /usr/lib/codecs/ and ran your "definitive test" :

```
xxx@xxxxx:~$ mplayer -vc help | grep -i appleprores

qtprores    qtvideo   working   Apple ProRes 422 (HQ) decoder  [AppleProResDecoder.qtx]

```But...

when I try to open a quicktime file encoded in Apple Prores 422 (HQ) I get the following error:
"failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: no such file or directory" and I get no video.

I've tried changing the video output settings but all that does is remove the error message - still no video.

I can't find that in my synaptic package manager search.... not sure what I am missing or where to get it, and I am not sure if not having a nvidia display card is relevant or not (I am on an Acer 1410 netbook with an integrated Intel card but I think that doesn't matter).

I had figured I just could not ever view my ProRes footage on my netbook at all in Ubuntu -- it would be great if I could! (Now if I could just run FCP in Maverick also, I'd be all set...)

Edited to add update: according to several sources, I need to use vaapi not vdpau since I have an intel graphics chip. I will keep researching this...

---

### Post by andrew.46 on 2011-03-24
> **carbon512 said:**
> when I try to open a quicktime file encoded in Apple Prores 422 (HQ) I get the following error:

```
failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: no such file or directory
```

and I get no video.

Could you run your test file from the commandline in the following manner:
```

mplayer -v *[COLOR="Red"]my_file[/COLOR]*
```

with the obvious substitution of the actual filename for *[COLOR="Red"]my_file[/COLOR]* and post the command and terminal output here? This should give a few hints as to what is going on here.

---

### Post by carbon512 on 2011-03-25
Aha! yes, it does shed some light --

```
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Genuine Intel(R) CPU           U2300  @ 1.20GHz (Family: 6, Model: 23, Stepping: 10)
extended cpuid-level: 8
extended cache-info: 67125312
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/cjs/.mplayer/codecs.conf'
Reading /home/cjs/.mplayer/codecs.conf: Can't open '/home/cjs/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'file:///media/Iomega/grizzly%20movs/Grizzlies1-3.mov'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/cjs/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/cjs/.mplayer/input.conf'
Can't open input config file /home/cjs/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Grizzlies1-3.mov.conf') -> '/home/cjs/.mplayer/Grizzlies1-3.mov.conf'

Playing file:///media/Iomega/grizzly%20movs/Grizzlies1-3.mov.
get_path('sub/') -> '/home/cjs/.mplayer/sub/'
File not found: '/media/Iomega/grizzly%20movs/Grizzlies1-3.mov'
Failed to open file:///media/Iomega/grizzly%20movs/Grizzlies1-3.mov.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
``` I don't have a codecs.conf file in my /home/cjs/.mplayer/ folder. All I have in there is a "config" file that has the following:

"# Write your default config options here!


[gnome-mplayer]
vo=xv
msglevel=all=5
vf=eq2"

so... yes... 
can't. quite. grasp. almost. trying. so. close...

---

### Post by andrew.46 on 2011-03-26
This is the immediate problem:

```
File not found: '/media/Iomega/grizzly%20movs/Grizzlies1-3.mov'
Failed to open file:///media/Iomega/grizzly%20movs/Grizzlies1-3.mov.
```

Perhaps drag the file onto your desktop and open it up from there?

Andrew

---

### Post by mc4man on 2011-03-26
Another way to eliminate  path error  as the issue is to just open a terminal and type in your command (in this instance mplayer -v

After typing the command hit the space bar, then just drag and drop the file to be played onto the terminal window.
Click anywhere in the terminal to return focus and press enter on keyboard.

(I use a couple of 'drag & drop' desktop launchers, (set as application in terminal), to run mplayer in slightly different ways

---

### Post by carbon512 on 2011-03-26
I completely missed that. (Red-faced). 

Here is the output for a valid file location:

```
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Genuine Intel(R) CPU           U2300  @ 1.20GHz (Family: 6, Model: 23, Stepping: 10)
extended cpuid-level: 8
extended cache-info: 67125312
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/cjs/.mplayer/codecs.conf'
Reading /home/cjs/.mplayer/codecs.conf: Can't open '/home/cjs/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'Desktop/Grizzlies2-13.mov'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/cjs/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/cjs/.mplayer/input.conf'
Can't open input config file /home/cjs/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Grizzlies2-13.mov.conf') -> '/home/cjs/.mplayer/Grizzlies2-13.mov.conf'

Playing Desktop/Grizzlies2-13.mov.
get_path('sub/') -> '/home/cjs/.mplayer/sub/'
[file] File size is 118301101 bytes
STREAM: [file] Desktop/Grizzlies2-13.mov
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: QuickTime/MPEG-4/Motion JPEG 2000 format
libavformat file format detected.
==> Found video stream: 0
======= VIDEO Format ======
  biSize 50
  biWidth 1280
  biHeight 720
  biPlanes 0
  biBitCount 24
  biCompression 1751347297='apch'
  biSizeImage 2764800
Unknown extra header dump: [0] [0] [0] [a] [66] [69] [65] [6c] [1] [0] 
===========================
[lavf] stream 0: video (unknown), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 30580 (0x7774)
Channels: 2
Samplerate: 48000
avg byte/sec: 0
Block align: 1
bits/sample: 16
cbSize: 0
==========================================================================
[lavf] stream 1: audio (pcm_s16be), -aid 0, -alang eng
LAVF: 1 audio and 1 video streams found
LAVF: build 3424258
VIDEO:  [apch]  1280x720  24bpp  29.970 fps  108820.2 kbps (13283.7 kbyte/s)
[V] filefmt:44  fourcc:0x68637061  size:1280x720  fps:29.970  ftime:=0.0334
get_path('sub/') -> '/home/cjs/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1366x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [qtvideo] Quicktime Video decoder
sh->ImageDesc not set, cannot use binary QuickTime codecs (try -demuxer mov?)
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x68637061.
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
dec_audio: Allocating 2048 + 65536 = 67584 bytes for output buffer.
AUDIO: 48000 Hz, 2 ch, s16be, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16be -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16be
[dummy] Was reinitialized: 48000Hz/2ch/s16be
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 48000Hz 2ch s16be (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16be -> 48000Hz/2ch/s16be...
[dummy] Was reinitialized: 48000Hz/2ch/s16be
[dummy] Was reinitialized: 48000Hz/2ch/s16be
Video: no video
Freeing 1 unused video chunks.
Starting playback...
Increasing filtered audio buffer size from 0 to 50048
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
EOF code: 1  1) of 8.6 (08.6)  2.3% 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: pcm
vo: uninit ...

Exiting... (End of file)
```Did  I just did not properly install it --? Many directories and files not found... So the install from Synaptic package manager is not the same as the compile instructions I saw you had elsewhere?

[an aside - is it helpful or not to use the "code" tags when copying terminal output here? Doesn't the lack of word wrap for those long lines make it harder to read?]

---

### Post by andrew.46 on 2011-03-26
There seems to be a problem here:

```
Opening video decoder: [qtvideo] Quicktime Video decoder
sh->ImageDesc not set, cannot use binary QuickTime codecs (try -demuxer mov?)
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x68637061.
```

Perhaps try the suggested syntax, which will make your command:

```
mplayer -demuxer mov $HOME/Desktop/Grizzlies2-13.mov
```

Code tags are preferred as they make reading easier and do not distort the line spacing.

Andrew

---

### Post by carbon512 on 2011-03-26
Well, here is the output of that command; still no joy. At this point I am not sure what I am reading any more. I thought I was on to something with the missing codecs.conf file but now I am lost. Appreciate the help. (note - I got some "permission denied" so I ran it again with sudo but still no go.

```
cjs@xxxxxx:~$ mplayer -demuxer mov $HOME/Desktop/Grizzlies2-13.mov
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/cjs/Desktop/Grizzlies2-13.mov.
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [apch]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [qtvideo] Quicktime Video decoder
Win32 LoadLibrary failed to load: QuickTime.qts, /usr/lib/codecs/QuickTime.qts
unable to load QuickTime.qts
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x68637061.
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 48000Hz 2ch s16be (2 bytes per sample)
Video: no video
Starting playback...
A:   8.2 (08.1) of 8.6 (08.5)  0.1% 

Exiting... (End of file)
  
```

---

### Post by mc4man on 2011-03-26
> Then I got the codec, put it in /usr/lib/codecs/ and ran your "definitive test" :

Code:

xxx@xxxxx:~$ mplayer -vc help | grep -i appleprores

qtprores    qtvideo   working   Apple ProRes 422 (HQ) decoder  [AppleProResDecoder.qtx]
That doesn't quite qualify as "definitive" in the sense that the codec is installed and working, just means that your installed version of mplayer supports it and is considered 'working'

this stands out in your log - 
> Win32 LoadLibrary failed to load: QuickTime.qts, /usr/lib/codecs/QuickTime.qts
unable to load [COLOR="Red"]QuickTime.qts[/COLOR]

Note it's looking to use QuickTime.qts 

Would be good if there was a common sample of a 'problem' file available

---

### Post by andrew.46 on 2011-03-27
Hmmm.... not sure if the QuickTime.qts thing is a red herring..... but it would not hurt to check if both are in place:
```

sudo find /usr -iname QuickTime.qts
sudo find /usr -iname AppleProResDecoder.qtx
```

But as mc4man has mentioned, can you post the file somewhere?

Andrew

---

### Post by mc4man on 2011-03-27
> can you post the file somewhere?
If not possible then if there is an  online sample that you can't play. ( not sure how easy to find..

---

### Post by carbon512 on 2011-03-27
Nope, no QuickTime.qts :

```
cjs@XXX:~$~$ sudo find /usr -iname AppleProResDecoder.qtx
/usr/lib/codecs/AppleProResDecoder.qtx
cjs@XXX:~$:~$ sudo find /usr -iname QuickTime.qts
cjs@XXXX:~$
```I put up a test file, encoded in AppleProRes 422 (HQ); you can get it at [http://www.io.com/~csperber/prores.html]("http://www.io.com/%7Ecsperber/prores.html")

Sorry for the large file, I don't have a reliable way to edit it and keep the original codec right now. For what it is worth, the sample file at [http://samples.mplayerhq.hu/V-codecs/HCPA/](http://samples.mplayerhq.hu/V-codecs/HCPA/) doesn't work either -- that is a smaller file to play with though.

---

### Post by mc4man on 2011-03-27
With a recent mplayer build can play the mplayer sample on 1 setup  using a -demuxer mov option
> mplayer -vo xv  -demuxer mov /home/doug/Downloads/Boar__Apple_ProRes_422-partial.mov

On another couldn't, even though both codecs were installed. 
i'm pretty sure it's the versions of those codecs and the working set are the most recent
Try getting the new set from mplayerhq.hu and totally replacing your current set (don't merge, I'd just delete all the codecs  in the   /usr/lib/codecs folder and replace w/ all the new codecs.

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2
```
or go directly and dl

Your sample produces a 404, if inclined to re up or happen find a decent one online would be nice to have a sample that lasted longer than the mplayer one does.

---

### Post by carbon512 on 2011-03-27
whoo hoo!
Got the new codecs and the file played! There are some other error messages... but it plays, so all is good.

Thank  you so much, great assistance, much appreciated. (Here is the terminal  output in case the errors are significant or relevant)

```
mplayer -vo xv -demuxer mov Grizzlies226.mov
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Grizzlies226.mov.
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [apch]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [qtvideo] Quicktime Video decoder
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
 86 00 00 00 61 70 63 68 00 00 00 00 00 00 00 00
 00 00 00 00 6C 70 70 61 00 00 00 00 FF 03 00 00
 00 05 D0 02 00 00 48 00 00 00 48 00 00 00 00 00
 01 00 15 41 70 70 6C 65 20 50 72 6F 52 65 73 20
 34 32 32 20 28 48 51 29 00 00 00 00 00 00 00 00
 00 00 18 00 FF FF 00 00 00 10 70 61 73 70 00 00
 00 01 00 00 00 01 00 00 00 12 63 6F 6C 72 6E 63
 6C 63 00 01 00 01 00 01 00 00 00 0A 66 69 65 6C
 01 00 00 00 00 00
=============== ImageDescription at 0x91c9e08 ==================
idSize=0x86  fourcc=0x68637061
ver=0 rev=0 vendor=0x6170706C
tempQ=0 spatQ=1023  dim: 1280 x 720  dpi: 72.00 x 72.00  depth: 24
dataSize=0 frameCount=1 clutID=-1
name='Apple ProRes 422 (HQ)'
00 00 00 10 | 70 61 73 70 | 00 00 00 01 | 00 00 00 01
=========================================================
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Packed YUY2 
theQuickTimeDispatcher catched -> 0x6693c3e0
Selected video codec: [qtprores] vfm: qtvideo (Apple ProRes 422 (HQ) decoder)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 48000Hz 2ch s16be (2 bytes per sample)
Starting playback...
WARNING: CreateThread flags not supported
WARNING: CreateThread flags not supported
A:   3.2 V:   2.7 A-V:  0.499 ct:  0.000  82/ 82 109%  4%  0.1% 60 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  10.8 V:  10.8 A-V:  0.001 ct:  3.652 326/326 108%  3%  0.1% 246 0 
WARNING! Invalid Ptr handle!

Exiting... (End of file)
```Sorry  about the bad link -- (Careless html... That's why I'm not a  programmer.) I'd be happy to provide a longer sample and can put it up  at [http://samples.mplayerhq.hu/V-codecs/](http://samples.mplayerhq.hu/V-codecs/) as well, for others. I'll look  for something else next week and see what I can do -- I have a lot of  Apple ProRes 422 footage but need to find something more suited to an  indefinite lifespan on the internet. (I am exceedingly over-protective  of privacy, rights, etc.)

Gnome mplayer GUI (older version) does  not play the file. But I've downloaded the latest version and am working  on configuring, building and installing it... I am getting more error  messages in trying to do that. But-- as much as I would like to continue  getting help here because this you two have been incredibly helpful  --  these are problems that at this point I can/should keep working through  on my own, to learn more.

If I get really stuck trying to get  Gnome Mplayer working right, I may come back for some tips instead of  beating my head against the wall to the point of spilling my brains on  the floor. That's such a mess to clean up later.

---

### Post by mc4man on 2011-03-28
I did get gnome-mplayer to play that short sample, will only say that by default it wouldn't. (your idea to try to figure it out yourself is the way to go, if need be then ask.

---

### Post by andrew.46 on 2011-03-28
Good news that it all works now :). A better sample than the daggy one on the MPlayer site would be nice if you get round to it!

---

### Post by carbon512 on 2011-03-30
You can grab an 11-second sample (97MB) from [http://www.io.com/~csperber/AppleProRes422.mov]("http://www.io.com/%7Ecsperber/AppleProRes422.mov") 

Feel free to use or distribute as you wish. I won't keep it up there very long as it's not really a storage server, but I'll leave it there for a few weeks. It is not an ideal sample to evaluate a codec's quality (no motion, low quality audio) but since ProRes422 is not a distribution codec anyway, that shouldn't really be a concern; it is fine for testing functionality.

I've asked how to make it available through [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/) 

Gave up trying to make gnome mplayer play the file... will have to let it simmer in the back of my brain and see what else strikes me to try next time I revisit this puzzle. If you have any hints (besides changing some defaults), I'll take 'em... Next up is to see if I can get mplayer (and gnome mplayer) using vaapi ([http://reverserplus.wordpress.com/2011/02/04/getting-mplayer-vaapi-working-under-ubuntu-10-10-on-viliv-n5/](http://reverserplus.wordpress.com/2011/02/04/getting-mplayer-vaapi-working-under-ubuntu-10-10-on-viliv-n5/)) since my intel video chip supports that and my Little Netbook That Could can use all the help it can get.

---

### Post by mc4man on 2011-03-30
> If you have any hints (besides changing some defaults), I'll take 'em.
Not sure if that means a 'hint' or just tell me....

For a hint - remember the mplayer option -demuxer mov (Edit...P...

you can find several threads on a vaapi mplayer - use a google site search on this forum
( I use a bookmarks toolbar in fire fox so added a bookmarklet from here, very handy - using the "Google Site Search" one, just dragged to middle of my toolbar
[http://www.imilly.com/bm.htm](http://www.imilly.com/bm.htm)

Thanks for the sample....

---

### Post by carbon512 on 2011-03-30
Yes, I did mean "hint," not "tell me," thanks -- I will check into that when I next delve into it. I think in fact I did start going down that road, but can't recall where it ended up;  most likely in distraction.

Appreciate all the help and the tips and playing along with Ubuntu as a puzzle.

---

### Post by andrew.46 on 2011-09-20
Resurrecting a slightly old thread just to mention that FFmpeg now has an Apple ProRes decoder and this works well with the current svn MPlayer. Great news for those running MPlayer on a 64bit installation...

---

### Post by Robertjm on 2011-09-20
Begging the questions, is there any love for those of us using 32 bit still?

Robert

> **andrew.46 said:**
> Resurrecting a slightly old thread just to mention that FFmpeg now has an Apple ProRes decoder and this works well with the current svn MPlayer. Great news for those running MPlayer on a 64bit installation...

---

### Post by mc4man on 2011-09-20
> **Robertjm said:**
> Begging the questions, is there any love for those of us using 32 bit still?

Robert
There has always been love codec wise for 32 bit (w32/Win32codecs), what Andrew was meaning is that now 64 bit can get support for this codec.
(w64codecs is practically worthless

---

### Post by andrew.46 on 2011-09-25
BTW I have found a nice if somewhat huge Apple ProRes 422 High Quality file:

```
wget http://www.marcocordero.com/gh13/gh13_prores.zip
```

Best one I have found so far, I guess the difficulty in finding samples lies in the fact that ProRes is intended as an intermediary format rather than an end result.

---

### Post by paulinchen on 2011-11-21
Hi there, did anyone had success playback ProRes 4444? I tried it following this guide, but wasn't successful.

---

