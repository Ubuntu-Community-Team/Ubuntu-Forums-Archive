---
title: "TV sound is fine but no sound in internet video"
date: 2012-10-26
forum: Mythbuntu
---

### Post by dheianevans on 2012-10-26
Upgraded to .26 and Mythbuntu 12.04 over the weekend. Though sound from recording and videos is coming through fine, I used Myth's Search Internet video yesterday and was suddenly not getting sound from the youtube videos.

What do I need to check to make sure sound from "Search Internet Videos" is working.

My myth sound setup is:

ALSA:hdmi:CARD=NVidia_1,DEV=3 ;

Thanks.

---

### Post by nickrout on 2012-10-26
You need to assign a default sound device in /etc/asound.conf

---

### Post by dheianevans on 2012-10-26
this is what it says right now:

pcm.!default {
type plug
slave.pcm {
type hw
card 1
device 3
}
}

are there any utils to help with this? do i need to change card to nvidia_1?

---

### Post by dheianevans on 2012-10-26
Okay...I tried various command lines and I get sound from the TV speakers if I enter:

speaker-test -Dhw:1,9 -c2

Changed my asound.conf to:

pcm.!default {
type hw
card 1
device 9
}

Still no sound in Firefox and Myth's net video. (Again, myth sound elsewhere is fine.)

I remember JYA in the myth list wondering why people hand wrote asound.conf setting, but I don't appear to have any sound setting stuff in my xfce menus.

---

### Post by nickrout on 2012-10-26
> **dheianevans said:**
> this is what it says right now:

pcm.!default {
type plug
slave.pcm {
type hw
card 1
device 3
}
}

are there any utils to help with this? do i need to change card to nvidia_1?There is a utility to change the default sound device in standard ubuntu (or there used to be pre unity anyway) but I don't think the utility is in the xfce menus you get with mythbuntu.

asound config files are a b***y mystery to me unless someone tells me exactly what to write, so I am not much more help, except to point here [http://alsa-project.org/main/index.php/Asoundrc](http://alsa-project.org/main/index.php/Asoundrc)

---

### Post by dheianevans on 2012-10-26
The config is a mystery to me too. 

What's annoying is that it worked fine in 11.04. Obviously MYth working is the main thing, but if ya can't occasionally use Media->Search Internet Videos or browse shows in mythnetvision, that;s annoying too.

---

### Post by johnvic on 2012-10-27
I had problems that are similar to what you are having. My thread may help.

[http://ubuntuforums.org/showthread.php?t=2052545]("http://ubuntuforums.org/showthread.php?t=2052545")

gl

---

### Post by dheianevans on 2012-10-27
thanks. we've been working on the asound.conf file but so far no luck.

---

### Post by Kantalias on 2012-10-27
> **dheianevans said:**
> What's annoying is that it worked fine in 11.04.

I had the same experience going from 11.04 to 12.04 using HDMI audio from an NVIDIA card.  See the links in my second post here: [http://ubuntuforums.org/showthread.php?t=1967755]("http://ubuntuforums.org/showthread.php?t=1967755").  You may need to follow the entire guide, but you you could just trying to jump to the section that fixed it for me (noted in my post).

---

### Post by dheianevans on 2012-10-27
hmm, one of the steps is:

[COLOR=#ffffff][FONT=Courier New]grep "eld_valid *1" /proc/asound/NVidia/eld*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]

That directory doesn't have any eld* stuff in it.

NVidia_1 does though, but that grep doesn't find anything...so I'm not sure what the next step would be.

---

### Post by dheianevans on 2012-10-31
Situation solved. Please see: [http://ubuntuforums.org/showpost.php?p=12328152&postcount=40](http://ubuntuforums.org/showpost.php?p=12328152&postcount=40)

p.s. how do you mark a thread as [solved]?

---

