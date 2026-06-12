---
title: "Sound system has died"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by JohnPettigrew on 2007-02-23
I installed Skype on my Kubuntu system and tried to get it working (OK, I know, it's my fault). Prior to this, my sound worked fine - I could record in Audacity etc. However, Skype doesn't want to know - will play sounds and play the voice in a test phone call, but apparently doesn't send anything I say over the wire.

As a result, I played a little with Skype's settings, swapping between ALSA and OSS to see whether that helped. Then, I tried starting the app with 'artsdsp -m skype', which is advised on the Skype forums for those of us running KDE. That didn't work, either. However, I now find that my sound system has been hosed. Skype won't run and now nor will Konqueror (freezes showing a blank window when I try to open a directory). When I log into KDE, I get an error saying that arts couldn't start and do I want to try again. However, other users are unaffected, so it's clearly a b0rked setting somewhere in my account.

So, basically, I want to know where the arts settings are stored so that I can copy a working file across from another user (or just delete it for auto-recreation). I've had a poke inside ~/.kde to no avail. Anyone know the answer?

(And, in future, I guess I'll just try OpenWengo or LinPhone...)

---

### Post by mizar001 on 2007-02-23
These problems you have seems more than a sound issue. Try to stop skype and sound server processes, after the restart of the system.

Never got problem in Ubuntu with skype calls.

---

### Post by JohnPettigrew on 2007-02-23
I've already restarted the machine - I had assumed that a restart would set everything back how it had been. The fact that it's still not working was what worried me.

Anyone know where the arts settings are stored?

---

### Post by JohnPettigrew on 2007-02-23
To clarify:

1) Sound system used to work perfectly (e.g. I could record and play back through Audacity).
2) Configuring Skype and using 'artsdsp -m skype' has hosed it.
3) Rebooting the machine and killing artsd has no effect.

More details:

a) I seem to have 2 artsd processes running all the time (killing them causes them to be restarted), whereas other users on the same machine (with functional sound) have only one.
b) Running Konqueror causes it to freeze before displaying folder contents - until I kill artsd, at which point it works. Even after artsd respawns, Konqui continues working, until I quit and restart it.
c) Running System settings works, and I can run the Sound module. However, any attempt to change the config causes it to freeze (requiring forced termination) - but the changes do get saved, suggesting that it's the restart of the sound system that's failing. Again.
d) Despite these problems, I can still get sound in my account through e.g. amarok and kaffeine.

What I need is, I think, simply to know where the artsd config is kept (including, by the look of it, how many instances to spawn) so that I can replace the obviously defective copy.

---

