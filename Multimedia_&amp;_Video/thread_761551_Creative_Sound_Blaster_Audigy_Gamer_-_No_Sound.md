---
title: "Creative Sound Blaster Audigy Gamer - No Sound"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by CaptainCanuck on 2008-04-21
I'm aware there are 500 posts on the usual no sound issue, I've read most of them. I think mine might be a little bit different though....

At one point I had the sound working, 2 days later I turned the computer on again and it was gone. 

In the course of trying to fix that (I have no clue what I did) I broke something. I'd try re-installing, but theres already a lot of stuff that I worked my way through (about 10-15 other major all ruining problems...) and I don't want to have to try and figure them all out all over again...


[COLOR="Magenta"]THE PROBLEM[/COLOR]:

alsamixer won't start, and the driver isn't even being loaded for the sound card. 
Error Message: alsamixer: function snd_ctl_open failed for default: No such device



I'm currently at work, which is why I'm posting this without ANY output info here. What all outputs should I be posting for this problem? (please specify the whole command, I'm still a total *nix moron, I'm trying to change that).

Is there an easy way to reset the alsa config to default or something similar to that? I have no clue what i did and/or where to break it.

Outputs I know I'll need:
aplay -l
lspci -v
sudo modprobe

---

### Post by CaptainCanuck on 2008-04-22
Nobody?

---

