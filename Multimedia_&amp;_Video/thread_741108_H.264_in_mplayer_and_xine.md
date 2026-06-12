---
title: "H.264 in mplayer and xine"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by tribunal on 2008-03-31
Hi all!
I am trying to convert .mts files to avi files.
They are converted quite well.
Format of .avi is H.264
But I have one trouble.
I can play resulting .avi using mplayer without any troubles, but with any player using xine (totem, kaffeine, any other) I have troubles - sound and video move asynchrounously.
What can I do?
All codecs are installed.

---

### Post by theacoustician on 2008-03-31
> **tribunal said:**
> Hi all!
I am trying to convert .mts files to avi files.
They are converted quite well.
Format of .avi is H.264
But I have one trouble.
I can play resulting .avi using mplayer without any troubles, but with any player using xine (totem, kaffeine, any other) I have troubles - sound and video move asynchrounously.
What can I do?
All codecs are installed.

Why not use a container designed to hold H.264 such as .mp4, .mkv, or .mov?

---

### Post by tribunal on 2008-03-31
I'm not a guru :)
I am just using a script of other man:
here it is (main part)
```
if ( ! -f $audiofile ) then
		echo xporthdmv -hn $file 1 1 1
		     xporthdmv -hn $file 1 1 1 && mv bits0001.mpa $audiofile
	else
		echo $audiofile already exists, not creating it.
	endif

	#mkfifo $videofifo

	echo ldecod -i bits0001.mpv -o $videofifo
	     #ldecod -i bits0001.mpv -o $videofifo & 
	     ldecod -i bits0001.mpv -o $videofifo

	if ( ! -f $outputfile ) then
		echo mencoder $videofifo -demuxer rawvideo -rawvideo w=1440:h=1080 -aspect 16:9 -ofps 29.97 \
			      -audiofile $audiofile \
			      -oac pcm -ovc x264 -x264encopts bitrate=20000 \
			      -o $outputfile

		     mencoder $videofifo -demuxer rawvideo -rawvideo w=1440:h=1080 -aspect 16:9 -ofps 29.97 \
			      -audiofile $audiofile \
			      -oac pcm -ovc x264 -x264encopts bitrate=20000 \
			      -o $outputfile
	else
		echo $outputfile exists, not creating it.
	endif
```

scrpt works, but only mplayer can play these files

---

### Post by warp99 on 2008-03-31
The index is corrupt. Use the following string:

```
mencoder -forceidx -oac copy -ovc copy movie_new.avi -o movie.avi
```

That should rebuild the index so the other players will sync the audio/video.

---

### Post by eye208 on 2008-04-01
> **theacoustician said:**
> Why not use a container designed to hold H.264 such as .mp4, .mkv, or .mov?
That's what I've been asking every time the topic comes up. Isn't it funny how people run into the same problems over and over again? Using H.264 without B-frames is such a waste of resources. I guess when wavelet-based video codecs become state of the art, people will still wrap those streams in AVI containers, sacrificing 50 percent of efficiency and still messing up A/V sync. :mrgreen:

AVI is a dead horse. Stop riding it, folks! ;)

---

### Post by theacoustician on 2008-04-01
> **eye208 said:**
> That's what I've been asking every time the topic comes up. Isn't it funny how people run into the same problems over and over again? Using H.264 without B-frames is such a waste of resources. I guess when wavelet-based video codecs become state of the art, people will still wrap those streams in AVI containers, sacrificing 50 percent of efficiency and still messing up A/V sync. :mrgreen:

AVI is a dead horse. Stop riding it, folks! ;)

Some of us already have wavelet encoders ... :D

But yes, perhaps point out that Microsoft essentially ripped AVI from the RIFF format standard which itself is borrowed from IFF which was DEVELOPED OVER 20 YEARS AGO  people would think twice about its use.  To be clear : you cannot put modern codecs in AVI without hacks and those hacks are non standards based.  There is absolutely no guarentee that an AVI containing a modern codec will work from program to program or cross platforms.  You're using an open source OS, use an open standard container.

---

