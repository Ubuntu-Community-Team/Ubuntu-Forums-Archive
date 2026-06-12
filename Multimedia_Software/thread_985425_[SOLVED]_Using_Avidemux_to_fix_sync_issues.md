---
title: "[SOLVED] Using Avidemux to fix sync issues"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Voorhees1979 on 2008-11-17
Hi there

I have a video on my hd that is 200ms out of sync. Could someone tell me the best way to get avidemux to resync it.

Many Thanks

---

### Post by sensimilla on 2008-11-18
First you need to open the file in avidemux, then make sure that on the left video and audio are both set to copy.
Check that format underneath is set to the same as the original file.

Tick the box which says shift under the audio section, enter 200 or -200 in the box next to it and then hit save choose a filename and it's done.

It don't think that there is a way for avidemux to work out the exact shift or to preview the shift so I would reccomend using the A & B buttons to select a small section of the file and save that, check it for sync and then redo the shift amount until it is spot on and then save the whole video.

Hope this helps

---

### Post by Voorhees1979 on 2008-11-18
That was it, wow didnt know it was as easy as that.

Thanks alot for helping me.

---

### Post by sharat87 on 2008-12-05
hello, i haven't tried this, but can't this be done with ffmpeg on command line?

or any other way on command line :)

i'll try this 'avidemux' anyway... thanks

EDIT: ohh, i just noticed the 'avidemux-cli' package in synaptic... thanks anyway :)

---

### Post by Skerit on 2009-01-11
What do you do when avidemux is actually the cause of your sync problems?

(avidemux can't work with mythtv mpeg files, it ignores the sync data or so ...)

---

### Post by sensimilla on 2009-01-11
> **Skerit said:**
> What do you do when avidemux is actually the cause of your sync problems?

(avidemux can't work with mythtv mpeg files, it ignores the sync data or so ...)

I used to run the files through a java program called projectX which cleans up and repairs sync issues with mpeg files. The way it works is to demux (seperate) the audio and video stream into two seperate files which you load into avidemux.

You can install it with

```
sudo apt-get install project-x
```

unfortunately it is not the easiest program to use in the world...

There is a guide here which should get you started:
[http://www.doom9.org/index.html?/DigiTV/projectx.htm]("http://www.doom9.org/index.html?/DigiTV/projectx.htm")

There may be an easier to use program by now which can fix sync errors in mpeg files but as I haven't had a capture card for four years I wouldn't know.

---

