---
title: "Video codec advantages vs disadvantages"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Marco7 on 2009-12-19
What is your favorite video codec (AVI, DIVIX, MPEG, etc), and how to you make them?

I have a bunch of vob. files from windows dvd rips and would like to make into single compressed files for PC playback only.  
What codec should I use?  Can I adjust the bit rate or resolution to my preferences?  What program should I use?

Thanks.

---

### Post by lovinglinux on 2009-12-19
[AVI](http://en.wikipedia.org/wiki/Audio_Video_Interleave) is not a codec, it is a [container format](http://en.wikipedia.org/wiki/Container_format_%28digital%29#Multimedia_container_formats). [DivX](http://en.wikipedia.org/wiki/DivX) is a codec, but mostly the brand of a series of products, including the DivX codec, the DivX player and the DivX container. They are proprietary and run only on Windows and Mac. The open source equivalent codec, which is available for Linux is [Xvid](http://en.wikipedia.org/wiki/Xvid). [MPEG](http://en.wikipedia.org/wiki/MPEG) is a standard for audio/video compression, which includes a container and specifications used by several codecs.

Examples of video containers: [AVI](http://en.wikipedia.org/wiki/Audio_Video_Interleave), [MP4](http://en.wikipedia.org/wiki/MP4), [MKV](http://en.wikipedia.org/wiki/MKV), [MOV](http://en.wikipedia.org/wiki/QuickTime#QuickTime_file_format), [MPEG](http://en.wikipedia.org/wiki/MPEG_program_stream), [OGG](http://en.wikipedia.org/wiki/Ogg).

I use mostly MKV, AVI and MP4. MKV is the best in my opinion, because it supports multiple streams and features, including subtitles. But some formats are better than others, depending on how you are going to watch. For instant, hardware like XBOX, PS3 and standalone DVD players have limitations on which formats and codecs they can play.

About the codecs, I use mostly **[FFmpeg's](http://en.wikipedia.org/wiki/FFmpeg#Codecs) [libavcodec](http://en.wikipedia.org/wiki/Libavcodec#Implemented_video_codecs) codec family**, more specifically [mpeg4](http://en.wikipedia.org/wiki/FFmpeg#Codecs) (MPEG-4 ASP), [mjpeg](http://en.wikipedia.org/wiki/FFmpeg#Codecs) (Motion JPEG) and [libx264](http://en.wikipedia.org/wiki/FFmpeg#Codecs) (MPEG-4 AVC/H.264) for video and [libfaac](http://en.wikipedia.org/wiki/FFmpeg#Codecs) (AAC) and [mp3lame](http://en.wikipedia.org/wiki/Mp3lame) (MP3) for the audio stream.

To convert your vobs you can use [mencoder](apt:mencoder).

Some examples of mencoder commands using those codecs/formats:

```
mencoder source.vob -o output.[COLOR="DarkRed"]avi[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]mpeg4[/COLOR]:vbitrate=1200
```

```
mencoder source.vob -o output.[COLOR="DarkRed"]avi[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]mjpeg[/COLOR]:vbitrate=1200
```

```
mencoder source.vob -o output.[COLOR="DarkRed"]mp4[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]libx264[/COLOR]:vbitrate=1200
```

The x264 is extremely slow, but renders the best quality results. I usually don't use it. The best speed/quality ratio I could find is with mpeg4. The mjpeg codec also renders better results than mpeg4 with decent encoding speed, although bigger file sizes.

Fore more info about mencoder options see [this](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#GENERAL%20ENCODING%20OPTIONS%20%28MENCODER%20ONLY%29)

You can transcode/edit/merge several formats to MKV files with [mkvtoolnix-gui](apt:mkvtoolnix-gui).

Also see these:

[http://en.wikipedia.org/wiki/Video_codec#Commonly_used_video_codecs](http://en.wikipedia.org/wiki/Video_codec#Commonly_used_video_codecs)
[http://en.wikipedia.org/wiki/Comparison_of_video_codecs](http://en.wikipedia.org/wiki/Comparison_of_video_codecs)
[http://en.wikipedia.org/wiki/Comparison_of_audio_codecs](http://en.wikipedia.org/wiki/Comparison_of_audio_codecs)

---

### Post by Marco7 on 2009-12-20
Great Post, Thanks.

That clears up and makes sense of a lot of unknowns and gives me some resources to dig even deeper.

This is a little off topic, but say I wanted to take the same project (a DVD that I ripped and encoded with DVDshrink, i.e. I have VIDEO_TS and AUDIO_TS folders) and I want to burn them to a DVD that will play in stand alone player.  

I read somewhere that all I would have to do is make a data disc with these folders, making sure the titles were all caps and no spaces, but it didn't work.  Do I have to create an .ISO?  What can I use to do this?  Does it have to be UDF?  

I could re-author everything again with K9copy, but I just want to burn them as they are, like NERO would do at this juncture.

Any input would be greatly appreciated, thanks.

---

### Post by lovinglinux on 2009-12-20
> **Marco7 said:**
> Great Post, Thanks.

That clears up and makes sense of a lot of unknowns and gives me some resources to dig even deeper.

This is a little off topic, but say I wanted to take the same project (a DVD that I ripped and encoded with DVDshrink, i.e. I have VIDEO_TS and AUDIO_TS folders) and I want to burn them to a DVD that will play in stand alone player.  

I read somewhere that all I would have to do is make a data disc with these folders, making sure the titles were all caps and no spaces, but it didn't work.  Do I have to create an .ISO?  What can I use to do this?  Does it have to be UDF?  

I could re-author everything again with K9copy, but I just want to burn them as they are, like NERO would do at this juncture.

Any input would be greatly appreciated, thanks.

I don't know. I don't burn may DVDs, since I prefer to watch videos on my computer, but I guess just burning the folders should be enough. Perhaps your player is having a hard time with the codecs used to shrink the original DVD or maybe the DVD burn is faulty. 

You could try to use devede or dvdstyler to re-build the DVD structure. Devede is very popular, but I prefer dvdstyler.

---

### Post by lisati on 2009-12-20
> **Marco7 said:**
> 

This is a little off topic, but say I wanted to take the same project (a DVD that I ripped and encoded with DVDshrink, i.e. I have VIDEO_TS and AUDIO_TS folders) and I want to burn them to a DVD that will play in stand alone player.  

I read somewhere that all I would have to do is make a data disc with these folders, making sure the titles were all caps and no spaces, but it didn't work.  Do I have to create an .ISO?  What can I use to do this?  Does it have to be UDF?  

I've only ever burned a "DVD folder" through Windows, using an option specifically for that purpose.

---

### Post by Marco7 on 2009-12-22
> **lovinglinux said:**
> 

To convert your vobs you can use [mencoder](apt:mencoder).

Some examples of mencoder commands using those codecs/formats:

```
mencoder source.vob -o output.[COLOR="DarkRed"]avi[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]mpeg4[/COLOR]:vbitrate=1200
```

```
mencoder source.vob -o output.[COLOR="DarkRed"]avi[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]mjpeg[/COLOR]:vbitrate=1200
```

```
mencoder source.vob -o output.[COLOR="DarkRed"]mp4[/COLOR] -oac lavc -lavcopts acodec=[COLOR="DarkRed"]libfaac[/COLOR]:abitrate=128 -ovc lavc -lavcopts vcodec=[COLOR="DarkRed"]libx264[/COLOR]:vbitrate=1200
```

The x264 is extremely slow, but renders the best quality results. I usually don't use it. The best speed/quality ratio I could find is with mpeg4. The mjpeg codec also renders better results than mpeg4 with decent encoding speed, although bigger file sizes.

Fore more info about mencoder options see [this](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#GENERAL%20ENCODING%20OPTIONS%20%28MENCODER%20ONLY%29)

You can transcode/edit/merge several formats to MKV files with [mkvtoolnix-gui](apt:mkvtoolnix-gui).



Mencoder proved to be a little to much for me so I tried to find a GUI based encoder and I settled on Avidemux.  I was a little apprehensive about windows compatibility with the GUI for MKV so I moved on, but I will continue to research it.  K9copy, aside from being KDE, was not to my liking, and WinFF was too simple (not enough settings aside from additional command line entries).  I had checked out Avidemux before and couldn't make any sense of it, but now it seems reasonable, Thanks.

Now I have the quad-core working around the clock making nice avi's with x264 video , and LameMP3 audio. :P  For my own qaulity prefferences I have found for a 2.5 hr. film I have to keep the total size of the .avi above 2GB. 

(Note to others: I had to change my alsa audio device to "default" under preferences before I could get any sound in Avidemux)


On VIDEO_TS and AUDIO_TS folders: My ripped DVD's generally contain the full DVD structure within the Video_TS folder.  Sometimes encoding these into .avi, for instance, fails, because the third .vob file in a sequence of four, for example, will have the editors commentary as the main audio track, or some other nonsense probably derived to keep people from encoding DVD's on their computers.  To smooth out these problems the DVD files may need to be re-authored before they can be encoded.  DVDShrink does this beautifully in Windows and can produce an .iso image for later burning, burn it directly, or just save the DVD structure back to the hard drive, however, there are many other programs that can do this in Windows or Linux.  If you are like me and have a collection of VIDEO_TS and AUDIO_TS folders **_it is important to first distinguish between simply ripped/decoded DVD files, and re-authored DVD files_**.  Once you have re-authored VIDEO_TS and AUDIO_TS folders (all caps no spaces) you can burn to DVD for use in a stand-alone DVD player, however, you must create an .iso image (UDF format) of the folders before burning, or use a burning application that will create one for you (The title of the DVD must also be all caps and no spaces).

On my system (Ubuntu 9.04 - Multimedia-enabled) DVD::rip decodes and rips the main title from a DVD very well, and these files can be encoded directly to .avi with Avidemux.

For DVD's ripped/decoded in Windows I must first re-author the DVD structure and then can they be encoded with Avidemux.

I'm still figuring it out for myself, but perhaps someone else will find this useful.

---

