---
title: "FIX for video drivers on VIA mini-itx platforms..."
date: 2008-02-06
forum: Mythbuntu
---

### Post by Flecko on 2008-02-06
So, I recently switched to Mythbuntu from Knoppmyth(as, at the time, Mythbuntu was not released, and no other distro's supported my hardware) and I really like what I see.

I am running a frontend/backend on a VIA mini-itx board with the CN700 chipset. As some of you may know, this is not the ideal board for Myth, but stick with me. Mythbuntu(and I believe Ubuntu Gutsy also) will use the Vesa drivers by default. This isn't going to work for Myth, so in order to fix it, you need to follow these steps:

 - install xserver-xorg-openchrome (or whatever the package is called...its very similar)

 - install the mesa-dri package (similar name)

 - change xorg.conf to use the 'via' driver instead of 'vesa'

 - reboot

All should be well now. I had this problem, and couldn't find any help on the forum, so I thought I'd share my fix for anyone trying a mini-itx board.

---

### Post by drbisio on 2008-03-12
Hello,

do you have tv-out working with openchrome??

byebye!

---

### Post by Flecko on 2008-05-21
Just for the record, I have not tried TV-out...and this no longer works with 8.04.

I will update with more progress as it occurs.

---

