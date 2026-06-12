---
title: "ALSA types: multi + dmix (combine dmix with same sound in multpile sound cards mixin)"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by darck on 2008-01-18
I have 2 sound cards which doesn't support hardware mixing. I use one for stereo speaker and second for headphones. I have configured ALSA to play the same sound on both sound cards with following code:

```

pcm.!default {
	type plug	
	slave.pcm "multi"
	ttable.0.0 1.0
	ttable.1.1 1.0
	ttable.0.2 1.0
	ttable.1.3 1.0
}

pcm.multi {
	type multi
	slaves.a.pcm "hw:0,0"
	slaves.a.channels 2
	slaves.b.pcm "hw:1,0"
	slaves.b.channels 2
	bindings.0.slave a
	bindings.0.channel 0
	bindings.1.slave a
	bindings.1.channel 1
	bindings.2.slave b
	bindings.2.channel 0
	bindings.3.slave b
	bindings.3.channel 1
}

ctl.!default {
	type hw
	card 1
}

```

I want also turn on software mixing in ALSA, to allow playing sound in more than one programme at once. This code allow that, but only for one sound card:

```

pcm.!default {
	type plug
	slave.pcm "dmixer"
}


pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:1,0"
		period_time 0
		period_size 1024
		buffer_size 4096
		periods 128
		rate 44100
	}
	
	bindings {
		0 0
		1 1
	}
}

```

Question is how to mix those 2 codes into one working. I tried using pcm "multi" instead of pcm "hw:1,0" and few other things, but i didnt work. Problem is that i' was getting just information that something is wrong, without any specific debug information. Some experienced person in ALSA coding would be very helpful. (or info, where i can find one)

Only similar thing i found on google is [http://209.85.129.104/search?q=cache:UVFu-JWiZvkJ:www.mail-archive.com/alsa-user%40lists.sourceforge.net/msg13654.html+%22type+dmix%22+%22type+multi%22&hl=en&ct=clnk&cd=14&client=opera](http://209.85.129.104/search?q=cache:UVFu-JWiZvkJ:www.mail-archive.com/alsa-user%40lists.sourceforge.net/msg13654.html+%22type+dmix%22+%22type+multi%22&hl=en&ct=clnk&cd=14&client=opera)  but it doesn't work the way he did.

[http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=DmixPlugin](http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=DmixPlugin) 
Uder above url is written:
"NOTE: For ALSA 1.0.9rc2 and higher you don't need to setup dmix. Dmix is enabled as default for soundcards which don't support hw mixing."
Why it's not true when i use the config for same sound on 2 sound cards. I have ALSA Version 1.0.14, which is more than 1.0.9rc2.

---

### Post by darck on 2008-01-20
bump

---

