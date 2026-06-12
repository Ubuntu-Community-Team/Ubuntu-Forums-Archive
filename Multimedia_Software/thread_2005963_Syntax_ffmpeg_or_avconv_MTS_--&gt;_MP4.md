---
title: "Syntax: ffmpeg or avconv MTS --&gt; MP4"
date: 2012-06-18
forum: Multimedia Software
---

### Post by wilburi on 2012-06-18
Hello,

I tried to solve this problem first in german forums, but there seems nobody to know anything about it. I have to say sorry about my poor knowledge of your language, but I hope you can see, what I mean.

I have a Panasonic Lumix TZ22 and with this, I can have video files as MTS-files. 
Typ: MPEG-Video, 
Container: MPEG-2 Transport-Stream
Abmessungen: 1920 x 1080
Video
Codec H.264
Bildfrequenz: 25
Bitrate: k.A.
Audio
Codec: audio/x-eac3
Kanäle: Stereo
Abtastrate: 48000 Hz
Bitrate: 192 kb/s

In my folder are some files like this:
norbert@norbert-NB:~/Bilder/Pictures/2012/06$ dir *.MTS
00012.MTS 00016.MTS 00020.MTS 00024.MTS 00028.MTS 00032.MTS 00036.MTS
00013.MTS 00017.MTS 00021.MTS 00025.MTS 00029.MTS 00033.MTS
00014.MTS 00018.MTS 00022.MTS 00026.MTS 00030.MTS 00034.MTS
00015.MTS 00019.MTS 00023.MTS 00027.MTS 00031.MTS 00035.MTS

There is no problem to give the order
avconv -i 00014.MTS 00014.mp4

This works.
But what I want to have is an order to do this with all files at once.
I tried
avconv -i %05d.MTS %05d.mp4
Error:  %05d.MTS: No such file or directory

and with
avconv -i *.MTS *.mp4
Error: Unable to find a suitable output format for '00014.MTS'

The same is when I use ffmpeg.

Can someone help?

My System: Ubuntu 12.04
Gnome classic
Norbert

---

### Post by ron999 on 2012-06-18
Hi
Use 'cd' to move to the correct folder.
Then try a command like this:-
```
for f in *.MTS; do ffmpeg -i "$f" ${f%.MTS}.mp4; done
```

---

### Post by wilburi on 2012-06-18
Wow!
An answer given in less than 10 minutes!
This could be a record.

And in my opinion, i seems to work!

Thanks a lot!
Norbert

---

### Post by FakeOutdoorsman on 2012-06-18
> **wilburi said:**
> 
```
avconv -i %05d.MTS %05d.mp4
Error:  %05d.MTS: No such file or directory
```


This should have worked if your inputs were named 00001.MTS to 00025.MTS. Also, no need to apologize for your English.

> **ron999 said:**
> Hi
Use 'cd' to move to the correct folder.
Then try a command like this:-
```
for f in *.MTS; do ffmpeg -i "$f" ${f%.MTS}.mp4; done
```

Alternatively you can try:
```
for f in *.MTS; do ffmpeg -i "$f" -vcodec copy -acodec copy ${f%.MTS}.mp4; done
```
...otherwise ffmpeg will re-encode your output. I don't know if that's what you want or not. My example will simply "copy and paste" the input from MTS to MP4 container format.

Note that if you do want to re-encode ffmpeg will use either the "mpeg4" or "libx264" encoders depending on your ffmpeg version and available encoders (ffmpeg will show what it's using in the console output). Default quality of "mpeg4" is crappy, so add *-qscale* as an output option with a value of 2-5 (lower value is higher quality).

---

### Post by wilburi on 2012-06-18
Ooops!!!

What an idea! Simple rename the file from *.MTS to *mp4.

I nearly couldn't believe: This is enough! :p

But on the other side: This works if I simple rename a file. But when I use your code, the outpout- files are not working.

With re-encoding the files have the codec MPEG-4 AAC, but some are shorter than the original MTS-file. 

Would you say 
for f in *.MTS; do ffmpeg -i "$f" ${f%.MTS}.mp4 *-qscale 2*; done

is working?

Norbert

---

### Post by FakeOutdoorsman on 2012-06-18
> **wilburi said:**
> What an idea! Simple rename the file from *.MTS to *mp4.
I don't recommend this method. It's still in MTS container, but now mis-named. I should have asked earlier, but why do you want MP4? What is wrong with using your original files?

> **wilburi said:**
> But when I use your code, the outpout- files are not working.
I can only guess what the problem is without more detailed information.

> **wilburi said:**
> With re-encoding the files have the codec MPEG-4 AAC, but some are shorter than the original MTS-file.
Shorter duration?

> **wilburi said:**
> Would you say 
```
for f in *.MTS; do ffmpeg -i "$f" ${f%.MTS}.mp4 *-qscale 2*; done
```
is working?
It's in the wrong place:
```
for f in *.MTS; do ffmpeg -i "$f" -qscale 2 ${f%.MTS}.mp4; done
```

---

### Post by wilburi on 2012-06-18
The next step, what I do with the mp4-file, is to put in in ffDiaporama. I mix there pictures and videos and have a video at the end. 

And you are quite rigth: with a renamed file this will not work. 

With
for f in *.MTS; do ffmpeg -i "$f" -vcodec copy -acodec copy ${f%.MTS}.mp4; done
I see in terminal
[mp4 @ 0xa557e0] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 1 >= 1
av_interleaved_write_frame(): Invalid argument

And in vlc:
 [COLOR=#ff0000]VLC kann das Eingabeformat nicht erkennen.:[/COLOR]
 [COLOR=#000000]Das Format von 'file:///home/norbert/Bilder/Pictures/2012/06/Test/00012.mp4' konnte nicht festgestellt werden. Sehen Sie für Details im Fehlerprotokoll nach.[/COLOR]


[COLOR=#000000]That means: vlc is unable to know the format of input .[/COLOR]
I could look for a log-file, but I have no idea where this is to find.


Norbert

[COLOR=#000000]
[/COLOR]

---

### Post by FakeOutdoorsman on 2012-06-18
Try this:
```
for f in *.MTS; do ffmpeg -i "$f" -vcodec copy -acodec copy ${f%.MTS}.mkv; done
```

---

### Post by wilburi on 2012-06-19
Thank you.
The problem seems to bo solved now.

Have a nice day
Norbert

---

