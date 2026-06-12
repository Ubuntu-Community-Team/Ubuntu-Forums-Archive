---
title: "Shortcut keys problem on Ubuntu 7.10"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by viaduk on 2007-10-19
Hello,
Iam I have a problem with sound shortcut keys on my laptop keyboard. They actually doesnt do anything.In example if i press Mute sound shortcut key on laptop keyboard the Ubuntu shows that it muted the sound but it actually doesnt mute. All sounds work at same level. Even if i try to do volume up or volume down shortcut key.. They also doesnt work... What is the problem? Oh i forgot to mention that they worked in Ubuntu 7.04 and now I installed 7.10. Sorry for my bad english language ;)

---

### Post by Blairboy on 2007-10-19
Try reassigning them under Preferences->Keyboard Shortcuts.

---

### Post by viaduk on 2007-10-19
tryed ... Same thing. It shows on he desktop that it changes volume or mutes with that Speaker picture but it doesnt do anything to sound at all :(

---

### Post by viaduk on 2007-10-19
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/126542](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/126542) 
Here is the same problem but they didnt solved it there :(

---

### Post by viaduk on 2007-10-19
No help for me?:(

---

### Post by viaduk on 2007-10-19
nobody had this problem?

---

### Post by cojoco on 2007-10-19
I have this problem, too, with a Logitech keyboard.  Volume control shows 0 or 11, Mute button shows on screen OK, but neither work.

---

### Post by Cirrocco on 2007-10-19
[http://ubuntuforums.org/showthread.php?t=581690]("http://ubuntuforums.org/showthread.php?t=581690")

---

### Post by cojoco on 2007-10-19
No, doesn't help.

KDE/Ubuntu system sounds work; Mplayer works, but
Amarok and Keyboard volume control don't work.

---

### Post by Ymer on 2007-10-23
I had a similar situation, here is how I managed to solve it (after reading the bug page), might be useful for you:

Go to System>>Preferences>>Sound. At the bottom there is the Default Mixer Tracks, select your sound card from the device drop-down menu and also which channel you would like the mixer to control (I use Master). And that's it.

One other possibility is also to right click on the mixer's icon and select preferences, and do the same there. I did this before heading to the forum to find the solution (means didn't work on its own, but might solve yours).

---

### Post by Mithrilhall on 2007-10-26
I'm having a similar problem. What's actually happening is when I push my 'volume up', 'volume down' and 'mute' buttons on my keyboard (this is a desktop not a laptop) it's actually changing the volume for the headphones in kmix.


I still haven't found a solution for this.

---

