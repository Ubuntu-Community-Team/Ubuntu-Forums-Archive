---
title: "Stream video from one PC to another?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by Roasted on 2010-06-03
Is it possible that I can hook a video camera up to 1 Ubuntu system and broadcast that stream to another system?

I'd like to hook up a video camera to 1 Ubuntu computer, then from across the building, have another Ubuntu computer there to "catch" and essentially watch that stream, to where a projector will be there to project what's on screen. Is that possible?

---

### Post by xzero1 on 2010-06-04
You should be able to do this, at least if both computers are on the same network. The details will depend on your hardware.

---

### Post by tgalati4 on 2010-06-04
Although designed for security purposes, both motion and zoneminder will do that.

You can do it at a pretty low-level, assume your camera is located at /dev/video0; assume that your remote machine is networked and can mount the drive on the machine that hosts the camera.

cat /dev/video0 > /tmp/videofeed.mpg

Then on the machine that you want to project:

mplayer smb://remotemachinename/tmp/videofeed.mpg

Or something to that effect.

---

### Post by xzero1 on 2010-06-04
It depends on your hardware setup that why I was not specific. If tgalati4's method works then you can simplify it to one command via pipes. In my case:

```
cat /dev/video1 | buffer -s 500k -b 20 -m 20m  | ffmpeg -i - -f mpegts -vcodec mpeg4 -acodec copy -ac 2 -ab 64k -s vga -r 30 -re -b 2000k -threads 4 udp://192.168.0.80:1234
```

Where 192.168.0.80 is my target network IP. Note that I am transcoding on the fly and using buffer which may not be necessary.

---

### Post by Roasted on 2010-06-04
> **tgalati4 said:**
> Although designed for security purposes, both motion and zoneminder will do that.

You can do it at a pretty low-level, assume your camera is located at /dev/video0; assume that your remote machine is networked and can mount the drive on the machine that hosts the camera.

cat /dev/video0 > /tmp/videofeed.mpg

Then on the machine that you want to project:

mplayer smb://remotemachinename/tmp/videofeed.mpg

Or something to that effect.

That would be awesome! Except I've been unsuccessfully trying to get ZoneMinder working for about 2 weeks now.

:(

---

### Post by tgalati4 on 2010-06-04
Zoneminder is a little tricky to set up on Ubuntu.  I think it was originally developed for Fedora, so there are some vital tweaks needed to get it to work.

---

### Post by tgalati4 on 2010-06-04
I'm going to try that script @xero1!

I presume you can watch the stream with:

vlc udp://192.168.0.80:1234

---

### Post by xzero1 on 2010-06-05
> **tgalati4 said:**
> I'm going to try that script @xero1!

I presume you can watch the stream with:

vlc udp://192.168.0.80:1234

Well you could try it but I wouldn't expect it to work without a bit of tweaking. I don't know about vlc but you can use the command:

mplayer udp://address:1234

Where address is the target machine's network IP address. If some of this is too confusing, I can try to walk you through it. The advantage of this method is you won't have any huge temporary files or smb shares to worry about.

---

### Post by Roasted on 2010-06-07
> **tgalati4 said:**
> Zoneminder is a little tricky to set up on Ubuntu.  I think it was originally developed for Fedora, so there are some vital tweaks needed to get it to work.

The problem isn't installing it. It's just getting the interface to play nice. Example - I don't have a login screen to ZoneMinder, yet the instructions say I should. Etc.

---

### Post by xzero1 on 2010-06-07
Another option you might consider is VLC. VLC even has a streaming menu option and basically walks you through it.

---

### Post by Roasted on 2010-06-08
> **xzero1 said:**
> Another option you might consider is VLC. VLC even has a streaming menu option and basically walks you through it.

Any guides on that? Cause uh.. I tried that, and it errored out.

---

### Post by xzero1 on 2010-06-08
Can you be a bit more specific on the errors? What works and what doesn't.

---

