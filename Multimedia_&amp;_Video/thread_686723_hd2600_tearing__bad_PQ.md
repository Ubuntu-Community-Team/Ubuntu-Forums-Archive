---
title: "hd2600 tearing / bad PQ"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by agruman on 2008-02-03
I cant get my ati hd 2600 xt to work as it should, i get tearing when playing video and when comparing the quality between vlc in linux / windows and mplayer in linux / windows. Its a great deal better on windows.

I have the latest fglrx and glxgears gives approx 8k fps and glxinfo is reporting the correct info so i don't see any error there. I have tested with vga / dvi / hdmi no difference and have tried all "-vo" options to mplayer but nothing seems to help.

Anyone here running the hd2600 successfully on ubuntu?

Now i really want to run ubuntu, but with the problems i currently have i don't seem to have any choice but to run win.

I really appreciate all the help i can get.

Greetings

---

### Post by clicq on 2008-02-03
I have the same problem with video tearing an the same card. Some things you may want to try (they didn't work for me but maybe they might work for you):

sudo aticonfig --vs=on
sudo aticonfig --sync-video=on

(I believe those are the options, but I'm not in linux at the moment to actually check, you may need to run aticonfig --help to check). In theory, they enable vsync so you shouldn't get any tearing, but it doesn't make a difference for me :(

---

### Post by agruman on 2008-02-04
Thanks for the information clicq but they didn't make any difference for me either :(

The best quality / minimal tearing i got so far is when using "-vo x11 -zoom" though it is far from perfect.
I read the "known issues" from ati today and from what i can see our problem are not listed, they have a listing that tearing and blocky video might be noticed when using the xv extension, but i get tearing and blocky video when using any renderer :(

Guess i have to file a bug report to ati and hope they answers (not just one of those automated mails they send when receiving feedback).

I'm getting crazy from this :/

Greetings

---

