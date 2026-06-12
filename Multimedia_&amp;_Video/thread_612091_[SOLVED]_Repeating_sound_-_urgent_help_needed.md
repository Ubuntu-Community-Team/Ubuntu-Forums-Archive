---
title: "[SOLVED] Repeating sound - urgent help needed"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by dysphasi on 2007-11-13
Well, not actually done anything apart from let ubuntu updates run, but for some reason, ever since I last restarted, and each time after my sound has gone crazy.

The initial login sound repeats over and over in a loop. Subsequent mp3s I play will start, with a fuzz in the background, then loop. I'm stumped and my head is near exploding with the racket! .... I'm really close to just reinstalling, but would rather not if at all possible.

Please help someone, I'm a bit of a newbie, so idiot-friendly instructions would be appreciated!

ps... 
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by reckless2k2 on 2007-11-13
yeah just save your stuff and reinstall. 

you could try the community docs about sounds troubles to reinstall ALSA but you sound like something else crazy is going on. either than or you don't know that you have the repeat function enabled. hahaha

COMMENT: and is this really urgent? ahahahaha

---

### Post by dysphasi on 2007-11-13
lol, well it's really doing my head in, literally!

Why does nothing just...erm...work?!

---

### Post by reckless2k2 on 2007-11-14
i couldn't really comment. i don't enough about your hardware or environment. it might be a simple tweak or such. i know i don't have many problems in general but if i do have i have either learned enough to fix or know where or how to ask to fix it. if it was working and now not, it's fixable. just need more info and or tweaking. you might be better off with a reinstall though.

---

### Post by dysphasi on 2007-11-14
I took the plunge and started over from scratch. It was taking me so long getting to the bottom of things.

I suppose it's the best and worst thing about a linux system when compared to ms windows. Whilst it is more adaptable and can be tweaked more or less exactly as desired, with a bit of know how, in so doing it lacks the simplicity of, for example, being able to fire up device manager or pop open add/remove programs, wipe the faulty driver and software in question and start over.

---

### Post by reckless2k2 on 2007-11-14
well it is as easy as windows in that respect but is so much more highly customizable that machine specific nuances can sometimes get difficult to diagnose. as your education into linux grows, so will your better understanding of how it works and or how it relates to any machine that you install it on. i've been using it on various hardware for close to 6 years now. i've sampled several distros and i'm always still learning and or forgetting simple things sometimes. hahaha. 

sorry i couldn't help on with your situation but typically a sound base reinstall would clear it right up. that is well documented in the community help. i upgraded my wife's machine not too long ago from 3.5.6 to 3.5.7 of kde and had sound issues. a few queries later i reinstalled it and i was fine. sometimes kernel to kernel you will have these issues as well. i see it all the time if someone is using a nvidia driver which no proprietary drivers survive upgrades that are trying to figure out what happened. 

maybe things need to be better explained in windows terms. imagine you had a driver that only worked in windows 2000. when you upgraded to windows xp that device would not longer work until you got the xp driver. might help the thinking a little better. in linux case, you just have to typically reinstall the driver back in so now it sees the new kernel instead of looking for the old one that is gone. help?

---

### Post by dysphasi on 2007-11-15
I still find it a bit counter-intuitive not removing drivers etc... before re-installing. 
By the by, when I install something with for example apt-get, where are the installation files saved? Surely over time the computer just ends up being filled with unnecessary bits and pieces? Is there a good cleaning program that will search for unneed and temporary files and get rid of them?

With regards to the sound, wiping and reinstalling ubuntu worked a treat, but I carefully caused the problem to occur again (that's a contradiction in terms if there ever was one! ;)) and found out that by changing my grub/menu.lst to include acpi=force the repeating sound issue was initiated. Deleted the entry and back to working sound :D

Only problem I have now is that more often than not a shutdown won't work properly, everything goes blank but the computer doesn't turn off. This happens more when I've got usb devices and/or an external screen plugged in, so think it might have something to do with ubuntu not turning everything off properly.

Anyhow, with regards to this issue, solved :D any wise linux words with regards to the above qs would be gladly received however. Thanks for the comments to date.

---

