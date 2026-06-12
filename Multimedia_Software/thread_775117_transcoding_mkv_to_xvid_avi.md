---
title: "transcoding mkv to xvid avi"
date: 2008-04-29
forum: Multimedia Software
---

### Post by the_arm on 2008-04-29
Hi everyone - 
So, I have this DVD player that will take a usb stick and play divx/xvid avis, PAL or NTSC.  I've used it dozens of times to watch various shows that I've downloaded.

Anyway, I recently downloaded some .mkv files that contain xvid mpeg-4 video and 48KHz sampled vorbis audio.  Looking at the xvids that I have that work on my player, they are xvid mpeg-4 video and 48KHz sampled mp3 audio...

so, I was thinking it should be relatively straight forward to convert these mkvs into something I could watch.

My first shot was with DeVeDe.  I had it make a DVD iso (and eventually tried every output I could muster), and the audio was always sync'd off from the video by like 5 seconds or so.  I played with the audio delay feature in DeVeDe, but it didn't seem to help at all.  I've used DeVeDe successfully to make DVDs out of other formats...and mplayer and all my other video players seem to play the original mkv correctly, so I gave up there.

Next I tried to make my own file.  I figured out how to use the mkvinfo and then mkvextract tools to make a video.avi and an audio.ogg file.  I then transcoded the audio.ogg file to an audio.mp3 file using the Sound Converter gui on my ubuntu box.  I'm sure there is a command line transcoder, but the gui worked just fine.

I'm not sure how to assemble this video.avi and audio.mp3 into a real xvid video with sound, though.  I tried to use avimerge, but it says that the video isn't avi.  
specifically I tried:

avimerge -o my_output_xvid.avi -i video.avi -p audio.mp3

and it complained that:
scanning file video.avi for video/audio parameter
[avilib] V: 25.000 fps, codec=XVID, frames=66287, width=688, height=560
merging audio audio.mp3 track 0 (multiplexing) into 0 ...
AVI open: avilib - Not an AVI file


So here are my questions:

* Anyone have any idea how I can fix DeVeDe to not have the audio sync problem?  It's always just worked...and the audio delay doesn't seem to work at all.
* anyone know how to assemble this video (mpeg-4) and audio (mp3) into an xvid4 .avi video?
* is there a simple command line solution for this?  I took a look at transcode and there were way too many options for me to try to figure it out!  namely some way to extract the audio/video, then convert (I guess just the audio) and then reassemble into xvid?

thanks!!
-arm

---

### Post by cor2y on 2008-04-29
i don't know about devede or avimerge, when i need to replace an audio track in video i just use either ffmpeg, mencoder or avidemux.
On mencoder thats ```
 mencoder input.mkv -ovc copy -af resample=44100:0:2 -srate 44100 -oac mp3lame -lameopts cbr:br=128:aq=4:vol=1.1:mode=1 -o outputfile.avi
```That is if you wish to re-encode the audio but if you do not and just want an avi file then```
 mencoder input.mkv -ovc copy -oac copy -o outpuyt.avi
``` see how that works if they both fail then you can try converting both the auio and video to xvid with mp3 audio or mpeg4 with mp3 auido.
```
mencoder input.mkv -ovc xvid -xvidencopts pass=1 -af resample=44100:0:2 -srate 44100 -oac mp3lame -lameopts cbr:br=128:aq=4:vol=1.1:mode=1 -o output.avi
```

---

### Post by the_arm on 2008-04-29
Hi there - thanks for your quick help!

I ended up trying all three methods and none seemed to work.

The second one (with no re-encoding of the audio) fails because it didn't like the audio format...that makes sense...or at least I know that i'm trying to re-encode the audio from ogg to mp3.

Method 1 and 3 both failed at 16% in to the file, where it reports:

***
Too many audio packets in the buffer: (4101 in 593242 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16:9.
Setting audio delay to 0.040s.

Video stream: 2824.242 kbit/s  (353030 B/s)  size: 128460633 bytes  363.880 secs  10107 frames

Audio stream:  128.000 kbit/s  (15999 B/s)  size: 5828858 bytes  364.304 secs
***


I also tried turning off the resampling (since I know the example files that work preserve the 48KHz sample rate), and I tried doing what the output suggested and throwing the -ni flag on there.

neither worked; same "too many audio packets" result.

Any other thoughts?  I'd assume the file was bad, but it plays back just perfectly in all of my ubuntu video players (MPlayer, Movie Player, and VLC).

Thanks!
-arm

---

### Post by cor2y on 2008-04-30
well you could try dumping the audio  then remuxing it back as encoded mp3.
```
mplayer -vc dummy -vo null -ao pcm:file=out.wav input.mkv;normalize-audio out.wav;lame out.wav --cbr -b 128 out.mp3;mencoder input.mkv -ovc xvid -nosound -mc 0 -noskip -xvidencopts pass=1 -o input.avi ;mencoder input.avi -oac copy -ovc copy -audiofile out.mp3 -o output.avi
```
A bit complicated i know but this is what i got i am sure uing mencoder alone you could probably do what i just suggested, in that example you need the extra programs lame and normalize.

---

### Post by the_arm on 2008-04-30
Thank you!!  Actually that command
```
mencoder input.avi -oac copy -ovc copy -audiofile out.mp3 -o output.avi
```

was all I needed since I had already extracted the audio and video with mkvextract and converted the audio to mp3 using Sound Converter.

That said, it's nice to know how to do it all from the command line.

Thanks for your help!
-arm

---

### Post by Kleaefmiir on 2008-04-30
I, too have a bunch of MKV files I'd like to watch on my TV DVD player.
However, I got lost reading the posts.

How should I start to convert my MKV to DIVX?

Thanks! ^^

---

### Post by little_penguin on 2008-06-05
As an alternative to the command line, you can also use mkv2avi, it's a nice little KDE Kommander script that converts Matroska to Avi, point and click interface, see here:

[http://www.kde-apps.org/content/show.php/Mkv2Avi?content=74842]("http://www.kde-apps.org/content/show.php/Mkv2Avi?content=74842")

Regards,
LP

---

### Post by ekss on 2008-11-26
```
mencoder input.mkv -ovc xvid -xvidencopts pass=1 -af resample=44100:0:2 -srate 44100 -oac mp3lame -lameopts cbr:br=128:aq=4:vol=1.1:mode=1 -o output.avi
```


i successfully converted a file using the above commands, but it didnt play on my stand-alone divx player. what could be the problem?

thanx anyway :)

---

### Post by Skatespeare on 2009-03-16
> **ekss said:**
> ```
mencoder input.mkv -ovc xvid -xvidencopts pass=1 -af resample=44100:0:2 -srate 44100 -oac mp3lame -lameopts cbr:br=128:aq=4:vol=1.1:mode=1 -o output.avi
```


i successfully converted a file using the above commands, but it didnt play on my stand-alone divx player. what could be the problem?

thanx anyway :)

tnx m8 you helped me bigtime! I just bought a mediacenter, but I wasn't able to play back .H264 mkv files on it. It may take take a little more time converting the files, but I can finally play my HD films on new purchase :)

---

