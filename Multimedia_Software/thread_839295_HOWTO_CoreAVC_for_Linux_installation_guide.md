---
title: "HOWTO: CoreAVC for Linux installation guide"
date: 2008-06-24
forum: Multimedia Software
---

### Post by bruor on 2008-06-24
This guide is being created to help others get CoreAVC working on their ubuntu installations.  I will update this as feedback is left and welcome others to post any helpful information on the minor issues I am experiencing. 

For this guide i Used CoreAVC 1.7.

**Installation:**
Grab the CoreAVC installer and install wine from the add/remove in the applications list. 
once wine is installed, run the coreavc_professional_edition-setup.exe file and use all defaults. This will also install Halii media splitter which I have not used/tested.  once complete ensure that you have your slocate database up to snuff by running 'updatedb' you will need this to find the codec file you need later. 

next, you will want to follow [this guide to install coreavc-for-linux]("http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall")
when you get to step 2, use process 3 to obtain the binaries (precompiled for x64) if this is your architecture. otherwise process 1 should work ok for you.  When you get to step 3 you will need to do the following 'locate CoreAVCDecoder.ax' and then copy it to /usr/lib/win32/ (create if it doesn't exist).  When you get to the [registration process]("http://code.google.com/p/coreavc-for-linux/wiki/RegisterCoreAVC") it says to create the registry entries under registry32 for dshowserver with mythtv and use registry for mplayer or xine,  i needed to add the entries to both or i received an error from step 5 of the first guide. 

once you have gotten acceptable output from dshowserver, move on to getting mplayer to work properly.  I was able to find a guide that used the apt-build process to patch mplayer directly to use the CoreAVC codec, but i ditched that since dshowserver is their recommended method.  The easiest way I could find to complete this part was to follow [this guide]("http://ubuntuforums.org/showthread.php?t=558538") with a slight modification.  Once you have checked out the source from SVN,  run a ./configure as needed (running this with no switches will create a /usr/local/bin instance of mplayer which is separate from the apt installed version in /usr/bin) then patch the source using the [instructions found here]("http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation").

once complete you can foce the use of coravc for devoce by adding -vc coreserve to your mplayer command. 

**NOTES:**
In order to get playback to be smooth I needed to run mplayer  with nice -n 0 and the -fs switch to run it full screen.   If it is running in a window it gives jerky playback 

**Issues: **
After installation, I have found that playback is only possible using the CLI version of mplayer, gmplayer dies with an error about the -vo method.  forcing this to xv or x11 do not have an effect.  This may be compiz related but i have not tested it yet.   

Audo sync,  I have also noticed that using a terminal window to launch mplayer causes the audio to be out of sync on occasion, relaunching normally fixes this.  Right clicking a file and telling it to open with a custom command however, has never exhibited this problem.  This issue may be due to bandwidth, i was able to get smoother playback and seemed to have less issues with local files. 

TS files.  I have been unsuccessful at playing back TS file with coreavc so far.  I only have one to test however.   I get the same error that GMplayer throws about a -vo mode not matching the given codec etc. 

Please leave feedback so this guide can be made into a complete solution that works across the board.  Once the issues above have been solved i will add steps to replace the existing mplayer binaries with scripts that will call the new mplayer with the needed switches etc.

---

### Post by xxtommoxx on 2008-06-25
I don't know if this is a bug or not, but i put in an invalid key and i was unable to register it with a new one (showed dshowserverinstall missing serial)..did a fresh install and put in the key and was able to get dshowserver working

ALso: you wrote system and system32 should be registry and registry32

---

### Post by bruor on 2008-06-25
thanks, i have changed those entries so they are now correct.   Did you have to delete the registry files and recreate them?  I assume that's what you mean by a fresh install.

---

### Post by LifeIsAFractal on 2008-06-30
Thank you! great how-to.  One thing to note, I had an issue with the codecs.conf file in ~/.mplayer.  It was complaining about it being too old and not loading it and thus not letting you use the coreserve codec.  To fix this open codecs.conf and change the line that reads "release SOMEDATE" to the current date in YYYYMMDD format.

I also noticed that when the dshowserver is loading from mplayer it mentions that the postprocessing is set to the codec's max of 4 regardless of what I pass though with the -pp option.  I almost can get smooth playback with coreavc at 1080p, but I fell if I could drop the pp down I would get it.  Any ideas?

---

### Post by bruor on 2008-07-01
you could try tweaking the settings for the codec via the registry settings.   there is a section under the dshowserver guide on the coreavc-for-linux site that mentions different options you can set to affect the codec.   I am not sure how well they work as i have not had to try them,   If its any help,  i did get slightly better playback performance form local disk rather than over my 100mbit network conneciton,  i have yet to try gigabit to see if it has any impact.   i am also going to play around with cache settings as i have noticed jerky playback at first,  but rewinding the scene results in smooth playback.  this does not happen when reading the file from local disk so i assume it is definitely a bandwidth related issue. 

ATM i am working to try to resolve tearing issues i am experiencing.  I have it pretty much resolved with 1080p playback, but viewing low res xvid files gives me ugly output.  i need to do more testing as this could be source related rather than the output of my video card.   if i stumble across any 780g chipset specific info i will append a hardware spec to the guide as well as any notes for my platform/drivers

---

### Post by morphix on 2008-07-08
> **bruor said:**
> When you get to the [registration process]("http://code.google.com/p/coreavc-for-linux/wiki/RegisterCoreAVC") it says to create the registry entries under registry32 for dshowserver with mythtv and use registry for mplayer or xine,  i needed to add the entries to both or i received an error from step 5 of the first guide. 


Can you please be more specific as what commands you actually used to get this done as i am getting an error once i get to point 5 and do not understand what i need to do to add the other "entries for both" ?

---

### Post by bruor on 2008-07-09
In the registration guide for dshowserver it says:

option 1: If you are using dshowserver (for mythtv) do: 
export REGISTRY=$HOME/.mplayer/registry32

option 2: If you are using mplayer or xine do: 
export REGISTRY=$HOME/.mplayer/registry

then do this:  (for coreavc v1.7) 
registercodec -r $REGISTRY -k
"HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "55555-55555-CORE-55555-55555"


I had to do option 1, followed by the registercodec bit, then do option 2 as well. 
It looks like they have updated their guide slightly and it is now correct.  i would suggest setting registration information in both registry locations just to be safe.

---

### Post by morphix on 2008-07-09
> **bruor said:**
> In the registration guide for dshowserver it says:

option 1: If you are using dshowserver (for mythtv) do: 
export REGISTRY=$HOME/.mplayer/registry32

option 2: If you are using mplayer or xine do: 
export REGISTRY=$HOME/.mplayer/registry

then do this:  (for coreavc v1.7) 
registercodec -r $REGISTRY -k
"HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "55555-55555-CORE-55555-55555"


I had to do option 1, followed by the registercodec bit, then do option 2 as well. 
It looks like they have updated their guide slightly and it is now correct.  i would suggest setting registration information in both registry locations just to be safe.

i have followed the guide exactly and cannot get it to work :(
when i run "dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449" all i get is:

shm:/dshow_shm.(null)
sem1:/dshow_sem1.(null)
sem2:/dshow_sem2.(null)
Opening device
Segmentation fault

--

What could this possibly be?

---

### Post by bruor on 2008-07-10
have you verified that CoreAVCDecoder.ax is in /usr/lib/win32 ? 
also try a chmod -R 777 /usr/lib/win32
this should ensure that there are no file permission issues.

---

### Post by Jean__ on 2008-07-18
Any progress on this btw, do people have things working??
And is it what it promises to be, smoother h264 playback?

I followed all instructions, got mplayer to compile, but when I try to play with -vc coreserve I get:
Cannot find codec matching selected -vo and video format 0x31637661.
It's a mkv file, lord of the rings part 1.

---

### Post by bruor on 2008-07-18
I had issues with that as well.  the best way i found to work around it seemed to be sudo "command".    if that doesn't work i did have some success with invoking the command via the launch with custom command option on the right click menu of a file in Gnome.

---

### Post by Jean__ on 2008-07-19
Thanks.
I forgot to create a codecs.conf.
Now I've done that, using -vc coreserve, mplayer opens, displays a black screen, then hangs.

Well, at least I got my own compiled mplayer.:)

---

### Post by zdude on 2008-07-28
I got Coreavc running on both an x32 and x64 version of mplayer. The install was pretty straightforward - thanks to these instructions, but the x64 version gave me a bit of a problem. I compiled the svn mplayer under x32 as well as dshowserver as per instructions and once I had everything working in 32 bit I then basically did the same thing with the x64 OS. The dshowserver file did not work correctly with mplayer in 64 bit - it would pass the test but not run. I tried the precomiled x64 binaries noted in the google wiki (dshowserver install) but they did not work either. I then compiled the dshowserver file "on the x32 machine using the added switch STATIC=1" then copied that file to the 64 bit machine and everything came right up! 
I use "-demuxer lavf -vc coreserve -nocorrect-pts " to play either a TS or M2TS file. 
Hope this helps someone! BTW, the colors and sharpness is A LOT better than the x.264 decoder in mplayer, not to mention the video plays near perfectly. Best $15 I've spent in a while :)

---

### Post by searchforglory@web.de on 2008-08-05
Hi

I went step by step through the tutorial, but the patch is not applied to the mplayer sources. Or better the patchprocess does not finish. How long does it normally take?

---

### Post by TabletGuy on 2008-08-10
> **searchforglory@web.de said:**
> Hi

I went step by step through the tutorial, but the patch is not applied to the mplayer sources. Or better the patchprocess does not finish. How long does it normally take?

You may have missed a < in the patch command. This is easy to do with the way the wiki has been written. The patch should only take a few seconds to apply.

The command to patch mplayer is:
patch -p0 < "path-to-coreavc-for-linux"/mplayer/dshowserver.patch

Also, the dshowserver.patch doesn't install cleanly against the current mplayer svn source code (as of mplayer svn revision 27448). To get mplayer to call dshowever I had to apply the patch and then manually edit libmpcodecs/vd.c

vd.c needs &mpcodecs_vd_dshowserver, added as follows:

```
#ifdef CONFIG_OGGTHEORA
	&mpcodecs_vd_theora,
#endif[B]
	&mpcodecs_vd_dshowserver,[/B]
#ifdef CONFIG_WIN32DLL
        &mpcodecs_vd_dshow,
        &mpcodecs_vd_dmo,
```

This is because the current mplayer svn has changed the call to CONFIG not USE. Once you add in this line you should be able to build mplayer so that playback starts.

---

### Post by searchforglory@web.de on 2008-08-16
@TabletGuy

big thx, worked fine

---

### Post by Nullack on 2008-08-18
No offence, but why do this? Your running windows binaries through an emulator slowing it all down when there is existing AVC and H.264 decoders that are native and pretty fast.

I have compiled optimised SVN builds of ffmpeg and mplayer. That decodes H264 well including PAFF, Gstreamer as well with Totem will do it without much of a difference in performance.

---

### Post by gladstone on 2008-08-23
I had a go at CoreAVC/compiling Mplayer and didn't finish it easily.

Are there any hints for improving h264/x264 performance without going through ugly compilation?

I'm currently reading through this [1080p HD content: terrible performance](http://ubuntuforums.org/showthread.php?t=670816) thread for ideas

---

### Post by gladstone on 2008-08-31
Thought I'd bring something else up: I copied the HD vid in question (Elephants Dream) to my external drive (SATA II going thru USB, can't remember any of the other specs) and it played absolutely fine with none of the stutters it had while on my internal laptop drive...

I guess I should be testing my I/O speed.

---

### Post by ifinishwhatistar on 2008-08-31
I too have followed this guide on hardy 64 bit, and dshowserver passes the test, mplayer seems to find and load the codec just fine, but when playing a movie, I also get a blank screen and mplayer hangs.

---

### Post by DuncanCedm on 2008-08-31
Some problem here

What steps will reproduce the problem?
1. I followed all insturctions
2. dshowserver test outputs correctly
3. mplayer svn patches nicely (using patch found in issues section of coreavc for linux website
4. mplayer builds nicely. 
5. mplayer from CLI runs with what look like happy output but I get sound and NO VIDEO.. Just black screen.

What is the expected output? What do you see instead?
If i run
 mplayer -demuxer lavf -vc coreserve -vo xv -fs working.mkv 
on a short (5 second) 720p test video i download i get a squak of sound the
screen flashes and then instantly its over..  Here is my output from that.

MPlayer dev-SVN-r27496-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15,
Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
128 audio & 258 video codecs

Playing working.mkv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
[lavf] Subtitle stream found, -sid 0
VIDEO:  [H264]  1280x688  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Paprika  (2006)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
shm:/dshow_shm.b5a3d760
sem1:/dshow_sem1.b5a3d760
sem2:/dshow_sem2.b5a3d760
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.7.0
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
VDec: vo config request - 1280 x 688 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
VO: [xv] 1280x688 => 1280x688 Planar YV12  [fs]
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver
(CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   0.4 V:   0.0 A-V:  0.353 ct:  0.000   0/  0 ??% ??% ??,?% 59 0 
************
framecount=0
************
Destroying filter
Exiting... (End of file)
duncan@blackbox:~/Desktop$ mplayer -demuxer lavf -vc coreserve -vo xv -fs
working.mkv 
MPlayer dev-SVN-r27496-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15,
Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
128 audio & 258 video codecs

Playing working.mkv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
[lavf] Subtitle stream found, -sid 0
VIDEO:  [H264]  1280x688  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Paprika  (2006)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
shm:/dshow_shm.b5a1f760
sem1:/dshow_sem1.b5a1f760
sem2:/dshow_sem2.b5a1f760
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.7.0
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
VDec: vo config request - 1280 x 688 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
VO: [xv] 1280x688 => 1280x688 Planar YV12  [fs]
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver
(CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   0.1 V:   0.0 A-V:  0.078 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
************
framecount=0
************
Destroying filter
Exiting... (End of file)


If i run the same mplayer command on a Huge 1080P file I get a black screen
but the correct sound and this output is waiting when i hit escape.

MPlayer dev-SVN-r27496-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15,
Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
128 audio & 258 video codecs

Playing Planet.Earth.02.Mountains.2006.1080p.HDDVD.x264-AJP.mkv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
[lavf] Subtitle stream found, -sid 0
VIDEO:  [H264]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
shm:/dshow_shm.b5a43760
sem1:/dshow_sem1.b5a43760
sem2:/dshow_sem2.b5a43760
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.7.0
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
VDec: vo config request - 1920 x 1080 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x8da2170]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 1920x1080 => 1920x1080 BGRA  [fs]
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver
(CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...






What version of the product are you using? On what operating system?
Gutsy Gibbson. Ubuntu 8.04
Coreacv 1.7.0
mplayer svn as of Aug 29 08



Any ideas how I'm getting no errors but I can't see any video?

---

### Post by Nullack on 2008-09-09
Linux lacks GPU acceleration for video decoding for AVC / H.264.

If you dont want to compile, easiest is to use totem with the gstreamer backend and install the following gstreamer plugins:

good
bad
ugly
Including all multiverse variants
ffmpeg plugin

Then you will have a working AVC/H.264 decoder that is faster than CoreAVC through WINE.

---

### Post by nirdo on 2008-09-11
Hi,

Having trouble compiling the source code. Did everything in [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538) . used ./configure and then make. See compilation errors:

swscale.c: In function 'yuv2rgbXinC_full':
swscale.c:808: error: 'SwsContext' has no member named 'oy'
swscale.c:808: error: 'SwsContext' has no member named 'cy'
swscale.c:808: error: 'SwsContext' has no member named 'cvr'
swscale.c:808: error: 'SwsContext' has no member named 'cvg'
swscale.c:808: error: 'SwsContext' has no member named 'cug'
swscale.c:808: error: 'SwsContext' has no member named 'cub'
swscale.c:820: error: 'SwsContext' has no member named 'oy'
swscale.c:820: error: 'SwsContext' has no member named 'cy'
swscale.c:820: error: 'SwsContext' has no member named 'cvr'
swscale.c:820: error: 'SwsContext' has no member named 'cvg'
swscale.c:820: error: 'SwsContext' has no member named 'cug'
swscale.c:820: error: 'SwsContext' has no member named 'cub'
In file included from swscale.c:909:
swscale_template.c: In function 'yuv2yuv1_MMX2':
swscale_template.c:995: warning: initialization from incompatible pointer type
swscale_template.c:995: warning: initialization from incompatible pointer type
swscale_template.c:995: warning: initialization from incompatible pointer type
swscale_template.c: In function 'rgb24ToUV_MMX2':
swscale_template.c:2089: warning: unused variable 'i'
swscale_template.c: In function 'swScale_MMX2':
swscale_template.c:3087: warning: cast from pointer to integer of different size
swscale_template.c:3095: warning: cast from pointer to integer of different size
swscale.c: In function 'sws_setColorspaceDetails':
swscale.c:1956: error: 'SwsContext' has no member named 'cy'
swscale.c:1957: error: 'SwsContext' has no member named 'oy'
swscale.c:1958: error: 'SwsContext' has no member named 'cvr'
swscale.c:1959: error: 'SwsContext' has no member named 'cvg'
swscale.c:1960: error: 'SwsContext' has no member named 'cug'
swscale.c:1961: error: 'SwsContext' has no member named 'cub'
swscale.c: In function 'sws_getCachedContext':

---

### Post by Vietman on 2008-09-29
What does export REGISTRY actually do? I tried both these options:

option 1: If you are using dshowserver (for mythtv) do:
export REGISTRY=$HOME/.mplayer/registry32

option 2: If you are using mplayer or xine do:
export REGISTRY=$HOME/.mplayer/registry

And then this but with my key:

then do this: (for coreavc v1.7)
registercodec -r $REGISTRY -k
"HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "55555-55555-CORE-55555-55555"

It doesn't seem to work for me. I still get an error that there is no serial number.

Do I need a windows installation to export registry?

---

### Post by DCJuggler on 2008-11-15
Hi Guys,

Could someone help me?

When i try to import the key from the registry it tells me

Must specify '-r' and either '-k' or '-l'

And i cant get anywhere =/

---

### Post by nirdo on 2008-11-24
Hi DCJuggler,
Did you export REGISTRY=$HOME/.mplayer/registry32  , before invoking registercodec? 
The error message you're getting is returned when REGISTRY is not defined

---

### Post by ArchangelUriel on 2008-11-25
Firstly it's better not to split the commands in two line. Use it like this:

```
registercodec -r $REGISTRY -k "HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "55555-55555-CORE-55555-55555"
```

Secondly (and most importantly) "55555-55555-CORE-55555-55555" is not a **valid** CoreAVC key. You must use your own key. To find your key type
```
regedit
```

The Windows Registry Editor will open. Then go to HKEY_LOCAL_MACHINE\Software\CoreCodec\CoreAVC Pro and copy the value of Serial. This is your valid CoreAVC key. After that, try the above command, using your own key (quotas included). 

As for mplayer arguments, I use

```
-softvol-max 5000 -cache 30000 -autosync 30 -fs -zoom -quiet -monitoraspect 16:10 -lavdopts threads=2:fast:skiploopfilter=all -noslices -sws 0 -vc coreserve
```

-vc coreserve  -> Makes mplayer to use CoreAVC
-softvol-max   -> Give you sound amplify (x50)
-cache         -> Precaches 30MB for better fps
-autosync      -> Auto resync A/V
-fs            -> To have fullscreen
-zoom          -> To have proper fullscreen
-quiet         -> No output
-monitoraspect -> Sets the monitor aspect
-lavdopts threads=2:fast:skiploopfilter=all -> Read the man for more
-noslices      -> try it out. Sometimes gives better fps, sometimes not.

I use these to gnome-mplayer in a Turionx2 TL52 (1.6 GHz), 2 GB Ram, GForce Go 7300 and I can get 1080p with under 60% CPU usage.

---

### Post by tripmix on 2009-01-26
Thanks, just did this on my 64bit. Download codec pack, extract with wine. Copy codec and reg-key, patch mplayer, install, edit config. Pretty strait forward if you ask me. Playback is much better now. 

Here are a few options I use for smoother playback:  If you got an external sound system and hook it up whit spdif "-ao alsa:device=spdif" this makes your external audio receiver decode the audio giving your cpu less work.

Got an opengl compatible screencard? "-vo gl" or "-vo gl2" makes your videocard take some of the load of your cpu.

Now I can play 1080p content smoothly on my 3800+ 64 X2 AMD Athlon. 

Your guide could be a little shorter though:

download codec and keyg*n from torrent site
wine coreavc_professional_edition-setup.exe
wine keyg*n.exe
finish install, save key to text file. 
cp $HOME/.wine/drive_c/Program\ Files/CoreCodec/CoreAVC\ Professional\ Edition/CoreAVCDecoder.ax /usr/lib/win32/
download and extract  [http://code.google.com/p/coreavc-for-linux/downloads/list](http://code.google.com/p/coreavc-for-linux/downloads/list)
cp dshowserver /usr/local/bin
cp ../loader/registercodec /usr/local/bin
export REGISTRY=$HOME/.mplayer/registry32
registercodec -r $REGISTRY -k "HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "your-key-here"
thats why I made you save it, you can just generate a new one though.
run "dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449" to make sure it worked, valid output should end in "Starting, Initialization is complete"

Mplayer:
svn checkout [http://coreavc-for-linux.googlecode.com/svn/trunk/](http://coreavc-for-linux.googlecode.com/svn/trunk/) coreavc-for-linux 
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cp coreavc-for-linux/mplayer/* .
cd mplayer
patch -p0 < ../dshowserver.patch
./configure
make
make install

cp etc/codec.conf ../.mplayer
add:
videocodec coreserve
  info "Whatever 8.0 x86_64"
  status working
  format 0x10000005
  fourcc H264,h264 H264
  fourcc X264,x264
  fourcc avc1,AVC1 AVC1
  fourcc davc,DAVC
  fourcc VSSH
  driver dshowserver
  dll "CoreAVCDecoder.ax"
  guid 0x09571a4b, 0xf1fe, 0x4c60, 0x97, 0x60, 0xde, 0x6d, 0x31, 0x0c, 0x7c, 0x31
  out YV12,IYUV,I420,YUY2

to .mplayer/codec.conf
Done.

If you want you can add something like this to .bashrc
alias play='/usr/bin/mplayer -nojoystick -nolirc -msgcolor -vo gl -fs -zoom'
alias hd-play='/usr/local/bin/mplayer -nojoystick -nolirc -fs -ao alsa:device=spdif -vo gl -vc coreserve -nocorrect-pts'

This way the command "play" plays files using your apt-get mplayer while "hd-play" uses the one you just made. Note the commands above is an example I just copied from my bashrc, you might want/need diffrent options. You need to run "source $HOME/.bashrc" for the aliases to take effect, bash autocompletion work whit aliases and more flags can still be added on the commandline, example "play -playlist playlistfile"

Thanks for this very useful guide OP!

---

### Post by sirganya on 2009-01-26
Does anybody know if its possible to route the video through the framebuffer? The ivtv one?

I get "cannot find codec matching selected -vo and video format"

I'm thinking it might not be configured to allow the use of the framebuffer for the coreserv codec?

Any ideas?

Thanks for a great thread...

---

### Post by tripmix on 2009-01-27
Can't say I really understand what you mean? But if your talking about the ivtv mpeg4 decoder from a TV-card that will only be able to decode mpeg streams. High end video-cards have native x264 decoding, but only in win. If you are taking about the regular framebuffer ie: -vo fbdev, the question would be why?? If your box is to slow to run X there is no way you'll ever get high-def output. What happens if you use xv, x11 or gl? What kind of file are you trying to play?

EDIT: if you have a TV-card with native x264 decoding capabilities I don't see why not, but I only have a old WinTV card so I don't know how.Maybe -vo mpegpes

---

### Post by sirganya on 2009-01-27
Hey,

I'm using the PVR-350 and wanted to see if i could route the video out through its s-video. At the moment x uses the ivtv fb to output everything so I'm assuming it can show the coreavc output unless the coreavc is locked to its native resolution.

---

### Post by Macdelaney on 2009-02-12
CoreAVC is in version 1.9 now, any ideas on how to make that work?
I keep gettin the following error 

```

[mac@arch-desktop bin]$ ./dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
No id specified, assuming test mode
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.0
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete

```

Any ideas on what does that error mean???

---

### Post by johndoe20081026 on 2009-02-13
you need to have nvcuvid.dll file in /usr/lib/win32
I was able to find it here
[http://forum.doom9.org/archive/index.php/t-144867.html](http://forum.doom9.org/archive/index.php/t-144867.html)

here's the direct link from the forum to the package containing a working version of nvcuvid.dll:
[http://neuron2.net/dgmpgdecnv/dgmpgdecnv100b.zip](http://neuron2.net/dgmpgdecnv/dgmpgdecnv100b.zip)

---

### Post by regneva on 2009-09-09
I followed this guide. Now I have the following error when I run mplayer and no video appears "Error opening/initializing the selected video_out (-vo) device."

Any idea how to fix this? I tried -vo x11/xv/gl/xvidix. Did not help.

---

