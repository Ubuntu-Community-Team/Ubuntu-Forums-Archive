---
title: "[SOLVED] I killed my sound"
date: 2008-08-15
forum: Multimedia Software
---

### Post by CalderCoalson on 2008-08-15
Apologies in advance for the stupidity of my actions.  Yesterday, I installed Netatalk with ssl encryption, and that went fine.  Except that it has some conflict with roaming mode on my laptop, (which I kinda need, considering it's a laptop), so I made this thread: [http://ubuntuforums.org/showthread.php?t=890295](http://ubuntuforums.org/showthread.php?t=890295) .

Here's the stupid part, I got interested in the rc.d boot process, read up on that, and then tried tweaking it just a tiny bit, (which much to my surprise didn't end in a computational apocalypse) and I didn't even notice my sound was gone until I tried playing some music today.  When I did, all my speakers emitted were this quiet popping noise, and only when the song would be at high volume parts.  System beeps still work, but I suspect that's handled by something else.  I made sure alsa was starting at runlevels 2-5 using sysv-rc-conf, and even tried reinstalling the alsa drivers, but nothing changed.  Any help will be much appreciated.

---

### Post by CalderCoalson on 2008-08-15
Ok, sorry people, figured it out.  Somehow, it had changed the alsamixer settings, and all I had to do was turn the PCM one all the way up and unmute the IEC958 one.

---

