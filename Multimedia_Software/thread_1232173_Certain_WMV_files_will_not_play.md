---
title: "Certain WMV files will not play"
date: 2009-08-05
forum: Multimedia Software
---

### Post by Buschbarber on 2009-08-05
I receive tons of emails and many of them have WMV files attached. I have had no problems playing them. Earlier this week, I received an email with a link to [http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv](http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv).

When I try to play this I receive an error that I need a Codec. It searches for one but does not find one. It refers to video/x-asf.

I have installed the Ubuntu-Restricted-Extras and the W32 files. I have tried VLC, Mplayer Movie Player, Movie Player, etc. I get the same error for all.

Somewhere I saw this type of file referred to as WVP2.

See attachment

---

### Post by andrew.46 on 2009-08-06
Hi Buschbarber,

> **Buschbarber said:**
>  Earlier this week, I received an email with a link to [http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv](http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv).

When I try to play this I receive an error that I need a Codec.

Can I say that I actually quite enjoy hunting down codecs :-). This one was not too hard, FFmpeg identifies the file as:

```

Input #0, asf, from 'TeaPartyCommercial.wmv':
  Duration: 00:03:59.90, start: 5.000000, bitrate: 279 kb/s
    Stream #0.0(eng): **[COLOR="Red"]Audio: wmav2[/COLOR]**, 44100 Hz, 2 channels, s16, 123 kb/s
    Stream #0.1(eng):**[COLOR="Red"] Video: WVP2[/COLOR]** / 0x32505657, 640x480, 16 kb/s, 30 tbr, 1k tbn, 1k tbc

```

and a little bit of homework identifies this particular video codec as 'Windows Media Video 9.1 Image V2'. This type of video can be played by MPlayer using the so-called w32codecs available from Medibuntu. I attach a screenshot of SMPlayer doing just that :-). I note also that vlc will also play this particular file although this is not so straightforward. It looks like vlc uses FFmpeg for the audio:

```

[0x8127048] main decoder debug: looking for decoder module: 34 candidates
[0x8127048] avcodec decoder debug: libavcodec initialized (interface 0x341400)
[0x8127048] avcodec decoder debug: **[COLOR="Red"]ffmpeg codec (Windows Media Audio 2) started[/COLOR]**
[0x8127048] avcodec decoder debug: Using 192000 bytes output buffer
[0x8127048] main decoder debug: using decoder module "avcodec"

```

and vlc needs to be compiled with the --enable-loader option as it uses the same external codec as MPlayer:

```

[0x8117cb0] main decoder debug: looking for decoder module: 34 candidates
[0x8117cb0] dmo decoder debug: **[COLOR="Red"]DMO codec for WVP2 may work with dll=wmvadvd.dll[/COLOR]**
[0x8117cb0] dmo decoder debug: DMO input type set
[0x8117cb0] dmo decoder debug: DMO output type set
[0x8117cb0] dmo decoder debug: GetOutputSizeInfo(): bytes 460800, align 1
[0x8117cb0] main decoder debug: using decoder module "dmo"

```

and I am not sure where you can get such a copy of vlc, perhaps mc4man could suggest an appropriately configured package? I suspect your best bet is a trip to Medibuntu for their copy of MPlayer and the w32codecs + SMPlayer. Anyway I attach another screenshot of vlc playing this little 'PhotoStory'!

All the best,

Andrew

---

### Post by Buschbarber on 2009-08-06
Thank you for your response. I am not very handy with Linux. I am running UE2.3 and I believe I have installed the W32 Codecs and the Medibuntu Repository. I just installed SMplayer and tried to open the file but it said I had an outdated version of Mplayer. Would the latest version be included in Synaptic or is there a better way to obtain the latest version?

If someone could post Step by Step instructions as to what code to type in to correct this problem, I should be able to follow them.

---

### Post by rvm4000 on 2009-08-06
The w32codecs can be found here:
[http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html)

The warning that smplayer shows about an old mplayer has nothing to do with playing wmv files.

Anyway you can find updated packages in my PPA:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by martinbaselier on 2009-08-06
Did you already follow this guide? 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mc4man on 2009-08-06
> suggest an appropriately configured package?
The ubuntu repo's don't enable the loader and unless recently added neither do any of the launchpad vlc ppa's.

Why I'm not sure
3 reasons come to mind

They don't realize they could, - both the korn and kow ppa's weren't enabling global hotkeys in vlc 1.0.x till it was requested of them recently.
(( Though in the case of global hotkeys it's not a configure option, enabled thru the build deps instead
So I'd think they know of the option --enable-loader

Maybe because it's only for a i386 build something about the repo and ppa build methods make it not possible to enable...? ( if need be would think it could be worked around 

For the ubuntu repo possibly it's seen as similar to enabling libdvdcss in mplayer which they can't do. Though in this case it's just enabling a module, no codecs are involved.

I'd suggest if you use a ppa and want dmo enabled ask the ppa owner to enable and see.
Or file a bug in launchpad against the repo vlc and see what the response is.

(( the loader works great in 0.9.9.x, remains somewhat broken in 1.0.1 and also in  1.1 as of a few weeks ago.

---

### Post by andrew.46 on 2009-08-06
Hi Buschbarber,

> **Buschbarber said:**
> Thank you for your response. I am not very handy with Linux. I am running UE2.3 and I believe I have installed the W32 Codecs and the Medibuntu Repository. 

Don't worry, we are all learning :-). There is a simple test to measure up your copy of MPlayer for this file, just run:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep dmo[/COLOR]**
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
**[COLOR="Red"]wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll][/COLOR]**
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]
gotomeeting dmo       working   GoToMeeting codec  [G2M.dll]

```

and this should show the codec that I have outlined in red. If it does *not* this will be the reason you cannot play this file.

Andrew

---

### Post by Buschbarber on 2009-08-06
> **andrew.46 said:**
> Hi Buschbarber,



Don't worry, we are all learning :-). There is a simple test to measure up your copy of MPlayer for this file, just run:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep dmo[/COLOR]**
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
**[COLOR="Red"]wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll][/COLOR]**
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]
gotomeeting dmo       working   GoToMeeting codec  [G2M.dll]

```

and this should show the codec that I have outlined in red. If it does *not* this will be the reason you cannot play this file.

Andrew

This is a copy of my output

wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile Decoder  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]

---

### Post by andrew.46 on 2009-08-06
Hi Buschbarber,

> **Buschbarber said:**
> This is a copy of my output

wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile Decoder  [wvc1dmod.dll]
wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]

Hmmm... well in theory then MPlayer *should* be able to play this file on your system. On my system this runs as follows:

```

andrew@skamandros~/html/andrews-corner/samples$ **[COLOR="Red"]mplayer TeaPartyCommercial.wmv [/COLOR]**
MPlayer SVN-r29476-4.2.4 (C) 2000-2009 MPlayer Team

Playing TeaPartyCommercial.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVP2]  640x480  24bpp  1000.000 fps   17.0 kbps ( 2.1 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
**[COLOR="Red"]Selected video codec: [wmvadmo] vfm: dmo (Windows Media Video Adv DMO)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 123.1 kbit/8.73% (ratio: 15392->176400)
**[COLOR="Red"]Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
A: 249.8 V: 250.5 A-V: -0.624 ct: -0.101 7365/7365 14%  1%  0.6% 0 0 

Exiting... (End of file)

```

Can you run the same command on your system and post the output here? This should show what the problem is.

Andrew

---

### Post by Buschbarber on 2009-08-07
rich@UE23:~$ cd Desktop
rich@UE23:~/Desktop$ mplayer TeaPartyCommercial.wmv
MPlayer SVN-r29325-4.3.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing TeaPartyCommercial.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVP2]  640x480  24bpp  1000.000 fps   17.0 kbps ( 2.1 kbyte/s)
==========================================================================
Requested video codec family [wmvadmo] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x32505657.
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 123.1 kbit/8.73% (ratio: 15392->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 121.2 (02:01.1) of 250.0 (04:10.0)  0.2% 
Exiting... (Quit)
rich@UE23:~/Desktop$

---

### Post by andrew.46 on 2009-08-08
Hi Buschbarber,

> **Buschbarber said:**
> ```

==========================================================================
Requested video codec family [wmvadmo] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x32505657.
==========================================================================
```

That seems to be the root of the problem then. Can I ask where this copy of MPlayer came from? Possibly it has been compiled with:

```
--disable-win32dll        disable Win32 DLL support [enabled]
```

Andrew

---

### Post by Buschbarber on 2009-08-08
I believe the version of Mplayer I have is the one that came with UE2.3, however, I reinstalled it from Synaptic.

I have attached a Snapshot of Synaptic.

How do I get the correct one installed?

---

### Post by andrew.46 on 2009-08-09
Hi Buschbarber,

> **Buschbarber said:**
> I believe the version of Mplayer I have is the one that came with UE2.3, however, I reinstalled it from Synaptic.

Unfortunately I know absolutely nothing about the 'Ultimate Edition' and in particular I am not sure how this edition interacts with 'standard' repositories. Does the 'Ultimate Edition' have a forum/mailing list/wiki where such questions can be asked?

If you *can* use the standard Ubuntu repositories and PPAs then certainly I suspect RVMs build would be the one to get, although building your own from svn would perhaps be even better.

Andrew

---

### Post by Buschbarber on 2009-08-09
Here is the forum for UE

[http://forumubuntusoftware.info/viewforum.php?f=64](http://forumubuntusoftware.info/viewforum.php?f=64)

I believe they use the std PPA's as well as others

I did post a thread on the Codec subject. I am not very adept at many Linux related things so it is easier if I get Step by Step instructions.

I am not familiar with RVM so I do not know where it is or how to install the Mplayer from there.

Here is my post on the UE2.3 fourm

[http://forumubuntusoftware.info/viewtopic.php?f=64&t=3550](http://forumubuntusoftware.info/viewtopic.php?f=64&t=3550)

---

### Post by Buschbarber on 2009-08-09
I did a Google Search for Mplayer and RVM.

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

I executed this command in Terminal

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

I assume this just downloaded Source Code and I have to take further steps. I am not good at interpreting this stuff.

---

### Post by rvm4000 on 2009-08-09
Hi, I'm RVM ;)

This is my PPA with a recent version of mplayer:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Actually there's another one with even a more recent version:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by Buschbarber on 2009-08-09
> **rvm4000 said:**
> Hi, I'm RVM ;)

This is my PPA with a recent version of mplayer:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Actually there's another one with even a more recent version:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

OK!! I selected the Testing site. I added each source to System/Administration/Software Sources and then I ran the command to Authenticate the Key.

I looked in Synaptic for Mplayer. V2 was installed and there was a v3 that I tried to Upgrade to I received an error that something was missing.

See attachments

---

### Post by mc4man on 2009-08-09
Are you using a 64 bit install and attempting playback that requires the use of a win32 codec?

If so there are 2 workarounds I know will work, one that's been suggessted but I've not tried or seen confirmation of

What works
build and or install a 32bit mplayer and w32codecs in your 64 bit install

Download and extract to a folder the windows 32 mplayer (there is one available that requires no installation, just unpacking), dl the win32 codecs and place in the codecs folder in the above folder containing mplayer.exe, run mplayer.exe thru wine

While the above works it's better suited for locally stored files

It's been suggested to place the 32bit codecs in /usr/lib32/ (either from the win32codecs from mplayer site or extracting from a w32codec deb
don't see how that would work thru a 64 bit mplayer but have never tried so ....?

---

### Post by Buschbarber on 2009-08-09
I am running UE2.3 64bit. I believe I have both the W32 and W64 codecs installed.

Is there a separate 32bit and 64bit version of Mplayer? If so, I do not know which one I have.

---

### Post by rvm4000 on 2009-08-09
> **Buschbarber said:**
> OK!! I selected the Testing site. I added each source to System/Administration/Software Sources and then I ran the command to Authenticate the Key.

I looked in Synaptic for Mplayer. V2 was installed and there was a v3 that I tried to Upgrade to I received an error that something was missing.

See attachments

The missed libraries are available here:
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

Anyway I think you should have said in the first place that you were running a 64bit OS.

I'm afraid the w32codecs won't work with a 64bit mplayer. There's a w64codecs package but it only provides a few codecs, I think none for wmv.

One solution would be to compile mplayer in 32bit mode. I've never done (I'm also running 64bit) but it's explained in the mplayer documentation.

---

### Post by Buschbarber on 2009-08-09
This whole thread got started because I received the following link in an email

[http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv](http://d.yimg.com/kq/groups/15523565/1322781786/name/TeaPartyCommercial.wmv)

The video is a good one and I could not open it except in Windows. I wanted to make sure that if I received any more like this that I could open them.

What is it about this WMV file that is different than all the others I have received that play with no problem? Is this file only written for a 32bit player?

---

### Post by mc4man on 2009-08-09
> What is it about this WMV file that is different than all the others ....

In a nutshell, that format is not supported by ffmpeg and it's libraries. Most players use the ffmpeg libs one way or the other (built-in or system)

So if ffmpeg doesn't support the format, then the player must 'look' elsewhere for a decoder, in this particular case to win(w)32codecs.

There is no wmv, wma codecs of any sort in w64codecs, and most likely won't be

---

### Post by rvm4000 on 2009-08-10
From the [mplayer FAQ](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2982225):

> 
**Q:** How can I build a 32 bit MPlayer on a 64 bit Athlon? 

**A:** Try the following configure options: 
```

./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --with-extralibdir=/usr/lib

```


---

### Post by Buschbarber on 2009-08-10
What directory do I need to be in? I am getting the following error:

rich@UE23:~$ ./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --with-extralibdir=/usr/lib
bash: ./configure: No such file or directory
rich@UE23:~$

---

### Post by rvm4000 on 2009-08-10
You need to download the source code of mplayer, uncompress it and run that command in the directory with the sources.

I think you said on a [previous post](http://ubuntuforums.org/showpost.php?p=7757796&postcount=15) that you already downloaded the sources, so you'll probably have a *mplayer* folder with the source code.

So type something like this:
```

cd mplayer
./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --with-extralibdir=/usr/lib
make

```

---

### Post by Buschbarber on 2009-08-10
I received another error when trying as you suggested:

rich@UE23:~$ cd mplayer
rich@UE23:~/mplayer$ ./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --with-extralibdir=/usr/lib
Unknown parameter: --with-extralibdir=/usr/lib
rich@UE23:~/mplayer$ 

Perhaps the Mplayer in my Home folder is not the correct one?

By the way!! Where do the list of applications appear that you install using Winetricks? I do not see Firefox 3.5 anywhere.

---

### Post by rvm4000 on 2009-08-10
> **Buschbarber said:**
> I received another error when trying as you suggested:

rich@UE23:~$ cd mplayer
rich@UE23:~/mplayer$ ./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --with-extralibdir=/usr/lib
Unknown parameter: --with-extralibdir=/usr/lib
rich@UE23:~/mplayer$ 

It seems the option --with-extralibdir has been renamed to --libdir. So try with *./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --libdir=/usr/lib* instead.

Edit:
This post explains how to compile a 32 bit mplayer on a 64 bit system:
[http://ubuntuforums.org/showthread.php?p=4891266#post4891266](http://ubuntuforums.org/showthread.php?p=4891266#post4891266)

Another possibility (maybe easier) would be to install a 32 bit package of mplayer. This may help you:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by mc4man on 2009-08-10
Did a 32 bit mplayer build on a jaunty 64 bit live cd this evening and while it certainly works is a bit of a pita and to me hardly worth the effort for a few codecs.
(( the more useful dmo wma3(pro) can be patched into a 64 bit install.

Some of it was a bit frustrating and some still a bit of a mystery. (adding add. 'optional drivers'

I can give you a few observations, tips..?

this is a must do first
```
sudo apt-get install ia32-libs libc6-dev-i386 g++-multilib
```

This doesn't hurt
```
cd /usr/lib32 && ln -s libX11.so.6 libX11.so

```


This was the configure I settled on
```
CC="gcc -m32" ./configure --disable-runtime-cpudetection --target=i686-linux --libdir=/usr/lib32 --prefix=/usr/local --win32codecsdir=/usr/lib32/win32


```

Note that --win32codecsdir=/usr/lib32/win32 reflects a folder link (win32) I created that links to where I put the win32codecs (( created a dir. in /usr/lib32 named codecs, extracted the codecs there
You could actually just point to them dirctly

The results of first configure (note all the disabled codecs
> 
Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 libdvdcss(internal) dvdread(internal) vcd dvb network 
    Codecs: libavcodec(internal) qtx real xanim win32 faad2(internal)  libmpeg2(internal) liba52(internal) mp3lib(internal)  tremor(internal) libmad liblzo 
    Audio output: alsa openal jack pulse nas esd oss v4l2 mpegpes(dvb) 
    Video output: v4l2 dxr3 pnm jpeg png mpegpes(dvb) fbdev svga xvidix cvidix opengl vdpau xv x11 xover yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: vstream radio tv-dshow nemesi cddb cdda smb 
    Codecs: libdirac x264 xvid libschroedinger libdv libdca libopencore_amrwb libopencore_amrnb faac musepack speex libtheora toolame twolame gif 
    Audio output: sun arts ivtv dxr2 sdl 
    Video output: zr zr2 ivtv dxr2 sdl vesa gif89a caca aa ggi xmga mga winvidix 3dfx dga xvmc dfbmga directfb bl xvr100 tdfx_vid wii s3fb tdfxfb 


The results of the final configure (I gave up on a few, for some reason couldn't retrieve the i386 amr packages from smplayer repo

> Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 libdvdcss(internal) dvdread(internal) vcd dvb network 
    Codecs: libschroedinger libdirac x264 xvid libdv libavcodec(internal) qtx real xanim win32 faad2(internal) libdca libmpeg2(internal) liba52(internal)  
    mp3lib(internal) libtheora speex tremor(internal) libmad liblzo 
    Audio output: alsa openal jack pulse nas esd oss v4l2 mpegpes(dvb) 
    Video output: v4l2 dxr3 pnm jpeg png mpegpes(dvb) fbdev svga xvidix cvidix opengl vdpau xv x11 xover yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: vstream radio tv-dshow nemesi cddb cdda smb 
    Codecs: libopencore_amrwb libopencore_amrnb faac musepack toolame twolame gif 
    Audio output: sun arts ivtv dxr2 sdl 
    Video output: zr zr2 ivtv dxr2 sdl vesa gif89a caca aa ggi xmga mga winvidix 3dfx dga xvmc dfbmga directfb bl xvr100 tdfx_vid wii s3fb tdfxfb 

To add more i386 libraries I went with this, (couldn't figure out what this new ia32 apt-get was about, below worked fine

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Ex. of adding
```
getlibs -p libx264-65 libx264-dev libxvidcore4-dev libxvidcore4
 
```

After adding libs whether needed or not I ran this script followed by sudo ldconfig
[http://ubuntuforums.org/showthread.php?t=977064](http://ubuntuforums.org/showthread.php?t=977064)

The reason was because mplayer never would find the newly added libs, tried the above, and still wouldn't find.
Ran make distclean and still wouldn't find

Finally deleted the source, checked out a new one, ran the configure and mplayer suddenly found them.

Added a few more, same thing, once the source had been configured no more newly added libs would be found (that's the mystery
So got all the libs, **then a new svn source**, linked them even if not needed and configured, then built

Works fine, seems to work ok with the 64 bit smplayer, though only tried some audio files

> ubuntu@ubuntu:~$ mplayer ~/wl.wma -ao alsa 
MPlayer SVN-r29485-4.3.3 (C) 2000-2009 MPlayer Team

Playing /home/ubuntu/wl.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Have You Ever Loved a Woman
 author: Derek & the Dominos
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 1152.0 kbit/81.63% (ratio: 144000->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...



---

### Post by Buschbarber on 2009-08-11
> **rvm4000 said:**
> It seems the option --with-extralibdir has been renamed to --libdir. So try with *./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --libdir=/usr/lib* instead.

Edit:
This post explains how to compile a 32 bit mplayer on a 64 bit system:
[http://ubuntuforums.org/showthread.php?p=4891266#post4891266](http://ubuntuforums.org/showthread.php?p=4891266#post4891266)

Another possibility (maybe easier) would be to install a 32 bit package of mplayer. This may help you:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Still getting errors:

rich@UE23:~$ cd mplayer
rich@UE23:~/mplayer$ ./configure --target=i386-linux --cc="gcc -m32" --as="as --32" --libdir=/usr/lib
Detected operating system: Linux
Detected host architecture: i386
Checking for gcc -m32 version ... 4.3.3 
Checking for host cc ... gcc -m32 
Checking for cross compilation ... yes 
Checking for CPU vendor ... GenuineIntel (6:23:10) 
Checking for CPU type ...  Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of ssse3 ... failed 
It seems that your kernel does not correctly support ssse3.
To use ssse3 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
i386 
Checking for byte order ... failed to autodetect byte order, defaulting to little-endian 
Checking for extern symbol prefix ...  
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as --32 ) ... ok 
Checking for .align is a power of two ... no 
Checking for 10 assembler operands ... no 
Checking for yasm ... no 
Checking for bswap ... yes 
Checking for Linux kernel version ... 2.6.28-14-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... messages: en - man pages: en - documentation: en 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for llrint ... no 
Checking for log2 ... no 
Checking for lrint ... no 
Checking for lrintf ... no 
Checking for round ... no 
Checking for roundf ... no 
Checking for truncf ... no 
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for arpa/inet.h ... no 
Checking for inet_pton() ... no 
Checking for inet_aton() ... no 
Checking for socklen_t ... no 
Checking for closesocket() ... no 
Checking for network ... no 
Checking for inet6 ... no 
Checking for gethostbyname2 ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

Check "configure.log" if you do not understand why it failed.
rich@UE23:~/mplayer$

---

### Post by roharme on 2009-08-11
Missing Codecs
 
Download VLC. VLC implements software codecs.So all videos.musics should play.
 
But
 
sudo apt-get install vlc
sudo apt-get install xmms
are not working now. :(
 
need to visit the website.

---

### Post by andrew.46 on 2009-08-11
Hi roharme,

> **roharme said:**
> Missing Codecs
 
Download VLC. VLC implements software codecs.So all videos.musics should play.

You may have missed a post or 2 of this discussion I suspect :-). Try the following file:

```
wget http://andrews-corner.org/samples/TeaPartyCommercial.wmv
```

and you may find that the repository vlc will choke on this:

```

Input #0, asf, from 'TeaPartyCommercial.wmv':
Duration: 00:03:59.90, start: 5.000000, bitrate: 279 kb/s
Stream #0.0(eng): Audio: wmav2, 44100 Hz, 2 channels, s16, 123 kb/s
Stream #0.1(eng): Video: WVP2 / 0x32505657, 640x480, 16 kb/s, 30 tbr, 1k tbn, 1k tbc

```

Andrew

---

### Post by mc4man on 2009-08-11
I'm dumping this live cd, but a final note. Managed to get the amr stuff enaabled.
It appears you need to have the 64 bit libs installed first, then get the i386 libs, link, configure a **fresh** mplayer source and build
(( don't get why make distclean isn't allowing new libs to be found, maybe a live cd thing...?

> Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 libdvdcss(internal) dvdread(internal) vcd dvb network 
    Codecs: libschroedinger libdirac x264 xvid libdv libopencore_amrwb libopencore_amrnb libavcodec(internal) qtx real xanim win32 faad2(internal) libdca libmpeg2(internal) liba52(internal) mp3lib(internal) libtheora speex tremor(internal) libmad liblzo 
    Audio output: alsa openal jack pulse nas esd oss v4l2 mpegpes(dvb) 
    Video output: v4l2 dxr3 pnm jpeg png mpegpes(dvb) fbdev svga xvidix cvidix opengl vdpau xv x11 xover yuv4mpeg md5sum tga 

Tested with some more audio and video files, works fine either command line or thru smplayer(64 bit

---

### Post by Buschbarber on 2009-08-11
> **roharme said:**
> Missing Codecs
 
Download VLC. VLC implements software codecs.So all videos.musics should play.
 
But
 
sudo apt-get install vlc
sudo apt-get install xmms
are not working now. :(
 
need to visit the website.

VLC came with UE2.3 as one of many preinstalled apps.

---

