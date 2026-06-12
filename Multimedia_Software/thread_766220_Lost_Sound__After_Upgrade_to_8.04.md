---
title: "Lost Sound  After Upgrade to 8.04"
date: 2008-04-25
forum: Multimedia Software
---

### Post by martrn on 2008-04-25
I have lost my sound after I upgraded from gusty to hardy 8.04.  Everything works well but I have no sound at all.  I upgraded via adept, choosing the upgrade distribution option.  This box only has on-board sound and everything worked fine in gusty.  The kinfo center is reporting my multimedia audio controller as VIA Technologies VT82C686 AC97 Audio Controller, on IRQ7.

Is there any way to diagnose sound-card problems in hardy as I have not had problems with sound before, so do not know and can't not find anything revelevent to diagnosing sound card problems in hardy.  ?

Wow my spell-checker for firefox started working.  Cool.  Anyone else had a sound problem and sorted it  ?

---

### Post by blink0072005 on 2008-04-25
You should probably join us here: [http://ubuntuforums.org/showthread.php?t=766162](http://ubuntuforums.org/showthread.php?t=766162).  You're not completely alone...

---

### Post by mjskia1 on 2008-05-10
If you're having the same problem I had (which isn't by any means a certainty), where you have no sound *at all* after upgrading a Kubuntu installation to 8.04, here's what I did to fix it.

[LIST=1]
[*]Open your terminal of choice (Konsole, etc.) and run alsamixer.[*]Use the right arrow to navigate to the PCM control, and press the up or down arrow just once.
[*]You should have sound now; I found that just modfying PCM was enough to solve my problem.
[/LIST]

This almost certainly won't work if you're only missing sound from certain programs.  For example, if you only lose sound when playing mp3 files, check the link in the previous post.

---

