---
title: "mplayer firefox plugin  Gusty - not working"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by ashishgoel on 2007-10-19
today i upgraded from feisty to Gusty and most of things are workin fine or rather bit improved...

but having problems with mplayer-firefox-plugin... earlier i was able to watch embedded video thru it (in feisty) and now as soon as it launches -> status shows buffering -> and immediately status becomes 'stopped'...

please help...

Thanx

---

### Post by ashishgoel on 2007-10-20
i even tried uninstalling and reinstaling mplayer-plugin from automatix... no change

---

### Post by mjuhasz on 2007-10-20
I had the same problem and gave xine-plugin a try and found it quite promising although there was no control bar (play/stop button) but keyboard shortcuts worked.
Then I reinstalled mplayer plugin and set the video to x11 and the audio to alsa and mplayer plugin works properly now. I uninstalled xine-plugin as well.

---

### Post by GandalfNK on 2007-10-28
Hey, great! That helped me solve the same problem.
Thanks, mjuhasz!

---

### Post by wanesqatar on 2007-11-24
> **mjuhasz said:**
> I had the same problem and gave xine-plugin a try and found it quite promising although there was no control bar (play/stop button) but keyboard shortcuts worked.
Then I reinstalled mplayer plugin and set the video to x11 and the audio to alsa and mplayer plugin works properly now. I uninstalled xine-plugin as well.

Hi there,

I'm a new ubuntu user.. I'm having this same problem.. Apparently your solution works for the other guy.. but how do you set the video to x11 and audio to alsa? Could have please have detailed instructions?

---

### Post by pekka72 on 2007-11-25
... was also puzzled and then found a hint here : [http://forums.debian.net/viewtopic.php?t=21315](http://forums.debian.net/viewtopic.php?t=21315).

I did not do all the changes. I just edited /etc/mplayerplug-in.conf (where all lines were commented out) to have 

[INDENT]vo=x11[/INDENT]

Now I can watch tv again :)

---

### Post by ashishgoel on 2007-11-25
when the plugin load - just right click in the new plugin window and select properties, and do the changes there....

still that didn't worked for me on few websites but most work after then.....

i also tried Xine-plugin - works fine - but no controls....

---

