---
title: "Unwanted automatic wireless connection"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Casey797 on 2010-01-03
I'm new to Ubuntu so bear with me.  I installed 9.10 from a CD and it looks fine and works OK wired.  However, my wireless keeps picking up a connection at home via my Linksys router that is not mine and I can't get around it, blacklist it or delete it.  No matter what I do it keeps showing back up as an AutoConnection.  It is the same type of router as mine but the security is different (I use WPA-Personal and the offender is WEP).  How can I permanently block\disable\etc the extra connection? I can't get on my home network until the bad autoconnection is gone.  Thanks!

More info: I use an IBM R40 into which I installed a Toshiba mini-PC wireless card.  I know it works as I have used it to connect to other wireless networks other than my own.  I prefer to leave my router configured as it is due to other users at home and the configs I use for them.  I read about WICD if that is a possibility, but actually connecting wirelessly is not the issue.

---

### Post by slooksterpsv on 2010-01-03
I had this same problem on my Netbookt, you can go in and specify which Wireless connection to always use via System > Preferences > Network Connections.

The settings that you can specify are all there, let me know if you need help.

---

### Post by Casey797 on 2010-01-04
I have looked at Network Manager previously and have been unable to modify or delete the connection that is giving me the problem.  I can manually add my home connection there but the bad one seems to override anything I do.  If I try to modify it, i get no choice to save the changes (the Save button is grayed out).  If I go into Terminal, I can see it in IWCONFIG but do nothing else beyond that.  I'm stumped at this point and I have not been able to find anything close during my research of the problem. I figure that the connection is stored somewhere and IWCONFIG just brings it up to view.  I tried to blacklist it by name and alias and it still shows up.  None of my other home devices (multiple PC and Mac laptops, iTouch, iPhone) are having problems.  I appreciate the help!

---

### Post by Warren Watts on 2010-01-04
> **Casey797 said:**
> I can manually add my home connection there but the bad one seems to override anything I do.  If I try to modify it, i get no choice to save the changes (the Save button is grayed out).  If I go into Terminal, I can see it in IWCONFIG but do nothing else beyond that.

Perhaps its a permission related issue?  What if you run the network manager as root?  Is the button still grayed out?

---

### Post by Casey797 on 2010-01-04
Tried that.  The rogue connection returns.  By the way, does root have a password (embedded?) other than the one I used when I loaded the system?  I don't seem to have rights that I think I should. I would think that I should be able to find and delete the config for the recurrent connections and also to be able to block it from returning, especially as an autoconnect.  I've been a Mac\Windows guy for many years (I mean since the early 1980's) so my Linux\UNIX skills are rudimentary but I intend to correct that.

---

