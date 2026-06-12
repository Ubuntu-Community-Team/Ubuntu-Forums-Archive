---
title: "Intermittent sound problems in 9.10 64 bit, plasma desktop crashing, poss  related?"
date: 2010-04-18
forum: Multimedia Software
---

### Post by swiggy349 on 2010-04-18
Hi guys, I upgraded from windows to kubuntu about 6 months ago and have found it so much better, kind of wish id discovered linux ages ago.. 

Anyway I got a new laptop a couple of weeks ago and ive had one little niggling problem with it. (Its an asus, Turion m500 but i dont think this is a hardware issue, can post rest of specs if needed). I get sound out of firefox, but then if i open up any application that can produce sound, then the firefox sound is cut off, the only way to get sound again is to restart firefox. Occasionally when this happens the plasma desktop crashes, reporting a seg fault. the plasma desktop will then keep crashing until i restart, everything is back to normal then. Is there any way to stop 2 sound producing apps from interfering with each other? it sounds fairly trivial but is actually really annoying. Everything is up to date as of this morning.

Maybe this is also related, but I cant get amarok to play any of my music files. it worked the very first time i used it then hasnt since. it just gives `error in playback` for any files. i have the restricted extras package installed.

I know this sounds like a lot of questions in one go but i think its all related.

thanks for any help, cheers

---

### Post by Untitled_No4 on 2010-04-19
It's a known issue and as far as my experience go, it doesn't happen in Lucid, so the future's good.

In the meantime install pulseaudio to workaround the problem. Open Konsole and run the following:
```
sudo aptitude install pulseaudio paman padevchooser paprefs pavucontrol pavumeter
```

When it's installed, run
```
paprefs
```

Go to the Simultaneous Output tab and check "Add Virtual output for simultaneous output on all local sound cards".

This might also get Amarok to work for you, but if it doesn't post back.

---

### Post by swiggy349 on 2010-04-20
OK thanks a lot, if its a known issue i apologize for not finding this already on the forum. That has got it working perfectly thanks. Ill be going to lucid as soon as the full release is out anyway, cheers.

---

