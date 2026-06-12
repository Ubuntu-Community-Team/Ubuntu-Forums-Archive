---
title: "To Many Codecs........................."
date: 2010-01-25
forum: Multimedia Software
---

### Post by squid69 on 2010-01-25
Is there such a thing as to many codecs ??

I can't seem to play avi,mpg,wmv or flv files i have sound but no pic ?

Is there something that can tell me if I've got compatibility issues ?

It has all worked fine on previous installs ?

Ubuntu 9.10 64 bit

---

### Post by LuisGMarine on 2010-01-25
I spent countless hours trying to find every codec that I thought I would use, and yet I would come across certain file types that I had no code for.  The easy way is to just go ahead and install the ubuntu-restricted-extras.  Honestly this takes care of everything, you can open up a terminal window and type this in.

```
sudo aptitude install ubuntu-restricted-extras
```

I'm also using 64-bit 9.10.  It takes care of everything including flash, java, mp3 etc.  Hope this helps.

---

### Post by squid69 on 2010-01-25
I've  got that but i'll give it another go

It removed more than it installed and still nothing ?

But i forgot to say it works on GXine but the people are very blue ??

---

### Post by LuisGMarine on 2010-01-25
That's fine.  What it removed where probably dependencies that your system doesn't use.  That's what I like about aptitude is it does a good job of removing packages completely instead of leaving all the dependencies around.

As far as the blue people, have you tried other media players like VLC?  Also what type of video card do you have, and what ever the case might be, do you have the proper drivers installed for it?

---

### Post by l_square on 2010-01-25
**x3Codec**.. Can't play mp3s without it (using karmic koala.)I have already installed all the restricted but still missing this one.
Google didn't help. Can you guys help me?

---

### Post by Yellow Pasque on 2010-01-25
@OP Try medibuntu repo, install w32codecs package and use mplayer.

@l_square: What is x3codec and why do you need it for mp3's? You should just need gstreamer-ffmpeg or libxine1-plugins depending on what player you're using.

---

### Post by squid69 on 2010-01-25
> **LuisGMarine said:**
> That's fine.  What it removed where probably dependencies that your system doesn't use.  That's what I like about aptitude is it does a good job of removing packages completely instead of leaving all the dependencies around.

As far as the blue people, have you tried other media players like VLC?  Also what type of video card do you have, and what ever the case might be, do you have the proper drivers installed for it?

That is the only Media Player i can get any picture on !!

I have a Nvidia 8800GTS 312 mb i have 185 driver installed and all the extra visual effects work as per before.

I'm deleting all the media players and codecs that i can,reboot and take it from there ???

---

### Post by squid69 on 2010-01-25
Well it works with x11 codec in SMPlayer so i'll see how it goes for know,

---

