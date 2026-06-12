---
title: "JACK Audio or QSyncth terribly unstable"
date: 2010-09-12
forum: Multimedia Software
---

### Post by tgp1994 on 2010-09-12
Hi everyone. Apologies if this is in the wrong section, I don't know what to blame for this.

Anyhow, I wanted to try some music making in ubuntu. I referenced the wiki, and (in a seemingly biased statement) said that Qsynth was the best synthesizer out there. Trusting that, I downloaded it and installed it onto Mint 9 isadora.

After launching it, it told me to make a few changes to (I think) a policies file, which I did, and logged in again. After opening it once, it crashed after several seconds (nice catch, apport ;)). But then on the second try, it seemed to work for a bit.

At that point, I was able to load in what is apparently called a "Synthfont" (PC51f). Qsynth crashed again for no reason, but after starting up, it said it couldn't connect to JACK. (It was getting denied.) When I tried to open the JACK control panel, that took almost everything down - Firefox, its self, and the GNOME DE.

So what's going on here?

---

### Post by cchhrriiss121212 on 2010-09-12
Jack is the default output for qsynth or most other synths on Ubuntu, which is probably why qsynth was crashing on you. If you can open qsynth, go to setup and the audio tab, then select ALSA output instead of jack.

If you just want to play around with a few synths, then try using zynaddsubfx or LMMS, which are simpler to use.

---

### Post by tgp1994 on 2010-09-12
> **cchhrriiss121212 said:**
> Jack is the default output for qsynth or most other synths on Ubuntu, which is probably why qsynth was crashing on you. If you can open qsynth, go to setup and the audio tab, then select ALSA output instead of jack.

If you just want to play around with a few synths, then try using zynaddsubfx or LMMS, which are simpler to use.

Well, over the period of time of me trying to change Qsynth over to ALSA, it crashed at least 6 times, and took down GNOME at least twice. Not to mention that, but whenever I try to open Firefox after opening Qsynth, firefox will repeatedly close. (Where's apport when ya need it?) Shall I report this as a bug?

P.S. After all that, I still couldn't get the settings to stick on alsa. Is it possible that I don't even have it installed? If so, can I uninstall jack?

---

### Post by cchhrriiss121212 on 2010-09-12
You definitely have ALSA installed and there is no reason to uninstall jack as it will not interfere unless it is running.
If ALSA output does not work you could try using pulse output.
Try running qsynth in a terminal and post what error messages you get.

---

### Post by tgp1994 on 2010-09-12
> **cchhrriiss121212 said:**
> You definitely have ALSA installed and there is no reason to uninstall jack as it will not interfere unless it is running.
If ALSA output does not work you could try using pulse output.
Try running qsynth in a terminal and post what error messages you get.

The only things I got back in the console when I ran qsynth with it were Segmentation faults and bus faults. The segfaults came from when it just randomly crashed, and bus faults seemed to come from when I set it to alsa. Or tried to, that is.

---

