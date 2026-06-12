---
title: "Trouble with .wav to .ogg batch conversion"
date: 2009-09-12
forum: Multimedia Software
---

### Post by IanVonSpeedfreak on 2009-09-12
Okay, I have this folder full of high-quality wavs just taking up space on my hard drive.  I'm not particularly keen on lossless formats as I currently possess a very small HDD and I find lossy formats like mp3s and oggs to be more flexible.  So I'm dealing with a lot of wavs here (totally just over 1GB), and I want to convert them all but I don't have the patience to deal with them one by one.  So I've been looking for a method for batch converting to ogg.  SoundKonverter and SoundConverter have both been unreliable as they each have failed to produce a complete output file (playable, but noticeably shorter in length).  I used a command I found in [another thread on this forum]("http://ubuntuforums.org/showthread.php?p=7857135") using oggenc from the CLI, but it also failed to produce complete files (some were, some weren't).  So by far, I've been disappointed, but there appears to be some glimmer of hope.  I tried using what I knew of ffmpeg to convert an individual file, it worked!  The quality wasn't as good as expected (perhaps 192ab is too low), but the file was complete.  So now I would just like to know if there is a way to do batch conversions with ffmpeg?  I tried using * as a wildcard, but it didn't seem to work.  Of course, it doesn't have to be ffmpeg, I just need a method of conversion that can reliably produce a complete conversion.

Thanks in advance.

---

### Post by andrew.46 on 2009-09-12
Hi IanVonSpeedfreak,

You could try using a *for loop* for this one. (*With thanks to mc4man for this syntax :).*) Change to the directory with all your wav files and try:

```

for f in *.wav
do 
oggenc -q 6 "$f" -o "${f%.wav}.ogg"
done

```

This uses oggenc rather than FFmpeg which I believe is the better choice, but of course you can substitute FFmpeg commands here if you prefer or use a higher -q number with oggenc if you prefer a higher bitrate. I ran this on a test folder with a couple of wav files:

```

andrew@skamandros~/Desktop/test$ for f in *.wav
> do 
> oggenc -q 6 "$f" -o "${f%.wav}.ogg"
> done
Opening with wav module: WAV file reader
Encoding "Schumann Cello Concerto.wav" to 
         "Schumann Cello Concerto.ogg" 
at quality 6.00
	[100.0%] [ 0m00s remaining] | 

Done encoding file "Schumann Cello Concerto.ogg"

	File length:  24m 39.0s
	Elapsed time: 1m 43.1s
	Rate:         14.3595
	Average bitrate: 145.6 kb/s

Opening with wav module: WAV file reader
Encoding "schubert quintet.wav" to 
         "schubert quintet.ogg" 
at quality 6.00
	[100.0%] [ 0m00s remaining] \ 

Done encoding file "schubert quintet.ogg"

	File length:  55m 57.0s
	Elapsed time: 4m 00.3s
	Rate:         13.9724
	Average bitrate: 165.2 kb/s

andrew@skamandros~/Desktop/test$ 

```

and it runs beautifully. All the best with this one!

Andrew

---

### Post by IanVonSpeedfreak on 2009-09-13
Thanks for the reply ^^.

The reason why I'm not using oggenc is because it rarely ever reaches 100%.  The resulting file is playable but incomplete.  I'd like to figure out what is going on there, but I wouldn't know where to start.  For now I'm assuming it's a bug.  In any case, the same thing you are doing there can easily be achieved with this command:

```
oggenc -q 6 *.wav
```

Obviously you should cd to the folder containing the wavs you wish to change, just like your command.  Of course, your command allows me to use FFMpeg (which has yet to produce any incomplete files afaik).  If this method works, I'll be sure to mark the thread appropriately as well as post my version of the command using FFMpeg ^^.

Thank you!

---

### Post by mc4man on 2009-09-13
both oggenc and flac can be just wild-carded  because they don't specify an output file when batched

While i tend to use NeroAac, mainly from the cd, haven't had any length issues with oggenc at all, using a -q from 8 - 10  ( a -q of 9 is around 20 % of orig., 
 
I use  the 1.2 vorbis-tools on hardy, don't think it really matters, though you could try on yours , you'd need to upgrade  libspeex1, may be one other, not an issue to do so, they're 'deadended' so to speak
 
[http://packages.ubuntu.com/jaunty/vorbis-tools](http://packages.ubuntu.com/jaunty/vorbis-tools)

---

### Post by IanVonSpeedfreak on 2009-09-13
I'm marking this thread as solved, despite the fact that not everything was converted.  The files I was primarily concerned with did get converted, however, which is something that I hadn't achieved with oggenc.  I did try oggenc on maximum quality settings btw (as I copied the command directly in the thread I linked to in the OP), but regardless of the settings it still spat out a "deadended" file.  I don't mean to dog on oggenc either, as I can see that I'm probably the only one to have this issue (I haven't noticed any other threads about it).  It's probably something I'm doing wrong, but I would have no idea what that would be.

Anyway, using a *for loop* with FFMpeg did the trick!  As promised, here's the command I used:

```
for f in *.wav
do  ffmpeg -i "$f" -aq 100 "${f%.wav}.ogg"
done
```

The only hiccup is that FFMpeg apparently has a problem with any audio that uses more than 2-channel stereo, so a number of files failed to convert.  It's a shame, but at least the files that I was primarily concerned with just happened to be inside of the parameters.  Thanks to both of you, you were both very helpful!

Wow, amazing what one can learn in a night!

---

### Post by mc4man on 2009-09-13
> It's probably something I'm doing wrong, but I would have no idea what that would be.

That would seem unlikely as oggenc is pretty straightforward.
If you had sox installed you could try a whatever.wav in  whatever-1.wav out on one of the 'deadended files to see if it picked up on anything or if the whatever-1 was better handled by oggenc

If the unconverted files are multichannel, I've never had a problem (though never had too many), maybe one of the people here who know ffmpeg well can help you ( map the channels..?

---

### Post by andrew.46 on 2009-09-13
Hi IanVonSpeedfreak,

> **IanVonSpeedfreak said:**
>  In any case, the same thing you are doing there can easily be achieved with this command:

```
oggenc -q 6 *.wav
```



Oops :)

Andrew

---

