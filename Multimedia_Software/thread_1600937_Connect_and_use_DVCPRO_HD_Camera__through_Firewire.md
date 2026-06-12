---
title: "Connect and use DVCPRO HD Camera  through Firewire"
date: 2010-10-19
forum: Multimedia Software
---

### Post by IceDoE on 2010-10-19
I have a Panasonic DVCPRO HD camera with a Firewire output. I'd like to take the video footage off of the camera and put it into my Ubuntu (Studio, 10.04) machine. Unfortunately, neither my Ubuntu machine nor the camera seem to recognize a connection with each other. 

I've only used this camera like this with Mac OSX, in which I press a button a couple folders pop up with everything in them which I can then digitize in Final Cut Pro. I'd prefer being able to use my Ubuntu setup with Open Source Software to view and edit this footage. 

Any thoughts on how to get ubuntu and this camera to talk to each other and play nice?

---

### Post by no2498 on 2010-10-20
i do not use fire wire but have seen that it uses 1394
you can read and see i think its webcam Studio
just look for webcam in the repose

---

### Post by arvliet on 2011-02-07
bump bump.  Anybody?

---

### Post by mocha on 2011-02-07
You can use dvgrab on the command line or Kino.  I use the following to capture DV tapes:

```
sudo dvgrab -frames 0 -size 0 -format raw -timestamp output.dv
```

man dvgrab for more info on capturing from USB and HD cameras.

---

### Post by rhk on 2012-09-02
I'm trying to solve similar problem with TRV-900 and Ubuntu 12.04 and can't make it recognize the camera. There seem to be many people fighting with the same problems and it seems that some of it started after the old FW stack was dropped (in Natty? Can't remember).

So please let us know if you ever solved this, it'll propably help others looking for solutions.

---

### Post by wildmanne39 on 2012-09-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

