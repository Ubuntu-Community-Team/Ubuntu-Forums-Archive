---
title: "Installing RhythmBox plugin via Bazaar?"
date: 2010-10-09
forum: Multimedia Software
---

### Post by ThisIsVictor on 2010-10-09
Hello all,

I'm trying to install [this plugin]("https://code.launchpad.net/~snaggen/rhythmbox/rhythmbox-bpm") for RhythmBox. I installed Bazaar and ran "bzr branch lp:~snaggen/rhythmbox/rhythmbox-bpm" but the plugin didn't show up in RhythmBox. I suspect I'm missing a step but I'm new to Ubuntu. 

Any help would be great, thanks!
--Victor

---

### Post by mc4man on 2010-10-09
A few things
(your link is missing an h - no matter
What you're retrieving from bzr isn't a plugin, it's the rhythmbox source patched to include bpm support and you'd need to compile it.
 actually it's quite an old source  - rhythmbox version 0.9, not to suitable I'd imagine.

The newer bzr rhythmbox source is here - version 0.12.8 (must be built
bzr branch lp:~snaggen/rhythmbox/bpm

Also note that support has apparently been added to current version -  0.13 that's available in maverick.

---

### Post by ThisIsVictor on 2010-10-09
Hmm, ok. Well, I fixed the link, but that's about it.

I attempted to install RhythmBox 0.13.1 from [here]("http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.13/") but it didn't work. I got to the ./configure step and got: 


```
checking for RB_CLIENT... configure: error: Package requirements (glib-2.0 >= 2.18.0 gio-2.0 >= 2.18.0 gio-unix-2.0 >= 2.18.0) were not met:

No package 'glib-2.0' found
No package 'gio-2.0' found
No package 'gio-unix-2.0' found
```

I tried installing gir1.0-glib-2.0 using the package manager, which is the only that came up what I searched for glib, but I got the same error.

I'm running 10.04 Netbook, any advice for getting RhythmBox 0.13 to work would be awesome!

--Victor

---

### Post by mc4man on 2010-10-10
> I'm running 10.04 Netbook, any advice for getting RhythmBox 0.13 to work would be awesome!
The best way would be to get a livecd of maverick, give it a test and if all ok hardware wise, ect. then use that instead of 10.04

Or..

Maybe there's a rhythmbox  ppa for lucid. (myself prefer maverick 

this shows up 
[https://launchpad.net/~webupd8team/+archive/rhythmbox](https://launchpad.net/~webupd8team/+archive/rhythmbox)

---

### Post by ThisIsVictor on 2010-10-10
Ah ha! You, sir, are a genius. I award you one internet for solving this problem.

I just started out using Ubuntu, so I'm probably going to stick to the stable releases for now. Once I have some serious Linux-fu I'll try the more recent releases. 

Again, thank you!
--Victor

---

