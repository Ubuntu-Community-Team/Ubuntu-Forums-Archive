---
title: "cmus -- no volume control anymore"
date: 2008-11-09
forum: Multimedia Software
---

### Post by notebooktessler on 2008-11-09
Hello, 

In Ubuntu 8.10 I can't control the volume in cmus anymore. Pressing +/- has no effect, nor does ":vol +10%" and the like. The current volume is not shown at all in the status bar. There is sound, but it's volume can't be controlled from within cmus. 

Any idea what could be the reason? Everything worked perfectly in Hardy and cmus is still the same version. 

Thanks, 
Ludwig.

---

### Post by super breadfish on 2009-04-14
I am also having the same problem. I've Google'd around but found nothing.

Volume control does not work, and neither does pause. When I pause a track with c or :player-pause I can't unpause it again.

Any ideas?

---

### Post by euchrid on 2010-04-22
I managed to recover my volume control by removing Pulseaudio, following Nullrend's instructions here:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1313253](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1313253)

Returning the system to ALSA also removed a nasty, crackling effect that Pulseaudio's implementation seemed to cause.

Seems to have been a problem for a while:
[https://bugs.launchpad.net/ubuntu/+source/cmus/+bug/296229](https://bugs.launchpad.net/ubuntu/+source/cmus/+bug/296229)

I couldn't find a better solution than removing Pulseaudio. Hope it works for you.

---

### Post by bleakwizard on 2013-03-25
in case someone still strugling with this:

if your volume options are missing you may need to configure them in the config "tab"
1. press 7 (config "tab")
2. browse down to"softvol", set value to true
3. one line down set "softvol_state" to "100 100"  (don't use a comma, just space)

good luck

"the bleak wizard"  ;)

---

### Post by wildmanne39 on 2013-03-25
Thanks for sharing,please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

