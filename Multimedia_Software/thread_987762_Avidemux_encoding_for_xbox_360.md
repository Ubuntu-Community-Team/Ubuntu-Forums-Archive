---
title: "Avidemux encoding for xbox 360"
date: 2008-11-19
forum: Multimedia Software
---

### Post by jim1964 on 2008-11-19
I'm having trouble encoding xbox 360 video using avidemux in intrepid. I have successfully done this with hardy. Avidemux version is 2.4.3. I'm using MPEG4 ASP (lavc) video, AC3 (lavc) audio and an avi container. This worked in hardy and now the xbox reports unsupported format when encoded with intrepid. Has anyone else gotten this to work in intrepid? Thanks.

---

### Post by Walter Melon on 2009-01-04
I got it to work but I used a different audio format.  I started out with an .avi and DivX MS-MPEG-4 Version 3 AND MPEG 1 Audio, Layer 3 (MP3).  I used avidemux to encode the video with the previously mentioned MPEG ASP (lavc) and left the audio the way it was.  What audio format did you have before trying to encode it with avidedmux?

---

### Post by jellygoeswobble on 2009-02-21
Sorry if this reply is late, but ac3 is not compatible with mp4 or mov in xbox360 for some reason. Here is a table of compatibility. hope this helps.
[http://www.afterdawn.com/guides/archive/what_will_xbox_360_play.cfm]("http://www.afterdawn.com/guides/archive/what_will_xbox_360_play.cfm")

---

### Post by juanjo_vlc on 2009-10-08
Sorry for taking back from the land of the dead this thread, but I usually get lost while trascoding files for play on xbox 360 (¡God save XBMC, and bring it to xbox 360!), so my question is:
Can anybody post a saved profile for avidemux which is know to work?

Thanks in advance and sorry for my poor english.

---

### Post by spiritofcat on 2009-10-08
I've been playing with avidemux to try to get a video working on my 360 recently too.
You can read about my adventures in this thread: [http://ubuntuforums.org/showthread.php?t=1284661](http://ubuntuforums.org/showthread.php?t=1284661)

The file I was working with began as DivX video and MP3 audio in an MP4 container.
I tried all sorts of combinations of re-encoding the video and audio and putting it in different containers.
The simplest way I found of getting it to work was to leave the video encoded as it was, re-encode the audio as AAC and leave it in an MP4 container.
I don't see an option in avidemux for encoding video as DivX, but according to that compatibility table on AfterDawn it should work just as well with XviD. Don't know for sure though since that table also says that XviD + MP3 + AVI should work and it didn't for me.

So anyway, try XviD + AAC + MP4 and see if it works for you.

Edit: I've got a new challenge.

I have a japanese movie in an MKV container and I'm going to try to convert it so it can play on the 360.

These are the stats:
Container: MKV
Video: XVID
Packed Bitstream: Yes
Audio: Ogg Vorbis
It has two audio tracks: English and Japanese.
It has five subtitles tracks: English, French, Japanese, Chinese and Chinese.

I generally prefer to use Japanese audio with English subtitles, so I'll have to find a way to hard-encode the subtitles since the 360 doesn't support any sort of subtitle file as far as I'm aware.
My other option of course is to just put up with the English audio. That will be the easier option so I'll leave it as Plan B to use if I can't get the subtitles going in an acceptable way.

First step, I open the movie in VLC to see that it works okay on the computer and to find out which track numbers are which languages.
Turns out that Audio Track 1 is English and 2 is Japanese.
Subtitle Track 1 is English.

Now it seems that Avidemux has the ability to hard encode subtitles from an external file, but it can't extract the subtitle track from the MKV.
To extract the subtitle track I'll need to use mkvtoolnix.

I like GUIs, so I'll install the GUI version. I found it by searching for MKV in Synaptic Package Manager.
Once installed, it is found under Sound & Video > MKV files creator.
When I run it it seems to be called mkvmerge GUI.

On the Input tab, I click Add and choose my MKV file.
It loads it up, and shows me a list of all the tracks in the file.
When I click on a track it tells me a bit about it, including what language each subtitle track is, so I didn't need to check them out in VLC after all.

According to mkvmerge GUI, the subtitle track that I want to extract is the 4th track in the file. It's the first subtitle track, just like VLC told us, but the video and audio tracks come before the subtitle tracks, making this track 4.

To extract it, I have to get my hands dirty in the terminal.
Since it is track 4 that I want to extract, I use the command:
```
mkvextract tracks movie.mkv 4:file.***
```
Where movie.mkv is the name of the mkv file I'm extracting from.

Once that is done, I have two new files called file.idx and file.sub
Now I just need to work out how to use them with Avidemux to hard-encode them into the video.

---

