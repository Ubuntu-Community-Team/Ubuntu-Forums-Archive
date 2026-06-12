---
title: "Standard nvidia-problem (5200 128mb / 7.10 Gutsy)"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by .gurkburk on 2008-03-24
Ive read about this exact problem in several threads, and in other forum's aswell, but I cant find a solution that solves my problem, so im making a go for some help here if there is anything "all the other threads" didnt touch uppon.

First a note: Im not trying to get nvidia-drivers in the computer for games, I wanto use it as a HTPC for files and musik with some simple GUI (like XBMC or Elisa), but Im having problems starting both of them (graphical problems) this is why I wanto get nvidia in and restart my problem with the htpc-systems.

Note2: The board is a ITX with builtin Chrome-VGA (disabled in bios and nothing pluged in, just a sidenote).

Ok, what ive done is simply trying to activate the restricted drivers in ubuntu, that gave me a black screen upon login, had to use SSH and reset xorg.conf to get X again.

Ive also tried the envy-program to get the drivers in (both automatic and 169.12 manual), results in the same thing: machine boots up, gives me a black screen and I hafto SSH-in and replace Driver: "nvidia" with Driver: "nv" to get X...

Appart from that ive tried getting some packages in with apt-get through som guides, but anything I try results in black screen, and I hafto get into xorg.conf and remove nvidia and put in nv again.

Help?
I sure dont know what to do ;-)

Let me know if you want a xorg.conf paste, some log, or similiar, to make more sense into this.

Thanks in advance!

---

### Post by .gurkburk on 2008-03-25
shameless bump since it had fallen to the 4th page...

---

