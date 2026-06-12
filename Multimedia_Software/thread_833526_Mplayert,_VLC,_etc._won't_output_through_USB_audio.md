---
title: "Mplayert, VLC, etc. won't output through USB audio"
date: 2008-06-18
forum: Multimedia Software
---

### Post by djbon2112 on 2008-06-18
I've got a Turtle Beach USB sound card that Amarok and the system output sound through fine, but for whatever reason I can't configure either of these media players to use this USB output. Does anyone have any tips?

---

### Post by djbon2112 on 2008-06-19
As an update, Firefox 3 doesn't work either. They all try to route through the onboard sound. I'm going to try some other things and post back my results.

---

### Post by djbon2112 on 2008-06-19
Tried editing modprobe.d/alsa-base but it didn't change anything.

---

### Post by djbon2112 on 2008-06-19
HELP Alright I restarted and now I can't even get the USB audio anymore! At first it said "USB Audio (Disconnected)" but now it doesn't even show anything! The card shows up with *lsusb* but not *cat /proc/asound/cards*

EDIT: Alright I fixed it, it was because I tried to give that card spot 0 in alsa-base, but there's still gotta be a way to make this card the default for linux, instead of my onboard. Any suggestions? Please?

---

### Post by markbuntu on 2008-06-19
You should be able to select it in System/Prefences/Sound or Mutimedia Systems Selector. If you are using alsa and not pulseaudio you can get:

asoundconf-gtk  (choose default alsa sound card)

and use that to select your sound card. 

I had all sorts of problems with my two sound cards and pulseaudio so I disabled pulseaudio and got all the alsa plugins and wrappers and utilities, etc and now have a pure alsa setup that works great for everything, all the time, through numerous kernel updates etc. rock solid.

---

