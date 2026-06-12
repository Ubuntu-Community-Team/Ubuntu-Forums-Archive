---
title: "Skype bit the dust..."
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by voided3 on 2006-11-18
Hello. I recently removed the surround sound card from my computer and decided to use the integrated audio instead. While every other audio/video application is working properly (some that didn't before even), Skype is having some issues. When I make a call to the "Skype test call" it immediately says "problem with audio device". I reinstalled the program but the problem persists, and my integrated sound is recognized properly in the program prefs (VIA 82C686A/B rev50). Also, if this helps diagnose, when I log in, i get the conga drum roll, but no start up or log out sound (i'm running Dapper 6.06). Any thoughts? Thanks!

---

### Post by rpalyvoda on 2006-11-18
What version of Skype are you using? If it's 1.2, try installing 1.3

---

### Post by rpalyvoda on 2006-11-18
> **voided3 said:**
> . Also, if this helps diagnose, when I log in, i get the conga drum roll, but no start up or log out sound (i'm running Dapper 6.06). Any thoughts? Thanks!

Btw, what happens when you test your sound device in
system - preferences - sound?

You may as well try to run Skype in terminal and post log file here

---

### Post by voided3 on 2006-11-18
Hey, i'm running 1.3

---

### Post by voided3 on 2006-11-18
When I go into system sound prefs I don't get sound, though the correct and only sound card is recognized just fine. When I run the command "skype" I don't get any output in the terminal itself, but when I make a call I get this:


ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'ICE1724'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


By looking at this, I can tell it still is looking for my old sound card for some reason, which was the 'ICE1724' seen above, even though the only card listed in its prefs are the integrated VIA one. Hmm...

---

### Post by gosh on 2006-11-18
Have you tried setting the sound preferences in Skype itself?

---

### Post by voided3 on 2006-11-18
Yes, I setup sound in both system and Skype prefs without success. On an interesting note, I went to open volume level monitor and it couldn't open and told me to run "esd" in a command prompt, so I did and got the same error message I did from Skype, refferring to the ALSA lib. How do I reconfigure ESD and ALSA? Thanks!

---

### Post by voided3 on 2006-11-18
Hello. I upgraded to Edgy today and Skype works, so all is good. Thanks anyway!

---

