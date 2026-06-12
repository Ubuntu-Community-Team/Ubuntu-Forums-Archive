---
title: "No sound after restarting"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Azslande on 2007-07-19
I was trying to boot up HL2 to wine and It froze, and got stuck in an infinite sound loop. So I Alt F1'ed and ended the program, but the sound loop remained. I had to totally reboot my PC to make the sound loop stop. Now I have no sound what soever. Anyone have any ideas?

My soundcard is a Turtle Beach - Montego DDL

lspci gives me the following "02:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)"

I know the chipset is C-Media.

---

### Post by Azslande on 2007-07-19
Fixed it myself... For anyone in need of help with this topic for future reference.

I had to go into my BIOS, and disabled my onboard soundcard (Comes with my Nvidia chipset), so that Ubuntu would allow my other card to take back over.

---

