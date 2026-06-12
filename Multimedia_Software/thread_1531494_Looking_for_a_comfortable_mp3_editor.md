---
title: "Looking for a comfortable mp3 editor"
date: 2010-07-15
forum: Multimedia Software
---

### Post by Leed on 2010-07-15
Hi 

I'm looking for some tips for a good programm to edit mp3 files

[LIST]
[*]I have many tracks that have speech, empty spaces or cheering at the begining/end of the Track, I would like to cut this off
[*]Some MP3 Files are much quieter than the others, I would like to amplify the volume on them
[*]I do not want to convert the Files to wav or anything else
[*]I don't need a Tag editor, but I wouldn't want to loose the Tags after editing (resaving) the file. 
[*]Also a nice to have would be the inclusion of Artwork
[/LIST]

Does anybody know a good programm to do this. So far I don't like avidemux and would also prefer to have a tool that is soley for mp3s, not for videos.

---

### Post by amsterdamharu on 2010-07-15
I use audacity after editing you can export the file to mp3 and other formats.

---

### Post by linuxisfree on 2010-07-15
Audacity suits my needs quite perfectly, actually. I think it should suit yours too.

---

### Post by ron999 on 2010-07-15
Hi
**mp3DirectCut** runs well with Wine.
(_**Version-2.11**_)
When importing and exporting it does not re-encode, so it's quicker than Audacity.
From here:-[http://mpesch3.de1.cc/mp3dc.html]("http://mpesch3.de1.cc/mp3dc.html")
But if you prefer not to use Wine then Audacity is OK.

---

### Post by Royle Lindsey on 2010-07-15
Hi guys,
Not sure if this is the right place to ask, but I am just looking for a freeware software that can help me edit an mp3 file. 
Basically the file is 5:26 minutes in length, I would like to trim off the middle part and join in towards the end. Can anyone help please? Thanks.

---

### Post by Leed on 2010-07-15
Seems like you want to do the same as me.

I'll try audacity once I get home. I'm actually quite excited to do so, been looking for something like that for a long time. Thanks for the replies :D

---

### Post by lymanjayan on 2010-07-15
You have to try " Wave Mp3 Editor PRO". It is the software what you'r looking for. Its hard to edit an audio file but with this s/w you have amplify & edit the sound of audio. Here's what you'll get in this s/w

1. Full featured audio editor - edit audio files visually.

2. Powerful audio recording feature(s) - record from any supported source/ device.

3. Supports WAV, MP3, OGG, WMA and VOX audio files.

4. Apply various effects and filters easily.

5. Burn your sound files to CD - via it's included CD Writers.

6. Many (over 30) specialized audio tools - Converters, Rippers, Splitters, Players, ID Tag Editor,  Widgets, etc. Each one of these tools are full blown applications in their own right.  

7. Download and free usage of several specialized audio tools. 

8. Option to have a tool created and customized to your specs.

---

### Post by magiclinux on 2010-07-15
u must use ... audacity it's the best 

```
sudo apt-get install audacity

```

---

### Post by Leed on 2010-07-19
Audacity is perfect, does what I want and much more, thanks a lot for the replies.

---

### Post by Akovia on 2011-09-19
For anyone else that lands here, you might want to know that you will be loosing quality by using Audacity to do simple edits on mp3s.

From the [Audacity Wiki]("http://wiki.audacityteam.org/index.php?title=MP3").

> Re-encoding to MP3

Every time you export from Audacity as an MP3 (or other lossy audio format), this encoding necessarily degrades some of the original quality of the audio. If you import an MP3 into Audacity, edit it then export it as an MP3, you are thus losing quality twice - once in the original MP3 encoding of the imported audio, then again when you export it from Audacity as MP3. Therefore when you are exporting as MP3, work with the highest quality copy of the audio that you can - preferably a copy in a lossless format such as WAV, AIFF or FLAC. You can always obtain a lossless copy of an audio CD by extracting its audio to a WAV or AIFF file. Never extract the audio from a CD to MP3 if you want to export it from Audacity as an MP3. 

If you can't avoid importing an MP3 into Audacity and then re-encoding to MP3, don't believe what you sometimes hear that using the same or higher bit rate as the original file will prevent quality loss. This is incorrect. All you can say is that the higher the bit rate you re-encode to, the less will be the quality loss that results. 

If you only want to perform simple edits on your MP3 (cut, copy, paste, join, fade or normalise), you may prefer an application that can edit MP3s directly without having to decompress then re-encode them as Audacity does. MP3 DirectCut  for Windows and Audion  for OS 8, 9 and X are two such applications. For more advanced edits such as effects, the audio needs to be decompressed in an editor like Audacity, so you must then accept any perceptible quality loss from re-encoding the MP3.

I'm a staunch Audacity supporter, but it's not the right tool for the job unfortunately. I've already degraded plenty of mp3s unknowingly, but now am hunting down a good replacement just for this type of work. If I find something I like, I'll try to update this post with what I found, unless someone else wants to chime in first.

---

### Post by dniMretsaM on 2011-09-19
Audacity is nice, but as was mentioned, it degrades the quality of an MP3 a lot (I don't think it does this for other formats though, at least not as much). You might try these instead:
[QUOTE=Tech-Freedom (my blog)]Linux MultiMedia Studio - [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)
Traverso DAW -  [http://traverso-daw.org/](http://traverso-daw.org/)
Wavosaur - [http://www.wavosaur.com/](http://www.wavosaur.com/)[/QUOTE]

I have never used any of these, so I don't know if they degrade MP3 quality or not. And as with almost any MP3 related thread, I must ask why you are using MP3 instead of a format like Ogg Vorbis. It's better quality (especially at lower bitrates), it has a higher compression, and it's more computationally efficient.

---

### Post by Akovia on 2011-09-21
> Audacity is nice, but as was mentioned, it degrades the quality of an MP3 a lot (I don't think it does this for other formats though, at least not as much). You might try these instead:

Thanks for the suggestions, but the first two are mainly designed for music creation and the last is for Windows as far as I can tell. I did hunt down everything I could find for Linux that would do lossless mp3 editing and was left wanting. The closest I came was XMPGEdit, which I had to compile from source and was the most unintuitive interface I think I've ever used and never really got it working properly.

I am spoiled by Audacity's ease of use and only get frustrated trying to work any other way than visually. I also was not able to find a single Linux based app that would do lossless MP3 fades. In the end I installed [mp3DirectCut]("http://mpesch3.de1.cc/mp3dc.html") as was suggested on the Audacity Wiki on a Windows partition =/

> I must ask why you are using MP3 instead of a format like Ogg Vorbis. It's better quality (especially at lower bitrates), it has a higher compression, and it's more computationally efficient.

Fair question, and I have used most every type over the years. I've been using flac for years now as my main format, but not many devices support these less popular formats, even if they are better. So portability is the biggest reason, as well as support in popular applications. (Editing and playback)

On top of that I have lots of older material that I only have as mp3's. My old iRiver mp3 player recorded radio and voice for instance. So unless itunes takes over the world soon, (possible) I would think that mp3 is still the most widely "supported" compressed audio format. Which is why we could really use a proper losses editor for Linux. Until then I would love to find out that I've overlooked something that would fit my needs.

Thanks again for your suggestions, and I hope some developer sees that there is a need for this type of mp3 editor.

Ako

---

### Post by dniMretsaM on 2011-09-21
> **Akovia said:**
> ...the last is for Windows as far as I can tell.

Oh wow I did not know that. My bad... Anyway, I hope you find what you are looking for (that sounds way too philosophical for a Linux forum...).

---

### Post by IWantFroyo on 2011-09-21
Using ffmpeg2theora can change lossless formats with pretty much no audio loss (none, as far as I know).
You have to apply a few criteria, though.
```
ffmpeg2theora -a 10 file.mp3 -o file.flac --novideo
```

As far as I know, you can't do this inside Audacity.

Also, I've used Audacity before, and I liked it. I don't have much experience with the sound editing stuff, simply because I don't have to use any of the advanced settings, so don't let my opinion have too much weight.

---

