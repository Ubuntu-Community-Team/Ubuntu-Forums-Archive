---
title: "VNC Corrupts Video Configuration???"
date: 2008-08-11
forum: Mythbuntu
---

### Post by Just4Fun20 on 2008-08-11
Several times, over the past year, my video drivers (NVidia GEForce 6600), or at least the xorg.conf, have gotten corrupted.  I won't be able to get any image on the TV screen.  I reboot and when the system comes up it says that it's running in a default low resolution mode.  Fixing it can be tedious, but basically I just reselect the NVidia 6 series driver and then enable the advanced functions. 

I've a couple of questions. 

First, is everything I need in the xorg.conf?  That is, if I get it all working properly and save the xorg.conf, would restoring this file "fix" all the problems? 

The second question is more difficult.  I don't really use VNC very often but I did recently use it to access the Mythbuntu box and apply updates(one unit, BE and FE, installed about a year ago with all updates applied).  I do updates once a month, or so, although usually directly on the box.  This time I used VNC.  Often, after using VNC, I have problems with Video on my TV.  The colors are wrong.  I generally reboot and everything is fine.  There was nothing different this time but the reboot gave me the "low resolution" message and the process I listed above. 

Does it make sense that VNC might be causing this problem?  Any suggestions on how to avoid it in the future (other than not using VNC :-) )?  It's possible that my xorg.conf is not complete since I've had to use an "old" backup version more than once just to get the MythBuntu box working again.  

TIA for any help.

---

### Post by timcredible on 2008-08-11
i see you didn't want to quit using vnc, but...... quit using vnc, use xdm instead, it's what you use when you login locally, so why not use it remotely?  click on my sig link for a how-to.

---

