---
title: "Fix for choppy hda_intel sound"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by QuinnStorm on 2007-05-29
This is just a quick little post about a way to fix your choppy HDA_intel sound card's sound (may work for some other choppy sound too)  Others have also described this as "crackly".

Copy the following into ~/.asoundrc

```

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer {
	type dmix
	ipc_key 1024
	slave {
		pcm {
			type hw
			card 0
		}	
		rate 44100
		period_time 0
		period_size 2048
		buffer_size 32768
	}
	slowptr 1
}


```

---

### Post by terrax on 2007-06-15
Hello.

It acutally did my sound make more crackly noises (In sdl sound apps only). I had to use thiese instead:

```

pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}

```

And then turn my volume to max. Then there is no other sound, than sweet quality sound :-)

---

### Post by Daniel15 on 2008-01-03
**Thank you!** I've been looking at heaps of posts detailing fixes for choppy sound on the hda_intel sound card, but this seems to have actually worked! Most games seem to have perfect sound now :)

Thanks again :D

---

