---
title: "WTF? Volume Control applet &quot;didn't find devices to control&quot; - Sound still works"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Agent ME on 2008-02-04
I started up my laptop and the volume control applet thing in the system tray had a mute symbol on it. When I clicked it I get this:
[IMG]http://img127.imageshack.us/img127/8356/volumeerrorvf4.png[/IMG]

I've searched online about this message - the pages I've found the people either have more problems than me (no sound at all, soundcard not detected), or somehow they were removed from the 'audio' group. I've checked, I'm still set up as part of the group.

Sound still works. And if I double-click the muted sound icon, the volume control window comes up - and it still works perfectly - I can adjust volume there fine. Wtf?

If I go to System -> Preferences -> Sound, on the devices page now all of the drop-down boxes are empty. Pressing test on anything on that page gives an error message.
If I go to System -> Preferences -> Multimedia Systems Selector, everything still works there, including the sound page.


I have the latest version of ALSA - I even re-ran the scripts to re-install it, rebooted, and I still have this problem. I'm on Gutsy 7.10.

If it matters - yesterday I tried to install gstreamer 10.17 from the source. I managed to compile and install the core code fine, but I was getting some compiler error with gstreamer-plugins, and I decided it wasn't worth the effort, so I went into the synaptic package manager, searched (name) 'gstreamer' and set every single package that I had with it to reinstall just to go back to the last version and fix anything I might've screwed up.
Volume control still worked then, and I'm pretty sure I rebooted some time that day and it still worked, but I might be wrong.

I heard on one page that running "gst-register" would fix this and re-set-up the plugins, but I can't find any "gst-register" program on my system. Typing it in terminal says command not found, and I can't find it anywhere with Places -> Search for Files...

Help is appreciated! Thanks!

---

### Post by Agent ME on 2008-02-05
Bump.

Anyone have ideas?

---

### Post by Agent ME on 2008-02-06
I fixed it by upgrading fully to gstreamer 10.17.

The problem was I tried to use the gst-plugins module, which has be deprecated and replaced by several others (why is it still on the downloads page?!), which didn't work, causing me to try to go back to the version in the ubuntu repo, but apparently it doesn't downgrade correctly.

---

