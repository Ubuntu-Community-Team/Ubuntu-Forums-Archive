---
title: "intermittent, persistent samba printing problems"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by eyrieowl on 2010-09-24
I've had persistent, intermittent problems with printing from Windows XP installations to a printer connected to an Ubuntu server which is shared via Samba.  The problem exists both from standalone XP installs as well as XP VM instances, even ones hosted on the Ubuntu machine itself.  The problem is that if the printer hasn't been printed to...in a while (I don't have any good feel for exactly how long is necessary), if I try to print to it from a Windows instance, the print job will never end up in the print queue on the Ubuntu box.  However, if I jostle Samba a bit (say, by stopping and starting it), I can resend the print job and it will work just fine.  When I'm in this state, the Windows machines can browse to the Ubuntu box and see all its Samba shares; however, attempts to actually print just stall indefinitely.  If I print from the Ubuntu box itself, however, I never have a problem, never have to, say, disable and re-enable the printer itself.  It seems Samba related, but it could also be something about the hand off between Samba and CUPS.  The printer itself is a Canon iP-4200, although I'm not inclined to believe that has much to do with the problem.  Personally, I find the problem a pain in the arshe,  However, the bigger problem is that its ones of those "ubuntu-isn't-working-quite-right" issues that causes my wife to be frustrated that I made the switch.  So for the sake of marital bliss, does anyone have any ideas?  I've seen the problem both in Karmic and Lucid.

---

