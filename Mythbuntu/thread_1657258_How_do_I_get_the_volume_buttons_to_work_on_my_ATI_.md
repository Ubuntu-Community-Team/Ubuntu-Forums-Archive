---
title: "How do I get the volume buttons to work on my ATI Remote Wonder?"
date: 2011-01-01
forum: Mythbuntu
---

### Post by bludshot on 2011-01-01
I got my remote wonder working with mythbuntu. I can use the mouse directional pad to move the mouse around, and the right and left mouse click buttons on the remote.

But the volume + and - buttons don't seem to do anything (in VLC).

I've read some stuff like this: [http://www.mythtv.org/wiki/ATI_Remote_Wonder#Mythbuntu_10.10_without_lirc](http://www.mythtv.org/wiki/ATI_Remote_Wonder#Mythbuntu_10.10_without_lirc)

and this: [http://www.uluga.ubuntuforums.org/showthread.php?t=95146](http://www.uluga.ubuntuforums.org/showthread.php?t=95146)

but it is utterly confusing and I don't even know what of it applies to me (and I don't want to try to decipher doing certain things when I don't even know if I should be doing them or if they would just mess things up more...)

---

### Post by bludshot on 2011-01-01
Ah. Apparently my volume buttons DO work in mythtv. But they don't work out in ubuntu for just general volume of other things.

I wonder if there is a way to do that, like maybe assign a couple other buttons to control the system volume or something...

---

### Post by bludshot on 2011-01-02
I was also trying to get my media keys working on my keyboard, and I did this: [http://ubuntuforums.org/showthread.php?t=1657985](http://ubuntuforums.org/showthread.php?t=1657985)

Apparently, the volume keys on my keyboard generate the same input code as the volume buttons on my remote (I think my remote is being seen as a keyboard or something since I use ati_remote module, not lirc (something I must do, because that's the only way to get my remote to function)).

So now simply because of what I did to get my keyboard keys working, the volume buttons on my remote do something different now, they control the master volume (actually the headphone volume) instead of doing whatever they did before.

Now what they did before was control the volume just IN mythtv, not the master system volume.

So it was a bit unexpected that fixing my keyboard would change my remote's behaviour, but it's better this way since now I can control the volume of everything, not just mythtv.

---

