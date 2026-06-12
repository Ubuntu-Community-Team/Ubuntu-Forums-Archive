---
title: "after upgrade from gutsy to hardy nightmare begins"
date: 2008-05-13
forum: Multimedia Software
---

### Post by kelvin911 on 2008-05-13
first thing is the fonts.  they look all fat and ugly.  i try changing them in appearance, but this only fix some app.  app like opera, terminal, k3b, skype, all looks ugly and fat.  then i install kcontrol and change the font there and it seems to fix the fat font problem.  but the font in skype is still small and unreadable until i install qt4-qtconfig to fix that problem.  why hardy dont have gt4-qtconfig preinstalled?

second thing is it takes another extra 30 sec to 1 min to start hardy then gutsy.  and hardy has been freeze on me more than twice.  and then the sound randomly crashes and i need to restart computer to get the sound back

third thing is recently i notice that i cant play sound in more than one app.  if i play mp3 in vlc, then i can not play sound in mplayer.  when i am watching youtube then i cant play my music or no sound in skype.  i spent 2 two days to figure this out it is the pulseaudio problem.  "kill pulseaudio" fix the problem.  but i sudo apt-get remove pulseaudio anyway it is piece of crap.  but then it takes longer to load ubuntu (dont know why?)  and the startup sound is gone.  but i can live with that as long as i can play mp3 and play games at the same time.

and one more thing doom3 no longer working in hardy.  i got black screen


In conclusion, hardy is worse than Win ME.  piece of crap should have stick with gutsy

---

### Post by enbuyukfener on 2008-05-13
1) Bad luck, this must have been a problem with the migration/upgrade, not hardy. But then, I assume you have KDE which I don't know too much about.

2) On a clean install, Hardy's boot time is marginally slower than Gutsy's, definitely not near 30 seconds difference, not that this should matter, how often do you boot anyway? (if you are suspending/hibernating)

3) That was a bit on and off for me, and happened in gutsy too. It hasn't happened in over a week for me. Setting audio to pulse-audio or something like that seems to have helped.

Re "doom3" not working, we need more details. Any output, logs, graphics card diagnostics?

And that last statement was better not said.

---

### Post by kelvin911 on 2008-05-13
> **enbuyukfener said:**
> 1) Bad luck, this must have been a problem with the migration/upgrade, not hardy. But then, I assume you have KDE which I don't know too much about.

2) On a clean install, Hardy's boot time is marginally slower than Gutsy's, definitely not near 30 seconds difference, not that this should matter, how often do you boot anyway? (if you are suspending/hibernating)

3) That was a bit on and off for me, and happened in gutsy too. It hasn't happened in over a week for me. Setting audio to pulse-audio or something like that seems to have helped.

Re "doom3" not working, we need more details. Any output, logs, graphics card diagnostics?

And that last statement was better not said.

I am not using KDE, that's the point.  The appearance in gnome can not change the the font in QT app.

setting audio to pulseaudio doesnt help.  It creates more problem, but killing pulseaudio solve the problem.

when running doom3, i got black screen, the moniter gives me out of range error

---

