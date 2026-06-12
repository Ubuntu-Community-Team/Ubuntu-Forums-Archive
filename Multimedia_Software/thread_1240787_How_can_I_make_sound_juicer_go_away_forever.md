---
title: "How can I make sound juicer go away forever?"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Dirjel on 2009-08-15
I really hate sound-juicer.  I much prefer an all-in-one music program, so I rip my CD's via rhythmbox.

However, sound-juicer insists on opening whenever I mount a music CD.  I set system > preferences > removable drives & media to rhythmbox, and I set the edit > preferences in Nautilus, and still sound-juicer opens when I mount a music CD.

I uninstalled sound-juicer, and now I get an error when I mount a CD, because Ubuntu STILL wants to open sound-juicer, even though it's not even on the computer anymore D:

What can I do to make my computer forget about the program entirely?

---

### Post by mc4man on 2009-08-15
the settings are in file management (cd's. dvd's ect
various ways to open

[http://ubuntuforums.org/showthread.php?p=7783887#post7783887](http://ubuntuforums.org/showthread.php?p=7783887#post7783887)

---

### Post by Dirjel on 2009-08-15
Already did that (see screenshot).  Didn't work.  When I mount an audio CD, it still says:

**Could not open location 'cdda://sr1/'**
Failed to execute child process "sound-juicer" (No such file or directory)

---

### Post by Dirjel on 2009-08-15
Alright, I tried some different methods of mounting it, and it seems like Ubuntu only wants to open sound-juicer when I mount the CD via the "Places" menu from the panel.

How can I change that behavior?  The places menu is, by far, the most convenient way for me to mount CD's, as they refuse to mount automatically.

---

### Post by mc4man on 2009-08-15
In regards to places Atm don't know, never used places for audio cd's, though it does indeed seem to be tied to sound-juicer independant of the default action.

Audio cd's don't 'mount' in a traditional sense (there's no filesystem to mount), they're accessed at a location. So if you can see them in places that's as 'mounted' as they're ever going to get

What happens if you insert a cd and hold down the shift button?
(( you should get a pop up asking what to do and whether to always do that action

Do you not see an icon on desktop?

Edit-
if you don't see the icon on desktop go in terminal
```
gconf-editor
```

apps -> nautilus -> desktop and make sure "volumes_visible" is checked

---

### Post by Dirjel on 2009-08-15
I have compiz drawing the desktop, so I don't have any icons at all on the desktop.

I tried letting nautilus draw the desktop, and lo and behold, my audio CD automounted when I put it in, and there was no mention of sound-juicer anwhere.

I set compiz back to draw my desktop, and took a screencap to show an unmounted audio CD.  The computer knows I have an audio CD in the drive, but... it's not mounted.

---

### Post by mc4man on 2009-08-15
> unmounted audio CD. The computer knows I have an audio CD in the drive, but... it's not mounted. 

This may just be a matter of semantics,, if "computer knows..." thens it's "mounted" as I described before.

you just can't see the icon due to the manner you're running your desktop

There is no obvious way to change what clicking on the audio cd icon places does, and there may not be. ( nor worth the time to track down due to easy 'workaround'

If you've uninstalled sound-juicer  it is quite easy to make clicking on the places icon do pretty much anything you want

(( i don't have sound-juicer so I set the places icon to run a script that autoplays cd's in amarok

While I would be a bit careful with exec's, here's a quick rundown (( a ~/bin thats in your path is really best for such activities

When you click on the icon a file named sound-juicer that's in your path will be executed if found and executable (/usr/bin ; /usr/local/bin ; ~/bin

I would use either /usr/local/bin or preferably ~/bin

Just put a script or executable that does whatever you wish in one or the other and name it sound-juicer

---

### Post by Dirjel on 2009-08-16
> **mc4man said:**
> Just put a script or executable that does whatever you wish in one or the other and name it sound-juicer

Oh.  I'm surprised I didn't think of that.  Thanks.  Problem is taken care of; computer has ceased to annoy me.

---

