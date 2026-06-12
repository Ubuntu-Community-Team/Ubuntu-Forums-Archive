---
title: "No sound"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by MoshNet on 2005-10-18
I have no sound,and when I try playing an mp3 file it ask me to download a decoder using totem. Where do I get this decoder? I am using a sound blaster audigy 2 card.

---

### Post by kombipom on 2005-10-18
Use synaptic to get the gstreamer0.8-misc package, this will install all the common decoders for totem-gstreamer.  If you have no sound anywhere else (outside totem) this won't fix that though.

Kombipom

---

### Post by MoshNet on 2005-10-18
When I try to open synaptic manager, it does not open. So confused...

Edit.. I had to /sudo synaptic/ to get it open via terminal.

Edit: It already says gstreamer is installed, and I can get totem to play, and cd player, but only cds..

---

### Post by kombipom on 2005-10-19
Just gstreamer or gstreamer and all the extra gstreamer0.8-"whatever" packages?  For ideological reasons a standard ubuntu install doesn't include the codecs for non-free compression routines like mp3 and dvd so you have to add them, they should all be in the repositories.  Sorry if I'm "teaching a grandma to suck eggs" here .  Do you have the universe and multiverse repositories in Synaptic?

---

