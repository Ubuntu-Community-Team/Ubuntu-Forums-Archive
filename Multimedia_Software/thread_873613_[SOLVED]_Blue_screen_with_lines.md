---
title: "[SOLVED] Blue screen with lines"
date: 2008-07-29
forum: Multimedia Software
---

### Post by zombrax on 2008-07-29
hey gurus,

just had a couple of quests...

first the main prob is that after i play say 2 or 3 movies on my laptop, the nex one usually just goes all blue on the screen with vertical lines and the only way around this is to turn my laptop off by pushing the button in.

why is this doing this? its random and erratic as in it could be after 3 maybe 4 etc. my video0 card is an xblade and i'm running a pretty old laptop with only 256mb ram but lots of virt mem. any rememdies for this? i am also running vlc media player for all my vid requirements..

secondly, what player plays .mov files flawlessly? i tried both vlc and movie player but both stalls at the 1st frame but shows that its playing as in the time counter is moving forward.

many thanks in advance guys.

---

### Post by TenPlus1 on 2008-07-29
I tend to use mplayer for .mov files since they play ok with that...  skip gnome mplayer (very basic interface) and go with the simple mplayer from synaptic...

As for the blue screens appearing, not quite sure what that could be, so maybe try playing your movies in mplayer for a while to see if it continues happening...  VLC also lets you change Video -> Output Module (need to tick Advanced) to test other mods and see if that helps...

---

### Post by zombrax on 2008-07-31
umm does anyone know how to install mplayer from command line please?

many thanks.

---

### Post by TenPlus1 on 2008-07-31
sudo apt-get mplayer

---

### Post by zombrax on 2008-08-01
nope this command doesnt work.. gives me a 
"E: Invalid operation mplayer" err... 

any tips?

---

### Post by zombrax on 2008-08-06
the command is::

sudo apt-get install mplayer

Installs everything inclufd libraries but I couldnt play any videos initially till I played around with my video drivers under VIDEO tab. Good Luck. No more crashes on my system when playing through mplayer.

many thanks once again to those that gave suggestions :)

---

