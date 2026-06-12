---
title: "Video colour randomly inverts on multiple playback applications"
date: 2008-06-10
forum: Multimedia Software
---

### Post by mat28590 on 2008-06-10
This is a weird one.

Videos all play fine for a while, in both totem and vlc. Then for no apparent reason the color inverts or something, because people look blue and stuff. From the time it happens all new videos I open in vlc or totem have this inverted color. If I restart the pc or logout, it all goes back to normal.

Running Hardy Heron
Nvidia 8600 series graphics card

This is most strange and annoying because it keeps happening

Any Thoughts?

---

### Post by ambidextrousone on 2008-12-22
bumping this, its an issue im having, and i assure you its not my graphics card drivers (nvidia 177.80) im on 8.10 btw, im also using a GeForce 8600 GT..

I have tried both totem and vlc so far, both of them have this issue, i would assume, with mine and 'mat28590' having the same card, that it is indeed a problem with this model, although 3d applications, run extremely well and without error. had a good hunt around google for a solution to no avail.

---

### Post by ambidextrousone on 2008-12-22
up you get :popcorn:

---

### Post by pognonec on 2009-03-26
Dell M1330, Ubuntu 8.10.
Same symptom, same solution (restart).
No idea on what to do either...

---

### Post by ACLBandit on 2009-03-30
Weirdest thing I've ever seen. This is new, too-- never happened before up until recently. I *think* you can fix it by an x-server restart (ctrl+alt+backspace), which saves from a full reboot, but still, super-annoying.

Running an nVidia 8800GTS; occurs in VLC, mplayer, AND totem.

Ubuntu 8.10 64-bit

---

### Post by kubug on 2009-03-30
Temporary fix for it is to start the "Nvidia Settings" applications and resetting the color to default values.

I am still trying to figure out how to get a permanent fix.

---

### Post by kubug on 2009-04-03
Another quick solution is to run this command in a terminal:

```
xvattr -a XV_HUE -v 0
```

You will have to have to xvattr package installed. If it isn't, put this in a terminal:

```
sudo apt-get install xvattr
```

Theoretically you could put a little launcher on the desktop or panel with the first command, and have it reset on a click of a button.

---

### Post by Kismet on 2009-10-06
I was just wondering if anyone found a better solution. The xvattr command works, but I have to do it every time I play a video. It's kinda ridiculous.

---

### Post by Kismet on 2009-10-06
Never mind a little googling and I finally found the answer. Apparently with NVIDIA drivers, they assume the Default HUE setting to be 0. Several of the Media players set the HUE to 180 by default.

In Totem (Movie Player) I was able to fix this by going to preferences - > Display, and setting the hue all the way to the left (0). This will save the setting in the player so it will work whenever you watch a movie. 

Hope this helps someone, as I found it extremely annoying.

---

### Post by chrwei on 2009-10-09
interesting.... so I was having no issues until I upgraded to karmic then I get the wrong hues.  i go into totem prefs and the hue is already all the way to the left (don't recall doing that but who knows) so I reset to defaults and it's correct now.

so for those that adjusted this, when you upgrade you'll need to adjust it back.

---

### Post by cutlerite on 2009-10-31
> **chrwei said:**
> interesting.... so I was having no issues until I upgraded to karmic then I get the wrong hues.  i go into totem prefs and the hue is already all the way to the left (don't recall doing that but who knows) so I reset to defaults and it's correct now.

so for those that adjusted this, when you upgrade you'll need to adjust it back.

This is the fix I needed to resolve the video playback turning green or the wrong hue.  Thanks for posting the solution.

---

