---
title: "Networking file shares between dif. OS's"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by surelock22 on 2009-08-21
Howdy.

My step daughter got an early Christmas present yesterday when her grandfather bought her a 'netbook. I haven't gone through the details of what the specs are yet, I do know that he paid something to the tune of $500 or more at one of the local electronics places. Now I'm pretty damn sure it's gonna be running Vista out of the box. And my other laptop runs XP. My main, ultra large, kick *** desktop computer (well it was a year ago) runs Ubuntu. That's connected to the router directly. What can I do to be able to share files between the three machines OUTSIDE of using a flash drive (c'mon, I'm cooler than that).

If I was using XP for all my PC's, I could figure it out. I've done that. But I haven't been able to share files via Ubuntu, XP and Vista, and I'm keeping Ubuntu on the main PC because it's just plain ol' cleaner.

Appreciate the help.

---

### Post by cgb on 2009-08-21
Ubuntu is actually about the same as sharing files with XP.  You can simply create a folder, then right click on the folder and select sharing options.  Then select Share this folder and either turn Guest access on or create accounts on your computer for the users that need to be able to access the shares.  

Same pretty much applies in XP.  You create a folder, right click and select properties and then click on the sharing tab.  Again with XP you need to create a user account for all other computer users you wish to share with or enable the guest account for passwordless access.  

Hope this helps...

---

### Post by cariboo on 2009-08-21
For the Windows computers to communicate with your Ubuntu computer, you will need to install Samba. [This]("http://ubuntuforums.org/showthread.php?t=202605") is one of the better howtos.

---

### Post by jonpz on 2009-08-21
setting up a samba share is pretty dead simple even if you've got to manually configure your smb.conf file, but in recent versions of ubuntu it's even easier as all you have to do is right-click on a folder in nautilus and click on Sharing Options... really self-explanatory from there.

---

