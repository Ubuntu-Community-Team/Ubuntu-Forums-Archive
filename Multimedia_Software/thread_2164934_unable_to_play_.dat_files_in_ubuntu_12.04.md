---
title: "unable to play .dat files in ubuntu 12.04"
date: 2013-08-02
forum: Multimedia Software
---

### Post by nashtrik on 2013-08-02
[ATTACH=CONFIG]245039[/ATTACH][ATTACH=CONFIG]245041[/ATTACH][ATTACH=CONFIG]245042[/ATTACH][ATTACH=CONFIG]245040[/ATTACH][ATTACH=CONFIG]245043[/ATTACH]This is the 21st century, I am running one of the latest versions of ubuntu i.e. 12.04 and still I cannot run the video cds containg *.dat files.....Pathetic...isn't it ?!! all of them run seamlessly in windows ( even in the Before Christ versions...),and still I am to get an acceptable solution to the problem...no forum has given any satisfactory way to do so. Why doesn't a simple video cd which autoruns in windows can't do in linux is my simple question....?
PS:- tried movie player and VLC media player...still the same result....!!!!

---

### Post by TheFu on 2013-08-02
Never heard of ".dat" before - to me that sounds like a binary data file use by a specific program. Are you sure it is a video format?  Which codec does it use?  Have you tried changing the extension to .mpg?

BTW, I have 100 .dat files on my netbook right now. None of them are video files. 
/var/cache/debconf/config.dat is an example that you probably have too.  Regardless, this doesn't help you playback the file.

My personal opinion is that if **VLC** can't play it, then I don't need to see it.  OTOH, I might try to view it with **mplayer** - that is the other swiss-army knife of video playback.

"movie player" that comes with any Linux has never worked well for any video I wanted to watch. I'm with you on that. Probably best to just purge it, just like nano, gedit, lxterm, and 50 other "included" packages that I'll never use.

BTW, there are many codecs invented by porn websites that only work on Windows. They require an install of their specific codec and often include malware.  NOT being able to play them on Linux is a great thing in my mind.  I'm not anti-porn, just anti-proprietary codec.

If you can play this file on Windows, you might be able to convert it to mpeg2/mpeg4/h.264 and watch it anywhere.  After all, this is the 21st century.

---

### Post by slw210 on 2013-08-02
Perhaps you need to check out what a .dat file is? 

> DAT is a file extension used in the Microsoft Windows Operating System to mean "data". In video the DAT extension is usually used to store MPEG-1 encoded video on VCD or SVCD discs (the predecessors of DVD


What have you tried so far? Saying "no forum has given any satisfactory way to do so" is not much help.

Just to start you off and me having absolutly no clue what you have tried, see [**THIS THREAD**]("http://ubuntuforums.org/showthread.php?t=793086")?

---

### Post by GwL3eNC on 2013-08-02
Hi, 

a dat file is simple renamed mpg file i believe.
Every simple player should play them.

---

### Post by shantiq on 2013-08-02
see next post

---

### Post by shantiq on 2013-08-02
well there is a dat sample[ here]("http://file.fyicenter.com/a/sample.dat")   and it plays in VLC and mplayer on my 13.04 system
so Linux not the problem clearly




so i suggest run mediainfo on your files see what they contain in this dat container


[URL="http://file.ms/extension/dat/"]info on dat
[/URL]






> mplayer *datMPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


[COLOR=#a52a2a]Playing sample.dat.[/COLOR]
[COLOR=#a52a2a]Detected file format: MPEG-PS[/COLOR]
[COLOR=#a52a2a]VIDEO:  MPEG1  352x240  (aspect 12)  29.970 fps  1150.8 kbps (143.8 kbyte/s)[/COLOR]
[COLOR=#a52a2a]Load subtitles in .[/COLOR]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2float @ 0x7f9a0e8e2320]Header missing
AUDIO: 44100 Hz, 2 ch, floatle, 224.0 kbit/7.94% (ratio: 28000->352800)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
Starting playback...






and mediainfo reads


> mediainfo *datGeneral
Complete name                            : sample.dat
Format                                   : CDXA/MPEG-PS
File size                                : 429 KiB
Duration                                 : 2s 35ms
Overall bit rate                         : 1 727 Kbps


Video
ID                                       : 224 (0xE0)
Format                                   : MPEG Video
Format version                           : Version 1
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Default
Duration                                 : 2s 35ms
Bit rate                                 : 1 469 Kbps
Maximum bit rate                         : 1 151 Kbps
Width                                    : 352 pixels
Height                                   : 240 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 29.970 fps
Standard                                 : NTSC
Color space                              : YUV
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.580
Stream size                              : 365 KiB (85%)


Audio
ID                                       : 192 (0xC0)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Mode                                     : Dual mono
Duration                                 : 1s 855ms
Bit rate mode                            : Constant
Bit rate                                 : 224 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Delay relative to video                  : -67ms
Stream size                              : 50.7 KiB (12%)




---

### Post by nashtrik on 2013-08-03
I have edited the post with screenshots.Kindly have a look and suggest what could be done . Thanks

---

### Post by shantiq on 2013-08-03
mediainfo will show us what is in your file


so   > sudo apt-get install mediainfo


then run   

> find ./  -iname  '*AVSEQ01.DAT*' -exec mediainfo  {} +    and paste the results here please   so we all see what is in your file codec wise

---

### Post by thespirit3 on 2013-08-05
Does ubuntu install the non-free codec package without prompting now?  It could be that he's missing the codecs.

---

### Post by Rob Sayer on 2013-08-05
> **shantiq said:**
> mediainfo will show us what is in your file


so   


then run   

    and paste the results here please   so we all see what is in your file codec wise

You beat me to it, except I'd recommend mediainfo-gui instead.  I use it too much to want to have to open a terminal for it.  In dolphin it integrates quite well in services.

If they are playable vcd video files (which is possible if archaic) mediainfo will probably say they're avi format using divx codec.  If so you could just rename the extension to .avi.

However, I suspect they're not really video files.  As mentioned, vlc should be able to play them.  Smplayer (a front end for mplayer) is the only program I've used that's better than vlc as a video "swiss army knife".

---

### Post by nashtrik on 2013-09-08
[ATTACH=CONFIG]246108[/ATTACH][ATTACH=CONFIG]246109[/ATTACH]> **shantiq said:**
> mediainfo will show us what is in your file


so   


then run   

    and paste the results here please   so we all see what is in your file codec wise
.....

.
.
.
.
.
So here is the screenshot of the mediainfo information on the aforementioned .DAT file.....hope the jargon means something to you....it is all for you to do the postmortem.....! thanks

---

### Post by shantiq on 2013-09-09
ok well that gave nothing so try see and please maybe print here what avconv has to say if anything


[COLOR=#000000][I]> find ./ -iname '*AVSEQ01.DAT*' -exec avprobe {} +


[/I][/COLOR]

---

### Post by nashtrik on 2013-09-10
Nah buddy....it simply doesn't run...here is the screenshot of the terminal after executing your suggested command
[I]find ./ -iname '*AVSEQ01.DAT*' -exec avprobe {} +


[/I]

 [ATTACH=CONFIG]246155[/ATTACH]

---

### Post by shantiq on 2013-09-10
is your file lower case at the end?   try again with name of your file as it is on your system without '**'    like this

> [I]find ./ -iname AVSEQ01.dat -exec avprobe {} +



[/I]

---

### Post by nashtrik on 2013-09-11
it IS a video file....Infact, the VCD autoruns on windows 7......and here we are... raking aur grey matter to its limits......you know,sometimes Linux disappoints me, that too on petty issues...all i want is just to play a VCD, not to run a program of some rocket launch.......

---

### Post by zombienerd1 on 2013-09-11
Have you tried to "Open Disc" from VLC??  I find it's much more intuitive than trying to open individual files...

Open VLC, Click The Media menu, Open Disc, Select SVCD/VCD, and point it at your disc drive.

I bet it will work like this.

---

### Post by nashtrik on 2013-09-11
U are a Geeeeeeeeniiiiuuusssssss zombienerd1......great job man.....it ran in a flash.....Thanks a lot buddy....and lots of thanks to you all who posted replies for my query...especially shantiq....!!!!!!

---

### Post by zombienerd1 on 2013-09-11
> **nashtrik said:**
> U are a Geeeeeeeeniiiiuuusssssss zombienerd1......great job man.....it ran in a flash.....Thanks a lot buddy....and lots of thanks to you all who posted replies for my query...especially shantiq....!!!!!!
No problems.  That's how I've always opened DVD's and VCD's in VLC.  It's weird that they won't open manually, but at least it works for you now.  Cheers.

---

