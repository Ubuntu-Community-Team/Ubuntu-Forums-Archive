---
title: "Mkv to mkv?"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by jubej on 2008-04-17
Hello! i recently recived a popcorn hour, its a media streamer that can play a lot of files even mkv. but not all mkv, some videos or sound formats are not supported.

so my question is.

how can i change or convert a mkv movie that wont work in my popcorn hour, but works otherwise in the computer...to a mkv file that the player can play.

some bakground. I have never ever convert anything in my life. ive installed something call mkvtoolnix but  i dont know how to convert it.

i know that mkv its a container. so the quiestion its how to convert the stuff inside, like the vide or the audion and then save it in the container mkv.

thx in advance for any reply

---

### Post by Rhubarb on 2008-04-17
Converting media formats and containers can be quite tricky at times.
So, I recommend you try playing / streaming your mkv files that won't play nicely in popcorn in vlc.
```
sudo aptitude install vlc
```
You'll find vlc in Applications --> Sound & Video --> VLC media player

VLC can play lots of different media files, in lots of different formats.  It can also display a stream of a video and can even stream out video if you so wish.

I've had a quick look at de-muxing mkv files (getting the original video, audio, and subtitles) out of the mkv container.  This can be done, but unfortunately doesn't work easily on some types of video / audio.

I'll give you a push in the right direction, as I haven't found an mkv that I can't play, and haven't had the need to reconvert the contents of mkv files before (I do know how to make mkv files though).

As you've already got mkvtoolnix, we'll proceed proceed.  Make sure your mkv file is in your home directory, to make things easier - as we'll be using the command line to do this.

Open up a terminal, and type in:
```
mkvmerge -i movie.mkv
```
(Where movie.mkv is the name of the mkv file you wish to extract)
This will give you something like this:
```
       File &#8217;movie.mkv&#8217;: container: Matroska
       Track ID 1: video (V_MS/VFW/FOURCC, DIV3)
       Track ID 2: audio (A_MPEG/L3)
       Track ID 3: audio (A_VORBIS)
       Track ID 4: subtitles (S_TEXT/UTF8)
       Track ID 5: subtitles (S_TEXT/UTF8)
```
To extract the video and the ogg vorbis audio track, you'd type this in:
```
mkvextract tracks movie.mkv 1:video.avi 3:audio.ogg
```
This gives you 2 files that you can transcode to a more friendly format (you can use ffmpeg or mencoder, or some nice frontend GUI to do this - search the forums here).

Then once transcoded, you can put the transcoded video / audio back into an mkv container, the easiest way of doing this is with the "MKV files creator" gui that you should already have installed.
```
sudo aptitude install mkvtoolnix-gui
```
Add the video track in first, then add the audio track in, then add any other tracks that you wish to be put in (if there are any other tracks you'd want to put in).
Then press the "Start muxing" button, and there you have it, a nice more friendly mkv file for you to use.

Hopefully this'll get you started.  You may indeed not need to do all this, running vlc might just do the trick and allow you to play the troublesome mkv files easily.

For more help on mkvtoolnix, have a look here: [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

---

### Post by daengbo on 2008-04-17
It might be easier to install [mencoder]("apt:mencoder"), then type
mencoder -oac lavc -ovc lavc old-file.mkv -o new-file.mkv

mencoder is a transcoding program. I generally prefer ffmpeg for ease of use, but it doesn't handle mkv.

-oac lavc sets the audio codec to the lavc default, This should be mp3 unless you did something.

-ovc lavc sets the video codec. This should be divx -- again -- unless you changed something

-o new-file.mkv gives the new filename

Both ffmpeg and mencoder are awesome programs.

Check them out.

---

### Post by jubej on 2008-04-17
daengo thnx that really worked, but the video quality was kind of bad..the original video is: Macross frontier.mkv

1 PM: identify 1: output[0]: ``File '/media/sda7/serier/anime/[Gattai] Macross Frontier - 02 [1280x720 h264] [A406A2E6].mkv': container: Matroska [duration:1469181000000]''
02:35:21 PM: identify 1: output[1]: ``Track ID 1: video (V_MPEG4/ISO/AVC) [language:jpn track_name:Macross\sFrontier\s02\s-\sHard\sChase display_dimensions:16x9 default_track:1 ]''
02:35:21 PM: identify 1: output[2]: ``Track ID 2: audio (A_VORBIS) [language:jpn track_name:Macross\sFrontier\s02\s-\sHard\sChase default_track:1 ]''
02:35:21 PM: identify 1: output[3]: ``Track ID 3: subtitles (S_TEXT/***) [language:eng track_name:English\sSubtitles default_track:1 ]''
02:35:21 PM: identify 1: output[4]: ``Attachment ID 3534160308: type 'application/x-truetype-font', size 352736 bytes, file name 'calibri.ttf'''
02:35:21 PM: identify 1: output[5]: ``Attachment ID 2209395131: type 'application/x-truetype-font', size 205008 bytes, file name 'corbel.ttf'''
02:35:21 PM: identify 1: output[6]: ``Attachment ID 818880692: type 'application/x-truetype-font', size 137568 bytes, file name 'GOTHIC.TTF'''



what options can i have in mencoder to get the exakt same video quiality ..because i can play the video but not the sound in my media streamer. so if i want to have the same video or maybe in x22264 and change the audio to something else like ac3 stereo or acc?

that will be great...

---

### Post by jubej on 2008-04-17
Rhubarb's Avatar  	
Rhubarb


thnx for your help...do you have any recomendation on some frontend GUI i tried vivo. but the compiling and all did not work that good.

what i want its download any mkv...if it dosent work i dont want to download it again...just reconvert it to the highest quality posible video and audio.

sometimes the video dont work sometimes the audio wont work, so I want to be able to change either of them, the mencoder with the options that was posted here worked i could play it in my popcorn hour but both the video and the audio was mutch less quiality than the original, ill want to keep the same quiality but convert it to other working format... thnx

---

### Post by Rhubarb on 2008-04-17
> **jubej said:**
> 1 PM: identify 1: output[0]: ``File '/media/sda7/serier/anime/[Gattai] Macross Frontier - 02 [1280x720 h264] [A406A2E6].mkv': container: Matroska [duration:1469181000000]''
02:35:21 PM: identify 1: output[1]: ``Track ID 1: video (V_MPEG4/ISO/AVC) [language:jpn track_name:Macross\sFrontier\s02\s-\sHard\sChase display_dimensions:16x9 default_track:1 ]''
02:35:21 PM: identify 1: output[2]: ``Track ID 2: audio (A_VORBIS) [language:jpn track_name:Macross\sFrontier\s02\s-\sHard\sChase default_track:1 ]''
02:35:21 PM: identify 1: output[3]: ``Track ID 3: subtitles (S_TEXT/***) [language:eng track_name:English\sSubtitles default_track:1 ]''
02:35:21 PM: identify 1: output[4]: ``Attachment ID 3534160308: type 'application/x-truetype-font', size 352736 bytes, file name 'calibri.ttf'''
02:35:21 PM: identify 1: output[5]: ``Attachment ID 2209395131: type 'application/x-truetype-font', size 205008 bytes, file name 'corbel.ttf'''
02:35:21 PM: identify 1: output[6]: ``Attachment ID 818880692: type 'application/x-truetype-font', size 137568 bytes, file name 'GOTHIC.TTF'''
To me (for this video anyway) it looks like the audio is simple ogg vorbis.
VLC should be able to play this file without any problems.

Get VLC from the Ubuntu repositories, and then just open up the video in vlc.

---------------------------
I don't know of any nice front ends for mencoder / ffmpeg off hand, mainly because I like to use the command line (makes converting batches of videos / scripting encodes much easier and faster in the long run).

---------------------------
To preserve the quality of your video (if sound isn't playing, and vlc won't play the movie correctly), try this:
```
mencoder -oac lavc -ovc copy old-file.mkv -o new-file.mkv
```
If you would rather a better sound quality, but don't mind a larger file size, we could use uncompressed PCM audio (which is inefficient, but there's no loss):
```
mencoder -oac pcm -ovc copy old-file.mkv -o new-file.mkv
```

---------------------------
To preserve the quality of your audio, but re-encode the video:
```
mencoder -oac copy -ovc lavc old-file.mkv -o new-file.mkv
```
And if you want a better video quality (this will take a long time to encode):
```
mencoder -oac copy -ovc x264 -x264encopts threads=auto:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b old-file.mkv -o new-file.mkv
```

---------------------------
Or, if you just want one line that'll work with any video, but will create a big file, that'll take quite a while to encode:
```
mencoder -oac pcm -ovc x264 -x264encopts threads=auto:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b old-file.mkv -o new-file.mkv
```

---------------------------
Seriously, I'd recommend trying out VLC before attemting anything else, it's a good player, and can play pretty much any format under the sun.

---------------------------
**edit1**: I didn't realise popcorn hour was a piece of hardware that connects to your TV, hence why I'm guessing VLC wouldn't be suitable in your case.
There are many other options you can give mencoder, so you can choose which audio format and video format you want it to use.
If you're somewhat comfortable with the command line, I recommend you do an internet search for mencoder examples / usage.
Alternatively you can view the very large mencoder man page by opening up firefox, and pasting this into the URL:
```
file:///usr/share/doc/mplayer-doc/HTML/en/index.html
```

edit2[/B]: your popcorn hour box may not be able to play the x264 encoded video that I used in some examples above, it may not even be able to play PCM audio either.
I suggest you look into the mencode man page and find some options that may work with your player (like using a higher bitrate mp3, and using xvid at high bitrate for video).

---

### Post by jubej on 2008-04-17
hello the popcorn plays pcm ac3 dts and some acc. for video it plays x264 no problems there.

i tryed the: One line that will work with any video i get this error:


 mencoder -oac pcm -ovc x264 -x264encopts threads=auto:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b  Macross\ Frontier\ -\ 02.mkv -o new-file.mkv
MEncoder dev-SVN-r26345-4.2.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xe5cf1e9
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Macross Frontier 02 - Hard Chase", -vid 0
[mkv] Track ID 2: audio (A_VORBIS) "Macross Frontier 02 - Hard Chase", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "English Subtitles", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x720  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar I420 as output csp (no 1)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.

Exiting...
[andres@digitalbone:~]$                                        

i dont know where to put the rate controll method.

x24 its no problem or dts, ac3, The PCH  supports AAC-LC but not AAC-LC-SBR


By the way when i convert i got a LOT of skiping frames and very few duplicate..is it some development packages or something that i misssing?  or just havin mencoder its all i need? i tried all the commands from you and from daengdo and both skippip frames. when i play the movie its deformed... i think i do something wrong..dont know what...

---

### Post by Rhubarb on 2008-04-17
Ok, try specifying a nice high bitrate for your x.264 encoded video (like 8Mbit) like so:
```
mencoder -oac pcm -ovc x264 -x264encopts bitrate=8192:threads=auto:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b old-file.mkv -o new-file.mkv
```

---

### Post by jubej on 2008-04-17
wow that was mutch better...thnx..i took a lot of time for a 249 meg and it converted to 486 meg file, the video quiality its really nice and big. but there is only one problem:

i think its because of this:

Pos: 558.1s  14871f (56%)  8.47fps Trem:  22min 855mb  A-V:0.083 [5683:1536]
Skipping frame!
Pos: 558.5s  14881f (56%)  8.47fps Trem:  22min 855mb  A-V:0.083 [5679:1536]
Skipping frame!
Pos: 558.8s  14891f (56%)  8.47fps Trem:  22min 855mb  A-V:0.083 [5677:1536]
Skipping frame!
Pos: 559.2s  14901f (56%)  8.48fps Trem:  22min 855mb  A-V:0.083 [5673:1536]
Skipping frame!
Pos: 560.0s  14921f (56%)  8.48fps Trem:  22min 855mb  A-V:0.083 [5667:1536]
Skipping frame!
Pos: 560.4s  14931f (56%)  8.49fps Trem:  22min 855mb  A-V:0.083 [5664:1536]
Skipping frame!
Pos: 560.4s  14935f (56%)  8.49fps Trem:  22min 855mb  A-V:0.017 [5664:1536]
1 duplicate frame(s)!
Pos: 560.4s  14936f (56%)  8.49fps Trem:  22min 855mb  A-V:0.021 [5663:1536]
2 duplicate frame(s)!


it seem that skips still, whats does that mean? is it that it skips frames and not include them in the new mkv file? specially when a scene its pan, like moving up/down or sideways, its lagg. why does it skip frames?

is there a way to prevent skipping, and is there a way to make it faster.

its seem that when making then -ovc copy it cant just copy the video, it get deformed. i dont know what.

the best so far its the las line by Rhubarb. but it does some skip still.

by the way what does the opstions means?

it feels that its almos there

by the way this are the last line are converting:


Pos: 562.5s  14988f (56%)  8.51fps Trem:  22min 855mb  A-V:0.071 [5643:1536]
Too many audio packets in the buffer: (4103 in 1105990 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16:9.
Setting audio delay to 0.083s.

Video stream: 5641.898 kbit/s  (705237 B/s)  size: 396827968 bytes  562.687 secs  14988 frames

Audio stream: 1536.000 kbit/s  (192000 B/s)  size: 108096000 bytes  563.000 secs
x264 [info]: slice I:200   Avg QP:10.06  size: 59936
x264 [info]: slice P:7199  Avg QP:10.57  size: 42472
x264 [info]: slice B:5471  Avg QP:12.03  size: 14454
x264 [info]: mb I  I16..4: 30.6% 53.8% 15.6%
x264 [info]: mb P  I16..4: 10.0% 21.6%  6.5%  P16..4: 29.7%  9.2%  3.5%  0.3%  0.2%    skip:19.0%
x264 [info]: mb B  I16..4:  0.7%  1.3%  1.2%  B16..8: 29.5%  3.1%  5.8%  direct:12.8%  skip:45.5%
x264 [info]: final ratefactor: 7.70
x264 [info]: 8x8 transform  intra:55.6%  inter:39.9%
x264 [info]: ref P  71.3% 13.6%  7.3%  4.1%  3.7%
x264 [info]: ref B  70.9% 15.1%  7.0%  4.0%  2.9%
x264 [info]: kb/s:5914.0

---

### Post by Rhubarb on 2008-04-18
To see the documentation on mencoder, you'll need to install the documentation:
```
sudo aptitude install mplayer-doc
```

All things mplayer and mencoder related can be found here (open up firefox, and paste this into the address bar):
file:///usr/share/doc/mplayer-doc/HTML/en/encoding-guide.html

Specific options for mencoder's x264 options can be found here (open up firefox, and paste this into the address bar):
file:///usr/share/doc/mplayer-doc/HTML/en/menc-feat-x264.html

I can't help you with the problem where mencoder seems to drop frames, as I'm not sure why it does this myself.  (perhaps mencoder setting needs to be tweaked, or maybe ffmpeg would be better to use)

A faster way to encode the video would be to use subq=5, this makes for slightly less quality, with a performance boost of 25-100%
So try this instead:
```
mencoder -oac pcm -ovc x264 -x264encopts bitrate=8192:threads=auto:subq=5:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b old-file.mkv -o new-file.mkv
```

There are many options you can adjust to make encoding times faster / higher quality encodings.
It is also possible to do 2 pass encoding which results in an excellent quality encode.

---

### Post by molises on 2008-04-18
FOR MKV POPCORN HOUR [http://www.popcornhour.com/onlinesto...ask=wheretobuy](http://www.popcornhour.com/onlinesto...ask=wheretobuy) oficial popcorn reseller [www.tododvd.com](www.tododvd.com) a 219€ vat included
[http://www.tododvd.com/product_info....oducts_id/1910](http://www.tododvd.com/product_info....oducts_id/1910) they have in sotck, if you whant to buy it send an email to [email]comercial@tododvd.com[/email] and they will answer in english , to make payment PAYPAL, the can serve instantly and the postal cost is 19€

---

