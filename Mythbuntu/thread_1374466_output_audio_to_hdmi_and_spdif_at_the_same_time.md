---
title: "output audio to hdmi and spdif at the same time"
date: 2010-01-06
forum: Mythbuntu
---

### Post by iitywygms on 2010-01-06
Just got a new frontend for myself.
zotac mag hd-nd01 :)

Anyway.  Can someone point me in the right direction to enable digital audio out of mythtv to hdmi and spdif at the same time?
Been looking for a good how to but having no luck.
Ubuntu .22 with fixes.  Karmic.
Thanks

---

### Post by Dewey_Oxberger on 2010-01-07
To get audio over hdmi working look at this:

[http://ubuntuforums.org/showpost.php?p=8184659]("http://ubuntuforums.org/showpost.php?p=8184659")

Follow the instructions in the file on that post.

From their you'll need to mod the asound.conf to split the audio.  I think I've seen examples in the alsa docs somewhere.  There is an alsa plug that knows how to do it but I can't recall it's name.

---

### Post by iitywygms on 2010-01-07
Thankk you for the link and suggestions.
I can get audio over hdmi.  I can get audio over spdif.  I cant get both at the same time.  THAT is what I would like to have.

---

### Post by iitywygms on 2010-01-09
Okay, I am getting places.

Here is my current .asoundrc

pcm.!default {
type plug
slave {
pcm "both"
}
}

pcm.both {
type route
slave {
pcm multi
channels 4
}
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}

pcm.multi {
type multi
slaves.a {
pcm "tv"
channels 2
}
slaves.b {
pcm "receiver"
channels 2
}
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

pcm.tv {
type hw
card 0
device 3
channels 2
}

pcm.receiver {
type hw
card 0
device 1
channels 2
}

I have mythtv setup to use alsadefault and stereo. Doing this results in stereo sound output to both hdmi and spdif at the same time.
If I set up mythtv to output 5.1, I get distortion to the tv (hdmi) but the spdif (stereo) is correct.
I think the hdmi is distorting because it is trying to play digital sound but cant decode it.
I would like to have 5.1 digital sound go to the spdif, and stereo analoug go to hdmi.
Anyone know of a way to make alsa or mythtv do this.
Oh so close!

---

### Post by iitywygms on 2010-01-10
bumpity

---

