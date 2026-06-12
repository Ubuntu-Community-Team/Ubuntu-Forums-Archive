---
title: "What is best screencast program? For me, Kazam has been destroyed by updates"
date: 2013-03-08
forum: Multimedia Software
---

### Post by sdowney717 on 2013-03-08
Kazam used to work good, now it has been ruined IMO on the latest version.

---

### Post by ajgreeny on 2013-03-08
What about the command line and using ffmpeg, or now presumably, avconv, with perhaps slightly diferent syntax.
```
ffmpeg -f x11grab -s 1280x1024 -r 15 -i :0.0 -s 1280x1024 -r 15 -sameq video.avi
``` records desktop activity to video.avi.  You will probably need to play with the resolution figures I quote here, but it certainly works well even on my old desktop machine.

---

### Post by sdowney717 on 2013-03-08
That works fairly decent.
How do you also capture the sound?

---

### Post by sdowney717 on 2013-03-08
ffmpeg -f alsa -i pulse -f x11grab -r 25 -s 1280x720 -i :0.0+0,24 -acodec pcm_s16le 
   -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mov

gives sound but sound is at a very low level

---

### Post by mc4man on 2013-03-08
> **sdowney717 said:**
> 

gives sound but sound is at a very low level

What sound are you recording? (system, mic, or both

Here I use the real FFmpeg so command(s) are a bit different but for mic I use the default  -  (screen 1), for system the monitor - (screen 2,  note for purpose of screens  am running recorder so they show but not actually outputting any sound so levels are nil
(am going to fool around with a both later on different install, believe it requires a null sink with 2 loopbacks - 
[http://www.linux.com/learn/tutorials/367395:weekend-project-record-from-skype-calls-and-other-apps-on-linux](http://www.linux.com/learn/tutorials/367395:weekend-project-record-from-skype-calls-and-other-apps-on-linux) (Full-Duplex Recording
copy of above
[http://www.pclinuxos.com/forum/index.php/topic,105968.0.html](http://www.pclinuxos.com/forum/index.php/topic,105968.0.html)

You may have a setting in alsamixer to boost mic or maybe in sound settings

---

### Post by silverburst on 2013-03-08
I've used the ffmpeg method previously and it works well but now I have a need to record my second monitor instead. Anyone know how this can be accomplished?

---

### Post by sdowney717 on 2013-03-08
Running pavucontrol when recording show no apps?

Ok, it does show and it was set to my webcam. I set to monitor of built in internal audio:p

And the sound is ok. I can only play the mov file with smplayer??
VLC will play the file but with no sound?
Movie player looks for a codec and gives up trying?


This is the commandline I am using.
ffmpeg -f alsa -i pulse -f x11grab -r 25 -s 1680x1024 -i :0.0+0,24 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mov

---

### Post by Chatoyer on 2013-03-28
I hope it's not inappropriate to return to the original topic.  I'd like to ask whether Kazam had performed the same for others as it had for me.  I'd installed this and found that it worked once to export video to avidemux, although in false color.  Is there a trend among Ubuntu developers to disable their packages, as if they were trial-ware?  Is it their expectation to sell licensed versions instead when users find working versions unavailable?

Thanks for the helpful topic, too, and for the informative reply vis. ffmpeg.

---

