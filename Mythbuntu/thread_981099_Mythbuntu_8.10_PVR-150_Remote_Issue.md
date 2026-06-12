---
title: "Mythbuntu 8.10 PVR-150 Remote Issue"
date: 2008-11-13
forum: Mythbuntu
---

### Post by J.H. on 2008-11-13
Hello, I'm trying to find some advice regarding a weird remote issue with Mythbuntu 8.10 and my PVR-150 remote.

This remote worked fine before, and I recently upgraded my system from 8.04 to 8.10. After the upgrade the remote no longer worked.

I set up LIRC and the remote again, and the remote works fine if I run IRW in a terminal (I see output corresponding to the correct buttons when I push them on the remote) but it no longer works with the MythTV front-end, I get no response from the remote.

I've spent the last couple of days re-checking the lirc configuration and lircrc, and checking online to see if anyone else is having this issue. I'm at a loss. Any suggestions or an idea as to what I'm missing?

---

### Post by Chuffinora on 2008-11-13
I think I have the same problem.   I not running Mythbuntu, but am running Myth 0.21 and have remote problems after upgrading to Ubuntu 8.10.

Initially my remote did not work at all.  By using the installing and uninstalling LIRC then folowing the instructions at [www.blushingpenguin.com](www.blushingpenguin.com) I have my remote working - mostly.
I can select menus, recodings etc.   BUT it does not recognize channel change in live TV (Nor does my channel change for recording)

(I posted my problem here [http://ubuntuforums.org/showthread.php?t=980304](http://ubuntuforums.org/showthread.php?t=980304) )

At this point my best guess is that there could be some problem with Ubuntu loading the firmware,  but I am not sure where to look.

Sorry it does not help you very much.

---

### Post by J.H. on 2008-11-13
Thanks for the reply.

I'll go through the guide from the blushingpenguin site and see if it helps at all.

---

### Post by J.H. on 2008-11-14
UPDATE:

I loaded the lirc package from the blushingpenguin site, and the remote now works with the frontend, however some of the buttons still have issues. I'll have to check the lircrc file and see what I need to fix, but at least it's working with the frontend.

---

