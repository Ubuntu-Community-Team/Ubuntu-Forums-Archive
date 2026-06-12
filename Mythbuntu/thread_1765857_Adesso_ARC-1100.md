---
title: "Adesso ARC-1100"
date: 2011-05-23
forum: Mythbuntu
---

### Post by Aries68 on 2011-05-23
I have the above remote that purchased from Newegg and I can't seem to get this remote to work.
Everywhere I read about this remote, ppl say it is plug and play.
But I can't seem to work out the lirc configuration.
I have even tried the hama_mce that what linked to from a post at the XBMC forums.
It would be nice if all the buttons worked but I know that may not be possible.
All I can seem to get to work are the dpad and volume keys as well as close, clear and enter keys in Mythtv.
I would like to map the keys to Mythtv commands particularly M, S, and I but more would really be nice.
I can't figure out xmodmaps, gizmo daemon didn't work either. I've tried everything I have found searching the web and after 2 weeks I'm ready to take a hammer to this $22 piece of ****!!

---

### Post by novellahub on 2011-05-24
From the information here:

[http://www.mythtv.org/wiki/Adesso_ARC-1100](http://www.mythtv.org/wiki/Adesso_ARC-1100)

It appears that you don't use LIRC for the remote.  It registers itself as a keyboard device.  Then it appears you need to modify some of the key mappings using Xmodmap.

---

### Post by Aries68 on 2011-05-24
Thank you but I read that and I can't seem to figure out Xmodmap.
I tried xbindkeys and that didn't work either.
I really wanted to be able to disconnect my full keyboard so I could most things without it, and upkeep from my main desktop no problem if I could get the remote to work.

Thanks again and sorry for my rant but after 2 weeks of no progress I was getting frustrated.

---

