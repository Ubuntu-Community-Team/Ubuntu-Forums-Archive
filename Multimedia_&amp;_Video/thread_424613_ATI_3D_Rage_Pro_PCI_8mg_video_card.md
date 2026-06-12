---
title: "ATI 3D Rage Pro PCI 8mg video card"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Chappy7777 on 2007-04-26
I just got an upgrade machine, from my old P2-333 to a AMD Duron 1Gig. Also has 1 Gig DDR Ram. What it doesn't have is a descent video card. It came w/an S3 2mg card. Looked ok on XP that came on the HDD. I found an old ATI 3d rage PCI card that is working fine in XP. The hangup is it only has 8mgs memory.

Will this card work with Dapper version 6.06? I know I can install and find out, but before I go thru that, I'd rather get a definitive "yes" or "no" answer from someone here.

As I said, the card is working and looks fine in XP. I have no plans on using my Linux Box for graphic work. My prob is I live to far from a town to go and grab some kind of Geforce (lower end) card. For some reason I can't get my TNT 2 Ultra that was in my old Linux Box to work in the new one. It's AGP and the machine doesn't see it for some reason. I have already gone into BIOS and enabled AGP, so that isn't the prob. The card does work in the old P2. Beats me.

Point: Will this card work with Dapper version 6.06? I know I can install and find out, but before I go thru that, I'd rather get a definitive "yes" or "no" answer from someone here.

Thnx, Chappy

---

### Post by r.k.maroon on 2007-04-27
What I can say is that I've used Rage (agp and pci) cards on debian, freebsd, openbsd, slackware and redhat - all flawlessly.  In fact, I've found that these old cards are excellent desktop-cards with great visual acuity.  8mb is fine for regular desktop use.

I haven't tried these cards with Xorg, however, only XFree86.  The 'ati' driver *should* work fine, though.

Check your X configuration with the TNT2 card, it might just be the Device stanza that has the wrong setting.  Or run 'sudo dpkg-reconfigure xserver-xorg' (or whatever xserver-* you use). 

Hope that helps some little maybe
/ RK

---

### Post by mr_lars on 2007-04-30
yes, is's running now under xubuntu but works since 4.10

---

