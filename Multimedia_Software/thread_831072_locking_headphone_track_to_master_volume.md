---
title: "locking headphone track to master volume"
date: 2008-06-16
forum: Multimedia Software
---

### Post by SpaceMaster on 2008-06-16
Currently, I'm using Hearty Heron on a Dell Inspiron 600m.  The audio mixer works well enough, but things are a little hairy with headphones.

the headphone track only wants to adjust from the volume control window, on its own.  With previous installs, it would lock to the master volume track, allowing me either to adjust it from the task panel volume control or through media button shortcuts.  I have assigned the media buttons to control volume.  Also, I selected "Headphone" as one of the tracks to control through the main volume bar.  Still, no cigar, and the headphone volume only responds to the volume control window.

Any suggestions, or workarounds?

---

### Post by rainwalker on 2008-06-17
I also have this issue with Hardy on my Dell Inspiron 8600...I'll post back if I find anything

---

### Post by SpaceMaster on 2008-08-07
Lemme rephrase what I'm asking.  Is there a way to assign the Volume Control media buttons to control audio tracks separately from the master track?  The Keyboard Shortcuts interface only seems to assign to the master track.

---

### Post by SpaceMaster on 2008-08-19
Okay, so I finally figured this one out.

In previous versions of Ubuntu, what I was doing was right-clicking on the volume control icon, and selecting "properties".  While in properties, I Ctrl-selected all tracks I wanted to control.

It's a hair different in Hardy, though you end up doing something that looks almost the same (my point of confusion).  Click System -> Preferences -> Sound.  Under Default Mixer Tracks, there is a list in which the desired tracks to be controlled with the keyboard can be selected.

There you have it.  Keyboard shortcuts assigned to whichever volume track(s) you desire.

---

### Post by cormic on 2008-09-10
Thanks for that SpaceMaster.  It was just what I was looking for :)

---

