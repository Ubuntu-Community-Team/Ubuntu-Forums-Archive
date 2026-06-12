---
title: "Video (Ogg Theora) editing software?"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by Vinze on 2007-05-02
Hello, I have this Ogg Theora file created with RecordMyDesktop but I want to edit this. However, I can't find any video editing software that can edit .ogg or software that can convert Ogg Theora to other formats.

The video editing software I'm looking for should be able to cut off a part of a video, have a .deb package available and preferably be GTK.

Thanks in advance.

---

### Post by fakie_flip on 2007-05-02
> **Vinze said:**
> Hello, I have this Ogg Theora file created with RecordMyDesktop but I want to edit this. However, I can't find any video editing software that can edit .ogg or software that can convert Ogg Theora to other formats.

The video editing software I'm looking for should be able to cut off a part of a video, have a .deb package available and preferably be GTK.

Thanks in advance.


Get Avidemux. I think the package in Synaptic/Apt-get is called avidemux2. It is a shame that you want to re-encode the video to a different format. You will also lose quality when doing so. If you need the video to play in windows, then you should get vlc player for free or add a codec to WMP.

---

### Post by Vinze on 2007-05-03
> **fakie_flip said:**
> Get Avidemux. I think the package in Synaptic/Apt-get is called avidemux2. It is a shame that you want to re-encode the video to a different format. You will also lose quality when doing so. If you need the video to play in windows, then you should get vlc player for free or add a codec to WMP.

I also think it's a shame, but I had already tried Avidemux (avidemux2 is not in the repo, just avidemux) and when I try to open my screencast, it says

> Attempt to open /home/vincent/Documents/videos/screencasts/grabbl1.ogg failed!

And then

> Could not open the file.

So I thought Ogg Theora was an unsupported format, also because there is this "format" drop-down menu that lists AVI, MPEG, OGM, MP4 and PSP but not Ogg. So is there a way I can open a .ogg with Avidemux?

---

### Post by fakie_flip on 2007-05-04
I read here that Instabul is a good program for screencasts and support ogg.

[http://ubuntuforums.org/showthread.php?t=318007&highlight=screencast+ogg](http://ubuntuforums.org/showthread.php?t=318007&highlight=screencast+ogg)

BTW, what are screencasts? I have never used them.

---

### Post by Vinze on 2007-05-05
> **fakie_flip said:**
> I read here that Instabul is a good program for screencasts and support ogg.

[http://ubuntuforums.org/showthread.php?t=318007&highlight=screencast+ogg](http://ubuntuforums.org/showthread.php?t=318007&highlight=screencast+ogg)

BTW, what are screencasts? I have never used them.

Thanks for the link, but I already use RecordMyDesktop to make screencasts, and I've already found out how to convert the .ogg it produces to .avi's. I had also looked into Istanbul, but that unfortunately depends on the Gnome panel which I do not need on Xubuntu.

Screencasts are like screenshots, however, instead of making an image that shows you desktop at that moment, it records a whole video showing everything you did on your desktop while recording your video.

---

### Post by fakie_flip on 2007-05-06
So why don't you tell what you did? This is a forum, and others are supposed to be able to benefit from it.

---

### Post by Vinze on 2007-05-06
> **fakie_flip said:**
> So why don't you tell what you did? This is a forum, and others are supposed to be able to benefit from it.

Sorry, you're right, I should've done that ;)

A friend of mine suggested to issue the following command from the command line, in the same folder as my screencast (grabbl1.ogg) was located. It would output grabbl1.avi:

```
mencoder grabbl1.ogg -o grabbl1.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800 -oac mp3lame
```

I did need to have mencoder installed and I also had ubuntu-restricted-extras installed which I guess you'd need for this.

After having encoded it to .avi I could edit it with Avidemux.

Thanks,

Vincent

---

### Post by wrongo on 2007-06-06
ok but the thread began with a question simply of how to edit .ogg / .ogm files - then someone assumed (correctly) that the person wanted to change formats

well i don't - i literally just want to edit .ogm files - anyone?

needed: video editing software capable of handling .ogm's

---

### Post by wrongo on 2007-06-22
solution in ubuntu feisty

1.) record desktop session using istanbul

2.) convert file to .mpg using devede...

3.) open result with avidemux

4.) do ALL your editing - reopening edited mpg's with avidemux degrades the video

5.) save

note -

---

### Post by Saoshyant on 2007-07-22
Use [Kino](http://www.kinodv.org) to edit video on Linux.  You can work with Theora there.

Do not transcode Theora files.  You lose quality and, more importantly, Theora is an Open Media format.  There's no point in using free software like Ubuntu when you want to lock yourself into flawed proprietary formats.

---

### Post by Vinze on 2007-08-05
> **Saoshyant said:**
> Use [Kino](http://www.kinodv.org) to edit video on Linux.  You can work with Theora there.


Weird... I heard about Kino but I can't recall I've tried it, dunno why. It looks good.

> **Saoshyant said:**
> 
Do not transcode Theora files.  You lose quality and, more importantly, Theora is an Open Media format.  There's no point in using free software like Ubuntu when you want to lock yourself into flawed proprietary formats.

Well, the freedom part is not my main reason (though a nice plus ;-)) to use Xubuntu, I just use it because for me, it's the best available OS.

---

### Post by diablo75 on 2007-10-26
I tried Kino.  It instantly made my video look terrible.  So I'm using DeVeDe now to convert my theora ogg videos to mpg.  This works but takes forever, and you have to experiment with your bitrates a little bit to get it to look good.  And for some reason, it tells you you need gigs and gigs gigs of free space when it reality it only uses a fraction of that space.  What's worse is if the estimation is greater than your free hard drive space, it won't let you do the conversion.

I never wanted to transcode my videos.  But since nobody in here seems to think it practical to have an application out there that doesn't have to do any transcoding before theora video can be edited.  I didn't even want special effects, just splices and cuts.  I'm not asking for much.

Here's the deal.  I record a screencast with gtk-recordmydesktop, and I'd kind of expect this format to have at least one application out there (besides movie player) that I can open, and have it appear on my screen within a second.  Not go through some sort of long import process.  Not have it say, "Sorry, can't do that...(try transcoding into one of these other 20 or 30 OTHER video codecs, we can open those up in a jiffy.)"  Makes no sense.  How can you hold a codec that, while it is nice to say that it is "open", can't ***BE*** opened and edited in a matter of seconds?

---

### Post by TB2 on 2007-11-02
> How can you hold a codec that, while it is nice to say that it is "open", can't BE opened and edited in a matter of seconds?
I guess this is because if you would rely on another format you could never promote ogg, which is a very good format. An *because* it sucks having to recode the vids to use them some of the developers might include support for .ogg editing in their software. So I guess for everyone to support .ogg you first have to force it onto the user so that he complains and creates some motivation for the devs... ^^

---

### Post by Dai777 on 2007-11-02
Cinelerra should be able to re render your videos for you

---

### Post by zorkerz on 2007-11-29
I'm trying to cut out the beginning of a movie with an .ogm extension and merge it with another .ogm file. Im not sure what program can do this. I DO NOT want to convert to another format. 

I tried Pitivi but it crashes when it tries to open the .ogm file.

Kino is asking me what video standard to import it too (PAL or NTSC). I don't know the first thing about this. Can I still use kino without converting the file and if so what standard should I use?

When I try to import it to either video standard it says "failed to import media" bummer

---

### Post by zorkerz on 2007-11-29
So im been searching around and apparently ogm is a container format (like avi) that can contain various video, audio, subtitle tracks and the like. Does anyone know how I can find out what media formattes I am actually trying to edit with these two files?
thanks

---

### Post by olejorgen on 2007-11-29
Try ogmtools

---

### Post by zorkerz on 2007-11-29
ok here is what I get from ogminfo
> (ogminfo.c) (v1/serial 0) fps: 25.000 width height: 640x352 codec: 0x44583530 (DX50)
(ogminfo.c) (a1/serial 1) Vorbis audio (channels 2 rate 48000)
(ogminfo.c) (a2/serial 2) Vorbis audio (channels 2 rate 48000)
(ogminfo.c) (t1/serial 3) text/subtitle stream

ogmmerge is supposed to merge files into an ogm container. Can I just merge two ogm containters (I suspect not). If I seperate both ogm files into their contained streams with ogmdemux can I then add them all together in one? How do I specify the order of the video or do i have to merge them somehow?

thanks again for all th ehelp

---

### Post by eye208 on 2007-11-29
> **diablo75 said:**
> Here's the deal.  I record a screencast with gtk-recordmydesktop, and I'd kind of expect this format to have at least one application out there (besides movie player) that I can open, and have it appear on my screen within a second.  Not go through some sort of long import process.  Not have it say, "Sorry, can't do that...(try transcoding into one of these other 20 or 30 OTHER video codecs, we can open those up in a jiffy.)"  Makes no sense.  How can you hold a codec that, while it is nice to say that it is "open", can't ***BE*** opened and edited in a matter of seconds?
Ogg Theora is a lossy compression format, similar to MPEG. Why do screen capture programs use formats like these? Because lossless video would fill your hard disc very quickly.

RecordMyDesktop's video quality slider is set to 100% by default, i.e. you get results which are very close to lossless video, but without the disc space requirements of lossless video. This is exactly what most users expect from a screen capture tool: small files that are instantly deployable, e.g. on a website.

Many people fail to realize that there is a conflict between editable video and efficient compression. This is because of the way video compression works. A compressed video clip has its individual frames stored in two different ways: either as an intraframe (I-frame) which is self-contained, or as an interframe (P-frame or B-frames) which is derived from the previous frame in the video. Interframes are much smaller than I-frames because they only store the differences between the current frame and the previous one.

The problem here is that frame-accurate searching and cutting is difficult and time-consuming if Interframes are used. That's why you have to convert the video into an editable format first. This is not Ogg Theora's fault; it applies to MPEG as well. Editable video streams are either completely uncompressed (huge!) or consist of I-frames only. This is commonly referred to as "intraframe compression". Examples are MJPEG and DV. MPEG 2 and 4 also support intraframe compression.

You can convert any video into an editable format without quality loss using FFMPEG with the options -sameq and -intra. You can also use FFMPEG to convert the video into sequences of numbered JPEG or PNG files for video editors that support this format (e.g. Blender). In the case of PNG, the -sameq option is not required since PNG is lossless by default.

When you are done with editing, you can render the result into any format you like.

---

### Post by procastino on 2008-01-30
Hi!
I'm exactly in this problem, i have recorded some screencasts with recordmydesktop, but when i open them, particularly in machines that run windows with media player, volume is too low. The only thing i would like to edit is that sound, denoise it a little and give it gain. I've converted them to avi using mencoder, and i tried to edit them using avidemux, but i think that program has not the features i want. I tried installing kino (i'm on feisty) but i can't, synaptic says that it has unresolved dependencies. Cinelerra crashes continuously and seems to hard to handle... I'm about to cry...
I think i'm only complaining to the sun but... anyone has any suggestion for me?
Sorry if this is not the way to use this forum, first time!!
Thanks a lot.

---

### Post by zorkerz on 2008-01-30
Just recently I had some success with pitivi I have found it much more straight forward and easier to figure out than others. But the files it created were drastically reduced in video quality even though all I did was clip one and add it to another of the some quality.

Also did not handle the different audio tracks.

I liked the feel of pitivi better than any other i used but it is still buggy and would crash for me all too often.

---

### Post by procastino on 2008-01-31
I've made a little advance, but i'm still quite unhappy :(, i post what i've done untill now:
1 - REcord screencast using gtk-recordmydesktop
2 - Convert the resulting .ogg file to .avi, using mencoder
mencoder video.ogg -ovc lavc -oac mp3lame  -o video_de_salida.avi
3 - Extract the audio from the .avi file,
mplayer -vo null -ao pcm:file=mysound.wav myvideo0.avi
4 - With audacity, denoise the wav file and give it gain
5 - Join the edited audio file with the .avi file.
mencoder -o myvideo1.avi  -ovc copy -audiofile myperfectsound.wav -oac pcm  myvideo0.avi

And here i'm stuck with two problems:
a) I would like to convert it back to .ogg, because i would like the videos to be in an open codec, and i don't know how... help?
b) As i've 25 screencasts to edit, and this process is quite tedious, anyone knows a better way to this thing?

Thanks a lot

---

### Post by eye208 on 2008-01-31
> **procastino said:**
> a) I would like to convert it back to .ogg, because i would like the videos to be in an open codec, and i don't know how... help?
Keep in mind that you are dealing with lossy compression here. Converting from Theora to MPEG and back will degrade video quality. Converting from Vorbis to MP3 and then back to Vorbis will degrade audio quality.

Since you want the final result in Ogg Theora/Vorbis anyway, you can optimize the procedure. In order to do that, you need to install the packages [vorbis-tools](http://packages.ubuntu.com/gutsy/sound/vorbis-tools) and [oggz-tools](http://packages.ubuntu.com/gutsy/utils/oggz-tools). Then you can go on like this:

oggzrip -c theora -o video.ogg screencast.ogg
oggzrip -c vorbis -o audio.ogg screencast.ogg

This will save the video and audio streams from the input file "screencast.ogg" to separate files "video.ogg" and "audio.ogg". No re-encoding will be done at this point, i.e. there will be no quality loss.

oggdec -o audio.wav audio.ogg

This will decode the audio stream to the uncompressed file "audio.wav" which you can load into Audacity and edit. After you have saved your changes to audio.wav, you can encode it to Vorbis again and merge it with the original video:

oggenc -o audio.ogg audio.wav
oggzmerge -o final.ogg video.ogg audio.ogg

> b) As i've 25 screencasts to edit, and this process is quite tedious, anyone knows a better way to this thing?
You can make shell scripts to save some typing.

---

### Post by procastino on 2008-01-31
Thanks a lot, just two final questions (i hope)
I've looked in the links you sent and i thinkvorbis tools and oggztools are not available for feisty, wich is what i have now, am i right?
AS you may have noticed, i'm quite a beginner and not very handy in this questions, so shell scripts sound to me a little bit remote, i'll try to learn but... is it difficult?
Thank you very much for the help.

---

### Post by Vinze on 2008-02-01
> **procastino said:**
> Thanks a lot, just two final questions (i hope)
I've looked in the links you sent and i thinkvorbis tools and oggztools are not available for feisty, wich is what i have now, am i right?
AS you may have noticed, i'm quite a beginner and not very handy in this questions, so shell scripts sound to me a little bit remote, i'll try to learn but... is it difficult?
Thank you very much for the help.

[vorbis-tools has been available since 6.06](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vorbis-tools&searchon=names&subword=1&version=all&release=all), and [so has oggz-tools](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=oggz-tools&searchon=names&subword=1&version=all&release=all) - you can just install them through Synaptic (System->Administration->Synaptic Package Manager I believe).

I believe shell scripts are files in which you enter a few commands and then you can execute those files with one command to execute all commands in there. I'm not sure how you're supposed to write them, but entering the commands by hand will also do ;)

---

### Post by alien53 on 2008-02-01
thanks for this advice :)

---

### Post by procastino on 2008-02-01
It's solved (well, i still have to do all the work, but i finally have a way to do it!).
I'll spend the rest of the week feeling thankful ;)

---

### Post by roaldz on 2008-02-22
> **Vinze said:**
> Weird... I heard about Kino but I can't recall I've tried it, dunno why. It looks good.



Well, the freedom part is not my main reason (though a nice plus ;-)) to use Xubuntu, I just use it because for me, it's the best available OS.

I´m sorry, but you have a name to keep as a Dutch man. If it´s free, it´s good!

Sorry, just kidding.

Roald

---

### Post by Vinze on 2008-02-23
> **roaldz said:**
> I´m sorry, but you have a name to keep as a Dutch man. If it´s free, it´s good!

Sorry, just kidding.

Roald

Whaha, yes, the fact that Xubuntu is free of charge weighs in too, but since most people don't realize they're paying for Windows or aren't paying for Windows (i.e. using it illegally) that's not really a compelling argument :P

---

### Post by Zatta on 2008-04-17
I had several "recordmydesktop" ogg/theora videos and I wanted to concatenate (join) them. I found a way to do it and I want to share it here.

I couldn't find a way to concatenate theora videos in ogg container directly. Instead, I appended them inside a matroska container using the tools of the *mkvtools* package (following a post I found in lists.xiph.org). In the command line:

```
$ mkvmerge -o name-of-file.mkv first.ogg +second.ogg. +third.ogg
```

... as many .ogg files as I had.

Then, I had to demux both video and audio from matroska and remux into an ogg file. Well, this time mkvtools wasn't able to help me because mkvextract can't extract the video into an ogg file (mkvextract can only extract audio into an ogg file).

The solution was to use gst-launch, from *gstreamer*. I passed the mkv file through a demuxer, splitting audio from video, and after it rejoins them in an .ogg file, using a muxer:

```
$ gst-launch-0.10 filesrc location=name-of-file.mkv ! matroskademux name=demux demux.video_00 ! queue ! theoraparse ! mux. demux.audio_00 ! queue ! vorbisparse ! mux. oggmux name=mux ! filesink location=final-file.ogg
```

and, voilà, I had my ogg/theora video comprising several concatenated clips.

Be careful, though:

1) I read elsewhere that you can concatenate ogg/theora videos by concatenating the files (using cat). It didn't work for me, mplayer/xine/etc don't play videos concatenated this way.

2) Clips must all have the same dimensions (height x width) for this to work. You can see this information using (from package *oggz-tools*):

```
$ oggzinfo name-of-file.ogg
```

3) "mkvmerge" from the mkvtoonix package in the repositories didn't work for these ogg/theora files (complained about something in the ogg/theora input files). I have had to download source code from [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/) and compile it.

---

