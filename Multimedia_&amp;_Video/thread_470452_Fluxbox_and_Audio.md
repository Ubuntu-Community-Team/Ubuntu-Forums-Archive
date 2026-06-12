---
title: "Fluxbox and Audio"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by saggio on 2007-06-11
Hi there, 

I've recently installed Fluxbox and I am in the middle of configuring it to my liking. So far, things have gone off without too much trouble - however, I have noticed that I am unable to globally control volume for all applications (via my keyboard, which has a volume knob) as I was able to do under GNOME. Is there some specific application that can enable this, and, if so, is it compatible with fluxbox? How does one configure it to launch automatically at the beginning of a session?

Thanks in advance.

---

### Post by aquavitae on 2007-06-11
Its just key bindings set in ~/.fluxbox/keys.  You can find the keycodes using xbindkeys - mk (you have to have xbindkeys installed) and then map them to your mixer (e.g. amixer) command line arguments.  Alternately you can just use xbindkeys, howto at [http://www.howtoforge.com/linux_multimedia_keyboard]("http://www.howtoforge.com/linux_multimedia_keyboard").  Btw, in case its any help, there's a good fluxbox howto on the gentoo website (only slight adaption needed for ubuntu) at [http://www.gentoo.org/doc/en/fluxbox-config.xml]("http://www.gentoo.org/doc/en/fluxbox-config.xml").

---

### Post by saggio on 2007-06-11
> **aquavitae said:**
> Its just key bindings set in ~/.fluxbox/keys.  You can find the keycodes using xbindkeys - mk (you have to have xbindkeys installed) and then map them to your mixer (e.g. amixer) command line arguments.  Alternately you can just use xbindkeys, howto at [http://www.howtoforge.com/linux_multimedia_keyboard]("http://www.howtoforge.com/linux_multimedia_keyboard").  Btw, in case its any help, there's a good fluxbox howto on the gentoo website (only slight adaption needed for ubuntu) at [http://www.gentoo.org/doc/en/fluxbox-config.xml]("http://www.gentoo.org/doc/en/fluxbox-config.xml").

That's awesome, thanks!

Now...how would I configure it so that when I press a certain key, the volume in the alsa-mixer will be increased? I'm not sure how I would go about notating that in the config file for xbindkeys.

---

### Post by aquavitae on 2007-06-11
Hmmm, I'm not entirely sure - its so long since I've done it I can't remember!  Have you had a look at the xbindkeys man page?  And possibly 'man xbindkeysrc' too.  You might also have to have a look at the mixer man page to find out what arguments to pass to it.  Use xbindkeys -mk to find out the keycodes, and you might be able to make a bit more sense of the example in that link I gave you.  I'm at a windows computer at the moment, so I'm afraid I can't test anything and give you a straight answer.

---

### Post by saggio on 2007-06-11
Well, I haven't been able to figure out how to get xbindkeys working directly with alsa-mixer, but I have gotten most of my audio controls working with audacious. The link you posted was most helpful.

---

### Post by aquavitae on 2007-06-12
You don't necessarily need to use alsamixer - it'll take a bit of hunting, but there's proably a mixer that can be set up for keyboard shortcuts.  I use kmix, but that's kde and if you're using fluxbox you presumably want something more lightweight.  There might be something for the blackbox WM that you could use - fluxbox is based on blackbox, so the tools integrate nicely.

---

### Post by andrew_howlett on 2007-06-12
Hi, here is what I use in my .fluxbox/keys file:

```
None 176 :exec amixer -q set Master 10%+
None 174 :exec amixer -q set Master 10%-
None 160 :exec amixer -q set Master toggle 
```

amixer is part of alsa-utils

I found the key numbers (160, 174, etc) using the xev app.

The "None" modifier is for Alt, Ctrl, etc. See the fluxbox man page.

later,
Andrew.

---

