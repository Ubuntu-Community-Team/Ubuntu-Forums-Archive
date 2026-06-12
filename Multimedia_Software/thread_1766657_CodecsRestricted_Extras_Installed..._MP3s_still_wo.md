---
title: "Codecs/Restricted Extras Installed... MP3s still won't play"
date: 2011-05-24
forum: Multimedia Software
---

### Post by tlalteuctli on 2011-05-24
I'm on 11.04

I've installed the Ubuntu Restricted Extras, and MP3s still just skip through instead of playing. I've tried Banshee and smplayer.

Where do I go from here?

---

### Post by anthony2010 on 2011-05-24
Be sure 'Lame' is installed from synaptic, then ensure 'gstreamer' (all of them) are also installed.

Synaptic is usulaaly found under 'administration'.

I have another trick up my sleeve but for the purpose of remaining legal, lets see how this goes for you first.

Ant.

---

### Post by tlalteuctli on 2011-05-24
Thanks for the quick reply! After 2 days of trying to figure this out... I did it.

In the "Output" tab under sound options, I had "HDMI" instead of the "Internal" option selected.

Strangely, I had selected "Internal" from the "Hardware" tab and all my other sound worked fine--I could stream music and movies online with sound, just not play MP3s.

Weird.

---

### Post by anthony2010 on 2011-05-26
Ah nice one!

Glad you are sorted. I choose not to route my sound to the tv because I prefer the sound quality via my old but trusted amp.


Ant

---

