---
title: "Can't get software mixing working with surround sound"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by kinjin on 2007-11-05
I can get surround sound working on all my speakers, and I can get software mixing working, but only on my 2 front speakers. My surround sound .asoundrc looks like this:

```

pcm.!default {
	type plug
	slave.pcm "surround51"
	slave.channels 6
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 0.5
	ttable.1.4 0.5
	ttable.0.5 0.5
	ttable.1.5 0.5
	}

```

And my .asoundrc for software mixing looks like this:
```

pcm.!default {
	type plug
	slave.pcm "swmixer"
	}

pcm.swmixer {
	type dmix
	ipc_key 1234
	slave {
	pcm "hw:0,0"
	channels 4	
	period_time 0
	period_size 1024
	buffer_size 4096
	rate 44100
	}
}

```

I can't seem to find a way to combine these so I can get software mixing and surround sound. Any suggestions?

---

