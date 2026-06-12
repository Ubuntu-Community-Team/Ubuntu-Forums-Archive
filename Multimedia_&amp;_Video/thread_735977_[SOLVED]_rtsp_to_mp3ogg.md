---
title: "[SOLVED] rtsp to mp3/ogg?"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by kaiju on 2008-03-26
i'd like to know if there is any way to rip rtsp streams directly to a compressed format.

i'm currently using mplayer to dump the stream to a wav file that i can later encode with lame/oggenc, and i'm wondering if there is a way i could avoid creating the few hundred megabites big intermediary wav.

---

### Post by eye208 on 2008-03-26
Use the -dumpstream option.

---

### Post by kaiju on 2008-03-26
i was a bit puzzled when i read your reply because i thought '-dumpstream' would use pcm, too. now i see that it rips the file in the original realaudio format, however it seems that i still have to first convert that to wav to be able to use lame on it.
(currently i'm using "mplayer -vc null -vo null -ao pcm:fast:file=$tempwav $stream" to directly rip to wav.)

so the question is whether there's a way to get rid of the intermediate wav for good.

---

### Post by ron999 on 2008-03-26
Hi
Use the dumpstream method to download a file in ra format.
Then you can do without a  wav file by using ffmpeg and a pipe:-
```
ffmpeg -i < name of your downloaded file > -f wav - | lame - foo.mp3
```

Insert the name of your own downloaded ra file.
You can speed things up by using gogo encoder instead of lame.

---

### Post by kaiju on 2008-03-26
thanks for your replies, ron999.

i tried the fifo trick, which made my script look like this:
```
#!/bin/bash
wget -O /tmp/ramfile $1
stream=`cat /tmp/ramfile | awk -F'?' '{print $1}'`
genfile=`echo $stream | awk -F/ '{print $NF}'`
tempfile=/tmp/$genfile
encfile=~/$genfile.mp3
echo ================================================================
echo "stream url:" $stream
echo "  tempfile:" $tempfile
echo "  mp3 file:" $encfile
echo ================================================================
sleep 5
mkfifo $tempfile
mplayer -vc null -vo null -ao pcm:fast:file=$tempfile $stream &
lame $tempfile $encfile ;
rm /tmp/ramfile $tempfile
```
the problem with that was that i got gaps in the mp3 file, probably because lame is working much faster than the stream is downloading. i first thought about giving a bigger cache to mplayer with the -cache option, but that would probably only delay the gap effect a bit.

i'll change the script to use ffmpeg and report back on that.

---

### Post by kaiju on 2008-03-26
here is the script with the ffmpeg part added:
```
#!/bin/bash
stream=`cat $1 | awk -F'?' '{print $1}'`
genfile=`echo $stream | awk -F/ '{print $NF}'`
tempfile=/tmp/$genfile
encfile=~/$genfile.mp3
echo ================================================================
echo "stream url:" $stream
echo "  tempfile:" $tempfile
echo "  mp3 file:" $encfile
echo ================================================================
sleep 5
mplayer -dumpstream -dumpfile $tempfile $stream ;
ffmpeg -i $tempfile -f wav - | lame - $encfile ;
rm $tempfile
```
i don't know what ram files usually look like, but the 'stream' part works with the files i tried it on (e.g. [http://www.bbc.co.uk/radio4/reith2003/ram/lecture1.ram](http://www.bbc.co.uk/radio4/reith2003/ram/lecture1.ram)).
and this way the large wav file is finally bypassed too.
thanks again :)

---

### Post by ron999 on 2008-03-26
OK, I'm glad it worked out for you.

In the past I have used a script which downloads the stream and encodes it to mp3 'on the fly' without creating any extra files. But it needs a fast, unbroken stream.

It's fairly easy though to download the stream using the dumpstream method. That results in a file named stream.dump.
After that, the simplest method is to rename the file stream.ra and listen on your PC using mplayer.
If it's necessary to convert to mp3 then either
use ffmpeg on its own
or
use ffmpeg piped through lame
or
use ffmpeg piped through gogo.
:)

---

### Post by kaiju on 2008-03-26
i did look up this gogo thingy you mentioned, but only got this far: [http://homepage2.nifty.com/kei-i/](http://homepage2.nifty.com/kei-i/). i'm very inexperienced and all, but i just wasn't sure it really is a serious alternative to lame, especially since it doesn't seem to have been updated in the past three-four years...

---

### Post by ron999 on 2008-03-26
Hi

Gogo is a version of lame that has been tweaked for speed.
Used from the command line like lame.
Options are similar.
When it's installed type gogo -h for information.
There's a deb package available, gogo-no-coda_3.13-1_i386.deb from here:-[http://rarewares.org/debian/packages/unstable/index.php]("http://rarewares.org/debian/packages/unstable/index.php")

So to use it your command would be like this:-

```
ffmpeg -i < name of your downloaded file > -f wav - | gogo stdin foo.mp3
```

Put some options in too if you like.
:)

---

### Post by kaiju on 2008-03-27
thanks again.
i'll give gogo a try sometime later. however, since mplayer has to work for the time corresponding to the length of the broadcast in order to download the real time stream anyway, the small additional encoding time is not a big issue in the case of this script.

---

### Post by andrew.46 on 2008-03-27
Hi,

 Looks like you have solved your issue but have a look at a simpler effort I put together for a radio broadcast:

[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

The script is down towards the bottom and has been working well. The wav file generated from this is about 1.4gig and the final ogg file is 130 megs or so.

      Andrew

---

### Post by eye208 on 2008-03-27
> **kaiju said:**
> i was a bit puzzled when i read your reply because i thought '-dumpstream' would use pcm, too. now i see that it rips the file in the original realaudio format, however it seems that i still have to first convert that to wav to be able to use lame on it.
From your description it wasn't clear you were talking about converting a RA file. RTSP has nothing to do with that. It's a protocol, not a format. You can stream anything through RTSP, not only RealAudio.

---

### Post by kaiju on 2008-03-27
> **eye208 said:**
> From your description it wasn't clear you were talking about converting a RA file. RTSP has nothing to do with that. It's a protocol, not a format. You can stream anything through RTSP, not only RealAudio.

oh, i see. i thought the two sort of went together.
thanks for your replies :)

---

