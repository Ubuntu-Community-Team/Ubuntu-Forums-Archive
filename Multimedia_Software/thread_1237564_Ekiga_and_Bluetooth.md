---
title: "Ekiga and Bluetooth"
date: 2009-08-11
forum: Multimedia Software
---

### Post by Arla on 2009-08-11
Not sure if this is the right place, but figure I'll give it one more go.

I'm trying to use Ekiga as a replacement for Skype on Ubuntu (Skype really doesn't seem to like my system, plus I have issues with Skype). So anyway, in that regard, I'm playing with Ekiga, I've got my bluetooth headset and got it working with arecord and aplay just fine, but I'm stumped how to get Ekiga to allow me to use it (being something of a newbie to Ubuntu probably isn't helping).

My .asoundrc is setup as follows

```
pcm.!default {
	type hw
	card 0
}

ctl.!default {
	type hw           
	card 0
}

pcm.btheadset {
        type bluetooth
        device 00:19:7F:99:BC:C5
        profile "auto"
}
```

The btheadset part seems to work (curiously aplay and arecord seem to work fine if I use device=bluetooth or device=btheadset, not quite sure why).

I THINK I need to set the default input to be the pcm.btheadset, but I'm stumped as to how to do that?

---

