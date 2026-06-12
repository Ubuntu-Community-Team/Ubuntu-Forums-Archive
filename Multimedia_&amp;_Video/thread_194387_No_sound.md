---
title: "No sound"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by bleakcabal on 2006-06-11
Hi, sound stopped working when I upgraded to 6.06 LTS.

lspci still sees my sound card. alsamixer also sees it and nothing it muted and everything is just fine. 

I checked my alsa .conf file and everything looks ok. I followed the instructions on the Ubuntu Wiki. I checked to make sure sound wasn't muted anywhere.

I made sure I was plugged in the right spot on my comp. 

I checked to make sure I was using the latest versions of alsa and kdearts.

Now I'm all out of ideas. A google search hasn't found any new information so I'm basicly stuck. Anyone have any clues as to what I should do next ?

---

### Post by bleakcabal on 2006-06-11
bump

---

### Post by stephen_sing on 2006-06-11
I have got the same question. everything sees ok, and i do have sound effect when i logged into the system and when i have do sth wrong. but it just be no sound when i play a CD, or MP3s, etc.

[QUOTE=bleakcabal]Hi, sound stopped working when I upgraded to 6.06 LTS.

lspci still sees my sound card. alsamixer also sees it and nothing it muted and everything is just fine. 

I checked my alsa .conf file and everything looks ok. I followed the instructions on the Ubuntu Wiki. I checked to make sure sound wasn't muted anywhere.

I made sure I was plugged in the right spot on my comp. 

I checked to make sure I was using the latest versions of alsa and kdearts.

Now I'm all out of ideas. A google search hasn't found any new information so I'm basicly stuck. Anyone have any clues as to what I should do next ?[/QUOTE]

---

### Post by bleakcabal on 2006-06-11
I don't have any sounds whatsover. I just tried removing and reinstalling a ton of packages and things are still not working.

EDIT: I installed Xubuntu's package in case it was just KDE but I still don't have sound under XFCE.

EDIT2: I have found a partial solution to my problem. I re-enabled on-board sound in my BIOS and found it is still working.

---

