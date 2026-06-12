---
title: "no system sound"
date: 2008-11-22
forum: Multimedia Software
---

### Post by chunchengch on 2008-11-22
I am using Ubuntu 8.10, the sound works normally except the system sound, I set different sounds for every particular events in System/Preferences/Sound, but only the Login sound works when I boot the computer, the other sound effects don't work.

I follow the instruction in this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) , but no success.

Here is the screenshot of setting, hope there is solution for this problem, thanks for any reply.

[ATTACH]93688[/ATTACH]

---

### Post by forkandles on 2008-11-23
I hope you find the Sound Setting section useful in here:

[http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro](http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro)

---

### Post by chunchengch on 2008-11-23
> **forkandles said:**
> I hope you find the Sound Setting section useful in here:

[http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro](http://ubuntuforums.org/showthread.php?t=990057&highlight=experiences+8.10+skype+vision+pro)


Thanks for reply.

I create a ~/.asoundrc and post the following lines in it, but no success, 

[COLOR="SeaGreen"]pcm.!default {
type hw
card 0
}

ctl.!default {
type hw           
card 0
}[/COLOR]

then, I post the following lines to replace, but still no success,

[COLOR="SeaGreen"]pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}[/COLOR]

I still can not enable system sounds, such as alert sound and sound effects, is there any other solution? thanks a lot.

---

### Post by chunchengch on 2008-11-27
Doesn't anyone have this problem?

I am still looking for the solution, hoping someone can give me a hand, thanks a lot!

---

### Post by Favux on 2008-12-16
Hi chunchengch,

I had the same problem.  Go to Synaptic Package manager and search for "ubuntu-sounds".  This is the Ubuntu sound theme.  It will show up with the box in front "greened" indicating it is installed.  It is lying to you.  Right click on it and pick "Mark for Reinstallation".  Then pick "Apply" in the toolbar.  When it's done you'll be able to click on the little arrows in "Alerts and sound effects" and hear the sounds.

I hope this helps.

---

