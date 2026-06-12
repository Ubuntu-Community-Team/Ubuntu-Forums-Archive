---
title: "Feisty Sound Problem ca0106"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by enpey on 2007-04-25
Hello all,

I was tinkering about trying to get sound through all 5 speakers rather than simply the front/centre or rear speakers and I have managed to break something. I have just updated to 7.04 Ubuntu.

aplay -l gives this:
$ aplay -l
aplay: device_list:222: no soundcards found...

I follow this guide 
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
and arrive at a failed Step 4. I have tried "Getting the ALSA drivers from a *fresh* kernel" and "ALSA driver compilation", along with the instructions found here 
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106)
but run into errors when running make. I have a build log from the module-assistant that is a few kB too big to attach but I have split it into two parts (1 and 2) and that is attached for completeness.

If anyone could offer any help or suggestions I would greatly appreciate it. Any other info needed just ask and I will grab it ASAP.

Thanks, Nathan

---

### Post by enpey on 2007-04-25
Mmm...well I just bit the bullet and reinstalled..this time making a separate partition for / and /home so it wont be a nuisance if my tinkering urge gets the better of me again.

But I am still unable to hear sound out of more than one "group" of speakers (ie the front two, the centre, or the rear two). If anyone has idea about what to do or look at that would be a great help.

Thanks, Nathan

---

### Post by tical_84 on 2007-04-29
I'm experiencing the same problem as well :(

---

