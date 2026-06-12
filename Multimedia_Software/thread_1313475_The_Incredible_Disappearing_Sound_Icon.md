---
title: "The Incredible Disappearing Sound Icon"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Maximus559 on 2009-11-03
Today when I started up Ubuntu 9.10, I noticed that there were two audio icons in the panel at the top of the desktop. One of these functioned like the audio icon should (left click = volume slider, right click = more options), but the other did not (left click = no effect, right click = more options, but not related to sound). I did what any sane individual would do and clicked "remove from panel" in the menu for the non-functional icon. To my surprise, both icons disappeared. Now, when I enter the "add to panel" dialogue box, the audio icon is not listed among the choices. More recently, I noticed that my network indicator icon is also missing, and is also not in the "add to panel" list. Any ideas?

---

### Post by lidex on 2009-11-03
Have a look [here]("http://ubuntuforums.org/showthread.php?t=1312090") and let me know if it helps.

---

### Post by Maximus559 on 2009-11-04
Thanks for the reply, but I don't think the post you linked to is describing the same problem. I'm not getting any error messages or anything - the volume and network icons just aren't showing up. Also, rebooting doesn't seem to have any effect.

---

### Post by lidex on 2009-11-04
> **Maximus559 said:**
> Thanks for the reply, but I don't think the post you linked to is describing the same problem. I'm not getting any error messages or anything - the volume and network icons just aren't showing up. Also, rebooting doesn't seem to have any effect.

Right, and the items you're having an issue with are *applets* on the *panel*.

---

### Post by Maximus559 on 2009-11-04
Alright, applets then :D And I suppose it *could *be the same problem manifested in a different way. If I understood the post correctly, he used the error dialog box to delete the applets and then used some console code to reinstall them. How would I go about doing that, given that I haven't seen an error dialog box yet?

Also, in case it matters, I've discovered an interesting piece of evidence. Since the problem I'm having appears to be related to sound in some way, I used the "sudo lshw" command to have a look at what hardware devices were installed. Interestingly enough, Ubuntu seems to think I have an Ensoniq card, when, in fact, I have a Sound Blaster PCI 128. Could this driver confusion be the source of the trouble?

---

### Post by Maximus559 on 2009-11-04
Ah-HA! Figured it out. Turned out that the whole time while I was looking for the audio control and network indicator icons to add back, both of them were contained in the "Notification Area" aplett. Perhaps that particular applet should have a more descriptive title.

---

### Post by Popaul on 2009-12-18
Hi Maximus559... I have the same problem, however I do have a Notification Area applet that seems to work (shows all the other stuff like the network connection, skype icon etc..) but does not show the xs?<!r@~ icon for the sound.
So what did you do exactly to show this out?

---

