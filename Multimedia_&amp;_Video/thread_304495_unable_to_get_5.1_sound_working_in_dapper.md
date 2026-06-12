---
title: "unable to get 5.1 sound working in dapper"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by drakebiosci on 2006-11-21
newbie alert!

Trying to get 5.1 sound to work in dapper. Really all I want is to route 2.1 sound through logitech z-5450 speakers to play mp3s with xmms. Have Audigy SB0570 sound card. Visited sites like

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)

[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

and

[http://alsa.opensrc.org/FAQ028](http://alsa.opensrc.org/FAQ028)

Tried numerous variations on these instructions. Most promising (in the sense that I actually get sound out) is to add to .asoundrc

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

Then, run the following test:

aplay -Dplug:ch51dup ~/cow.wav

and get sound out of left and right front speaker but nothing else.

any ideas?

---

### Post by Rajiv_Nair on 2006-11-21
i dunno wether this will wrk for u.try installing ALSA mixere GUI...and set output.u'll find ALSA in synaptic

---

### Post by drakebiosci on 2006-11-22
have alsamixer gui but playing with the settings can only turn 2.1 on/off but can't get 5.1 working. other ideas...

---

### Post by pauldinu on 2008-05-06
i have tried allot of configurations for .asoundrc also but finaly the one that worked was ```
pcm.!dmix {
type plug
slave {
pcm surround51
channels 6
}
}
pcm.!default {
type plug
slave.pcm "dmix"
slave.channels 6
route_policy duplicate
}
```
For those who don't know how to modify .asoundrc:
-open a terminal and type $ gedit .asoundrc
-in .asoundrc copy paste the code above, save and exit
-make sure you have your Analog Center, Analog Front, Analog Reat in ALSA unmutted
-try and type $ speaker-test -Dplug:surround51 -c6 -l1 -twav
-when you do the test you must close all sound emitting sources... like movies, audio or streaming videos.

i got my information from [http://ubuntuforums.org/archive/index.php/t-586411.html](http://ubuntuforums.org/archive/index.php/t-586411.html)
Cheers.
btw i have a creative sb live 24bit, ca0106

---

