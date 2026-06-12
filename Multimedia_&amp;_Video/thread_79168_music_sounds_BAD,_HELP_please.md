---
title: "music sounds BAD, HELP please"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by GrayMatter4tw on 2005-10-19
When I play MP3's with XMMS or Rythm, they sound rather distorted, or low quality, how do I fix this?

---

### Post by michael117 on 2005-10-20
What sound card are you using and are you using ALSA or OSS? I have a turtle beach santa cruz 5.1 pci sound card and I get the same thing. I've noticed that I get slightly better quality out of the OSS drivers than the ALSA drivers, but it still sounds distorted. I'm also interested in getting this corrected.

---

### Post by Lem on 2005-10-20
If you reduce the levels in the mixer, does this help? 

Have the same prob with Via boards, but if you reduce the pcm and master levels to about 3/4, it sounds peachy.

(Used to be able to set the VIA DXS levels in Hoary instead, but can't in Breezy, why is that?)

---

### Post by Binnikemasken on 2005-10-21
Yay! I had the same problem and this worked (what Lem said)! I thank you a lot!
\o/

---

### Post by nullmind on 2006-03-26
I had the same problem with my notebook. I noticed that I had **muted the Thread "PC Speaker"**. I unmuted the speaker later (for no real reason) and noticed the change. I have a Gateway MX6027 and the card is something AC97' based.

Cheers,
Kris

---

### Post by Syirrus on 2006-03-27
I noticed this too.  Everytime I run linux with my SBlive, the sound is of low quality.  I have an Xfi, but there aren't drivers for it :(  Is there anything else I can do to improve the sound quality?


Syirrus

---

### Post by imon9 on 2007-01-17
i am not 100% positive this can help, but uninstall your mixer software and installing other one might help...in my case, i have a Realtek AC 97 soundcard build-in with my twinhead laptop (nevermind if u never heard of it)....as i was saying, i tried ALSAmixer, xfce-mixer, gnome mixer but all somund bad, but when i changed to QAMix, all went to nice normal sound, go try your luck...

my mic however is currently not functional after changing mixer, so be aware of the possible problem with mic recoding for now..

if this workes,  please post a reply..and if it is not too much of toruble, please private massage me too...

i cant keep track where i answer these treads in the forums, so i can't check back wether it is working, but if this solve the problem, i want to write an article for the rest fo the ubuntu commmunity to know it... (and port it in the forum, in hope it can help others)

---

### Post by vitalejd on 2007-08-17
I had the same problem...I lowered the PCM volume to about 75% like previously stated and that worked good!

---

