---
title: "ffmpeg hangs computer when using reverse"
date: 2018-06-14
forum: Multimedia Software
---

### Post by Paddy Landau on 2018-06-14
I'm trying to reverse a video clip. But when I do, my computer hangs, and all I can do is reboot with [REIBUS]("http://blog.kember.net/articles/reisub-the-gentle-linux-restart/").

Making a straight copy works fine. For example, to copy the second minute of a video to a new file, this works flawlessly.
```
ffmpeg -i input.avi -ss 60 -t 60 -codec:a copy -codec:v copy copy.avi
```

However, doing the same thing in reverse causes my computer to hang.
```
ffmpeg -i input.avi -ss 60 -t 60 -vf reverse -af areverse copy.avi
```

How can I reverse a short video clip without the computer hanging? In fairness, I don't understand [FONT=&amp]ffmpeg[/FONT] well, so I've copied instructions from the web. If I'm using incorrect or inefficient options, please let me know!

**EDIT 1:** I specifically want to use the command line in order to automate a large number of clips, so a GUI solution won't work for me.

**EDIT 2:** I am trying to mix various clips together, only some of which are reversed, so it would be great if I could use [FONT=lucida console]ffmpeg[/FONT]. Otherwise I need to look at concatenating videos outside [FONT=&amp]ffmpeg[/FONT].

---

### Post by #&amp;thj^% on 2018-06-14
Hi Paddy Landau long time no see. I hope this is not to confusing.
I too a long time ago had to do something along these commands: 
```

cat $(ls -t *jpg) | ffmpeg -f image2pipe -vcodec mjpeg -r 25 -i - -i backwards.wav -vcodec libx264 -vpre slow -crf 20 -threads 0 -acodec flac output.mkv
```
Or something like this also "should" work.
**For video only**>> this is from my notes back in the year 2016:
```
ffmpeg -i /storage/emulated/0/ffvid/frameCount.mp4 -vf reverse reversed.mp4
```
**For audio and video:**
```
ffmpeg -i /storage/emulated/0/ffvid/frameCount.mp4 -vf reverse -af areverse reversed.mp4
```
This filter buffers the entire clip. For larger files, segment the file, reverse each segment and then concat the reversed segments.
I got this idea form stackexchange and I think things have changed some since then.
Good Luck

---

### Post by Paddy Landau on 2018-06-15
Thanks for the reply.

I find your first example confusing — where do the JPG files come from? Did you split the original video into its individual frames, and extract the audio into a separate file? This seems like a fairly time-consuming and inefficient way to do it, but if it's the only way, that's how it will have to be. My problem with this method is that I wouldn't know how to figure out the frames per second, especially if the original had a variable rate (does that ever happen)?

If you compare your third example with my original post, you'll see that it is precisely what I'm already doing, which seems to hang my system. (Your second example excludes the audio, which isn't what I want.)

---

### Post by #&amp;thj^% on 2018-06-15
It seems that  it isn't possible using ffmpeg to encode a video in reverse **without first dumping it to images and then back again.**
Have a look here: [https://stackoverflow.com/questions/2553448/encode-video-in-reverse](https://stackoverflow.com/questions/2553448/encode-video-in-reverse)
I was just as confused at first as you are now. Keep in mind that at times what we want to do _**is** sometimes very time consuming and awkward._ :(
I know you have said you prefer command line but Openshot might be a more eloquent solution. (it's a very intuitive an easy to use video editor.
You have to right click on the imported clip then properties -> speed tab, change the direction of the clip.)

Or even "kdenlive" reverse clip>> right-click on the clip: clip jobs / reverse clip. (I have also used this with xenial 16.04)
Just trying to help. ;)

---

### Post by Paddy Landau on 2018-06-16
I think that I've figured out what the problem is with [FONT=lucida console]ffmpeg[/FONT] hanging when reversing. It worked when I used a tiny clip of just 5 seconds. Looking at what was happening as I tried a longer clip, it seems that [FONT=lucida console]ffmpeg[/FONT] fills the swap partition rapidly. A 60-second clip quickly reached filled 1.6 Gb of swap, at which point I cancelled before the computer would hang.

I've been trying the method described for [dumping frames and resurrecting them in reverse]("https://nhs.io/reverse/"), but without success. It seems that the [FONT=lucida console]ffmpeg[/FONT] command has changed since that was posted.

I'm officially giving up now. It's become far too difficult.

---

### Post by #&amp;thj^% on 2018-06-16
> I'm officially giving up now. It's become far too difficult. 
Or just bite the bullet and use "OpenShot" it just took me under 5 mins to choose the clip I wanted to reverse from a 1 hour video>>>the clip itself was 1min 45secs long.
Way easier than using the CLI method. :p

---

### Post by Paddy Landau on 2018-06-17
> **1fallen said:**
> Or just bite the bullet and use "OpenShot"…
Thanks, but as I said, this is for "a large number of clips." I do use OpenShot, and unfortunately it's not appropriate in this case.

Until the bug in [FONT=lucida console]ffmpeg[/FONT] is resolved, I'll do without this function. It's become way too complicated for my rather simple needs :(

---

