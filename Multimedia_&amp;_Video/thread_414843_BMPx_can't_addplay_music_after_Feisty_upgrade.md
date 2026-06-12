---
title: "BMPx can't add/play music after Feisty upgrade"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by abelthorne on 2007-04-20
Hello,
I've just finished to upgrade my system from Edgy to Feisty and I have a problem with BMPx (Beep Media Player). It may have been updated (as I changed the repository from Edgy to Feisty, although I don't know if there has been a new version of the software recently).

While I had Edgy, I added some albums to BMPx. Most of them were ripped recently directly from my CDs, in OGG format, with correct tags added. All played in Edgy.
After the update to Feisty, I launched BMPx and double-clicked on one album to play it and the program crashed. Thinking it was a random crash (I think this player is considered beta software), I tried again. It crashed again. Looking closer, it seemed that although ll the albums list was correct, the songs list when selecting one was grayed out. Looking through the preferences, I saw that I had an unknown device listed in the media library, unmounted and pointing to a strange path. As I couldn't remove it, I tried to remove all my albums from the library. After that, the device isn't listed anymore but I can't add my albums back to the library : for each song added, I get an error message "no HAL information available for this file".

What is happening and why can't I add my music anymore ? :( 
I wanted to reset BMPx settings and see what happens, but I can't find its user directory (no .bmpx, .beep-media-player or such in my home dir).

---

### Post by groggyboy on 2007-05-09
i have a similar problem with BMPx - sucks, cuz i like the app!  in my case, i installed bmpx to a fresh feisty installation.  scanning my collection resulted in every single song coming back with the same error about "No HAL Volume/Device Information for this file" - 1500+ songs scanned, and not a single one added to my collection!

it's just a shot in the dark, but do you by chance have your music on an lvm partition?  i do.  i think it would explain all the HAL errors, and the unknown device crap...

---

### Post by abelthorne on 2007-05-09
I don't know what a "lvm" partition is.
I have a single partition for my system (Ubuntu, no other OS) and a partition for swap. The disk has been partitioned automatically by Ununtu Dapper installer monthes ago.
My music is in a subfolder of my home folder.

I found a message from a person that has a similar problem on the BMPx forums. It seems that it comes from a compilation option and the solution is
a) compile BMPx yourself
b) wait for an updated version
c) use another music manager & player

Personally, I removed BMPx and switched to Amarok. I'll wait for an updated version of BMPx.

---

### Post by groggyboy on 2007-05-09
well, i guess that's that.

maybe i'll try compiling it then.

---

