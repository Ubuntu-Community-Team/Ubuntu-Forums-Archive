---
title: "No capture device. No Sound. TVTime works?"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by phossal on 2007-01-14
I have an ATI TV Wonder 200 which I simply plugged in.
I configured it like so:
```
	sudo -s
	cd /etc/modprobe.d/
	echo "options cx88xx card=4 tuner=44" > cx88xx
	modprobe -r cx8800
	modprobe cx8800
```

When I run TVTime at the command prompt, I get TV and Sound. Perfect. But when I try to run xawtv, or capture tv from /dev/video0, I'm being told no capture device is found.

Worse, I'm able to capture tv like this:
```
ffmpeg -target ntsc-svcd new.mpg
```
This is great, except I don't get sound on playback. I need *sound*. Help!

---

### Post by 0chamba0 on 2007-01-23
Sorry if this is not the right place to post. i couldn't find a link or icon to start a new one. I have been using ubuntu for the last 3 months. I went step by step and still haven't finished.
My tv card is not working. i have Xawtv, the software works but doesn't recognize any channel. i go edit and doesn't show anything. Ubuntu recognize the tvcard (i think, bc i can see it) 
Could someone tell me what to do. that way i don't have to go back to windows to watch TV. i know how to work with some media now(DVD, CD, AVI, MPEG, etc) but want to watch TV.
Thank you for reading my post guys and dolls.

---

