---
title: "How to convert wma to mp3"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Tholley on 2009-06-06
I am using 9.04 and have been experimenting with different media players. My Rythmbox
stopped playing anything, so I have tried Amarok, Quod Libet, Exaile and now Songbird, which I like the best since it has allot of versatility I like.

Anyway I realized it won't play my wma files, I converted a couple of songs to Ogg, but Songbird won't play them either. It seems it will play mp3 and itunes only. The "wma add-on" seems to be for Windows only. 

So I'm thinking of just converting all wma to mp3, (something funny... when I searched "convert wma" in _Ubuntu_ Support Documents, it showed several Google ads for what I was looking for, but they are all for Windows!) so does this sound logical and if so, is there an apt that will do the job. And hopefull not one song at a time like the OggConvert.

---

### Post by logos34 on 2009-06-06
Amarok (using xine engine) and Audacious (with -plugins) can both playback wma files.  I thought for Rhythmbox all you needed was [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats/#Ubuntu%209.04%20(Jaunty%20Jackalope)") and maybe w32codecs (-->[Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo).

Avoid transcoding them if possible (unless you need/want tag edit capability)...degrades the sound.

---

### Post by mastermindg on 2009-06-06
VLC can transcode anything include WMA when use with the DMO codecs.

---

### Post by Tholley on 2009-06-06
> **logos34 said:**
> Amarok (using xine engine) and Audacious (with -plugins) can both playback wma files.  I thought for Rhythmbox all you needed was [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats/#Ubuntu%209.04%20%28Jaunty%20Jackalope%29") and maybe w32codecs (-->[Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo).

Avoid transcoding them if possible (unless you need/want tag edit capability)...degrades the sound.

I don't care much for Amarok 2, and Audacious is one of the few left I haven't tried.
My second choice after Songbird would be Exaile, but it is now giving me problems too.
It will play wma's but seems like it didn't import everything correctly, because it as it goes thru the playlist, it keeps giving me msgs that it is unable to locate several songs, and the location and format it says it is supposed to be in is wrong.

Anyway, I know I have both restricted-extras and medibuntu, but when I went to add/remove to double check, add/remove was gone. Which I just posted a new thread about here [http://ubuntuforums.org/showthread.php?t=1180356](http://ubuntuforums.org/showthread.php?t=1180356).

I guess that is now priority, then worry about music next.

---

### Post by Tholley on 2009-06-06
Ok problem with Add/Remove solved. 

I do have the above as stated. Not sure how to check medibuntu, but I remember going thru the 2 sudos. Would it hurt to run them again just in case?

---

### Post by Tholley on 2009-06-06
> **mastermindg said:**
> VLC can transcode anything include WMA when use with the DMO codecs.

Ok I installed VLC, how do I convert? I went to Media - Convert/Save - picked folder with a cd worth of wma songs, higlighted them, clicked Convert/Save, picked profile = mp3, clicked save (?), the window just disapears. When I go to Media - Convert/Save it opens it right were I left off. Obvioulsy I am not doing something correct.

---

### Post by SuperSonic4 on 2009-06-06
No it won't, if it's installed it will just throw up a "version xxx is the latest version"

There is always ffmpeg but I don't have a wma file to test it with >.<

---

### Post by Tholley on 2009-06-06
> **SuperSonic4 said:**
> No it won't, if it's installed it will just throw up a "version xxx is the latest version"

There is always ffmpeg but I don't have a wma file to test it with >.<

Installed ffmpeg, tried one song twice, showed it converted from wma to mp3, but I don't know were it put it. The song in the orig folder is still wma.

---

### Post by jjross on 2009-06-06
Its probably in your /home folder
Post the ffmpeg command you used to convert it.

---

### Post by logos34 on 2009-06-06
it's probably in your home folder (or whatever dir you were in when you ran ffmpeg)

why are you trying to convert?  Because there must be 3, 4, 5 different media players that support .wma (vlc, totem, gxine, + already mentioned)

---

### Post by ad_267 on 2009-06-06
With ubuntu-restricted-extras you should be able to play wma. It's likely the wma files are encrypted if nothing can play them.

---

### Post by logos34 on 2009-06-06
the only problem you will definitely run into is with wma *lossless* and wma pro...hardly any players support that

If Exaile is the only player that works for you, stick with that and google for solution of importing tracks, or check for bug reports at launchpad...Because when you convert you end up with crappy sounding files

---

### Post by donniezazen on 2009-06-06
have u tried sound converter?

---

### Post by MadViper on 2009-06-06
I personally use media-convert.com for my music and video converts, using the site if pretty simple and its safe so nothing like that to worry about

---

### Post by Tholley on 2009-06-06
> **logos34 said:**
> it's probably in your home folder (or whatever dir you were in when you ran ffmpeg)

why are you trying to convert?  Because there must be 3, 4, 5 different media players that support .wma (vlc, totem, gxine, + already mentioned)

1st. I found it in home folder, moved it to music but Songbird still can't find it.

2nd. the reason I am trying to convert because every media player I have tried is different. One (that I like ) will play one format were another will play another but not all. 

I like Songbird but it will not play wma, so I would like to convert all my wma to mp3.
But even now I'm finding out it is not "seeing" all my mp3 even, like the one I just converted.

I just want a good media player, that will play ALL formats and have all the attributes of either Rythmbox, Exaile or especially Songbird. I do not like any of the others.

---

### Post by logos34 on 2009-06-07
Ok, I think I know where you're comming from...I had a similar experience when I first switched to linux with Amarok...it could playback my apple .m4a lossless (.alac) files but not display the tag info perfectly--let alone edit them--without having to compile from source with that feature enabled...But as they were lossless I could transcode them into flac without any loss of quality (that's what so nice about lossless), so it was a non-issue...

I wish I could help you with Songbird, but I had to uninstall because it's just too bloated...don't have that much ram

---

### Post by logos34 on 2009-06-07
just thought I'd post this batch convert script if you're interested:

> #!/bin/bash
#
# Dump wma to mp3
for i in *.wma
do
filename=`basename "$i" .wma`

#Rip with Mplayer / encode with LAME
echo "Ripping $i"
mplayer -quiet -vo null -vc dummy -af volume=0,resample=44100:0:1 -ao pcm:waveheader "$i"
echo "Encoding $i to "$filename".mp3"
lame **[COLOR="Blue"]-V 2[/COLOR]** audiodump.wav -o "$filename".mp3

rm audiodump.wav
done

Just paste it into a new .txt file and save in your home dir as sth like 'wma2mp3'.

[B]sudo chmod +x wma2mp3

sudo cp wma2mp3 /usr/local/bin[/B]

To use, just cd into dir containing .wma files and type:

**wma2mp3**

That'll give you mp3 @ VBR quality 2 (~192K).  It's super fast--uses fifo method (although it temporarily results in a large wav file)

Need to have mplayer installed:

**sudo apt-get install mplayer**

Or for fixed-bitrate/CBR:
> 
lame [COLOR="Blue"]-b 160[/COLOR] audiodump.wav -o "$filename".mp3

(bitrate = 160kbps)

man lame

for more details


There's also a nautilus script called **audio-convert-mod**


hope that helps

---

### Post by Tholley on 2009-06-07
Thanks! I might look into doing all that, but I may have figured out one solution. Since pretty much the reason I have so many wma files is from ripping cds to wmp. I can probably just re-rip them using Rhythmbox to mp3. Then just delete the duplicate wma's.

---

### Post by LPGDEV on 2009-06-09
> **logos34 said:**
> just thought I'd post this batch convert script if you're interested:



Just paste it into a new .txt file and save in your home dir as sth like 'wma2mp3'.

[B]sudo chmod +x wma2mp3

sudo cp wma2mp3 /usr/local/bin[/B]

To use, just cd into dir containing .wma files and type:

**wma2mp3**

That'll give you mp3 @ VBR quality 2 (~192K).  It's super fast--uses fifo method (although it temporarily results in a large wav file)

Need to have mplayer installed:

**sudo apt-get install mplayer**

Or for fixed-bitrate/CBR:


(bitrate = 160kbps)

man lame

for more details


There's also a nautilus script called **audio-convert-mod**


hope that helps


Script worked like a charm.  Thanks!

---

### Post by andrew.46 on 2009-06-09
Hi logos34,

> **logos34 said:**
> the only problem you will definitely run into is with wma *lossless* and wma pro...hardly any players support that

Indeed it seems early days for both of these files under Linux but it is good to see my favourite media player MPlayer leads the way by allowing playback of wmal using an external codec:

```

andrew@skamandros~/samples$ mplayer luckynight.wma 
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

Playing luckynight.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Lucky Night
 author: Jody Marie Gnant
 copyright: 1995 Sirius Publishing
**[COLOR="Purple"] comments: 1-minute song sample demonstrating Windows Media lossless audio compression[/COLOR]**
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 868.7 kbit/61.55% (ratio: 108583->176400)
**[COLOR="Purple"]Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  63.1 (01:03.0) of 63.0 (01:03.0)  3.4% 

Exiting... (End of file)

```

and wmapro using either the same external or codec or utilising code admittedly not released to the mainstream MPlayer yet:

```

andrew@skamandros~/samples$ mplayer WMVHDsplash.wmv 
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

Playing WMVHDsplash.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  6500.0 kbps (793.5 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
**[COLOR="Purple"]Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)[/COLOR]**
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
[wmapro @ 0x8f63610]input buffer to small413/413 25%  5%  1.9% 0 0 
A:  22.9 V:  22.9 A-V:  0.007 ct:  0.086 479/479 24%  5%  1.8% 0 0 

Exiting... (End of file)

```

Very exciting times for MPlayer enthusiasts :-)

Andrew

---

### Post by logos34 on 2009-06-09
> **andrew.46 said:**
> Hi logos34,

Indeed it seems early days for both of these files under Linux but it is good to see my favourite media player MPlayer leads the way by allowing playback of wmal using an external codec:

```

andrew@skamandros~/samples$ mplayer luckynight.wma 
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

```

so how exactly do you do that?  my build chokes on lossless...'external codec'?...only wmal lossless playback I have are RealPlayer and Foobar2000 w/ **wmfdist11.exe** installed

> and wmapro using either the same external or codec or utilising code admittedly not released to the mainstream MPlayer yet:

```

andrew@skamandros~/samples$ mplayer WMVHDsplash.wmv 
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

Playing WMVHDsplash.wmv.

```

yeah, can do that too (WMVHDsplash.wmv  video + audio track) since recompiling a couple of weeks ago.

I see you also hacked vlc for [lossless support]("http://forum.videolan.org/viewtopic.php?f=13&t=60256")

---

### Post by logos34 on 2009-06-10
> **logos34 said:**
> 
I see you also hacked vlc for [lossless support]("http://forum.videolan.org/viewtopic.php?f=13&t=60256")

Andrew.46, 

where can I get **wma9dmod.dll** and is it as simple as copying it to vlc codec dir?

Granted, there is Realplayer and foobar2000 (which, happily, can also decode it to wav), but it would be nice to know that at least one native-linux app offers playback. 

Why *is* wmal support lacking in linux, anyway?  Quite a few people have at least some music in windows lossless

EDIT: just re-read [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?p=7269541")...I'm probably out of luck, being on x64

---

### Post by andrew.46 on 2009-06-10
Hi logos34,

> **logos34 said:**
> so how exactly do you do that?  my build chokes on lossless...'external codec'?...only wmal lossless playback I have are RealPlayer and Foobar2000 w/ **wmfdist11.exe** installed

As you realise in your next post I am using the 32bit MPlayer and codecs, I believe you are using the 64bit MPlayer?


> I see you also hacked vlc for [lossless support]("http://forum.videolan.org/viewtopic.php?f=13&t=60256")

I am not that clever, the work for that was done by mc4man :-).

Andrew

---

### Post by andrew.46 on 2009-06-10
Hi logos,

Sorry I missed this post :-).

> **logos34 said:**
> 

where can I get **wma9dmod.dll** and is it as simple as copying it to vlc codec dir?

Unfortunately I am pretty much a vlc n00b so I cannot answer at least that part of your question. Easy enough to get hold of wma9dmod.dll though as it is part of the codec pack from MPlayer:

```

andrew@skamandros~/source/mplayer$ **[COLOR="Purple"]tar tjf all-20071007.tar.bz2 | grep 'wma'[/COLOR]**
all-20071007/wma9dmod.dll
all-20071007/wmadmod.dll

```

> Why *is* wmal support lacking in linux, anyway?  Quite a few people have at least some music in windows lossless

I am not sure, is there some resistance to reverse engineering yet another variation of a Microsoft proprietary format perhaps?

Andrew

---

### Post by mc4man on 2009-06-10
You cannot have wma lossless in 64 bit, or anything else that's **solely** provided by w32codecs (or the 32 bit mplayer codecs.

You can get support **for any codec that ffmpeg supports**, either available in your default install, or in the case of wmapro by patching. (either the external static in mplayer or the installed ffmpeg itself.

So in 64 bit wmal is out until ffmpeg supports it, or someone creates a 64 bit wma9dmod.dll. (wouldn't hold breath on either.

The 2 64 bit mplayer workarounds for wmal I can think of are...

Install a 32 bit mplayer and w32codecs or
Download the 32 bit mplayer from mplayer.hu, don't try to install, simply run from it's unpacked folder thru  wine. (putting w32codecs of the folder with mplayer

The former is a far better and most likely is far more difficult.


Post on latter (#40) - kinda hokey - only a gui version
[http://ubuntuforums.org/showthread.php?t=848535&page=4](http://ubuntuforums.org/showthread.php?t=848535&page=4)

What would be interesting would be to get a cli win  version, get cmd.exe from xp and put in wine's windows folder.

Then create a wine wrapper script named cmd, put it your path (home/bin would be good) and see if you could use it to run the cli mplayer for conversions of wmal. (probably wouldn't work but would be an interesting exercise

---

### Post by mc4man on 2009-06-10
While a win based cli mplayer would be tedious to use for playback on 64 bit it would convert wmal to wav very quickly and is easy to set up.

Ex.
> doug@doug-laptop:~$ cmd
CMD Version 1.0

H:\>Mplayer1\mplayer.exe wl.wma -ao pcm:fast:waveheader:file=wl.wav
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
MPlayer Sherpya-SVN-r29312-4.5.0 (C) 2000-2009 MPlayer Team

Playing wl.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Have You Ever Loved a Woman
 author: Derek & the Dominos
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 44100 Hz, 2 ch, s16le, 1152.0 kbit/81.63% (ratio: 144000->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
[AO PCM] File: wl.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


Exiting... (End of file)
H:\>


---

### Post by fballem on 2009-06-10
Another solution that I have used, particularly with wma lossless is to purchase and install the fluendo codecs ([http://www.fluendo.com](http://www.fluendo.com)). They are inexpensive and are GStreamer based.

Once installed, I have used soundconverter to convert the wma lossless to flac or to mp3. Once converted, I can edit the tags using easytag.

Hope this helps,

---

### Post by logos34 on 2009-06-10
thanks guys...found the .dll--it's sitting in /usr/lib/codecs, don't remember installing w32codecs...funny thing is, like andrew.46 (iirc) I can 'play' a wmal file in vlc gui--i.e. the scroll bar moves as if it's playing but of course no sound...nothing at all happens from the cli, however, the problem being x64 (mine)...um, x86 version of mplayer (either in wine or running it from folder) would be interesting but for the fact I already have wmal playback in Realplayer11 and especially the amazing **foobar2000** (thanks again, mc4man, for the tip on **wmfdist11.exe**), which provides wmal playback AND decode/convert to .wav, .ogg, .flac etc. INCL. taginfo...Foobar has got to be one of the best wine apps...it's served me well in converting my apple lossless .m4a *+ metadata* when nothing else besides dBpoweramp would...

So although it still remains somewhat scandalous to my mind that linux doesn't support wmal (reluctance to devote time to a foss version of ms format? maybe), I do have two apps that will do the job.  Alas, they're non-native-linux solutions, but I'll stop worrying about it. 

That's what's great about linux--there's more than one way to do anything (and a good thing, too, in this case!)

---

### Post by Tholley on 2009-06-13
Hi guys, thanks for picking up on this and taking and knocking it out of the park! Even tho the last page and a half, was all foreign language to me. I'm still too new at this, and avoid the command line unless I have simple, kiss instructions.

Anyway, if any other newbies to Linux read this, I realized that WinFF (is that the same ffmpeg mentioned earlier?) will easily convert wma to mp3, I just had to point the output folder to somewhere I could find them once they were converted. I am converting a folder worth of wma's right now!

---

### Post by mc4man on 2009-06-13
> that WinFF (is that the same ffmpeg mentioned earlier?

winff uses the ffmpeg you have installed, but takes care of the commands for you.
So it's capabilities are the same as the ffmpeg you have. (to some extent

So for wma's it could certainly handle wma2 and or wmv with wma2 audio.

---

