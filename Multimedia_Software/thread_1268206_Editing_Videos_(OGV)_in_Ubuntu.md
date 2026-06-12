---
title: "Editing Videos (OGV) in Ubuntu"
date: 2009-09-16
forum: Multimedia Software
---

### Post by coldReactive on 2009-09-16
First and foremost... let's get the stuff I can't do out of the way:

-- I can't use avidemux, don't wish to compile from source to get OGV Support

-- I can't use Open Movie Editor, since its interface is extremely annoying.

Any recommendations on what editor I should use that I don't have to compile from source to install?

If you can't give me one, give me a place that I can upload over 500+ MB per video file and accepts OGV, and doesn't have a silly 10 minute limit like Youtube does. I also can't be bothered to sign up for extra status (IE: MotionMaker on DailyMotion) to upload videos.

---

### Post by coldReactive on 2009-09-16
Just tried cinelerra, no good either.

Just tried LiVES, no good either.

---

### Post by lovinglinux on 2009-09-16
I like Pitivi. It's simple and does the job well.

---

### Post by coldReactive on 2009-09-16
> **lovinglinux said:**
> I like Pitivi. It's simple and does the job well.

Can you tell me how to split an OGV from a specific point to the end of the file, and delete the first part of the split, then move the split part at the end so that it renders the last part of the split?

Sorry if that sounds confusing but it's the best I can explain. There ARE NO TUTORIALS that are text-only (I hate video tutorials) on how to split videos correctly in PiTiVi.

---

### Post by lovinglinux on 2009-09-16
> **coldReactive said:**
> Can you tell me how to split an OGV from a specific point to the end of the file, and delete the first part of the split, then move the split part at the end so that it renders the last part of the split?

Sorry if that sounds confusing but it's the best I can explain. There ARE NO TUTORIALS that are text-only (I hate video tutorials) on how to split videos correctly in PiTiVi.

Drag the extremities of the video or use the split function, select and delete the one you don't want.

---

### Post by coldReactive on 2009-09-16
> **lovinglinux said:**
> Drag the extremities of the video or use the split function, select and delete the one you don't want.

Doing so causes a big black part of the video to render before the part I want to show, when using the split function. I can't drag the video selection either, cause then the end goes farther off according to the end time above the time line. If I drag the end portion that I want to only show, then it works, somewhat, some of the portion that happens right before the portion I cut out renders with the portion I want to render, but I don't want that.

After about 6+ tries, I finally got it to do what I want.

---

### Post by cr33dog on 2009-11-22
See here:
[http://commons.wikimedia.org/wiki/Help:Converting_video#Ogg_Video_Tools](http://commons.wikimedia.org/wiki/Help:Converting_video#Ogg_Video_Tools)

apt-get install oggz-tools
man oggz-chop

---

### Post by SR_ELPIRATA on 2009-11-23
Stupid suggestion ahead:

Get your own webserver :) or make one at home. I dont really publish videos on the net but I figure if you dont want restrictions on 'free' providers... the way to go is get your own.

On the editing part, I'm with you. Some stuff here is really complicated to use. Gonna try pitivi though.

ELP

---

