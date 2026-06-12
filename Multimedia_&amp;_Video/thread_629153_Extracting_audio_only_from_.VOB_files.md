---
title: "Extracting audio only from .VOB files"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by drhiii on 2007-12-02
Have searched and found parts of answers but am still struggling.

Anyone point to a tutorial, how-to, etc on how to extract audio only from .VOB files?  Am trying to get to .mp3 or .wav (to work in portable players).  Part of the challenge is if there are multiple .VOB files string together.  I have only found command line options to extract from a single .VOB file so far.

Help anyone?

---

### Post by ron999 on 2007-12-02
Hi
I don't know where there's a how-to.

If there are multiple VOB files in the VIDEO_TS folder of a DVD then (imo) they are difficult to manipulate.
I have used AcidRip to extract a whole title (the main feature or the trailer etc) onto my hard drive as an AVI or MPG file then used a command line instruction to extract the audio from it.
AcidRip's in the Ubuntu repos.

---

### Post by jocheem67 on 2007-12-02
Here's a short howto:

Use dvddecrypter under wine with streamprocessing enabled and search within the dvd chapters for the right audio track. Rip the vob to your homefolder...
( There are tutorials how to do this, there's one on the cdfreaks forums, I just googled it )

Now fire up mplayer and use this command:

mplayer yourfile.VOB -ao pcm:file=yourfile.wav

This tells mplayer only to convert the audio to a wav pcm file.....

What I do next is using audacity to cut the wav into multiple wav's....

Next it's possible to use lame from the commandline to create mp3's:

 lame --vbr-new -V 1 --resample 44100 yourfile.wav yourfile.mp3...

This creates high quality mp3's resampled to 44100 since your wav files are still sampled in 48000, which is not that handy....

You could also use ffmpeg:

 ffmpeg -i yourfile.wav -acodec mp3 -ab 320k -ar 44100 yourfile.mp3

Ffmpeg is capable using aac also, or ogg:

ffmpeg -i yourfile.wav -acodec vorbis -q 70 -ar 44100 yourfile.ogg ( not sure 'bout this one though.. )

It's a bit of a project but very educating in using mplayer, lame and ffmpeg, which are really strong from the cli!

Cheers!

---

### Post by disturbedite on 2007-12-02
or just use avidemux.

---

### Post by drhiii on 2007-12-02
Thank you all for these approaches.  Late last eve I did discover avidemux and figured out how to extract the audio.  It was reasonably well and am sure it is my amateur workflow, but the output degraded.  I will continue to improve my undersatnd of avidemux.

And, I will also make a run at the prior methods as well.  This helps a great deal to consolidate how to handle this.  Our local library has been taping many concerts in the last couple of years, some quite excellent, and they freely give away the output.  Video is one thing, but it is nice to be able to extract the audio for listening to on a portable device too.  Hence this pursuit.

Anywayz, I appreciate the time everyone put into creating explanations, and I will work through each one.

drhiii

---

### Post by mc4man on 2007-12-03
If you don't mind using wine there's a program that will do an excellent job very quickly and easily, maybe 3-8 min. per track start to finish ( at least for 30 days). It's called' dvd audio extractor'. All you need to do is open up the disk or folder in a player and see if the cut you want is an exact chapter. If so just open it up in dvd a.e., choose the chapter/s, which stream, and what format/quality(or direct stream) to convert to and click start.
If the cut you want is less than or spans chapters the easiest solution  is to install dvd shrink - you already using wine anyway. Again open the source in a player and note the start/stop of your cut(s)
Then open the source in shrink, re author the title using the start/stop function and you'll get a small video_ts with just the track(s) you want (re author multiple chapters (tracks) as separate titles) Then pass along to dvd a.e.
To gain access to your dvd drive for dvd a.e. the profile should be set to win xp , the only thing non functional is the select/unselect button, if there's alot of chapters it's quicker to uncheck the title(s) in the left box and then check the chapter(s) you wish.
Both progs. work fine in any wine ver. I had.
note: this is shareware so I won't post a link, you can get a 30 day full function trial

sorry: I meant this reply to go to  another post,  sorry if  somewhat off topic

---

### Post by disturbedite on 2007-12-03
the funny thing is, avidemux can do all that, and you don't have to run it with wine cuz there is a native linux port...

---

### Post by t2000kw on 2007-12-03
> **mc4man said:**
> If you don't mind using wine there's a program that will do an excellent job very quickly and easily . . .     

Thanks. I have Crossover Office installed on my desktop and hope to put Ubuntu and Crossover on this new laptop, so if it runs in Wine, it will likely run as good or better in Crossover.

I'll also check out the other program mentioned in th eoost after yours. 

Thanks for answering, and when I get the DVD in the mail in a week or so, I'll try it. I bought the K-9 three movie set on one DVD. The first K-9 movie has a song in the credits, Iko, Iko, that isn't available anywhere but on the DVD. No soundtrack for the movie for sale. I didn't know there were three of the K-9 movies so I bought it from a reseller on Amazon.com.

---

### Post by t2000kw on 2007-12-03
> **disturbedite said:**
> the funny thing is, avidemux can do all that, and you don't have to run it with wine cuz there is a native linux port...

I'll check that program out, if it's available in Synaptics. If I have to compile it, I can try, but I've had rather poor success doing that with other programs. I'm on a Windows PC right now (just got the laptopo and it came that way, hopefully will change that soon) or I would check it out right away. 

Thanks for both of your replies!!!

Donald

---

### Post by disturbedite on 2007-12-04
its in the repo, so no need to compile it, unless you really want to.

---

### Post by t2000kw on 2007-12-04
> **disturbedite said:**
> its in the repo, so no need to compile it, unless you really want to.

I installed it, gave it a quick look before leaving for work in a few minutes, and it looks like it will be somewhat intuitive to use.

---

