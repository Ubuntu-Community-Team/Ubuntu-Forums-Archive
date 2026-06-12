---
title: "AVCHD video editor for Ubuntu?"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by xtaski on 2007-08-19
Does anyone know of a video editor that supports the new HD compression format called AVCHD? I'm willing to pay for a commercial app. I checked an Jahshaka does not seem to support this format... yet at least. 

Any recommendations? :confused:

---

### Post by NewRubberSoul on 2007-11-26
Bump.

I'm getting ready to buy a new Sony camcorder and this information would be really useful.  Thanks in advance if anyone knows.

---

### Post by xtaski on 2007-11-26
I never found an answer to this either... looked for a while, but no solution in sight.

---

### Post by homer168 on 2007-12-14
[http://www.getdeb.net/release.php?id=1840](http://www.getdeb.net/release.php?id=1840)

Try this. It will do AVC about as well as anything out there.

I don't know what your source is but AVC can be tricky to work with. Let me know if you need some advice.

---

### Post by xtaski on 2007-12-17
Afraid that doesn't work either...

[http://www.avidemux.org/admWiki/index.php?title=Input_formats](http://www.avidemux.org/admWiki/index.php?title=Input_formats)

---

### Post by disturbedite on 2007-12-17
> **xtaski said:**
> Afraid that doesn't work either...

[http://www.avidemux.org/admWiki/index.php?title=Input_formats](http://www.avidemux.org/admWiki/index.php?title=Input_formats)

i think you might be wrong there buddy.  did you actually try the program or did you simply read about it?

i was gonna recommend avidemux as well, cuz it does support all kinds of HD content.  but, its more of a post production targeted program, as far as its editing features go, but i do use it for that type of stuff.

there are other editing programs out there, but i don't know if they support that format.  here are some i can think of:
lives
kdenlive
cinelerra

---

### Post by wesleybailey on 2008-01-30
Right now there is no program that will directly edit AVCHD videos.

I found this out the hard way. I bought a Sony HDR-SR7, and found out it recorded into .mts(avchd) files.

The only solution I have found was converting the .mts into an .avi, and then you can edit it with avidemux.

I have created a tutorial [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/") that walks you through the process.

---

### Post by philc on 2008-01-30
> **wesleybailey said:**
> 

I have created a tutorial [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/") that walks you through the process.

You need to update your link! This one should work:

[http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/](http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/)

---

### Post by wesleybailey on 2008-01-30
Link updated.

Thanks for the feedback philc

---

### Post by eye208 on 2008-01-30
> **xtaski said:**
> Does anyone know of a video editor that supports the new HD compression format called AVCHD?
AVC, also known as H.264, is an export format. Even if a video editor has no built-in H.264 exporter, you can export to another format, e.g. DV or MJPEG, and encode to H.264 afterwards. Avidemux and MEncoder can do it. FFMPEG can do it too if you use the version from the Medibuntu repository. The name of the codec is "x264". It is free and open source.

Probably one of the best editors for HD footage on Linux is Blender. It has been used to edit the short film "Elephants Dream" which was produced in 1080p resolution.

---

### Post by agersi on 2008-06-04
Hi everybody,

I found the solution to my problem.
I bought a Canon Vixia hf100 -- wonderful camcorder !
After reading lots of high-tech information on how to convert my AVCHD .mts2 files to some more manageable format, I come up in ConvertxDVD.
Here is what I did (KISS --- Keep It Simple Stupid !)
I downloaded the trial version of ConvertxDVD from here : 
[http://www.vso-software.fr/products/convert_x_to_dvd/?ap=avangate&aid=675](http://www.vso-software.fr/products/convert_x_to_dvd/?ap=avangate&aid=675)
then I installed it on my Ubuntu HArdy amd64 with Wine and ... voila' !
I am now able to import .mts2 files (just use the "all files" option in the open file window to make the .mts2 files visible) and convert them, with the power of my two opteron 64 bit.
You can choose to burn directly a DVD (I didn't tried this yet) or abort/cancel the burning. You will find the converted files in the ConvertxDVD default directory (see Preferences-> general, you can browse going on Application-> Wine-> Browse C:\, mine is in /angelo/.wine/drive_c/windows/profiles/angelo/My Documents/ConvertXtoDVD/00027/VIDEO_TS). In this directory you'll find a file like this: VTS_01_1.VOB, which is playable with MPlayer or whatever player able to manage VOB files.

The trial version of ConvertxDVD leave a mark on your converted file. To eliminate this problem you need to buy it ... 
I hope you like this ....

Angelo

---

### Post by bsmith1051 on 2008-06-05
Interesting!  Does it support any filters or plugins, e.g. anti-shake?  That's the problem I'm having now -- I can't record anything on my Sony HDR-CX7 (which records 1080i AVCHD) without noticeable shaking.

---

### Post by agersi on 2008-06-05
As far as I know, it doesn't have filter support like the anti-shaking.
In my case, the Canon Vixia has a pretty good optical image stabilization system. ConvertxDVD can adjust resolution and other stuff, like crop and pan, but it is not a video-editing tool. I didn't try yet but I think that you can use the VOB file to feed a video editing program, like Cinelerra, to adjust your video.

Angelo

---

### Post by shanek on 2008-06-19
So far, the best I've been able to do is convert the .mts files to something that can be edited. 

Wes Bailey, nice guy that he is, emailed me about a post I'd made on his blog about a script he made to convert the files. His tips were to compile FFMPEG from a recent SVN checkout, and use the -copyts switch  to make sure the sound is synchronized with the video. 

My ffmpeg was compiled with: 
```
./configure --enable-gpl --enable-liba52 --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid
```

Of course, you'll need to install the appropriate *-dev packages to compile all those external libraries.
```
sudo apt-get build-dep ffmpeg
sudo apt-get install liba52-0.7.4-dev libfaad-dev libfaac-dev liblame-dev libxvidcore4-dev
```
should satisfy those dependencies. There might be a few others.

To make an avi that'll play in VLC, Mplayer, etc, the following command worked nicely for me.
```

 ffmpeg -s 1920x1080 -i inputfile.mts -acodec libmp3lame -ab 256k -ac 2 -vcodec libxvid -sameq -aspect 16:9 -b 15000k outputfile.avi
```
If you need to edit the video in Cinelerra, I found that the above command didn't import the video properly. Instead, use:
```
ffmpeg -s 1920x1080 -i inputfile.mts -acodec libfaac -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 15000k -copyts outputfile.mov
```

I'd be curious to play a bit with the bitrate settings. Maybe it can handle a higher rate?

The camera I've been using to test this is a Canon Vixia HF100 set to the full 1920x1080 resolution, and a 30p frame rate setting. You can also set your frame to 24p, which I haven't tested, and 60i, which would need to be deinterlaced.

---

### Post by motin on 2008-06-24
> **shanek said:**
> So far, the best I've been able to do is convert the .mts files to something that can be edited. 

Wes Bailey, nice guy that he is, emailed me about a post I'd made on his blog about a script he made to convert the files. His tips were to compile FFMPEG from a recent SVN checkout, and use the -copyts switch  to make sure the sound is synchronized with the video. 

My ffmpeg was compiled with: 
```
./configure --enable-gpl --enable-liba52 --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid
```

Of course, you'll need to install the appropriate *-dev packages to compile all those external libraries.
```
sudo apt-get build-dep ffmpeg
sudo apt-get install liba52-0.7.4-dev libfaad-dev libfaac-dev liblame-dev libxvidcore4-dev
```
should satisfy those dependencies. There might be a few others.

To make an avi that'll play in VLC, Mplayer, etc, the following command worked nicely for me.
```

 ffmpeg -s 1920x1080 -i inputfile.mts -acodec libmp3lame -ab 256k -ac 2 -vcodec libxvid -sameq -aspect 16:9 -b 15000k outputfile.avi
```
If you need to edit the video in Cinelerra, I found that the above command didn't import the video properly. Instead, use:
```
ffmpeg -s 1920x1080 -i inputfile.mts -acodec libfaac -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 15000k -copyts outputfile.mov
```

I'd be curious to play a bit with the bitrate settings. Maybe it can handle a higher rate?

The camera I've been using to test this is a Canon Vixia HF100 set to the full 1920x1080 resolution, and a 30p frame rate setting. You can also set your frame to 24p, which I haven't tested, and 60i, which would need to be deinterlaced.

Thanks man, your post means one step closer...

I have the HF10 model and have shots taken with the default max: FXP@17mbps. I have not changed 60i to 30p (frankly I haven't discovered how to accomplish that yet), and trying your method makes ffmpeg spit out a lot of "[h264 @ 0xb7c59590]PAFF + spatial direct mode is not implemented" while converting and ends up in either 

1. An 4x larger avi-file with a video consisting of correct sound but slow-motion (seems to be 2x longer than the audio) video with _very_ visible "interlace-artifacts" (unsynced fine lines)

or
2. An 3x larger mov-file with synced audio/video but with even more visible interlace-artifacts.

respectively. 

On a side note, trying the [m2tstoavi script]("http://www.avsforum.com/avs-vb/showthread.php?t=789775") results in a 11x larger file, correct sound but jibberish for video, so no luck there either.

Thus, so far the mov-conversion is the closest to be able to view 60i FXP AVCHD mts-files at the moment. The quality however is so poor that it can only be regarded as a rough preview of what the mts-files contains.

You mentioned deinterlacing first, can this be done with ffmpeg? Cheers

EDIT: I was too quick on submitting. man ffmpeg hinted the useful option "-deinterlace" and with it, the resulting mov-file indeed looks very nice! I cannot see if the HD quality is kept, or if this encoding results in lower quality, but it definitely makes for a possibility to maybe author DVDs from the mts files... Anyone have any experience on how to achieve this?

Btw, the command with deinterlacing looks like the following (I also changed 15000k to 17000k since FXP supposedly is 17mbps - not sure if this change is motivated/correct though):
```
ffmpeg -s 1920x1080 -i inputfile.mts -acodec libfaac -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 17000k -deinterlace -copyts outputfile.mov
```

Great, now at least I can view mts files after some encoding!

EDIT2: Two last things before I make a new post:
1. The resulting mov-file seems to have ended up in around 21mpbs regardless of "-b 15000k" or "-b 17000k"
2. I had to install a certain version of libx264-dev in order for the latest ffmpeg to compile, thanks for this thread (which also contains links to the relevant debs): [http://ubuntuforums.org/showthread.php?t=693867&page=3](http://ubuntuforums.org/showthread.php?t=693867&page=3)

---

### Post by motin on 2008-06-24
Altering the ffmpeg command a little, it is possible to get DVD-formatted mpegs at around 6mbps using the following command:

```
ffmpeg -s 1920x1080 -i inputfile.mts -pass 1 -target pal-dvd -aspect 4:3 -deinterlace -copyts outputfile.mpg
ffmpeg -s 1920x1080 -i inputfile.mts -pass 2 -target pal-dvd -aspect 4:3 -deinterlace -copyts outputfile.mpg

```

Adjust "pal" and the aspect to match your preferred format (read more here: [http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode))

As the resulting files are but 6mbps (as this seems to be all that is required for PAL/NTSC standards), an interesting follow-up would be if anyone know of a way to burn HD quality DVD:s without resorting to Blu-ray formats?

---

### Post by agersi on 2008-06-25
I don't understand why you are fighting on finding weird and unique ffmpeg codes and numbers and you are not using already working available solutions like ConvertxtoDVD under Wine, which I tested with positive results.
This system eats your mts files and output VOB files that you can even directly burn on DVD. I know it is not free but I am sure that there are other front end like ConvertxDVD out there that do are freeware.

KISS

---

### Post by motin on 2008-06-27
> **agersi said:**
> I don't understand why you are fighting on finding weird and unique ffmpeg codes and numbers and you are not using already working available solutions like ConvertxtoDVD under Wine, which I tested with positive results.
This system eats your mts files and output VOB files that you can even directly burn on DVD. I know it is not free but I am sure that there are other front end like ConvertxDVD out there that do are freeware.

KISS

If you cannot find and tell us about the "other front end like ConvertxDVD out there that do are freeware", I suggest you read on:

If I was not interested in making this possible with free software then yes I would have purchased ConvertXtoDVD for &#8364;40 and used it as it was intended to use. 

I would probably also use Windows and either empty my wallet on thousands of similar pieces of software or get most of my software through piracy. 

The relevant thing here is that instead of spending the 6 hours working with my own business (for which I could have bought many licenses of ConvertXtoDVD), I felt compelled to finding a way to do this with free software like ffmpeg, share my experiences and thus make it possible for others to have the choice of using free software. 
When having proved it is possible, it is a matter of routine for anyone that wishes to make a script or GUI that eats mts files and ends up with ready-to-burn VOBs, since free software and already existing projects can be used for it. In the end, methods using free software makes it easier on the whole.

I am quite frankly surprised over your comment here on Ubuntu Forums. I can recommend the following link: [http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

Keep it free.

---

### Post by zakeen on 2008-06-29
> **agersi said:**
> I don't understand why you are fighting on finding weird and unique ffmpeg codes and numbers and you are not using already working available solutions like ConvertxtoDVD under Wine, which I tested with positive results.
This system eats your mts files and output VOB files that you can even directly burn on DVD. I know it is not free but I am sure that there are other front end like ConvertxDVD out there that do are freeware.

KISS

I tried it and even bought the product. It does work like a breeze, very simple.

However this is for DVD only, not HD. So while its very good for DVD stuff Id prefer to have HD. But still many thanks as I will use it till I find a better way.

---

### Post by motin on 2008-06-30
> **zakeen said:**
> I tried it and even bought the product. It does work like a breeze, very simple.

However this is for DVD only, not HD. So while its very good for DVD stuff Id prefer to have HD. But still many thanks as I will use it till I find a better way.

Exactly - I am also looking for a HD solution. Feels like a bad trade-off to record in 14 or 17 mbps and only be able to burn around 6 mbps... 

Can DVD players play HD quality video, albeit be might not fit very many minutes per DVD?

---

### Post by shanek on 2008-06-30
> **agersi said:**
> I don't understand why you are fighting on finding weird and unique ffmpeg codes and numbers and you are not using already working available solutions like ConvertxtoDVD under Wine, which I tested with positive results.
This system eats your mts files and output VOB files that you can even directly burn on DVD. I know it is not free but I am sure that there are other front end like ConvertxDVD out there that do are freeware.

KISS

Doesn't help me much if I'm trying to import it into Cinelerra and edit it.

---

### Post by shanek on 2008-06-30
> 1. The resulting mov-file seems to have ended up in around 21mpbs regardless of "-b 15000k" or "-b 17000k"
2. I had to install a certain version of libx264-dev in order for the latest ffmpeg to compile, thanks for this thread (which also contains links to the relevant debs): [http://ubuntuforums.org/showthread.php?t=693867&page=3](http://ubuntuforums.org/showthread.php?t=693867&page=3)Reading through the ffmpeg documentation, it looks like the -sameq ("same quality") switch will override the -b ("bitrate") switch. Sure enough, when I test it out dropping the -b 17000k, it comes out exactly the same.

The --enable-libx264 is only needed if you want to *encode* h.264 compressed mpeg-4 file. If you only need to decode h.264 files, that's already built into ffmpeg. At least, that's the impression I get from reading through the output of ```
ffmpeg -format
``` Of course, looking at the Vimeo video sharing website's FAQ, they suggest h.264 encoding, so I recompiled ffmpeg, and had the same problem. Thanks for the tip.

> ...and trying your method makes ffmpeg spit out a lot of "[h264 @ 0xb7c59590]PAFF + spatial direct mode is not implemented" ... Yeah, I get a ton of those messages too, but it doesn't seem to cause any problems. **PAFF** (Picture-Adaptive Frame/Field) as far as I can make out, is some sort of interlacing scheme that's used by h.264 The video I'm feeding it is not interlaced, so I'm not sure why I get these messages. Googling around on that message, it looks like it's currently being worked on. Anyway, the video looks good!

A bit of disturbing output:
> Press [q] to stop encoding
[h264 @ 0x7dd600]B picture before any references, skipping
[h264 @ 0x7dd600]decode_slice_header error
[h264 @ 0x7dd600]no frame!
Error while decoding stream #0.0
[h264 @ 0x7dd600]B picture before any references, skipping
[h264 @ 0x7dd600]decode_slice_header error
[h264 @ 0x7dd600]no frame!
Error while decoding stream #0.0
[h264 @ 0x7dd600]B picture before any references, skipping
[h264 @ 0x7dd600]decode_slice_header error
[h264 @ 0x7dd600]no frame!
Error while decoding stream #0.0
[h264 @ 0x7dd600]B picture before any references, skipping
[h264 @ 0x7dd600]decode_slice_header error
[h264 @ 0x7dd600]no frame!
Error while decoding stream #0.0
[h264 @ 0x7dd600]PAFF + spatial direct mode is not implemented
[h264 @ 0x7dd600]PAFF + spatial direct mode is not implementedThe video seems fine, except for the first second or so. In the first second or two, the video seems to freeze, stutter, and then play normally. It stutters differently depending upon the media player I'm using. Anyone know what these mean? No luck with Google so far...

---

### Post by bsmith1051 on 2008-07-01
> **motin said:**
> Can DVD players play HD quality video, albeit be might not fit very many minutes per DVD?
Only HD models, e.g. HD-DVD or BluRay.  The former HD-DVD crowd is now working on a new "DVD 2.0" spec that will do something similar.

---

### Post by ArtInvent on 2008-07-02
Wow, this is sad. I'm looking at buying an AVCHD cam. Maybe a Canon HF-100 or a new Panasonic that isn't out yet. But then I tried to download a sample of AVCHD footage and simply play it back on Ubuntu. No luck so far! Not even halting playback in VLC or MoviePlayer. Zippo. Is there a way to get the codec to play this stuff?

I saw that Corel offers LinDVD to at least play back these files - but you can't get it at any cost because they only offer it to OEM's! Thanks guys!

I just sold a perfectly good Canon HV-20 because I really hate tape, and the editing workflow, especially in 24p on Linux and Cinelerra, is just too cumbersome. But AVCHD is even worse. 

I think that perhaps Kdenlive will be supporting AVCHD in the next few months, they mention it first thing on their roadmap. 

But it sure would be nice to simply have a codec support for this in VLC or MoviePlayer or SOMETHING. It's pretty pathetic that this codec has been out for quite a while now and is becoming the predominant HD format and we can't even *play it back*.

---

### Post by motin on 2008-07-02
> **ArtInvent said:**
> Wow, this is sad. I'm looking at buying an AVCHD cam. Maybe a Canon HF-100 or a new Panasonic that isn't out yet. But then I tried to download a sample of AVCHD footage and simply play it back on Ubuntu. No luck so far! Not even halting playback in VLC or MoviePlayer. Zippo. Is there a way to get the codec to play this stuff?

I saw that Corel offers LinDVD to at least play back these files - but you can't get it at any cost because they only offer it to OEM's! Thanks guys!

I just sold a perfectly good Canon HV-20 because I really hate tape, and the editing workflow, especially in 24p on Linux and Cinelerra, is just too cumbersome. But AVCHD is even worse. 

I think that perhaps Kdenlive will be supporting AVCHD in the next few months, they mention it first thing on their roadmap. 

But it sure would be nice to simply have a codec support for this in VLC or MoviePlayer or SOMETHING. It's pretty pathetic that this codec has been out for quite a while now and is becoming the predominant HD format and we can't even *play it back*.

I have the HF-10 - nice cam. Anyway, the only way to view MTS files is currently to convert them to another format using the latest version of ffmpeg. Instructions on how to do this is found on post #11 in this thread (page 2).

Kdenlive depends on ffmpeg's support it seems. 

As a side note, Windows users are also having troubles finding a codec to play these files, although there is at least one I've heard (don't know if it costs anything).

---

### Post by shanek on 2008-07-04
Ok, I played a bit more with the -sameq and -b switches this week. One problem I was having is that many of the files I'd converted using the -sameq switch would crash Cinelerra. They were also substantially larger - I'm looking at one right now that was 1.9 G out of the camera, and ended up being 4.2 G after converting. The HF100 camera supposedly records at a 17000k bitrate, so I tried dropping the -sameq and replacing it with the -b 17000k. Suddenly, I can open up the files without crashing Cinelerra, and they're about the same size as the original file - maybe another 100 Megs or so larger. Video still looks very good.

By the way, my computer's got 3G of RAM, and an AMD 4200+ X2 (dual-core) processor. It looks like FFMPEG is converting the video at about 9-11 frames per second, so conversion time is about 3x the length of the original movie. I can still play UT2004 while the conversion is going on, so it's not all lost time :) I wonder if using the -threads switch would speed things up at all at the expense of not being able to do anything else on the computer at the same time.

---

### Post by ArtInvent on 2008-07-04
I have a pretty similar level of computer, and also switched to Ubuntu AMD64 with the Hardy re-install, pretty much just because I heard Cinelerra runs better on 64 bit. It's better, but not really faster. Still, due to my preliminary tests with AVCHD footage, I'm staying away for at least a year or so. I would love an HF-10 or 100 but I just feel the workflow will be way too much. As with my HV-20, it's just cumbersome enough that I basically never used the camera. I probably won't give full 1080 a go again until something on Linux can edit it directly (or at least make an automatic proxy or automatically transcode it to a near lossless format.) I'll probably have a quad core by that time and 4 gigs of RAM, which is what you'll need.

I know Cinelerra can edit 720p mjpeg transcodes vith real time playback (that's what I usually use) and mpeg-4 in non-real-time; that's fine for my present casual use. It's not really fine if you've going for the fantastic imagery that 1080 ought to give you.

I've never been able to get a h.264 file out of Cinelerra that's playable on anything. So I've been rendering in mpeg-4 and then do yet another transcode into h.264 if I need to send it to someone or upload to Vimeo. So if I shoot in AVCHD, then transcode to something for editing, then mpeg-4, then h.264 - four encodes, all lossy. Why bother to shoot in pristine 1080 at this point?

I honestly believe that, once you get through all the transcoding and editing and rendering - if you're careful - you may be starting with great 1080 but you will effectively be ending up with the visual equivalent of a very good 720p image. 

The whole 'full 1080' thing has happened a bit prematurely imho. Even with a good computer it's still too machine intensive for my taste. It's a shame that 720p was never really given a shot on the mainstream prosumer camcorders. And these cams can switch down to standard def - but not to 720. WTF? Good 720p is as good, or better than 90% of the HDTV shown on television these days, and it's just so much easier to deal with all around. But if you can find a 720p camera at all it's a piece of junk. 

There are some little hybrid still higicams coming out that shoot 720p30 in a decent manner. I just ordered a Samsung NV24HD pocket cam - seems to offer the cleanest footage of those I've seen. Almost ordered the Panasonic DMC-TZ5 because it shoots 720p30 in mjpeg which doesn't look too bad - can be opened directly in Cinelerra (just think!) But I'm a little more impressed with the Samsung's footage. Hell, it's under $300 - thinking about getting two so I can do 2-camera shoots! 

Today I compared some NV24 720p footage I got off Vimeo with some over the air shows in 1080i. (The signal was pretty compressed, but still.) The Samsung looked as good and often better. 

Now, I'm not saying that this little Sammy is a killer camera. It's just that AVCHD + Cinelerra/Linux = misery. I would almost rather go back to Windows. Until then I think I'll be happier with 720p and probably do a lot more actual videos, get a lot more up on Vimeo, and do a lot less futzing with transcoding and watching my $1000 camcorder sit on the shelf and rapidly become obsolete.

Okay, harangue over.

---

### Post by motin on 2008-07-05
> **shanek said:**
> Ok, I played a bit more with the -sameq and -b switches this week. One problem I was having is that many of the files I'd converted using the -sameq switch would crash Cinelerra. They were also substantially larger - I'm looking at one right now that was 1.9 G out of the camera, and ended up being 4.2 G after converting. The HF100 camera supposedly records at a 17000k bitrate, so I tried dropping the -sameq and replacing it with the -b 17000k. Suddenly, I can open up the files without crashing Cinelerra, and they're about the same size as the original file - maybe another 100 Megs or so larger. Video still looks very good.

By the way, my computer's got 3G of RAM, and an AMD 4200+ X2 (dual-core) processor. It looks like FFMPEG is converting the video at about 9-11 frames per second, so conversion time is about 3x the length of the original movie. I can still play UT2004 while the conversion is going on, so it's not all lost time :) I wonder if using the -threads switch would speed things up at all at the expense of not being able to do anything else on the computer at the same time.

What destination format were you experimenting with? mov? My experience above is as well that converting with -b 17000k into mov using ffmpeg leaves you with files only marginally larger (maybe 10%) files in good quality. 

Interesting to hear if -threads can speed up the conversion two-fold... that would make around 20 frames per second according to your estimate - that is not bad at all!

My biggest concern currently however is about finding a way to archive the footage on a common media like DVD. Going down from 17 mbps to around 6mbps for default DVD encoding doesn't sound like a good trade-off. And Blu-ray burners costs more than the camera itself... Any ideas here?

---

### Post by ArtInvent on 2008-07-05
You seem to be talking about DVD-Video format. This would not really be 'archiving' as you are obliterating your precious 1080 resolution. DVD-Video resolution is 720x480. HF10 is 1920x1080. ???

I wouldn't even archive standard def DV tapes to DVD-Video format as this is a serious degradation in quality, going from 25Mbps to 6-something. (Actually AVCHD in high def takes up less space than DV - 17 vs 25.)

If you really want to put it on DVD discs, just burn the original .m2ts files on as data. After filling the 16GB memory you will need 3-4 DVD's. Obviously, it won't be playable on a normal DVD player. Though I think there are some HD-DVD players that can play these files.

'Archiving' to some kind of burned media is kind of an outmoded idea at this point. For backing up your footage, get a couple of USB 500GB HDD's - they're cheap and getting cheaper all the time. And will take up a lot less time, effort, and shelf space compared to burning to DVDs or BluRay. I have multiple hard drives scattered around, the best insurance there is. That's like having 500 DVD's and it will 'archive' any format in completely original form.

---

### Post by motin on 2008-07-05
Thank you for your insightful reply!

It seems now that the only viable archive solution is external HDs or Blu-ray discs...

I found a well-priced Blu-ray burner for 2000 SEK (about $300): [http://www.prisjakt.nu/produkt.php?p=248221](http://www.prisjakt.nu/produkt.php?p=248221)

Looks like a viable archive solution, especially since Blu-ray players will be able to play the discs directly without having to play them on a pc with a AVHCD-codec. 

The question then becomes: does anyone know the correct format and ffmpeg parameters to burn and author HD-quality Blu-ray video discs?

---

### Post by ArtInvent on 2008-07-05
Have you priced BluRay recordable discs?

DVD blank: $0.20
BluRay blank: $20.00

100 times the cost for 5 times the capacity. Then you have to have a burner. And without a player for your tv your investment wouldn't really make that much sense. 

I keep figuring the costs on these things will come down, but they haven't.

Can't tell you how many DVD's I've thrown away because the burn didn't work right for some reason. Or printing the label didn't come out right. A ruined BluRay burn would make me cry.

A DVD burner back in the day was pretty useful. You can archive movies and also send movies to people because they're so cheap, and guaranteed everyone can play a DVD. No one I know has a BluRay player and even if they did I could hardly afford to send them a $20 disc on a lark.

I find it easier, faster, and cheaper to hook my computer up to my tv with a long component or HDMI cable. And archive on HDD's. And send people all my HD videos by posting them to Vimeo. At some point Vimeo or whatever comes after will allow you to post 1080 online, edited or straight from the camera . . . Frankly, I just don't see much of a future for optical media anymore. 

If BluRay were reasonably priced and had 100GB I would be interested. Maybe.

---

### Post by shanek on 2008-07-06
> **motin said:**
> What destination format were you experimenting with? mov? My experience above is as well that converting with -b 17000k into mov using ffmpeg leaves you with files only marginally larger (maybe 10%) files in good quality. 

Interesting to hear if -threads can speed up the conversion two-fold... that would make around 20 frames per second according to your estimate - that is not bad at all!

My biggest concern currently however is about finding a way to archive the footage on a common media like DVD. Going down from 17 mbps to around 6mbps for default DVD encoding doesn't sound like a good trade-off. And Blu-ray burners costs more than the camera itself... Any ideas here?

I'm running a conversion right now with -threads set to 2. I was getting around 10 fps, and using the threads option at 2, I'm getting 13 fps. The computer is still completely usable for other tasks while this conversion is running. 

The archive thing was something I was wondering about too. The scenes I'm shooting at the moment are only about 20-30 minutes, so the .mts files I get will fit on a data DVD no problem. On the other hand, I'm not too crazy about storing files on DVDs for the long term. Hard drives seem the way to go for me too.

I agree with ArtInvent that Blu-Ray burning isn't viable for the moment, and won't be until the price comes down below $1 per disc, and a burner is less than $75 to buy. Besides, I bet that 3 years from now, you'll get a much faster burn rate. Most of the discs are rated for 2x transfer rate (is that the same as DVD 2x?) and a few are 4x. Have fun burning a 25G disc at that kind of speed!

The other Blu-Ray problem is that I don't know anybody who even has a blu-ray player, other than one guy who went out and bought a PS3.

The main reason I'm interested in having a 1080p camera is that we are doing a project that we want to keep the results around for people to view years from now. By then, the TV resolutions will probably have jumped again, but 1080p will look a whole lot better than 480i ;) (or even 720p for that matter) If we have to wait a year or three for direct AVCHD editing, it's not a big deal, and we can limp through with our current setup.

---

### Post by motin on 2008-07-06
> **ArtInvent said:**
> Have you priced BluRay recordable discs?

DVD blank: $0.20
BluRay blank: $20.00

100 times the cost for 5 times the capacity. Then you have to have a burner. And without a player for your tv your investment wouldn't really make that much sense. 

I keep figuring the costs on these things will come down, but they haven't.

Can't tell you how many DVD's I've thrown away because the burn didn't work right for some reason. Or printing the label didn't come out right. A ruined BluRay burn would make me cry.

A DVD burner back in the day was pretty useful. You can archive movies and also send movies to people because they're so cheap, and guaranteed everyone can play a DVD. No one I know has a BluRay player and even if they did I could hardly afford to send them a $20 disc on a lark.

I find it easier, faster, and cheaper to hook my computer up to my tv with a long component or HDMI cable. And archive on HDD's. And send people all my HD videos by posting them to Vimeo. At some point Vimeo or whatever comes after will allow you to post 1080 online, edited or straight from the camera . . . Frankly, I just don't see much of a future for optical media anymore. 

If BluRay were reasonably priced and had 100GB I would be interested. Maybe.

True, I had not considered Blu-ray media. The lowest prices I could find in Sweden was $6-$10 per disc (when buying 5-packs or 10-packs). However, the cheapest DVD media was around $0.12 per disc (in 25-pack spindle), so the relationship 100 times the cost is not inaccurate at all! It's basically insane...

> **shanek said:**
> I'm running a conversion right now with -threads set to 2. I was getting around 10 fps, and using the threads option at 2, I'm getting 13 fps. The computer is still completely usable for other tasks while this conversion is running. 

The archive thing was something I was wondering about too. The scenes I'm shooting at the moment are only about 20-30 minutes, so the .mts files I get will fit on a data DVD no problem. On the other hand, I'm not too crazy about storing files on DVDs for the long term. Hard drives seem the way to go for me too.

I agree with ArtInvent that Blu-Ray burning isn't viable for the moment, and won't be until the price comes down below $1 per disc, and a burner is less than $75 to buy. Besides, I bet that 3 years from now, you'll get a much faster burn rate. Most of the discs are rated for 2x transfer rate (is that the same as DVD 2x?) and a few are 4x. Have fun burning a 25G disc at that kind of speed!

The other Blu-Ray problem is that I don't know anybody who even has a blu-ray player, other than one guy who went out and bought a PS3.

The main reason I'm interested in having a 1080p camera is that we are doing a project that we want to keep the results around for people to view years from now. By then, the TV resolutions will probably have jumped again, but 1080p will look a whole lot better than 480i ;) (or even 720p for that matter) If we have to wait a year or three for direct AVCHD editing, it's not a big deal, and we can limp through with our current setup.

Thanks guys for your thoughts. Now, HDD archiving feels like the only viable solution. I'll happily burn DVDs to be able to watch them with friends and family on non-1080 capable TVs and/or upload to Vimeo, but also archive the m2ts files to HDD. Whenever all TV's are capable of 1080 and there exists some good option to archive by other means than raw HDD (for instance cheaper Blu-ray solutions or cheap media-devices with large flash memories, AVCHD codecs and HDMI output jacks for direct play) - that day that sorrow.

Everything feels in place now. What would be nice now is an easy to use graphical tool to organize, preview, convert (to cinelerra-editable as well as to DVD format) and archive (to HDD) m2ts-files as well as keep track of where all archived m2ts-files are located (which HDD etc). 

Maybe Kdenlive does this now automatically with the latest ffmpeg version? Gotta try...
EDIT: For the record, Kdenlive performs just as badly even with the latest ffmpeg...

---

### Post by ArtInvent on 2008-07-06
> 
The main reason I'm interested in having a 1080p camera is that we are doing a project that we want to keep the results around for people to view years from now. By then, the TV resolutions will probably have jumped again, but 1080p will look a whole lot better than 480i ;) (or even 720p for that matter) If we have to wait a year or three for direct AVCHD editing, it's not a big deal, and we can limp through with our current setup.

This is all mostly true. 1080p24 or 30p would be better to have for the future than 720p30 or 24p - all else being equal. And today you don't have much of a choice if you want the highest quality footage. It's 1080 or the highway.

However, the fact remains that we have never seen a really fine prosumer $1000 level camera that shoots 720p60 and 30 and 24 and approaches the *true potential of that resolution*. With a relatively large sensor, it could have much bigger photosites allowing super low light performance, great lens and handling etc. Maybe with a very high bitrate mpeg-4 or some even less compressed format. Possibly even higher frame rates like 120p would be possible for incredible slo mo with still 720p resolution. So much easier to edit, view, store etc. And better potential for avoiding all these multiple lossy re-compressions. I believe that such a camera would be extremely compelling to most prosumer-level shooters. 

Some people would still choose 1080, sure. I just think there ought to be a choice.

---

### Post by Cresho on 2008-07-14
> **ArtInvent said:**
> Wow, this is sad. I'm looking at buying an AVCHD cam. Maybe a Canon HF-100 or a new Panasonic that isn't out yet. But then I tried to download a sample of AVCHD footage and simply play it back on Ubuntu. No luck so far! Not even halting playback in VLC or MoviePlayer. Zippo. Is there a way to get the codec to play this stuff?

I saw that Corel offers LinDVD to at least play back these files - but you can't get it at any cost because they only offer it to OEM's! Thanks guys!

I just sold a perfectly good Canon HV-20 because I really hate tape, and the editing workflow, especially in 24p on Linux and Cinelerra, is just too cumbersome. But AVCHD is even worse. 

I think that perhaps Kdenlive will be supporting AVCHD in the next few months, they mention it first thing on their roadmap. 

But it sure would be nice to simply have a codec support for this in VLC or MoviePlayer or SOMETHING. It's pretty pathetic that this codec has been out for quite a while now and is becoming the predominant HD format and we can't even *play it back*.

xbmc plays 720p 1080i 1080p at any fps.  I have a sanyo xacti hd1000 or hd 1000 and they play very fluidly.  is is called "x-box media center".  It is open source.  It runs natively on linux.  It uses the keyboard.  It has lots of hidden keys like \ for full screen and tab for full length.  It uses projectM running way faster than any other mediaplayer.  I get like over 300fps.  ProjectM is enabled with a certain command found in the xbmc forums.  Darn!  I'm rambling.

For everybody here wanting to burn to blue-ray, I recommend archiving your mp4 videos or high definition clips for one reason alone: incase you want to edit them into a new video (like archiving the tapes).  The videos look good on a dvd if edited good enough andplayed back on a progressive dvd player.  Right now, there is no Fraken way i'm going to be paying 20 plus dollars for a blank blue-ray disk.

honestl!  I seen too many 1080p junk and movies and all(well, you get the drift).  I been readig up on the new technology coming soon with 64bit color....really 24bit is terrible. and super ultra high definition video that will make 1080p look like vhs.
[http://en.wikipedia.org/wiki/Super_Hi-Vision_television](http://en.wikipedia.org/wiki/Super_Hi-Vision_television)

I recommand 720p at 60fps camera.  1080i or 1080p at 30 is just so wrong (it would be nice to see 60fps at least).  if you read up on the section of potential advantages, the upscaling technology is way beyond what we currently run.

I'm almost done with my tutorial with h.264 editing in ubuntu linux.

---

### Post by ArtInvent on 2008-07-14
> **Cresho said:**
> xbmc plays 720p 1080i 1080p at any fps.  I have a sanyo xacti hd1000 or hd 1000 and they play very fluidly.  is is called "x-box media center".  It is open source.  It runs natively on linux.  It uses the keyboard.  It has lots of hidden keys like \ for full screen and tab for full length.  It uses projectM running way faster than any other mediaplayer.  I get like over 300fps.  ProjectM is enabled with a certain command found in the xbmc forums.  Darn!  I'm rambling....

I'm almost done with my tutorial with h.264 editing in ubuntu linux.

I have looked at that camera, the Sanyo Xacti HD1000 for one reason: as far as I can research, it's the only consumer camera on the market that will record in 720p60. It's also the only camera that will record in both 1080i and 720-(anything)! 99% of all the others either go for full 1080 or all the way down to SD - 480. Sucks. Furthermore, the update of that camera (the HD1010) is the only camera that records 720p60 as well as 1080p30. The other nice thing about the Sanyo is that the original footage files are just mp4s with no interlacing. Why doesn't everyone use this format?!

Unfortunately it is about the same price, if not more, than the Canon HF100. Overall, the Xacti's are not nearly the camera/video quality that the Canon is. I just hate the whole .m2ts format, progressive recorded as interlaced - none of which makes no sense any longer and is a complete pain. 

Where is your h.264 tutorial?

---

### Post by ArtInvent on 2008-07-14
I've been thinking more about getting a Canon HF100 / HF10, so I decided to try and find some actual camera samples on the web and try and view and edit them. I looked at the AVI conversion script mentioned here. But AVI files are not that useful to me. I ended up going with a custom compiled ffmpeg with some success. I want to be able to edit the files in Cinelerra, and for that you really need a .mov file with aac audio and mpeg4 video (not h264). Cinelerra is very picky. 

First I compiled the latest ffmpeg from CVS. I tried to follow the Wesley Bailey tutorial mentioned in previous posts at [http://wesleybailey.com/articles/transcode-divx-with-ffmpeg-for-xbox-360]("http://wesleybailey.com/articles/transcode-divx-with-ffmpeg-for-xbox-360") . I had a few unresolved dependencies, so I had to go and look for more codec packages. But eventually it configured and compiled, not too much trouble. 

I managed to find two samples from an HF10 straight from the camera at this Japanese website review page - [http://www.watch.impress.co.jp/av/docs/20080206/zooma344.htm]("http://www.watch.impress.co.jp/av/docs/20080206/zooma344.htm") 

Then I found some suggestions for commands to get a Cinelerra-happy file. Here is one that worked:
```
ffmpeg -i input.m2t -acodec libfaac -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 25000k -copyts output.mov
```

I also decided to try transcoding directly to 720p. It's one of my pet peeves that none of these new super video cams allow you to set the camera to 720. Many times that's all I need and it would really save card space. Anyway, here is the command I used:
```
ffmpeg -i hf10.m2t -acodec libfaac -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 15000k -copyts hf10.mov
```

Note that I'm keeping the bitrate pretty high. Mpeg4 is not as efficient a codec and needs a much higher bitrate to keep the quality decent. I'm sure I am still losing some quality in this, but that's why one keeps the original m2ts files around, isn't it?

The resulting file plays back beautifully in movieplayer. I have an AMD Athlon X2 with 2GB and Nvidia 6200-ish level graphics - not gamer quality by any means. I've also switched to 64 bit Ubuntu 8.04 because I've heard Cinelerra works better in 64b. (It does.)

What I was not expecting was how well the transcoded mpeg4 file works in Cinelerra. Previously I have worked with 720p footage in Cinelerra, and I tended to use mjpeg codec - mpeg4 looks better but seemed to cause the program to bog down. When I tried footage in mpeg4 before it seemed pretty sluggish, slow compositor playback, etc. I don't know if recompiling ffmpeg helped, but with this .mov file even at 1080p resolution, Cinelerra seems quite happy, plays back in the compositor in real time without dropping too many frames, even during a crossfade transition it doesn't complain too much. Renders back to mpeg4 completed well and quickly and looked quite good. 

Note that I believe this works pretty well with the cam set to 30p. I saw some footage with some juddering that looked like it might have been shot with 24p. This would require the whole reverse pulldown rigmarole that I struggled with using my HV24. Handheld with stabilization on I never quite figured out what was causing the juddering. I would will stick with 30p to avoid both the juddering and the RP hassles.

This may lead me to reconsider whether I'm ready to deal with the full 1080 resolution files and workflow. It's still a pain to have transcode, but I was thinking I needed a whole new quad core to deal with this stuff. It may not be so bad.

It would still be nice to be able to just play the m2ts files without transcoding first. I've heard that compiling mplayer from source can achieve that. I may want to look into that as well. If anyone has done that successfully give us a heads up.

---

### Post by Cresho on 2008-07-15
the spec for the hd1010 records 1080p@30fps 1080i@60fps.  I am skipping this model for the newer one.  I am hoping for 1080p@60fps at least with better focus and night recording.

Everytime I load up a video on my ubuntu box with my hpw2408, the colors are just way beautiful.  Just watching beach shots, mountain shots, baby shots...amazing stuff!

I basically use my 1080i@30fps for things that don't move too much.  I use the 720p@60fps for fast moving, walking, scenes.

---

### Post by ArtInvent on 2008-07-15
> **Cresho said:**
> the spec for the hd1010 records 1080p@30fps 1080i@60fps.  I am skipping this model for the newer one.  I am hoping for 1080p@60fps at least with better focus and night recording.

Everytime I load up a video on my ubuntu box with my hpw2408, the colors are just way beautiful.  Just watching beach shots, mountain shots, baby shots...amazing stuff!

I basically use my 1080i@30fps for things that don't move too much.  I use the 720p@60fps for fast moving, walking, scenes.

Sounds like you maybe could use a tripod and better OIS for handheld shots.

I am not so stoked about the near-time prospects of 1080p60, and if my camera had it available I would probably not use it. This represents a doubling of the data rate, assuming you want the same image quality. These will either be enormous files or seriously compressed and compromised image quality. Computers are already barely able to handle 1080p30, and even at 17Mbps compression we have just started to get decent image quality. To get that same image quality in 60p you would need 34Mbps. Just don't think that's gonna happen next year, that's a data rate that in AVCHD would not even be playable on 99% of computers. I would prefer 30p with a bitrate closer to 20Mbps+ if I could get it; a larger imager, next; better lens with wider angles, third; better stabilization. We don't really need more frames any more than we really need more pixels, what we need is better pixels. I absolutely applaud current Sanyo cameras for having sane choices in frame rates and image sizes. A lot of people could use 720p60, but they've bought these super HD cameras that have no 720 switch at all. 

On the other hand, most problems that can be helped by a higher frame rate, are probably due to camera movement, rather than subject movement. I mean, look at all the cool sports and action adventure films that are all shot in 24 frame. Personally I would rather see amateur video users discover monopods and tripods and other stability aids. I would rather buy a camera that's gyro stabilized or has a super effective form of optical image stabilization. 

Oh yeah, almost forgot to mention, while we're on wishlists - how about an awesome video editor that works on Ubuntu?

---

### Post by ArtInvent on 2008-07-15
Well, on the strength of my experience with Cinelerra and ffmpeg transcoding, I went ahead and ordered a Canon HF100. At $650 it seems like a bargain - the same price as what I sold the HV20 for on eBay. 

Compared to what I went through with HDV tape, it turns out that transcoding and editing should be far easier with this AVCHD system. I shot tape for years but I always hated the whole 'capture through firewire' rigmarole, not to mention the way I had to transcode, de-interlace, and reverse pulldown the 24p footage. It just stifled my whole process to the point where I pretty much left the camera on the shelf. Recording to SD cards is really my cup of tea. 

I'm also probably going to stick with 30p, just seems to work better than the screwy way Canon still does '24p.' 

Thanks to everyone for posting their experiences and help with ffmpeg compiling and command variations. 

If Kdenlive v0.6 ever gets released, it may have direct AVCHD editing. That would be pretty awesome - you might even be able to edit straight from the SD card!

---

### Post by Cresho on 2008-07-17
I'm currently experimenting with ffdshow beta5, virtualdub, and wine.  So far, I am able to view my 1080i 60fields/s videos on virtualdub and convert it to something else.  My workflow is coming together nicely so far.

At the moment, I have...

1. MP4Cam2AVI_v2.71.zip
2. virtualdub and ffmpeg under wine
3. xbmc for video viewing  and totem player(after conversion)


Under Linux, my sanyo 1080i videos are a bit of a pain to view but not after virtualdub conversion.  I had a few issues at first but it was not that hard to figure out what was going on.  My first bug I ran into: I had problems trying to view videos at all in virtualdub.  So what I did was go into options->prefference->display-> tick Use OpenGL

ahh, i just finished rendering my first 1080i video.  I set the audio for direct streamcopy and THen I set the video for normal recompression.  I use ffmpeg and changed my video to h.263+ or h.264.  I was also able to convert to divx.  I am also looking into converting it to mov files.

anyway, ill keep you guys posted.  I know and seen the mts2 video done with virtualdub.  If anybody has a link for one, i can try it out on my first test and ill post a small tutorial.

I have a 2 questions.  my 1080i videos get converted to 1080 but I don't know if it's i or p.  also, my 1080i is 60fields/s.  my new videos converted are now 1080@60fps and they do look like 60fps because i have seen other videos @30fps and looks poor.  Does this mean that I am @60fps?  the second question is if anybody have a workflow for hd video to blueray?

---

### Post by ArtInvent on 2008-07-17
(Edited) The HF100 makes a new .m2ts file whenever you stop and start the recording. (Not sure if you can 'pause' recording to get around this.) Also, it will not write any single file longer than 2GB so will create new .m2ts files every time it reaches that limit. If you just play back the second file after this break, you will probably lose frames, you need to recombine the files. Recombining also makes it easier to transcode, you only have to run your command on one file, don't need a batch command either.

It might be best to make a note of which scenes you want to combine by reviewing them in-camera, then transfer from the cam and pull all those .m2ts files into one directory. CD to that directory and run this command to combine all the files into one.
```

cat *.m2ts > combined.m2ts
```
or you can name each file by name thusly:
```
cat file1.m2ts file2.m2ts file3.m2ts > combined.m2ts
```
I tried this, combining three files into one, then transcoded with ffmpeg, and the resulting file played fine. With lots of other codecs, a simple cat command will not work, but with .m2ts files it is said to be fine due to the file structure. I read about this at the HF10 thread over at avsforum.com but it was buried in about 50 pages of thread.```

```



EDIT: Actually, I tried this again and the later segments of the conjoined file wouldn't play correctly. Can't figure out why it worked once but then not again. Wondering if the various .m2ts files were shot with different framerates or something. I'm still experimenting using clips others have posted. I should have my camera tomorrow so hopefully can figure this out.

---

### Post by Cresho on 2008-07-18
hey artinvent, have you tride transcode?

here is a script i use to capture video from my tvtime with video playback

-----------------------
#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

gnome-terminal --execute transcode -x v4l2,v4l2 \
           -M 2 \
           -i /dev/video1 \
           -p /dev/dsp \
           -w 6000 \
           -y ffmpeg \
           -F mpeg4 \
           -c 02:30:00 \
           -g 720x480 \
           -f 0,4 \
           -I 1 \
	   -J resample,levels,smartyuv,pv \
           -u 100 \
           -Q 3 \
           -Z 640x480,fast \
           -E 48000,16,2 \
           --lame_preset medium \
           -o /Multimedia/Cresho-stuff/My_Videos_Projects/tvtime-recorded/-${TODAY}-${NOW}.avi \




amixer -q set "Line" 100% mute &
----------------------------------------------------


I heavily modified this to unmute or mute my stuff and those lines can be removed.  also, I record line in, record from video0 or 1 and show an output but you can change that to a file..  You can modify each line as you want.

you can install it by sudo apt-get transcode and it is command line based or use a script.

Maybee this can help too!

[http://www.transcoding.org/cgi-bin/transcode](http://www.transcoding.org/cgi-bin/transcode)

In anycase, I am curious about your camera since my uncle wants me to set him up with the tools.  He is leaning towards a canon and I am curious how your workflow is coming along.

---

### Post by ArtInvent on 2008-07-18
I think there is a fundamental problem with the way I am decoding the  MTS stream. My transcodes from ffmpeg into mpeg4 .mov files (whether to/from 1080 30p or 60i 720 or whatever) all 'stutter' badly during almost any camera movement whatsoever, even relatively smooth tripod pans. (In a perfectly still tripod shot I don't notice it.) It's basically like I am dropping frames, lots of them. The stuttering is horrible and almost unwatchable. I see complaints about so called 'stuttering' on camera forums with many cameras such as the Canons, but I think there is some confusion. Many people seem to attribute this to the 30p or 24p framerate, but there is a **big big** difference between the normal motion blur inherent in 24p or 30p frame rates, which is really not that bad, and what I am referring to as 'stuttering.' Other people seem to think there's some problem with the image stabilization system, but I don't think either of these is the problem at all. 

I have seen a lot of 30p, correctly done, and it looks just fine. I have right now a Samsung NV24HD which shoots natively in 720p30 to h.264 files. You can carry the camera around, it's a tiny lightweight thing, but there is never any of this stuttering.

Furthermore, when you play back 30p in the camera itself, or through the camera connections to an HDTV, there is no stuttering. You can tell the difference between 60i which has that smooth video quality (don't really like it myself) and 30p footage, which has more of a film look. I would much prefer to have good 30p footage. Is there something I'm doing wrong with my ffmpeg command?

I realize that everything in an AVCHD mts stream is encode as a 60i stream. But I thought that this was being correctly decoded by ffmpeg.Or is there some other problem? 

I had this problem with my HV20 as well, only in that case I was shooting always in 24p. I'm not sure I've ever really transcoded this stuff correctly.

My ffmpeg gives line after line of something like this:
```
[h264 @ 0x7e49c0]PAFF + spatial direct mode is not implemented
```

Since I got playable footage I didn't think this was a problem but now I think it's just dropping frames.

---

### Post by ArtInvent on 2008-07-18
> **Cresho said:**
> hey artinvent, have you tride transcode?

here is a script i use to capture video from my tvtime with video playback



What are you using tvtime for?

I have looked into transcode and they never say anything about AVCHD support. Does it work on AVCHD?

---

### Post by ArtInvent on 2008-07-18
I've now compiled mplayer from the latest cvs trunk, getting the latest codecs at the mplayer website. This allows me to use mencoder on the HF100 files. I've generally had good luck with it in the past, rather than ffmpeg, which is giving me stuttering files.

The output from mencoder is a huge improvement and looks awfully good. No stuttering. I think it's still dropping a few frames. Console output indicates it's dropping about 3-5 frames in the first 2-3 seconds of each MTS file, but then it seems to settle down. 

Here is the mencoder command I'm using. Instead of a bitrate I'm using vqscale=2 - this supposedly gives the highest possible quality for the mpeg4 codec in only one pass, and though it's bit-wasteful, I'm not concerned with filesize, I just want pristine files that Cinelerra can edit. Files are about twice the size of original MTS files. Also note that this is pretty fast encoding - about 1/2 realtime. 

```
mencoder 00014.MTS -o 00014.mov -oac lavc -ovc lavc -lavcopts acodec=libfaac:abitrate=256:vcodec=mpeg4:vqscale=2 -of lavf -lavfopts format=mov -fps 60000/1001 -ofps 30000/1001

```

Next I'll do some editing and rendering in Cinelerra. I've imported this output to the timeline, but no time for more right now.

---

### Post by Sean4000 on 2008-07-19
I think Lumiera is going be the answer to all of our NLE needs.

---

### Post by Cresho on 2008-07-20
Lumiera?  Thanks for the post and That is a good find.

I finaly managed to get virtualdub to produce 1080i 60fps in various ways playable and editable easily in linux.

my 1080i files can be converted in many ways such as

1. 1080i 60fps to 1080p 120fps(and yes this produces fluid motion from choppy motion)

2. 1080i to 1080p with deinterlace using bob in 3 versions
   a.  blend fields together (film look)
   b.  dublicate first line   (sharp look)
   c.  dublicate second line  (sharp look)

and ontop of that, I can sharpen the videos further providing even sharper image and smoothen out anomalies that make each frame like a photo.

The guy tried making a virtualdub for linux but found it to be difficult.  I am just glad it works very good under wine.

Now that I have a workflow, I am going to try this method with the canon files and post information here.


ArtInvent!
ohh btw, I tried using the mencoder with my file but get tons of errors.  appearantly sanyo and apple have an issue with the h.264 spec.  anyway, Do you have a video so I can have a frame of refference on what you are using to convert your files?  I need to check out the mencoder and figure out why my output has many bunch of errors.

---

### Post by Sean4000 on 2008-07-20
[www.lumiera.org](www.lumiera.org)   

I do think this will be huge! You can even chat with developers and send in tips/ suggestions.

¨¨Create a new acct under IRC pick a screen name. I connected with the server irc.freenode.org, but I think you can just join with the default irc.ubuntu.com.

Then it'll ask you to verify your screen name. type /nick (your nickname)
then to join lumiera channel its /join #lumiera   ¨¨

---

### Post by ArtInvent on 2008-07-22
> **Sean4000 said:**
> [www.lumiera.org](www.lumiera.org)   

I do think this will be huge! You can even chat with developers and send in tips/ suggestions.



Sure, Lumiera will probably be great, good on them. But they're just getting started. It will probably be at least a year before they even have a beta release. An NLE, especially an advanced one like Cin/Lum, is a very complex piece of software. I need an editor I can use, like, while I'm still young. 

I've done some AVCHD to MJPEG conversions using mencoder. This is about the only format that allows me to edit in Cinelerra with near real-time playback. I've used MPEG-4 too which works pretty well but the playback just doesn't really work. It seemed that doing the conversion with ffmpeg to MPEG-4, the playback in Cin. was good, but ffmpeg drops frames all over and the file's not really usable. Looks like MJPEG will have to do for a while.

---

### Post by Sean4000 on 2008-07-23
> **ArtInvent said:**
> I need an editor I can use, like, while I'm still young.

That&#347; why I have a mac mini loaded to its little hilt running Avid/FCP and Premiere. It is my main editor and it does the job well. However, from I told from a developer friend on the project, Lumiera will be Avid, FCP, Premiere plus Smoke rolled into one. Minus the price tag of course.

Beta ETA Fall 08/Very early 09.

---

### Post by Cresho on 2008-07-24
I actually preffer converting my high definition video using algorythm lanczos3.  It is lossless.  high definition conversion to dvd quality is by far the best.  NO other video softwar can do this.

here is my example.  The high definition videos look awesome converted to dvd. It comes from my hd1000


These are not pictures.  these samples are actual video pics.  the dvd quality is a down converted from a 1080i 60fps sample. in order it is dvd to 1080i to 1080i with modified image sharpness increased.

my current workflow is using ffmpeg beta 5 for decoding, xvid for encoding.  I first start off with mp4cam2avi, to virtualdub to ManDVD with modified slideshow creator fix.  One problem with slideshow is that you cannot combine 4to3 with 16to9.  It is one or the other.

---

