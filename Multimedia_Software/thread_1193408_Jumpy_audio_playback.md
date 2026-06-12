---
title: "Jumpy audio playback"
date: 2009-06-21
forum: Multimedia Software
---

### Post by thewolfman on 2009-06-21
Hi chaps,

okay, the problem is that I have sound but when I play music it is very choppy/jumpy; now I have read the how-to's and have installed all the necessary bits and pieces that are required but I'm still getting bad sound reproduction on playback, I have tried switching between ALSA and PULSE but that doesn't help either.

I have tried various audio players including Songbird and Rhythmbox but none of them work well at all.

So if any of you have a plan; please share it with me.

Ubuntu Jaunty on a crappy generic PC but the sound works well under (dare I say) Windows and like I said before; I do have sound so the soundcard has been detected.

Listening to the band Reamonn at the mo (well trying anyway!)

Thanks for any help in advance.

thewolfman

---

### Post by thewolfman on 2009-06-21
Sorry a PS: I am using Ultimate Edition 2.2 (Jaunty 9.04) I thought I would give it a whirl.

---

### Post by RichLouth on 2009-06-23
This might help:

[http://ubuntuforums.org/showthread.php?p=7505646#post7505646]("http://ubuntuforums.org/showthread.php?p=7505646#post7505646")

---

### Post by thewolfman on 2009-06-25
Thanks for your reply, I tried to mess with the settings like you said but its still jumpy, do I need to edit anything else out of the .asoundrc file?.

Here's what I have so far:

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/stephen/.asoundrc.asoundconf>
pcm.dsp {
	type plug
	slave.pcm "dmixer"
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

ctl.!default {
	type hw           
	card 0
}

pcm.dmixer {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:0,0"
		period_time 2
		rate 34000
		period_size 8208
		buffer_size 16416
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


Now I didn't edit the text that was already in the file so do I need to edit anything there?.

Thanks for your help.

thewolfman

---

