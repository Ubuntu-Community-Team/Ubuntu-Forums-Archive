---
title: "I lost sound (after logging into KDE)"
date: 2008-07-24
forum: Multimedia Software
---

### Post by dkuhlman on 2008-07-24
My sound had been working.  Then one morning I turned on my machine and could not play any sound.  I've tried Amarok and mplayer, but I get no sound.

I always use Gnome desktop.  But I have kubuntu installed, and the previous night, I logged-on to KDE just to see what it looked like.  The next morning I had no sound.  Those two (logging onto KDE and sound) may not be related, but that's the only thing that I can think of that I did out of the ordinary, so I'm suspicious.  Could KDE have captured something.  How can I reset it?

Is there a list of things I can check or reconfigure?

What I've done so far:

1. Checked /proc/asound/cards:

     ~ [47] cat /proc/asound/cards
     0 [NVidia         ]: HDA-Intel - HDA NVidia
                          HDA NVidia at 0xddef4000 irq 23

2. Looked in System --> Preferences --> Sound.  When I click on a Test button, I do not hear anything.

3. Tried plugging my speakers into another computer.  The speakers work fine.

4. Checked the sound control thing in my panel.  It shows that sound is *not* muted, and master volue is at 80%.

- Dave

---

