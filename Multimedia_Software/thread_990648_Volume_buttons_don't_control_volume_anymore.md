---
title: "Volume buttons don't control volume anymore"
date: 2008-11-22
forum: Multimedia Software
---

### Post by master5o1 on 2008-11-22
I installed Intrepid several weeks ago and no I have a sudden problem: Volume hardware switches don't control anything anymore, although it still shows that it is changing the volume (no sound change).  I have to actually use my mouse to change the volume at the gnome panel applet.

(annoying)

---

### Post by b3n0 on 2008-11-23
Hey all, 
I have the same problem. Not only has my volume control stopped working, but my mute button also wont work any more. I tried System > Preference > Key Board shortcuts, only to find they were all still set up properly, according to that window. I'm running 8.10 on a HP DV6000 laptop. It comes with a remote which also use to work well. The Volume and Mute button on the remote are programed as a clone of the ones above the F keys so naturally the remote has also stopped working. 
Thanks

---

### Post by master5o1 on 2008-11-23
This here is a more annoying bug than the ones I experienced in Hardy.

---

### Post by madverb on 2008-11-23
Possibly it is controlling the Master sound channel but you need it to control PCM?

To change that you go to System>Preferences>Sound and highlight PCM down the bottom. This makes it so keyboard volume controls PCM instead of Master.

---

### Post by b3n0 on 2008-11-23
Still hasn't fixed it, the little box wont flash up at all now.

---

### Post by madverb on 2008-11-23
Do you know which volume it is controlling when you manually change/mute the volume?

---

### Post by b3n0 on 2008-11-29
Hey, I think I've just solved this.
In Intrepid the codes for all the shortcut keys are different compared to Hardy.

Firstly go System > Preferences > Sounds and ensure Master is selected, in the big list at the bottom of the window.

Now go to System > Preferences > Keyboard Shortcuts, find volume up, volume down, mute, next track.... etc
Click them and then hit your shortcut key.

For example, this is what was rolled across from Hardy for my mute '0xae'. By reprogramming it it now has 'XF86AudioMute'. All the keys above the F keys work now and also the remote.

Hope this helps. :D

---

### Post by master5o1 on 2008-12-12
That doesn't fix anything for me.

For me the visual notification that compiz gives (etc) in the middle of the screen appears to show it working but the volume doesn't change.
Might be more of a dbus problem or something else weird.

---

