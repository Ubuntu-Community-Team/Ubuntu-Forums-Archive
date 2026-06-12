---
title: "Convert large streaming wma file to mp3 or ogg?"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by hda on 2007-02-11
Hi,
I have a problem converting a large wma file with a length of more than 6 hours to mp3 or ogg.

I've tried to convert it to wav using mplayer and then convert to mp3 with lame or ogg with oggenc. All the results have only a length of about 37 mins.

Thanks for any helpful suggestions,
*hda*

---

### Post by RomeReactor on 2007-02-11
Hi. Have you installed Lame? If not, then

```
sudo apt-get install lame
```

then

```
lame -h FILE.WAV FILE.MP3
```

See if that works.

**EDIT:** Sorry, didn't see that you were trying to convert from WMA to MP3; see if the WAV files you converted are of the expected length; if so, try the method i propose and post back if it doesn't work...

**ANOTHER EDIT:** Again, didn't see that you already tried lame. Sorry.#-o

---

### Post by hda on 2007-02-11
The wav file produced by the mplayer wma->wav conversion had a size of 4.4 GB. When I try to play that file Rhythmbox tells me that the wav file has a playing time of roughly 37 mins, though it should be more than 400 mins.
I used **mplayer -vc null -vo null infile.wma -ao pcm:file=outfile.wav** to create the wav.

---

### Post by RomeReactor on 2007-02-11
Perhaps [soundkonverter]("http://kde-apps.org/content/show.php?content=29024") can be of use to you

```
sudo apt-get install soundkonverter
```

---

### Post by hda on 2007-02-11
I finally have a working mp3 copy of the wma original. Sound**K**onverter did not work, but Sound**C**onverter (GNOME) did.

The results:

**original wma:**
189 MB

**ogg:**
405 MB
192 kbps
1h26m conversion time
doesn't play correctly in moc, totem-xine and rhythmbox
('stuttered' sound)

**mp3:**
561 MB
192 kbps CBR
26m conversion time
plays fine on all players

Thanks for all your suggestions,
*hda*

---

### Post by tbroderick on 2007-02-11
I use this to convert wma to ogg;
```
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && oggenc -q 4 audiodump.wav -o "`basename "$i" .wma`.ogg"; done; rm -f audiodump.wav
```

It will convert all .wma's in the folder to .ogg.

---

### Post by hda on 2007-02-12
> **tbroderick said:**
> I use this to convert wma to ogg;
```
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && oggenc -q 4 audiodump.wav -o "`basename "$i" .wma`.ogg"; done; rm -f audiodump.wav
```It will convert all .wma's in the folder to .ogg.
That's excactly what I did and what didn't work. See my earlier postings

---

### Post by tbroderick on 2007-02-12
> **hda said:**
> That's excactly what I did and what didn't work. See my earlier postings

Your mplayer settings were much different. I have used this to convert many wma's to ogg and haven't had one bad convert.

---

### Post by disturbedite on 2007-02-12
if you insist on converting it to *another lossy format* (obviously for size reasons) i'd recommend ogg over mp3.  the ogg format will produce better quality (technically, maybe noticeably) and a smaller file size than mp3.  plus its oss!  but if the content of what you want to convert is only speech, or primarily speech, i'd recommend [speex]("http://en.wikipedia.org/wiki/Speex").  its like ogg but specifically developed for speech.

---

### Post by hda on 2007-02-13
> **tbroderick said:**
> Your mplayer settings were much different. I have used this to convert many wma's to ogg and haven't had one bad convert.

Thanks for your suggestion. It worked, though I still can't figure out what's the difference in our mplayer settings (resample?).

However, converting WAV to ogg or mp3 failed. Both oggenc and lame stopped at a length of 2:19. The whole WAV has a length of 6:48:07 and a size of 4.1 GB.

I still have to find out how to convert the large wav to ogg or mp3.

*hda*

---

### Post by disturbedite on 2007-02-13
have you tried oggenc?  thats what i would try if soundkonverter or ffmpeg/transcode wouldn't work.  you might also try sox.

---

### Post by tbroderick on 2007-02-13
> **hda said:**
> 
However, converting WAV to ogg or mp3 failed. Both oggenc and lame stopped at a length of 2:19. The whole WAV has a length of 6:48:07 and a size of 4.1 GB.

I still have to find out how to convert the large wav to ogg or mp3.

*hda*

I did a quick google search and I guess oggenc and lame have a problem with .wavs over  2 GB. The solution was to do this;
```
oggenc -q4 -o file.ogg - < file.wav
```

Change the quality to whatever you want.

---

### Post by hda on 2007-02-13
> **tbroderick said:**
> I did a quick google search and I guess oggenc and lame have a problem with .wavs over  2 GB. The solution was to do this;
```
oggenc -q4 -o file.ogg - < file.wav
```Change the quality to whatever you want.

Yeah! That will do the trick!

many thanks,
*hda*

---

