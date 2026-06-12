---
title: "PulseAudio failure to connect"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by shendric on 2007-12-21
I installed PulseAudio, and it seemed to be going fine, but now, it doesn't seem to be working anymore.  When I go to the PulseAudio Manager, I get a connection refused message.

Has anyone had this problem?

---

### Post by shendric on 2007-12-21
Ok, more information:

When I try to add both root and my primary user to the groups pulse-rt and pulse-access, the additions don't stick.  I restart the X server, go back to User and Groups, and neither user are listed as member of either group.  If I add to pulse, no problem, they stay.

That seems odd to me.

---

### Post by terminal on 2008-01-03
exactly same problem here .

---

### Post by jkzubu on 2008-01-03
I was able to get Pulse Audio (PA) working after a few attempts.  My solution was to completely remove Alsa using the complete removal command in the comprehensive sound guide and I checked to make sure Esound was removed.  Then, I did apt-get autoremove and autoclean and a restart.  After restarting, I did a complete install of PA using Synaptic, restarted and PA seems to be working pretty well.  Just a couple settings in Sound Prefs and almost everything else seemed to self-configure.  I currently have no sound with Flash 9 for Firefox  and no bongo drums for the login screen - I am still looking for a solution to these.  Prior to installing Pulse, I had no system sounds (bings, sirens, boings etc) and I now have these sounds.  

Also, I initially read the Debian perfect setup howto, for PA, but discovered that most of the configurations described there *seem* to have been completed in the Synaptic install.  My system is Gutsy (AMD64).  I tried 2x to install Pulse without removing Alsa, but found success after removing Alsa.

---

