---
title: "How do I convert .ogg to .avi???"
date: 2007-06-22
forum: Multimedia Production
---

### Post by tsav87 on 2007-06-22
I made a recording of my desktop with RecordMyDesktop and I need to know how to convert the .ogg file to .avi.  Any easy way to do this?  A video conversion program would be nice.

Thanks

---

### Post by Saoshyant on 2007-06-23
Hmm?  Do you mean you made a recording in Theora?  Because Ogg, like AVI, are containers for video and audio formats.  They aren't formats by themselves.  Think of it like a ZIP file.

Theora is an Open Media format.  If you want to promote free software and a world of Free Culture, you should not transcode it to a proprietary format.  Video formats that go inside AVI are proprietary and usually based on MPEG 4 like Xvid, which do not work on all Operating Systems.  Considering this and my former argument, you should stick to Theora, which is a great video format.

If you still insist on transcoding Theora to some proprietary video format, you should look into ffmpeg or VLC, since both have transcoding options.

---

### Post by jacob01 on 2007-07-10
yea not being compatable with any thing at all is good. what can you do with an .oog file, you can not edit it with any open source app let alone any comercial software
ok then you go and use an .oog file
so if it is better than any thing else then go convert every thing you have to an .oog file and tell us what you used ok that way you might help

---

### Post by jeffisawesome on 2007-07-11
Mencoder nuff said.  

Also I believe Cinelerra edits .ogg, I know Avid edits .ogg, I think premiere does, and you could always just transcode it for editing.

---

### Post by gsmith on 2007-08-12
This works for me for encoding the output from recordmydesktop to an avi

mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc

---

### Post by Eglo on 2007-08-23
:(
> mencoder clip.ogg -o clip.avi -oac mp3lame -ovc lavcMEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: 'clip.ogg'
Failed to open clip.ogg.
Cannot open file/device.
what can i doing?

---

### Post by kayosiii on 2007-08-24
To get from Record My Desktop to Cinelerra I used mencoder and then open movie editor to create a file I could use. Cinelerra seems to behave itself a lot better with uncompressed files.

---

### Post by FakeOutdoorsman on 2007-08-26
I would use ffmpeg from [Medibuntu]("http://medibuntu.sos-sts.com/repository.php") to create a raw dv file which any video editor should be able to handle (except Adobe Premiere which seems to only like Type 2 DV AVI, I think).
```
ffmpeg -i inputmovie.ogg -target ntsc-dv output.dv
```

You could also use -target pal-dv.

---

### Post by Vadi on 2007-08-26
I tried using ffmpeg, but it just gave me a blank file.

Any ideas? I're recoded a video in the .ogg format, which turned out to be 105mb. Gr, because all file hosting seems to be cut off at 100mb, and no raring/zipping helps to get it below 100mb.

I've tried Kino, but it doesn't even want to recognize the file, and while Pitvi opens it, it doesn't want to cut any clips...

---

### Post by FakeOutdoorsman on 2007-08-26
> **Vadi said:**
> I tried using ffmpeg, but it just gave me a blank file.

Any ideas? I're recoded a video in the .ogg format, which turned out to be 105mb. Gr, because all file hosting seems to be cut off at 100mb, and no raring/zipping helps to get it below 100mb.

I've tried Kino, but it doesn't even want to recognize the file, and while Pitvi opens it, it doesn't want to cut any clips...

Kino is good for editing, but it sounds like you want to re-encode the video to make a smaller file size.  The example I gave above should have created a DV file, which would have been very large in file size, but can be used by most video editing programs.  You can re-encode with ffmpeg, mencoder, or some GUI programs such as [Avidemux]("http://fixounet.free.fr/avidemux/"), [WinFF]("http://biggmatt.com/winff/"), [thin liquid film]("http://thinliquidfilm.org/"), and [Vive]("http://vive.sourceforge.net/").

The Ubuntu Wiki provides some good ffmpeg examples: [H.264 Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding#head-f90bfe71a2e1b38a667375e78725a6351d8685b2")

---

### Post by Vadi on 2007-08-27
Avidemux can't open the file, but I'll try others. Thank you

---

### Post by patambrosio on 2007-09-01
try mencoder, best solution i've found.

[I]mencoder -idx your_input.ogg -vf scale=640:480 -ovc lavc -oac mp3lame -o your_output.avi
[/I]

[HOWTO screen capture in ubuntu feisty fawn]("http://ubuntuchocolate.wordpress.com/2007/09/01/howto-screen-capture-in-ubuntu-feisty-fawn/") -> a full guide on how to screen capture in ubuntu, from recording to converting.

---

### Post by Vadi on 2007-09-02
Oh, thanks a ton.

I'm a bit dissapointed that Kino can open .avi files and not .ogg files atm, but I'll look at your guide.

---

### Post by vinutux on 2007-09-19
u hav e3 options

1. gmencoder (or mencoder)

2. winff (or ffmpeg)

3. avidemux

..................

or at least using vlc for converting files->wizad


:guitar:

---

### Post by eggdeng on 2007-09-21
Although I have ben able to get ffmpeg to recognise and convert ogg Theora, neither Mencoder nor Mplayer recognise the format, at least not the video part. Any ideas as to how I can enable Theora support in Mencoder?

---

### Post by vinutux on 2007-09-22
make sure u r correctly install all theora tools (ie libtheora0)........

or change ur audio and video codecs with right click-> preferences of mplayer
////////////////////////////////////:)

---

### Post by eggdeng on 2007-09-22
Thanks for the suggestions.
> apt-get install libtheora0
libtheora0 is already the newest version
I also tried telling Mplayer to use the ffmpeg codecs but no luck. Suspect Mplayer / Mencoder don't know where to find libtheora0.

---

### Post by andrew.46 on 2007-09-23
Hi,

> **Eglo said:**
> :(

what can i doing?

 You need to give mencoder the path of your file. If you have just opend a Terminal window you will be in your $HOME directory. Either navigate _to_the file or give the full path of it.


                 Andrew

---

### Post by vinutux on 2007-09-23
correct cammand for converting avi to ogg ........I think


......................................................................................
mencoder /inputfilepath.ogg -o /outputfilepath.avi -oac mp3lame -ovc x264 

.................................................................................................

.
option1 -oac output audio codec copy    

   - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encode

options2 -ovc output video codec 

   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

option3 output formats


avi
ogm
mp4
mpg -- mpeg
mov quicktime
.....................................

---

### Post by Vadi on 2007-09-23
I gave up on trying to get the avi, because it would just produce blank files after a while... I just point evebody to the windows version of the VLC player instead. Since people want to watch, they get it.

---

### Post by eggdeng on 2007-09-23
I get excellent results converting to avi using 
```
ffmpeg -i file.ogg  file.avi
```

---

### Post by TaoBoogie on 2008-01-03
> **eggdeng said:**
> I get excellent results converting to avi using 
```
ffmpeg -i file.ogg  file.avi
```

Just tried it and it worked like a charm, thanks eggdeng

---

### Post by pedja_portugalac on 2008-07-17
> **tsav87 said:**
> I made a recording of my desktop with RecordMyDesktop and I need to know how to convert the .ogg file to .avi.  Any easy way to do this?  A video conversion program would be nice.

Thanks
In synaptic manager install ffmpeg and ffmpeg2theora. Then in terminal run:
> ffmpeg -i out.ogg out.avi
And that's it. The quality of the output is not so good as with original theora+ogg but it's ok. I still recommends  to kip original open format. Blindows users can still install codecs to watch the video.

---

### Post by Vadi on 2008-07-20
You can recommend that people use **[vlc]("http://www.videolan.org/vlc/")** to play ogg on windows, it comes with codes built-in.

---

