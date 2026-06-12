---
title: "No sound for certain users (Kubuntu 9.04)"
date: 2009-08-03
forum: Multimedia Software
---

### Post by daryl314 on 2009-08-03
Hi all,

I just bought a new laptop and installed Kubuntu 9.04 on it.  With a fresh install, the sound was working fine.  When I copied over the /home partition from my old laptop, the sound stopped working.  I created a new user account, and the sound works okay for that account.

Could anyone tell me what sound configuration files I should delete to get the sound working again?  Or what settings I should look at?

Thanks!

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by daryl314 on 2009-08-03
so you'd recommend scrapping alsa for esound?

---

### Post by igorzwx on 2009-08-03
"so you'd recommend scrapping alsa for esound?"

What do you mean?

---

### Post by daryl314 on 2009-08-03
it looks like the link you gave me was a howto for installing esound.  is that what you were suggesting that i do?  or was it a different part of the howto?  i don't quite understand what you were suggesting

---

### Post by aesis05401 on 2009-08-03
Hello, 

Could this be a permission issue?  On another distro I used to see many posts about sound working only for root, and the solution is to change permissions on the right /dev device entry.

Since you have relocated /home you may need to add your old users to the local group that has permission to the device.  The fact that a new user account works properly makes me think you just need the right entry somewhere.

Then again, this is purely a guess.  Good luck.

---

### Post by aesis05401 on 2009-08-03
It looks like 'audio' is a default group on Ubuntu.  Here are some commands that may help:

```

# Check your groups
grep <usrname> /etc/group

# Add user to audio group
sudo adduser <usrname> audio

```

Does this help?

---

### Post by daryl314 on 2009-08-04
Thanks for the suggestions.  The group settings were the same for both accounts, so unfortunately that didn't help.  

I didn't figure out what files were causing the problem, but I did figure out that they were somewhere under ~/,kde.  When I deleted .kde, re-installed, and copied over the config files that I needed from .kde/share/apps (from my old laptop) the sound finally worked!

---

