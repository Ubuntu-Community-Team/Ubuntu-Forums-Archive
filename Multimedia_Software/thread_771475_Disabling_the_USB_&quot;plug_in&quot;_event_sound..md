---
title: "Disabling the USB &quot;plug in&quot; event sound...."
date: 2008-04-27
forum: Multimedia Software
---

### Post by tvst on 2008-04-27
Every time I plug in my USB soundcard I get the Ubuntu login sound. I would like to disable this, but I can't figure out how to do it. I couldn't find anything about this on gconf, and I already have the "Play system sounds" checkbox unchecked (under system > preferences > sounds > events). 

This is new. It never happened in Gutsy, but started as soon as I upgraded to Hardy. Help?

---

### Post by tvst on 2008-04-28
Nevermind, I figured it out. It's a PulseAudio thing: 

Edit /etc/pulse/default.pa and comment out the line that says 
"load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav"

---

