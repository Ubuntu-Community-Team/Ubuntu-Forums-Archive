---
title: "ALSA Dmix changes tempo from XBMC"
date: 2012-02-24
forum: Multimedia Software
---

### Post by darkscout on 2012-02-24
I'm *attempting* to use ALSA dmix plugin to solve the lack of the Dual Audio output in Eden. I also use it so that numerous other programs can use output at once. Sometimes I just want to fire up mplayer from ssh to play a stream rather than do anything GUI, I also run Shairport instead of XBMC's implementation of AirPlay (because I want to! And that's my choice!)

So I came up with a very very simple asound.conf that I thought would fix everything.

```
pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer  {
 	type dmix
 	ipc_key 1024
 	slave {
		pcm "hw:0,1"
	}
        slave {
                pcm "hw:0,0"
        }
	bindings {
		0 0
		1 1
	}
}

ctl.dmixer {
	type hw
	card 0
}

```

And it works great. I even fired up 2 instances of shairport and used my iPhone and iTunes to be a fake DJ. It works great... except with XBMC.

It took me an entire movie to figure it out and it wasn't until I started watching CSI, but sound is just a slight bit slower tempo. As far as I can tell XBMC is playing everything at 1.0x speed but all of the women sound a bit like men and all the men like the devil.

Without any changes to alsa elsewhere (All I did was change to plughw:0,1 in XBMC) it works just fine.

Does anyone have any ideas?

---

### Post by darkscout on 2012-02-25
Anyone?

---

