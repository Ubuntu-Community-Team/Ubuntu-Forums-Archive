---
title: "64 bit Ubuntu can not play MSS2 video encoded WMV files?"
date: 2011-03-12
forum: Multimedia Software
---

### Post by focaccio on 2011-03-12
Hello,

I'm running 64 bit Maverick.  

I am able to play some WMV files fine...those with video encoded as: WMV1
...but, I am not able to play WMV files when the video is encoded as: MSS2

Help.  How do I play these files?  Can someone share a proven method to transcode the files?

I play them fine in an XP VM with VMWare Player, but I would much rather play them natively.

Why can't 64 bit Ubuntu play MSS2 encoded WMV files?

I've encluded some terminal output to make matters clear:

When it works:
```
root@55KG:/buffer# mplayer works1.wmv
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing works1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV1]  800x600  24bpp  1000.000 fps   74.6 kbps ( 9.1 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv1] vfm: ffmpeg (FFmpeg WMV1/WMV7)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 800x600 => 800x600 Planar YV12 
A: 341.2 V: 341.2 A-V:  0.010 ct:  0.106 216/216  0%  0%  0.2% 0 0 
Exiting... (Quit)
```

When it does NOT work:
```
root@55KG:/buffer# mplayer problem1.wmv
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing problem1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x600  24bpp  1000.000 fps   19.8 kbps ( 2.4 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Requested video codec family [wmsdmod] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wms10dmod] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x3253534D.
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, floatle, 20.0 kbit/2.83% (ratio: 2500->88200)
Selected audio codec: [ffwmavoice] afm: ffmpeg (WMA Voice audio (FFmpeg))
==========================================================================
AO: [pulse] 22050Hz 1ch floatle (4 bytes per sample)
Video: no video
Starting playback...
[wmavoice @ 0x25433f0]WMAPro-in-WMAVoice support not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.If you want to help, upload a sample of this file to ftp://upload.ffmpeg.org/MPlayer/incoming/ and contact the ffmpeg-devel mailing list.        
A:  11.7 (11.7) of 2047.5 (34:07.4)  1.0% 

MPlayer interrupted by signal 2 in module: play_audio
A:  11.8 (11.7) of 2047.5 (34:07.4)  1.0% 
Exiting... (Quit)
```

Any further information on this is much appreciated.

Thanks,
Greg

---

### Post by andrew.46 on 2011-03-12
Hi Greg,

The problem you are encountering is that MPlayer uses either wmsdmod.dll or wms10dmod.dll to playback these files, details [here]("ftp://ftp2.mplayerhq.hu/MPlayer/DOCS/codecs-status.html"). These codecs are only available under 32 bit installations of MPlayer unfortunately. Test example here:

```
wget http://samples.mplayerhq.hu/V-codecs/MSS2/intro_windows.wmv
```

plays on a 32 bit system as follows:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer intro_windows.wmv [/COLOR]**
MPlayer SVN-r33076-4.5.2 (C) 2000-2011 MPlayer Team

Playing intro_windows.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x548  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8fa0fc0] BICUBIC scaler, from bgra to yuv420p using MMX2
VO: [xv] 800x548 => 800x548 Planar YV12 
**[COLOR="Red"]Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
A: 109.3 V: 109.1 A-V:  0.168 ct: -0.047 642/642  8%  5%  0.2% 0 0 


Exiting... (End of file)

```

It is possible I believe to compile a 32 bit MPlayer on a 64 bit system but I am unsure of the exact steps...

Andrew

---

### Post by focaccio on 2011-03-13
Thanks Andrew.  I appreciate your well informed answer, even though it is not the answer I was hoping for.

I guess there was just not enough demand?

It'll be easier for me to watch in the VM than to compile a 32bit player, so I'll stick with that for now.

Thanks Again!

Greg

---

### Post by zibou76 on 2011-03-15
hello, 
i have the same problem with some cbt nuggets video i'm trying to watch on maverick 64 bit. i got all codecs installed and when i issue: **mplayer -vc help** it shows that **wmsdmod **is working. but smplayer play only sound no video. 

my solution was to go back to win 7 convert them with movie maker and then play them on ubuntu, only problem is that a 13 mb file with mss2 is now 80 + with mp4.

---

### Post by lz1dsb on 2011-04-23
I've got exactly the same issue here. I'm running 64-bit Karmic Koala...

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-30
yesterday i installed Ubuntu 11.04 32bit version and i got the same problem

so how to fix it !

---

### Post by minijoe on 2011-05-03
Same here Lucid 64bit. The MSS2 file was playing fine with Karmic 32bit before I upgrade to Lucid 64bit.

---

### Post by sumith_p on 2011-07-02
Me also having the same issue...only audio in gm player,smplayer,vlc.....no video
I was actually trying to play cbt nuggets video...which is in .wmv format..
my system is 64 bit ubuntu 11.04..
wat to do..?

---

### Post by andrew.46 on 2011-07-03
> **&#1581 said:**
> yesterday i installed Ubuntu 11.04 32bit version and i got the same problem

so how to fix it !

On a 32bit installation of MPlayer you should be able to install the so-called win32codecs from Medibuntu and this will allow playback of the file. No such luck for 64bit users I am afraid :(.

---

### Post by sumith_p on 2011-07-04
Thanks..andrew...
I installed ubuntu 10.10 32 bit....now i am able to play the wmv file....

---

### Post by Fitzcarraldo on 2011-07-15
It is possible to play MSS2 codec encoded WMV files in 64-bit Linux but using SMPLayer for Windows (FOSS, of course) running under WINE. See my blog post: [How to play MSS2 codec (Windows Media Video 9 Screen) .wmv files in 64-bit Linux](http://fitzcarraldoblog.wordpress.com/2011/07/13/how-to-play-mss2-codec-windows-media-video-9-screen-wmv-files-in-64-bit-linux/) for details.

---

### Post by sumith_p on 2011-07-15
Great&#8230;!!!!! its working &#8230;.
Thanks alot&#8230;.
During installation we need to include the binary codecs&#8230;.then it will  download the windows codecs automatically during installation..
once again thank you&#8230;.

---

### Post by ecuasteelo on 2011-08-17
Hello Folks.

I'm glad I came across this thread and to read that some of you have been successful in getting CBT Nuggets to play on your box.

I have Ubuntu 10.10 and have tried to follow all the instructions on the several of websites scattered online without success.

Can you please layout the instruction on getting it to work on a 32bit system? This is the only thing that is holding be back from going 100% Ubuntu.

Thank you in advance.

---

### Post by sumith_p on 2011-08-18
> **ecuasteelo said:**
> Hello Folks.

I'm glad I came across this thread and to read that some of you have been successful in getting CBT Nuggets to play on your box.

I have Ubuntu 10.10 and have tried to follow all the instructions on the several of websites scattered online without success.

Can you please layout the instruction on getting it to work on a 32bit system? This is the only thing that is holding be back from going 100% Ubuntu.

Thank you in advance.
Download smplayer from ubuntu software centre....

Then u need to download a package from medibuntu called w32codecs....For medibuntu check out the following link....

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)....

by doing this new repository named medibuntu will added to your software centre....

then download the w32codecs from there...

Then u should be able to play the video file using smlayer....in ubuntu itself

---

### Post by ecuasteelo on 2011-08-19
Thank you Sumith_p. I will give it a try and see if it works for me.

---

### Post by keithspg on 2012-04-01
You are kidding me?!? No respite for this? This is a big issue and an oversight. I want to and do use ubuntu on all my computers, I am running 11.10 x64. I cannot control what others do and now need to watch an educational video for work and cannot as it is in this format. I installed the medibuntu repo and smplayer. They still do not play. These should 'just play' in mplayer/xine or even vlc IMO. Why is this still unresolved?

---

### Post by andrew.46 on 2012-04-01
This issue was discussed recently on the MPlayer-users mailing list. Have a quick read of this thread for [the current issues]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2012-March/084380.html").

---

### Post by keithspg on 2012-04-01
I get it. Does anyone have another solution? If X64 linux cannot play these, can we install some viewer in wine and still view these? I tried VLC under wine and that did not work. WMP11 is too advanced, I guess, for Wine. I am certain that I will need to watch more of these for work.

Keith

---

### Post by ron999 on 2012-04-01
...

---

### Post by LinuxQuint on 2012-04-02
> **keithspg said:**
> You are kidding me?!? No respite for this? This is a big issue and an oversight. I want to and do use ubuntu on all my computers, I am running 11.10 x64. I cannot control what others do and now need to watch an educational video for work and cannot as it is in this format. I installed the medibuntu repo and smplayer. They still do not play. These should 'just play' in mplayer/xine or even vlc IMO. Why is this still unresolved?

HA ... I was looking for the same answer, reading the thread, looking at the dates, thinking, "it must be fixed by now".  Then I saw your post from yesterday.  OH NO, still no fix ..... 

Someone in another forum said those codecs could just be re-compiled for 64-bit, but I don't know how to do it.  

So yeah, I'd love to find a way to play MSS2 on my 64-bit box.  I installed w32codecs on my 32-bit box, and opened the videos in gnome-mplayer. They play fine.  

On my 64-bit box I tried the w32codecs which gave me w64codes, but I still can't watch the videos -- the audio works in most players, but no video.  I tried smplayer, vlc, gnome-mplayer, banshee, and kmplayer .... no video.  

Darn, I'm trying to go all Linux.  

Maybe my 32-bit box with Mplayer can re-encode them ... bad solution though. 

Or maybe I should use Wine, or just put them in an XP VM ... bad solutions though.

---

### Post by keithspg on 2012-04-05
I even tried SMplayer under wine.

[http://fitzcarraldoblog.wordpress.com/2011/07/13/how-to-play-mss2-codec-windows-media-video-9-screen-wmv-files-in-64-bit-linux/](http://fitzcarraldoblog.wordpress.com/2011/07/13/how-to-play-mss2-codec-windows-media-video-9-screen-wmv-files-in-64-bit-linux/)

this is mentioned above as well. My version of oneric does not go back as far as 3.27 wine. I even updated to the latest wine. 1.4. It fixes a problem I was having with office, but crashes SMplayer on this file as well. Just in a different way. 

I installed the latest SMPlayer 0.8 and latest wine. Still sound with no video and a crash. mplayer.exe continues to play, but the frontend is dead. It almost plays, but not quite, as if I wait with the crash dialog box open, I see some of the video until I close it.

---

### Post by keithspg on 2012-05-08
not a member of winehq, yet, but tried this again today. Latest ubuntu, latest wine, wine-1.5.3. latest smplayer 0.8.0. Same deal as under wine 1.4. It starts to play, then errors out. I grabbed the backtrace generated when it tries to play a file. It plays for a while then gets to a point and repeats the last couple seconds of audio over and over. It looks like it is playing behind the error window.

Keith

---

### Post by Fitzcarraldo on 2012-12-11
OK, for those of you who used the procedure I gave in [my blog post]("http://fitzcarraldoblog.wordpress.com/2011/07/13/how-to-play-mss2-codec-windows-media-video-9-screen-wmv-files-in-64-bit-linux/") and cannot see the video component and only hear the audio component of a .wmv file using MSS2, you need to do the following:

When you launch the SMPlayer 0.6.9 Setup program (wine smplayer-0.6.9-win32.exe) and click on Next and accept the Licence Agreement, make sure Binary Codecs (under MPlayer Components) is ticked.

When you launch SMPlayer for Windows and open the .wmv file, click on Options > Preferences to open the Preferences window. Click on General in the left pane, then click on the Video tab in the main pane and select &#8220;directx (fast)&#8221; or &#8220;directx(slow)&#8221; as the Output driver. I have just done this again (I&#8217;m currently using WINE 1.5.18) and I&#8217;m watching a MSS2-encoded .wmv file &#8216;Kai_Software2.wmv&#8217; as I type this, as shown in the information listed by SMPlayer for Windows:

Kai_Software2.wmv
General
File H:/Kai_Software2.wmv
Size 3193 KB (3 MB)
Length 00:04:33
Demuxer asf

Video
Resolution 883 x 720
Aspect ratio 1.22639
Format MSS2
Bitrate 100 kbps
Frames per second 1000.000
Selected codec wmsdmod

Initial Audio Stream
Format 353
Bitrate 16 kbps
Rate 22050 Hz
Channels 1
Selected codec ffwmav2

Audio Streams
# 0
Language
Name
ID 1

Just to recap:

$ cd
$ export WINEPREFIX="/home/fitzcarraldo/.wine-smplayer"
$ export WINEARCH="win32"
$ winecfg
$ cd /home/fitzcarraldo/.wine-smplayer/drive_c/
$ cp ~/Downloads/smplayer-0.6.9-win32.exe ~/.wine-smplayer/drive_c/
$ wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
$ chmod +x ./winetricks
$ ./winetricks # 'Select the default wineprefix' + OK first then 'Install a Windows DLL or component' + OK and tick 'allcodecs' and OK.
$ wine smplayer-0.6.9-win32.exe # Make sure Binary Codecs is ticked.

---

### Post by andrew.46 on 2012-12-11
Mind you there is an MSS2 decoder in FFmpeg / libavcodec now so rather than make everything too complicated it is just as easy on a 64bit system to get an updated MPlayer + SMPlayer or even a copy of vlc with the required update. The change went in here:

MSS2 decoder
[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=ee769c6a7c1d4ec6560f5e5a6f457b770b10fb33](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=ee769c6a7c1d4ec6560f5e5a6f457b770b10fb33)

and means that the mplayer intro_windows.wmv file plays with no issues on 64bit linux using ffmss2:

```

andrew@skamandros~/media/testing$ mplayer intro_windows.wmv 
MPlayer SVN-r35649-4.7.1 (C) 2000-2012 MPlayer Team

Playing intro_windows.wmv.
libavformat version 54.49.100 (internal)
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x548  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.79.101 (internal)
**[COLOR="Red"]Selected video codec: [ffmss2] vfm: ffmpeg (FFmpeg MS Screen 2)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, floatle, 32.0 kbit/2.27% (ratio: 4006->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x1031000]BICUBIC scaler, from rgb24 to yuv420p using MMXEXT
VO: [vdpau] 800x548 => 800x548 Planar YV12 
A:  16.7 V:  16.7 A-V: -0.005 ct: -0.043  71/ 71  1%  1%  0.1% 1 0 

Exiting... (Quit)

```

Good to see some sense of closure from this old thread btw :)

---

