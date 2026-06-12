---
title: "how to: convert mkv to mp4 (mpeg - 4)"
date: 2012-03-26
forum: Multimedia Software
---

### Post by Claus7 on 2012-03-26
Hello,
(maverick)
[LIST]
[*]System->Administration->Synaptic Package Manager
then
[*]Settings-Repositories
(Ubuntu Software->Downloadable from the internet
have clicked the first 4 options)
[*]then install:
mkvtoolnix-gui
[*]and go to Applications->Sound and Video->MKV files creator

[*]from there: as input add the mkv file you want to convert
[*]and as output write the file name you like with the ending mp4->
[*]start muxing
[/LIST]

note: do not change anything else, and in the window in-between with some options checked leave it as it is

Regards!

---

### Post by ron999 on 2012-03-26
> **Claus7 said:**
> 
mkvtoolnix-gui

[*]and go to Applications->Sound and Video->MKV files creator

[*]from there: as input add the mkv file you want to convert

[*]and as output write the file name you like with the ending mp4->

[*]start muxing


Hi
This method looks suspicious.
Surely you will only create another matroska file - but with an mp4 suffix.;)

---

### Post by evilsoup on 2012-03-26
I don't know about this software, but ffmpeg reads the extension on the end of the output file in order to determine what container format to use. The GIMP does the same thing.

---

### Post by papibe on 2012-03-26
In my experience, most of the time you don't need to 'transcode' mkv -> mp4. I've seem that most of mkv files have h264 video, and either AAC, AC3 or MP3 audio.

Then, you can extract the tracks, and create a new mp4 container very easily. This is considerable faster than 'converting' the file.

Just some thoughts.
Regards

---

### Post by Claus7 on 2012-03-26
Hello to all!

Thank you very much for your answers. I will try to answer/comment on all of them and add some new things:

> **ron999 said:**
> Hi
This method looks suspicious.
Surely you will only create another matroska file - but with an mp4 suffix.;)

@*ron999*: I totally agree. The first time I tried this kind of thing I thought exactly the same, yet while opening the properties of the file (it seems) that it is indeed (I suppose) a mp4 file. I might make a mistake here.

> **evilsoup said:**
> I don't know about this software, but ffmpeg reads the extension on the end of the output file in order to determine what container format to use. The GIMP does the same thing.

@*evilsoup*: I tried ffmpeg, yet I do not know the right combination of options. Also, I suppose that it can be accomplished with mkvmerge, provided that the right options are given or the right version (maybe a newer one) is used. I'm using 4.0.x and if I state it correctly, at the time of writing, 5.4 is the latest.

> **papibe said:**
> In my experience, most of the time you don't need to 'transcode' mkv -> mp4. I've seem that most of mkv files have h264 video, and either AAC, AC3 or MP3 audio.

Then, you can extract the tracks, and create a new mp4 container very easily. This is considerable faster than 'converting' the file.

Just some thoughts.
Regards

@*papibe*: I have to admit that for an almost half GB file, 10 seconds max is not a big deal. I do not know how to do it in less than that time...

Thank you for filling in in this issue. Now something that worked flawlessly, yet it takes some time in order to be accomplished.

**open vlc:**
[LIST]
[*]go to Media-> Convert/Save
[*]and there under tab File add the mkv file you would like to convert
[/LIST]
and Click in the lowest part of this window the option *Convert/Save*.

**set Destination:**
e.g. /home/*your_user_name_here*/Desktop/*name_of_output_file*.mp4

**now the options:**
(under settings)
i) Profile: Video - H.264 + AAC (MP4)
ii) you will find a tools button on the right, hit it!
[LIST]
[*]Encapsulation: MP4/MOV
[*]Video codec: don't change anything
[*]Audio codec: Audio (checked), Keep original audio track (checked), Codec (MPEG 4 Audio (ACC)), Bitrate (128 kb/s), Channels (2), Sample Rate (48000)
[*]Subtitles (checked), right bar (empty), Overlay subtitles on the video (checked) -provided the original mkv file had subtitles-
[/LIST]
Don't forget **to save**!

Streaming is about to start. The time that is going to take, is almost the same as the time length of the video itself.

Thank you,
Regards!

---

### Post by ron999 on 2012-03-26
> **Claus7 said:**
>  yet while opening the properties of the file (it seems) that it is indeed (I suppose) a mp4 file. I might make a mistake here.

Yes, I think it is a mistake. Use MediaInfo program to check the properties properly.
From PPA here ---> [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)
> **Claus7 said:**
> 
**open vlc:**
[LIST]
[*]go to Media-> Convert/Save
[*]and there under tab File add the mkv file you would like to convert
[/LIST]
and Click in the lowest part of this window the option *Convert/Save*.

**set Destination:**
e.g. /home/*your_user_name_here*/Desktop/*name_of_output_file*.mp4

**now the options:**
(under settings)
i) Profile: Video - H.264 + AAC (MP4)
ii) you will find a tools button on the right, hit it!
[LIST]
[*]Encapsulation: MP4/MOV
[*]Video codec: don't change anything
[*]Audio codec: Audio (checked), Keep original audio track (checked), Codec (MPEG 4 Audio (ACC)), Bitrate (128 kb/s), Channels (2), Sample Rate (48000)
[*]Subtitles (checked), right bar (empty), Overlay subtitles on the video (checked) -provided the original mkv file had subtitles-
[/LIST]
Don't forget **to save**!

Hi
This is more like it....
but **video** codec should be set to "Keep original" too.
See the screenshots below...

---

### Post by evilsoup on 2012-03-26
Claus7, I was actually responding to ron999... but yeah, the downside of ffmpeg is the need to know the right options.

If the .MKVs are all similar, and all contain H.264 video and AAC/MP3 audio (or the other stuff that is compatible with .MP4s), then the 'copy' option in ffmpeg would be useful:

ffmpeg -i input.mkv -acodec copy -vcodec copy output.mp4

This takes only slightly more time than a cp operation, so I would recommend you try it out on some of your files.

If that doesn't work, and you want to encode to .MP4, then you should use the libx264 encoder for h.264 video and the libfaac encoder for AAC audio. For example:

ffmpeg -i input.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre normal output.mp4

would give you high-quality audio (audio bitrate of 192k - more than is necessary for most uses) and pretty good video (-vpre sets the video 'profile': other settings include 'hq' and 'max'. See[ here]("http://juliensimon.blogspot.co.uk/2009/01/howto-ffmpeg-x264-presets.html") for more information).

Of course, this takes actual time as ffmpeg needs to re-encode the streams (unlike with the copy function).

---

### Post by Claus7 on 2012-03-27
Hello,

> **ron999 said:**
> Yes, I think it is a mistake. Use MediaInfo program to check the properties properly.
From PPA here ---> [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)

Hi
This is more like it....
but **video** codec should be set to "Keep original" too.
See the screenshots below...

> **evilsoup said:**
> Claus7, I was actually responding to ron999... but yeah, the downside of ffmpeg is the need to know the right options.

If the .MKVs are all similar, and all contain H.264 video and AAC/MP3 audio (or the other stuff that is compatible with .MP4s), then the 'copy' option in ffmpeg would be useful:

ffmpeg -i input.mkv -acodec copy -vcodec copy output.mp4

This takes only slightly more time than a cp operation, so I would recommend you try it out on some of your files.

If that doesn't work, and you want to encode to .MP4, then you should use the libx264 encoder for h.264 video and the libfaac encoder for AAC audio. For example:

ffmpeg -i input.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre normal output.mp4

would give you high-quality audio (audio bitrate of 192k - more than is necessary for most uses) and pretty good video (-vpre sets the video 'profile': other settings include 'hq' and 'max'. See[ here]("http://juliensimon.blogspot.co.uk/2009/01/howto-ffmpeg-x264-presets.html") for more information).

Of course, this takes actual time as ffmpeg needs to re-encode the streams (unlike with the copy function).

thank you very much for your helpful responses. I tried both your proposals, which were really very comprehensible and very fast in order to be executed.

Yet, with both of them, I cannot retain the subtitles of the original mkv file. 
With ffmpeg I tried scodec (copy) without success.
As far as the vlc is concerned, subtitles do not seem to like being copied. Any idea would be more than welcome, because your proposals accelerate tremendously the conversion procedure.

Thank you once again,
Regards!

PS: I have to admit that I did not come across such detailed and comprehensible explanation in the net about such kind of conversion.

---

### Post by Claus7 on 2012-03-27
Hello,

> **evilsoup said:**
> ...

ffmpeg -i input.mkv -acodec libfaac -ab 192k -vcodec libx264 -vpre normal output.mp4

...

this one is giving me an error about libfaac, yet I guess that is because I have the ffmpeg from the repos.

Here:
[http://mytechieself.blogspot.com/2011/01/extracting-subtitles-from-mkv.html](http://mytechieself.blogspot.com/2011/01/extracting-subtitles-from-mkv.html)

I found out how to extract the subtitles, yet neither the -newsubtitle option nor vlc option helped to attach the subs to the mp4 file.

Regards!

---

### Post by evilsoup on 2012-03-27
> this one is giving me an error about libfaac, yet I guess that is because I have the ffmpeg from the repos.[URL="http://ubuntuforums.org/showthread.php?t=1117283"]
Here[/URL] is an easy way of getting all those codecs in ffmpeg, without having to compile it yourself (unless you really want to). I used option 'C'.

As for subtitles... I don't actually know if that works in ffmpeg. When I use 'ffmpeg -codecs | grep subtitle', it seems to be saying that it doesn't support SRT subtitles. So it looks like you'll have to use a different program.

Also, I'm pretty sure that .MP4s don't support SRT subtitles; you'll have to convert them to [dvdsub]("http://en.wikipedia.org/wiki/MPEG-4_Part_17") (which *is* supported by ffmpeg) and mux them in that way.

I'm not sure what program to use for that (converting your newly-extracted .SRT to dvdsub), but once you've done that you should be able to mux it in with ffmpeg.

EDIT: Wow, ffmpeg is weird WRT subtitles... it is perfectly capable of putting SRT subtitles into an MKV, but only if the subtitles come from a separate file. Not that this helps you, Claus7; you'll still have to find a way to convert SRT files to dvdsub, I'm just commenting on strange behaviour.

---

### Post by Claus7 on 2012-03-28
Hello,

> **evilsoup said:**
> [URL="http://ubuntuforums.org/showthread.php?t=1117283"]
Here[/URL] is an easy way of getting all those codecs in ffmpeg, without having to compile it yourself (unless you really want to). I used option 'C'.

As for subtitles... I don't actually know if that works in ffmpeg. When I use 'ffmpeg -codecs | grep subtitle', it seems to be saying that it doesn't support SRT subtitles. So it looks like you'll have to use a different program.

Also, I'm pretty sure that .MP4s don't support SRT subtitles; you'll have to convert them to [dvdsub]("http://en.wikipedia.org/wiki/MPEG-4_Part_17") (which *is* supported by ffmpeg) and mux them in that way.

I'm not sure what program to use for that (converting your newly-extracted .SRT to dvdsub), but once you've done that you should be able to mux it in with ffmpeg.

EDIT: Wow, ffmpeg is weird WRT subtitles... it is perfectly capable of putting SRT subtitles into an MKV, but only if the subtitles come from a separate file. Not that this helps you, Claus7; you'll still have to find a way to convert SRT files to dvdsub, I'm just commenting on strange behaviour.

thank you for your response. It did not occur to me that adding subtitles it would have been so difficult.

What I have tried up to now:
avidemux refuses to upload the subtitles
x264 encoder does not deal with sound
mencoder refuses to add subtitles
h264enc failed to convert from avi to mp4

Regards!

---

### Post by Claus7 on 2012-03-28
Hello,

> how to covert a mkv file with subtitles to mp4 with: h264/avc codec

[COLOR="Navy"]install mkvlinux[/COLOR]
(simultaneously you have installed mkvmerge)
Go to Applications -> Sound & Video -> MKV files creator
and in input tab add the mkv file you with to convert to mp4 one

*in tracks, chapters and tabs* you will find the subtitles like:
> S_TEXT/*** (ID **x**, type SUBTITLES)....

open terminal and type:
```
mkvextract tracks file.mkv **x**:subtitle.ssa
```
(where **x** stands for a number)

then [COLOR="Navy"]install avidemux[/COLOR] and open it from Applications -> Sound & Video

open the same mkv file as before with avidemux and choose the following:

[LIST]
[*]Video: MPEG-4 AVC
[*]In Video Filters choose Subtitles-> *** -> and load the subtitles file you have created (subtitle.ssa)

[*]Audio: COPY

[*]Format: MP4

[*]and press save.
[/LIST]
While doing so, you decide about the name and ending of the file (e.g. final.mp4)

Sometimes mkvmerge might crash, yet restart it.

Time of competion of streaming almost same as the length of the video (sorry about that!)

With this way you might avoid some lag that happens during conversion. Quality seems to be the same as the original file. 

And you are set.
Regards!

note: the asterisks [***] appear in place of the word a s s (type of file concerning subtitles) because of the filtering of the forums

---

### Post by chickenPie4breakfast on 2012-03-29
@evil soup,  thanks!!! this:
```
ffmpeg -i input.mkv -acodec copy -vcodec copy output.mp4
```

worked perfectly for converting an mkv tv episode so that I could watch on tv - my tv won't play back .mkv   I was converting to mpg and it was taking abt 20mins for each episode but this of copying into mp4  took about a minute!  I didnt know it was possilbe.:p

---

