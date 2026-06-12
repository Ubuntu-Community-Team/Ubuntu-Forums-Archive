---
title: "Mencoder experts: ready to rip vhs tapes, need your advice"
date: 2009-03-30
forum: Multimedia Software
---

### Post by megamania on 2009-03-30
I'm finally ready to rip my old vhs videotapes. Everything is working and I can record just fine.

I'm just asking for your advice on what quality to use. The main command of my recording script is:
```

mencoder -tv norm=PAL:chanlist=europe-west:driver=v4l2:
width=720:height=578:input=$input_type:fps=25:
amode=0:alsa=yes:immediatemode=0:adevice=hw.1,0:audiorate=32000
-o $filename tv:// -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=3200:aspect=4/3
-vf pp=lb/ha/va/dr,hqdn3d,harddup crop=700:570:10:0 &

```
I have two main concerns: (1) the video quality is not excellent, and (2) I read that when editing the recorded stream (to cut commercials or to trim the beginning/end of the movie) it's easy to get off-sync audio. Is that true?

I also tried using raw output (so that I could edit the file and then encode it), but the size of the files is enormous - is this the suggested way to go?

What video options can I use to improve the results without going with raw files (a higher vbitrate helps, but doesn't solve the problem)?

Regarding audio, would this be ok for vhs recording?
```
-oac mp3lame -lameopts cbr:br=128:mode=0
```

PLEASE give me your opinions, because I'm a bit confused and don't want to start ripping with wrong settings.

---

### Post by megamania on 2009-03-31
*bump*

Just need your opinions on what codec/quality to use when ripping...

---

### Post by andrew.46 on 2009-04-02
Hi megamania,

I am by no means an expert but can I comment on:

```
-lavcopts vcodec=mpeg4:mbd=1:vbitrate=3200:aspect=4/3
```

That seems a *huge* bitrate? Standard additions for encoding to high quality mpeg4 would be mbd=2:trell:v4mv so this would make your line:

```
-lavcopts vcodec=mpeg4:vbitrate=3200:mbd=2:trell:v4mv:aspect=4/3
```

I suspect that this should improve quality a little, I would be interested to hear if this is in fact the case. Another quick comment:

```
-vf pp=lb/ha/va/dr,hqdn3d,harddup crop=700:570:10:0
```

The syntax of your filter chain looks a little odd. Should it be:

```
-vf crop=700:570:10:0,pp=lb/ha/va/dr,hqdn3d,harddup
```

I will admit to knowing next to nothing about the filter you are using: pp=lb/ha/va/dr so presumably this is in the correct place in the chain :-).

Hope this helps a little?

Andrew

---

### Post by eye208 on 2009-04-02
Constant bitrate is a bad idea. Use constant quantizer (=constant quality) instead.

I would use Xvid like this:
```
-ovc xvid -xvidencopts fixed_quant=2
```

By the way, you don't need the deblock filters. There's no block noise in analog video. Put the deinterlace filter at the start of the chain, followed by the denoiser.

---

### Post by megamania on 2009-04-02
Well, after posting my first message I did a lot of research. I'm at the beginning of my digitizing career and my ideas are very confused. :-)

In an attempt to clean things up a bit, I came up with the following script, which doesn't reflect your suggestions yet:
```

SOURCE=/media/disk/video/movie.avi
DEST=/media/disk/video/movie2.avi
STARTPOS="06:10"
DURATION="01:10:27"
VF="pp=ha/va/dr,hqdn3d,harddup,crop=620:469:10:4"

OVC="lavc -lavcopts vcodec=mpeg4:aspect=4/3:vbitrate=1500"
OAC="mp3lame -lameopts cbr:br=64"

mencoder -vf $VF -ss $STARTPOS -endpos $DURATION -mc 0 -ovc $OVC -oac $OAC $SOURCE -o $DEST 

```
It still has to be tested.
At the moment, I'm recording in raw format, and plan to crop/cut/encode with the script above. What do you think? Is that a good idea, or just a waste of time? Is there any difference in quality if I encode directly?

Also, I think I read somewhere (the mplayer website?) that it's better NOT to deinterlace because it makes you lose lots in quality - they suggest to encode without deinterlacing and then make a deinterlaced copy if you need it.

Thanks for your suggestion, and please let me what you think - I'm still waiting for a "final" configuration before starting my copying job.

EDIT: I'm assuming "-ovc xvid -xvidencopts fixed_quant=2" is the way to go, but I tried it and I got
```

xvid: par=0/0 (vga11), displayed=699x564, sampled=699x564
xvid: Fixed Quant Rate Control -- quantizer=2/1=2.00
xvid: xvidcore returned a 'General fault' error
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x32315659.

```

Also, I'm still very confused as to what filters to use...

---

### Post by andrew.46 on 2009-04-02
Hi megamania,

> **megamania said:**
> Also, I'm still very confused as to what filters to use...

A lot of this is trial and error, have you considered using -endpos to allow a bit of experimentation:

```
-endpos 50mb
```

This will cause mencoder to stop after 50mb, then have a look at it, try something different, repeat until all of your spare time has gone :-).

Andrew

---

### Post by eye208 on 2009-04-03
> **megamania said:**
> EDIT: I'm assuming "-ovc xvid -xvidencopts fixed_quant=2" is the way to go, but I tried it and I got
```

xvid: par=0/0 (vga11), displayed=699x564, sampled=699x564
xvid: Fixed Quant Rate Control -- quantizer=2/1=2.00
xvid: xvidcore returned a 'General fault' error
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x32315659.

```
I've never seen that error message before. However, you can also use the LAVC MPEG-4 codec in constant quantizer mode.

Constant bitrate is a bad thing because it keeps the codec from adapting to the complexity of the video. You have to understand that high-motion scenes require much higher bitrates than static scenes. In constant quantizer mode, the codec will adjust the bitrate as needed, so that visual quality remains constant at all times. A constant quantizer encode will always look better than a constant bitrate encode of the same size.

By the way, since you already captured the video in a separate step, you need not encode in realtime any more, so you have a lot more options now. For example, you can do a 2-pass encode to make the video match a particular file size target. And you can use a more efficient codec such as H.264.

---

### Post by andrew.46 on 2009-04-03
Hi eye208,

> **eye208 said:**
> 
Constant bitrate is a bad thing because it keeps the codec from adapting to the complexity of the video. You have to understand that high-motion scenes require much higher bitrates than static scenes. In constant quantizer mode, the codec will adjust the bitrate as needed, so that visual quality remains constant at all times. A constant quantizer encode will always look better than a constant bitrate encode of the same size.

I have had a careful read of:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html)
**11.1.2. Constant quantizer vs. multipass**

and this document seems to suggest that there are in fact *3* choices:

[LIST=1]
[*]constant bitrate (CBR) which the OP suggested in his first post
[*]constant quantizer which you have mentioned in depth
[*]multipass (ABR, or average bitrate) which you have also mentioned in your post.
[/LIST]

The MPlayer document in fact suggests the 2 pass, using a constant bitrate, will produce better results than either 1 or 2 above. My comment is designed to make things clear in my own head rather than pick holes in your argument :-).

All the best,

Andrew

---

### Post by eye208 on 2009-04-03
I encode videos regularly (working for a fansub group) and never noticed a difference in quality between constant quantizer and 2-pass at identical size. The rate control method is the same, except that in the case of 2-pass, the findings from the first pass are scaled to meet the target file size.

If you have certain size requirements (e.g. 700 MB for a CD-R), there is no alternative to 2-pass. For everything else, constant quantizer is the best choice, because it's easier to select a quality level than to guess a bitrate. The codec is much better at doing the latter. A quantizer can be used over and over again, on very different source material, and the quality of the encodes will remain constant all the time. This is very convenient, and a timer saver too, because only one pass is required. For realtime encoding it is the only viable option because you can't run a second pass.

Note that in the case of x264, there's something even better than constant quantizer. It's called "constant rate factor" and takes into account the inability of the human eye to perceive fine detail in fast moving scenes. So the bitrate in those scenes can be lowered even further without degrading the perceived picture quality. Overall x264 is an extremely efficient codec. But it's slower than Xvid.

---

### Post by megamania on 2009-04-03
Thanks for your explanations. In the end, what I'm trying to do is digitize some old VHS video tapes. Most of them are movies which are difficult to find, a few others are family stuff.

These are my prerequisites:
- creating a raw file and encoding it later is fine, if that helps with quality.
- I'd like to have good results, but I'm not paranoid about it. Or maybe I'd like to have a choice between super-high quality results and good results, depending on what I'm encoding. :-)

Since xvid is not working for me for some reason, are you able to give me some parameters (ovc, oac, vf) that are supposed to produce good results with other encoders? 2-pass encoding would be ok.

Thanks for your help so far. I've invested a lot of time in this project (mencoder is not an easy thing!), and now I'm starting to understand the basics...

---

### Post by megamania on 2009-04-03
Ok, I have an update. I managed to encode using X264. A silly typo and some old options were causing problems.
I came up with this script:
```

BITRATE=1000
OAC="mp3lame -lameopts vbr=2:q=3"

# *** should I add pp=lb here?  ***
VF="-vf crop=698:564:8:4,scale=640:480"

STARTPOS="00:01"
DURATION=50mb #for testing purposes

mencoder "$1" $VF -ss $STARTPOS -endpos $DURATION -mc 0 -o /dev/null -nosound -ovc x264 -x264encopts subq=5:8x8dct:me=hex:frameref=5:bframes=3:b_pyramid:weight_b:pass=1:bitrate=$BITRATE
mencoder "$1" $VF -ss $STARTPOS -endpos $DURATION -mc 0 -o x264-$BITRATE.avi -oac $OAC -ovc x264 -x264encopts subq=5:8x8dct:me=hex:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:bitrate=$BITRATE

```
I tested it and it works, but suggestions are happily accepted. In particular, is the bitrate ok? Is it ok to rescale it?  And should I use the deinterlacer option (that's what I think LB does)? I've read very different opinions on this.

Also, I'd like to test encoding with constant rate factor, as suggested. Can you give me some directions, or post a sample mencoder command for constant rate factor? I think I understood I should do a 1-pass encoding with that option.

---

### Post by justsomedude on 2009-04-03
I'm not sure why the above works for you, but you technically can't do a 2 pass encoding while capturing. I'm confused???

The best way to go about this is to capture lossless and worry about everything else later, a 100 minute PAL movie should average to roughly 50 GB with a lossless codec like huffyuv (don't think it's available for Linux though).

x264 with a constant quantizer=0 should be lossless, too, but I'm not sure if it's implemented yet.

I'd advise you to go to [http://www.doom9.org](http://www.doom9.org) and read their TV-Capture guide. Most of the described tools there are not available in Linux, but the walkthrough should give you a general idea how the whole procedure is done.

And if you're serious about this, the combination of Avisynth and x264.exe works perfect in wine... ;)

---

### Post by megamania on 2009-04-03
> **justsomedude said:**
> I'm not sure why the above works for you, but you technically can't do a 2 pass encoding while capturing. I'm confused???
You're right. The script encodes a raw file.

I'd like to avoid using windows programs, because I have invested so much time on mencoder that I'd like to come up with a script that "just encodes" using mplayer/mencoder.
What do you think about my script? Are the parameters correct for what I'm trying to do? I'm still extremely confused with all the options with the encoders and codecs...

---

### Post by justsomedude on 2009-04-03
I didn't mean you should read the guide so you could use Windows programs to do the task, but to get an idea about the general procedure and steps neccessary to do a high quality capture and encode.

> What do you think about my script? Are the parameters correct for what I'm trying to do?

Again: Capturing with a lossless codec (like -ovc lavc -lavcopts vcodec=ffv1 haven't tested that yet, though) and encoding later is the way to go, normally.

If you don't want to do that, try something like:

```
-ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:turbo=1:bitrate=1000:threads=auto
```

as a starting point for the x264 command line, go higher with the bitrate if you can.

You'll need a fast machine for that, deinterlacing will slow this down even more. Remember you'll need to be able to encode 25 frames per second. 

I'd rather not deinterlace and let a player like VLC do it while playing. 

But again: Capture lossless and worry about stuff like that later.

> I'm still extremely confused with all the options with the encoders and codecs...

Believe me, you haven't even touched the surface yet. ;) But don't worry, you'll get there...

---

### Post by andrew.46 on 2009-04-03
Hi megamania,

> **megamania said:**
> Are the parameters correct for what I'm trying to do? I'm still extremely confused with all the options with the encoders and codecs...

You have my sympathies as a small deluge of advice is now heading your way :-). Can I make one small suggestion concerning your script? I note that on your first pass you are using '-nosound'. This *may* give you some problems with sync. The best way is to either use '-oac copy' or '-oac pcm -channels 1 -srate 4000' for this first pass and give your full sound options in the second pass.

Details of this can be found on [the MEncoder page]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html") I have mentioned previously under the heading **11.1.11. Audio**.

All the best,

Andrew

---

### Post by megamania on 2009-04-03
> **justsomedude said:**
> I didn't mean you should read the guide so you could use Windows programs to do the task, but to get an idea about the general procedure and steps neccessary to do a high quality capture and encode.

I just took a look at the guide, thank you. I was referring to your suggestion to use wine.

> 
Again: Capturing with a lossless codec (like -ovc lavc -lavcopts vcodec=ffv1 haven't tested that yet, though) and encoding later is the way to go normally.

But again: Capture lossless and worry about stuff like that later.

I am capturing raw files with a mencoder script. The script above is meant to process the raw file _after_ it is captured.

> 
Believe me, you haven't even touched the surface yet. ;) But don't worry, you'll get there...
Yes, I can tell. The point is that I just wanted to capture my old videotapes, and had no idea it would take me all this time... :-)

---

### Post by justsomedude on 2009-04-03
> **megamania said:**
> 
I am capturing raw files with a mencoder script. The script above is meant to process the raw file _after_ it is captured.

Aah, now we're talking. :D Sorry, I should have read your posts more carefully. :oops:

Try this:
```

# First pass
mencoder -v\
         source\
	-vf crop=698:564:8:4,scale=640:480,harddup\
        -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:bitrate=1000:threads=auto\
        -oac copy\
        -of rawvideo\
        -o /dev/null

# Second pass
mencoder -v\
         source\
	-vf crop=698:564:8:4,scale=640:480,harddup\
        -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:bitrate=1000:threads=auto\
        -oac copy\
        -of rawvideo\
        -o video.264

```

The command above will output a raw x264 stream, you'll have to remux it into a proper container. MkvToolNix or MP4Box do a good job for this.

General thoughts:

-I'd do audio separately. Encode to wav first, then to your desired audio format, this (plus the harddup option) will help to keep a/v sync.

-deintelacing (if you want to) should be done before cropping and resizing in the filer chain. If you want the the player to do it, don't crop and resize at all. Modern containers like .mkv or .mp4 can store information about the aspect ratio anyway.

-don't use .avi containers. They're outdated and cause a lot of trouble.

---

### Post by eye208 on 2009-04-03
> **megamania said:**
> These are my prerequisites:
- creating a raw file and encoding it later is fine, if that helps with quality.
- I'd like to have good results, but I'm not paranoid about it. Or maybe I'd like to have a choice between super-high quality results and good results, depending on what I'm encoding. :-)
If you have enough disk space, capturing to a lossless format is definitely preferable.

I think the Xvid error you've seen earlier was caused by the odd resolution of the input video. Width and height need to be at least multiples of 4 for Xvid to work.

Contrary to what justsomedude said, using AVI does make sense if you require compatibility with consumer electronics devices. There are many DVD players capable of playing back DivX files from CD, DVD or flash memory sticks/cards. DivX files are MPEG-4 videos (similar to Xvid) with MP3 audio in a standard AVI container. It's very easy to produce these files with MEncoder.

In your example above, you cropped your input video to 699x564. This is very close to 704x576, so I am assuming that the input video is PAL format. This is an anamorphic format (i.e. the pixels are not square) so you'll need to stretch the picture to correct aspect ratio (either 4:3 or 16:9). All these things can be done in the MEncoder filter chain.

Note that you can preview your filter chain in realtime using MPlayer. The syntax is the same (-vf ...). Don't start encoding until you know that your filter chain works as expected.

Here's a suggestion:
```
mencoder $INPUT -mc 0 -noskip -ofps 25 -vf pp=$DEINTERLACE,crop=$CROP,dsize=$ASPECT,scale=$RESOLUTION,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=$QUALITY:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:quant_type=mpeg:max_bframes=1:closed_gop:nopacked:profile=dxnhtpal:par=vga11:bvhq=1 -lameopts cbr:br=128:aq=0 -ffourcc DX50 -o $OUTPUT
```
DEINTERLACE should be either of lb, li, ci, md or fd. Choose the one that's giving you the best results. Use MPlayer to test it on the raw file before encoding.

ASPECT is typically 4/3 or 16/9, depending on the video. Cinema movies may require other values.

RESOLUTION may be up to 720:540 (4/3) or 704:396 (16/9), but it must not exceed 720:576. Make sure that width and height are multiples of 4.

QUALITY=2.0 will give you perfect results. If you need a smaller file, increase the value or use 2-pass encoding instead of fixed_quant.

---

### Post by megamania on 2009-04-04
So, I've read all your posts carefully and I thank you for giving some light. :-)  I have a question (sorry):
- Is it ok to scale the resolution up to PAL standard (720:576) after cropping the video to cut the black borders? Or should I scale it down? I'm currently scaling it up, but I'd like to be sure it makes sense.

I amended my previous script thanks to your suggestions. I also included eye208's suggestion (xvid instead of x264). I'm testing both versions.
```

BITRATE=1000
# Audio codec settings
OAC="mp3lame -lameopts vbr=2:q=3"
VF="-vf crop=686:568:14:2,dsize=4/3,scale=720:576,hqdn3d,harddup"
STARTPOS="00:04"
DURATION=15mb

** (1st option) **
mencoder "$1" -mc 0 -noskip -ofps 25 $VF -ss $STARTPOS -endpos $DURATION -o /dev/null -oac copy -ovc x264 -x264encopts subq=1:8x8dct:me=hex:frameref=1:bframes=3:b_pyramid:weight_b:pass=1:bitrate=$BITRATE
mencoder "$1" -mc 0 -noskip -ofps 25 $VF -ss $STARTPOS -endpos $DURATION -o x264-$BITRATE.avi -oac $OAC -ovc x264 -x264encopts subq=5:8x8dct:me=hex:frameref=12:bframes=3:b_pyramid:weight_b:pass=2:bitrate=$BITRATE

** (2nd option) **
mencoder "$1" -mc 0 -noskip -ofps 25 -vf $VF -ovc xvid -oac mp3lame -xvidencopts fixed_quant=2:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:quant_type=mpeg:max_bframes=1:closed_gop:nopacked:profile=dxnhtpal:par=vga11:bvhq=1 -lameopts cbr:br=128:aq=0 -ffourcc DX50 -o xvid.avi

```
Now, I don't want to go crazy and I don't want you to go crazy helping  me. ](*,)
So, I'll use either of the two. I just ask you to tell me if they can be considered equivalent in terms of final quality, and if I can expect both of them to give me a file that works with a DVX player.

Thanks again!

---

### Post by justsomedude on 2009-04-04
Sorry, I didn't quite get you were encoding for a standalone player last evening, mea culpa... :oops:

> **megamania said:**
> - Is it ok to scale the resolution up to PAL standard (720:576) after cropping the video to cut the black borders? Or should I scale it down? I'm currently scaling it up, but I'd like to be sure it makes sense.

Upscaling makes sense in a scenario where you have to use a certain resolution, for example you want to burn a PAL DVD. Since this is not what you're doing, don't. Unless the DivX player you're encoding for requires that (I don't think so).

May I ask you what player you're encoding for? It's worthwhile reading the respective documentation of the device, in order to find out what the player can handle.

> I amended my previous script thanks to your suggestions. I also included eye208's suggestion (xvid instead of x264). I'm testing both versions.
```

BITRATE=1000
# Audio codec settings
OAC="mp3lame -lameopts vbr=2:q=3"
VF="-vf crop=686:568:14:2,dsize=4/3,scale=720:576,hqdn3d,harddup"
STARTPOS="00:04"
DURATION=15mb

** (1st option) **
mencoder "$1" -mc 0 -noskip -ofps 25 $VF -ss $STARTPOS -endpos $DURATION -o /dev/null -oac copy -ovc x264 -x264encopts subq=1:8x8dct:me=hex:frameref=1:bframes=3:b_pyramid:weight_b:pass=1:bitrate=$BITRATE
mencoder "$1" -mc 0 -noskip -ofps 25 $VF -ss $STARTPOS -endpos $DURATION -o x264-$BITRATE.avi -oac $OAC -ovc x264 -x264encopts subq=5:8x8dct:me=hex:frameref=12:bframes=3:b_pyramid:weight_b:pass=2:bitrate=$BITRATE

** (2nd option) **
mencoder "$1" -mc 0 -noskip -ofps 25 -vf $VF -ovc xvid -oac mp3lame -xvidencopts fixed_quant=2:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:quant_type=mpeg:max_bframes=1:closed_gop:nopacked:profile=dxnhtpal:par=vga11:bvhq=1 -lameopts cbr:br=128:aq=0 -ffourcc DX50 -o xvid.avi

```

If you use .avi containers, VBR mp3 can cause problems. CBR may be a better choice here, also the standalone device may not be able to handle VBR. A standalone hardware DivX player will likely not handle x264, so I'd try eye208's suggestions. :)

> Now, I don't want to go crazy and I don't want you to go crazy helping  me. ](*,)
So, I'll use either of the two. I just ask you to tell me if they can be considered equivalent in terms of final quality, and if I can expect both of them to give me a file that works with a DVX player.

Thanks again!

The x264 one will likely not work. eye208's suggestions looks reasonable to me, so try that. I'm not sure if your player will handle anamorph video, so you better scale to suitable aspect ratio like eye208 described in his post.

Good luck!

---

### Post by megamania on 2009-04-04
> **justsomedude said:**
> Sorry, I didn't quite get you were encoding for a standalone player last evening, mea culpa... :oops:

I didn't mention that, I think. Sorry.

Anyway, I tried both versions on my DVD/Divx Player (brand: LG, model:I have to check the manual).
X264 encoding doesn't work. Xvid works, but I get no sound. It's the first time I have no sound on a movie on that player. The settings I used are the ones in the script above (second option - xvid). What can I try to get sound?

Also, I'd like a bit more quality for video: how can I change that to 2-pass, as suggested in previous posts?


I can tell that thanks to your help I'm very very close - please bear with me a bit longer!

**EDIT**: Ok. time to go to sleep. On my external DVD player, audio works with both versions of encoding. The scart lead was half-off (I'm very ashamed). So, since I can use both CBR and VBR, I should probably pick VBR, right?

---

### Post by justsomedude on 2009-04-04
You can try fixed_quant=1 with your one pass encoding to get better quality, but the filesize will be significantly larger. Also, it might not be playable at all, if the resulting bitrate exceeds the players limit.

Concerning your audio issues, did you leave
```
OAC="mp3lame -lameopts vbr=2:q=3"
```
at the beginning of your script? If so, leave it out.

Nevermind, I see you got it working now, so if VBR causes no a/v sync trouble, why not? :)

In order to come up with a suitable 2-pass command line, it'd be really helpful to know what encoding profiles your player supports. [The table at the bottom of this page]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html") will tell you what options of XVid are supported by what profile.

I'll help you if you want, good night!

---

### Post by megamania on 2009-04-05
> **justsomedude said:**
> You can try fixed_quant=1 with your one pass encoding to get better quality, but the filesize will be significantly larger.
I just encoded a 100-minute movie, and I got a 4,4GB file using fixed_quant=2, so I'll probably have to go with *lower* quality, I think.

Regarding 2-pass encoding, I can't find the manual for my DVD player, so I can't give you information. But it plays almost everything I try to play (has had problems only with one movie so far), so if you are able to suggest me a 2-pass string based on the one I'm using, I'd be grateful.

Another thing: when encoding the raw movie today, I got:
```

Badly interleaved AVI file detected - switching to -ni mode...
```
The movie was correctly encoded and apparently it works, but I was wondering why it happened and what problems it can give (I googled for it, but didn't find an explanation of the potential problems). The raw file was captured by mencoder itself, using this simple command:
```

mencoder -tv norm=PAL:chanlist=europe-west:driver=v4l2:width=720:height=578:input=1:fps=25:amode=1:alsa=yes:immediatemode=0:adevice=hw.1,0:audiorate=32000 -o /media/disk/video/movie.avi tv:// -oac pcm -ovc raw

```

---

### Post by justsomedude on 2009-04-05
Even if you can't find the documentation, the exact model of your player might be helpful... ;)

I don't know what the error message means, real men ignore such things.

> width=720:height=578

Height should be 576.

Ok, here's a suggestion to start with. I do a wild guess and assume the player supports DXN home theater PAL profile. This assumption could be totally wrong, though. It's been two years or more since I used XVid, so take this with a grain of salt and listen to other people who might chime in for help...

```
BITRATE=?
VF=harddup

# First pass
mencoder -v\
         $INPUT\
	-vf $VF\
        -ovc xvid -xvidencopts profile=dxnhtpal:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:max_bframes=1:pass=1:bitrate=$BITRATE:turbo=1\
        -oac mp3lame -lameopts cbr:br=128:aq=0\
        -ffourcc DX50\
	-o /dev/null

# Second pass
mencoder -v\
         $INPUT\
	-vf $VF\
        -ovc xvid -xvidencopts profile=dxnhtpal:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:max_bframes=1:pass=2:bitrate=$BITRATE\
        -oac mp3lame -lameopts cbr:br=128:aq=0\
        -ffourcc DX50\
	-o output.avi
```

The bitrate should be as high as possible, so you have to calculate. I don't know how much space you want to allocate per video, so you'll have to do the math yourself. I'm sure there are some bitrate calculators available in Synaptic. And don't forget to consider the audio bitrate.

Since quant_type=mpeg previously worked for you, I leave it in.

Oh, and you have to add your video filers and such...

Let me know how it works. :)

---

### Post by eye208 on 2009-04-06
If you encode to 720x576 anamorphic, don't forget to flag the MPEG-4 stream using either par=pal43 or par=pal169. The AVI container has no place to store aspect ratio information, so the bitstream aspect ratio field is the only way to tell the player how to display the video properly.

---

### Post by megamania on 2009-04-06
> **justsomedude said:**
> Even if you can't find the documentation, the exact model of your player might be helpful... ;)
It is an LG DVX286.

I tried a google search but didn't find the specs (only DVX/XVID was specified). Maybe you know where to look...


> **justsomedude said:**
> 
I don't know what the error message means, real men ignore such things.

Then I am a reeeeeeal man!  :-))

> **justsomedude said:**
> 
Ok, here's a suggestion to start with. I do a wild guess and assume the player supports DXN home theater PAL profile. This assumption could be totally wrong, though. 
I'm having difficulties finding a guide to such options. I was looking for an explanation of "-ffourcc DX50" but a google search gives me thousands of results which are mostly sample scripts.
I'll try your script as soon as possible and will let you know if it works though.

> **justsomedude said:**
> 
The bitrate should be as high as possible, so you have to calculate.
I read somewhere that 1100-1300 can be considered VHS Quality, and around 3000 is DVD quality. Can that be considered correct?

Thanks again, I'll test the script asap!

---

### Post by justsomedude on 2009-04-06
> **megamania said:**
> 
I'm having difficulties finding a guide to such options.

Quick `n dirty google search: [http://www.gromkov.com/faq/conversion/xvid_options.html](http://www.gromkov.com/faq/conversion/xvid_options.html) Didn't read it and it looks a bit dated, but could be a good starting point I guess...

Also, the mencoder guide should be helpful: [http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html)

> I was looking for an explanation of "-ffourcc DX50" but a google search gives me thousands of results which are mostly sample scripts.

-ffourcc DX50 basically means, that the video identifies itself as DivX 5 compatible. It doesn't change the video itself.

>  read somewhere that 1100-1300 can be considered VHS Quality, and around 3000 is DVD quality. Can that be considered correct?

No.

This could be roughly correct if you had very good source material to start with, let's say a Blu-Ray rip.

However, your starting off with with VHS quality, i.e. your VHS tape. Then, your doing an analog/digital conversion, which is a lossy process in itself.

And then, on top of that, you do another lossy conversion with XVid, so you'll loose image quality once again.

Also, the bitrate alone does not give any indication of all the other compression options an encoder uses, which also make a difference.


What you should do is using the max bitrate you can. I assume you're burning these files on a DVD or a CD, so if you have a 4.4 GB DVD and you want to fit two 100 minute movies on there you calculate the bitrate so that each movie takes 2.2 GB.


By the way, your files will likely not get better than the 4,4GB fixed_quant=2 one you encoded yesterday. Unless you use a bitrate so that the output file will be 4,4 GB and run two passes.

Your resulting quality will be below your raw capture in any case. What you could try is to apply some mild filtering, but that's a science in itself. You see, there are forums as big as ubuntuforums.org where they talk about nothing else all day... ;)

---

### Post by fbugnon on 2009-08-10
I'm about to begin my personal project VHS to DVD and found this discussion to be one of the most interesting and quite updated.

@megamania: where are you with your project?  Have you gone through? Could you please provide the code that worked out the best for you after all?

Thank you for sharing the knowledge.

Cheers,

---

### Post by megamania on 2009-08-11
> **fbugnon said:**
> I'm about to begin my personal project VHS to DVD and found this discussion to be one of the most interesting and quite updated.

@megamania: where are you with your project?  Have you gone through? Could you please provide the code that worked out the best for you after all?
I came up with a complete procedure to digitize the movie to raw format, crop the unneeded parts (beginning/end), encode it.
The encoding script is the result of my research on the web and the help I got in this thread.

Unfortunately I'm not at home and I'm leaving for the holidays shortly. I'll be away for a couple of weeks, so if you remind me at the end of the month (assuming you're still interested), I'll post my experience here.

---

### Post by mossroy on 2012-02-26
> **megamania said:**
> if you remind me at the end of the month (assuming you're still interested), I'll post my experience here.

I resurect this thread after a few years...
If you're still watching it, I would be very interested in your procedure and scripts!

---

### Post by howefield on 2012-02-26
Thread closed.

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

