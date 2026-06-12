---
title: "lame/oggenc with multi-threading support?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by lamborghiniwang on 2008-07-07
I am trying to encode a few hundred of audio files into either Vorbis or mp3, and it seems neither oggenc nor lame in the repo supports multi-threading. I am wondering if there is any vorbis/mp3 encoding applications that can take advantage of the dual core CPU.

  I found a project called [[COLOR="Blue"]**_Lame MT_**[/COLOR]]("http://softlab.technion.ac.il/project/LAME/html/lame.html") which supports multi-threading, but when I tried to compile from the source, I always get the error message:
```

$ ./configure
bash: ./configure: /bin/sh^M: bad interpreter: No such file or directory

```
```

$bash configure
: command not found 
configure: line 20: syntax error near unexpected token `elif'
configure: line 20: `elif test -n "${BASH_VERSION+set}" && (set -o posix) >/dev/null '>&1; then

```

Any suggestions?

---

### Post by lamborghiniwang on 2008-07-08
hoho, I just found out about the [Ogg Vorbis accelerating project]("http://homepage3.nifty.com/blacksword/index_e.htm"). I couldn't found source code or binaries for Linux, but they do provide Win32 binaries, and the best part is that the **[COLOR="Red"]Win32 binaries works with Wine[/COLOR]** :D. I compared Lancer+wine with the original oggenc in the official repo and Lancer is almost 3x as fast on my Core2 Duo T7300 (Hardy 64bit) when encoding a 440MB pcm .wav file:

original oggenc:
```

$ file audio.wav 
audio.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 32000 Hz
$ time oggenc audio.wav 
Opening with wav module: WAV file reader
Encoding "audio.wav" to 
         "audio.ogg" 
at quality 3.00
	[100.0%] [ 0m00s remaining] - 
Done encoding file "audio.ogg"
	File length:  60m 00.0s
	**Elapsed time: 1m 43.7s**
	**Rate:         34.7153**
	Average bitrate: 70.3 kb/s
real	1m43.717s
user	1m43.050s
sys	0m0.368s

```

Lancer+wine (change the quality parameter to "-q 5" has almost no effects on the encoding time, amazing. :D):
```

$ file audio.wav 
audio.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 32000 Hz
$ time ogg2 audio.wav 
Opening with wav module: WAV file reader
Encoding "audio.wav" to 
         "audio.ogg" 
at quality 3.00
	[100.0%] [ 0m00s remaining] /
Done encoding file "audio.ogg"
	File length:  60m 00.0s
	**Elapsed time: 0m 33.113s**
	**Rate:         108.730227**
	Average bitrate: 71.7 kb/s
real	0m33.584s
user	1m3.096s
sys	0m2.872s

```

The only thing is that it seems Lancer has not been updated since November 2006, so I am not sure how much audio quality difference it makes comparing with the original oggenc.
I also tried the [**Vorbis with aoTuV beta5 patch**]("http://ubuntuforums.org/showthread.php?t=651980"), it is about 5% faster than the origianl oggenc therefore still much slower than Lancer+wine, but is said to provide better audio quality.

Unfortunately, it seems Lame-MT doesn't support multi-threading under wine (or at least I couldn't make it work multi-threaded).

---

### Post by hugmenot on 2008-07-09
The script has Windows CRLF line endings.  Do you see the ^M? That is indicative of the wrong newline format.

Try this on the script:

```
tr -d \\r < configure > configure.new
```

Also, why don't you simply start two concurrent encodings?

---

### Post by AusIV4 on 2008-07-09
> **hugmenot said:**
> Also, why don't you simply start two concurrent encodings?
This was my thought.

If you have multiple files to encode, you can parallelize it just by encoding multiple files at a time. Encoding a single mp3 or ogg with multiple threads may be possible, but it's a hairy proposition. Encoding multiple files simultaneously should give you the same kinds of speedups without nearly as much complication.

---

### Post by ray^try on 2013-04-19
I made a small script for scaling jpg images in multiple threads.

```
#!/bin/sh

for i in $(seq 7265 7530);
do
    while [ $(ps | grep pnmtojpeg | wc -l) -gt 2 ]; do sleep 1; done
    source="/media/NIKON D7000/DCIM/110D7000/DSC_$i.JPG"
    target="DSC_$i.JPG"
    echo $source
    jpegtopnm -dct=float "$source" 2>/dev/null | pnmscale -xsize=1500 | pnmtojpeg -dct=float -optimize -quality 85 >"$target" &
done

while [ $(ps | grep pnmtojpeg | wc -l) -gt 0 ]; do sleep 1; done


```

You can easily modify it to convert audio files in multiple threads.

---

### Post by wildmanne39 on 2013-04-19
!Old thread closed! Please do not post in old threads.

---

