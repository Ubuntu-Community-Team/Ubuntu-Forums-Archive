---
title: "Totem makes Lucid crash."
date: 2010-07-11
forum: Multimedia Software
---

### Post by PewterHydra on 2010-07-11
No, seriously. If I start to play any kind of media file in Totem, the screen goes black, a terminal appears and flickers for a few seconds so fast I can't read it, and then the system shuts down. 


This is what shows up in the syslog: 

```
Jul 11 16:09:01 cylien CRON[4839]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/p$
Jul 11 16:09:41 cylien kernel: [23417.172040] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 11 16:09:41 cylien kernel: [23417.172060] render error detected, EIR: 0x00000000
Jul 11 16:09:41 cylien kernel: [23417.172105] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 830459 at 830458)
Jul 11 16:09:41 cylien gnome-session[1385]: WARNING: Detected that screensaver has left the bus
```

I'm not sure what to do from here.... I've tried reinstalling the pulseaudio drivers and Totem from the package manager.

---

### Post by flick on 2010-07-11
No trouble with Totem playing a Windows Media stream from the SomaFM website. I have the ubuntu-restricted-extras package installed for all the patent encumbered codec goodness.

---

### Post by PewterHydra on 2010-07-11
I'm sure this isn't a widespread problem, I can't even find another instance of it on The Internet. Nothing else, none of my audio players, nothing else using php, causes this problem. 

... but I've got no idea how to track down the source of it. I tried running totem -debug, but it never printed any error messages. It would get up to the point where it's loading the .mp3 or .ogg or what-have-ye, and then just die. 

And most of totem's code is in python, I don't think it even uses php, but it spawns something using php (or so it looks like from the syslog) that kills my system.

---

### Post by slashwannabe94 on 2010-07-11
i had this exact same problem with totem....... i decided to un-install it 

sudo apt-get remove totem 

the above command will get rid of totem for you. 

install banshee, vlc or both :D 

i highly recommend the two, they are reliable and very rarely crash, but programs crashing is down to your computer i guess. 

sudo apt-get install vlc 

sudo apt-get install banshee

---

