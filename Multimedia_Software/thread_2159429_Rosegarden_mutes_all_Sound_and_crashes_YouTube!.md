---
title: "Rosegarden mutes all Sound and crashes YouTube!"
date: 2013-07-03
forum: Multimedia Software
---

### Post by Sanitoeter on 2013-07-03
Hey, I already posted this in the absolute beginners section, but it got no responses whatsoever.


I downloaded Rosegarden because I needed a Midi/Sheet Music Editor, and the weirdest things started happening:
Once I run Rosegarden, all sound mutes. I can still control the volume etc, but there simply is no sound.

I also realized a slight  difference in YouTube videos: They run at 10x fastforward.
The sound doesn't return when you close Rosegarden, neither does the effect it has on YouTube.
Restarting doesn't help against this issue anymore, but I realized one thing: Before I enter my password and log in, there is still the Ubuntu Startup-Sound, or welcome sound or whatever you call it.
Everything is completely mute after this though.

I hope you can help me!
Desperately,
Sanitoeter

---

### Post by Sanitoeter on 2013-07-03
I just updated it to 13.04, and it crashed when rebooting. 2 hours of empty ubuntu background and a white square.
Then I did a hard reset, now the Computer is terribly slow and programs start crashing all over the place. Sound and Video playback is still fudged up.
Is there any way to reset Ubuntu completely without having to reformat the hard disk? I have about 400GB of data on it that I can't secure at the Moment.

---

### Post by SeijiSensei on 2013-07-03
Reboot into "recovery mode" and drop to a root shell when prompted.  You should be able to copy files to an external with something like rsync.

---

### Post by CraigPid on 2013-07-11
I think Rosegarden needs Jack to run. I imagine if you are not starting jack yourself then rosegarden is starting it for you.All programs that are not Jack aware (flash) will not be able to access the sound card while jack is running. Qjackctl is a graphical interface for Jack. You can control the starup and shutdown and all the options of Jack with it. Once you shut down jack the sound will return.

---

