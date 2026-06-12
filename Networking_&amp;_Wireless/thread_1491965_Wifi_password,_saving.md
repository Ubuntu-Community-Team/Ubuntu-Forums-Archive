---
title: "Wifi password, saving"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by mawil1013 on 2010-05-24
Wow!Through the years and I mean years. I have loaded ubuntu's many version's then within days uninstalled it after a long yawn. Well folks, I installed the latest greatest and guess what, a week later it's still on my pc and i'm loving it! Way to go! This may be the one i completely switch to!!! :KS

What I have is a minor issue, i'm having to re-enter the password for my wifi after closing and then reopening the laptop lid. How do I get ubuntu to permanently save the password?

UPDATE: Here's is what I gues/think happened. When I installed ubuntu (wubi install) I set up a user name and password was set up to ask for password when rebooting. At first the wifi password stayed saved but it seems that after I went in and set up not to ask for USER password after reboot, that the wifi password kept having to be re-entered after reboot, sooo, on a whim I reset to ask for user password after reboot and the first time wifi didn't ask for me to enter it's password. I will come back if this changes but let me suggest that if you are frequently being asked by ubuntu to reenter your wifi password, set up your main user name to ask for a password!?  

By doing a few Google searches this seemed to be a common problem.

Update 3: OK now, been a couple of days and wifi never once asked for password since setting up ubuntu to once again ask for user password at start up, sooo for me,, for now all is well.

---

### Post by mawil1013 on 2010-05-24
:popcorn:

---

### Post by kenbuntu75 on 2010-05-25
I am running 10.04 and I have only recently been having this problem, just the last few days. For now I have just placed a text file with the password for a quick copy/paste. I was thinking about disabling and re-enabling the wifi connection to see if that fixes it but I'll be trying that later and I'll post the results.

---

### Post by b k on 2010-05-25
> **kenbuntu75 said:**
> I am running 10.04 and I have only recently been having this problem, just the last few days. For now I have just placed a text file with the password for a quick copy/paste. I was thinking about disabling and re-enabling the wifi connection to see if that fixes it but I'll be trying that later and I'll post the results.
 
If the symptoms of your problem are similar to post #10 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883) , see the end of post #3 of that same link for the solution (it is actually what mawil1013 is saying at the end of post #1)
 
Hope the info is helpful

---

### Post by kenbuntu75 on 2010-06-03
> **b k said:**
> If the symptoms of your problem are similar to post #10 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883) , see the end of post #3 of that same link for the solution (it is actually what mawil1013 is saying at the end of post #1)
 
Hope the info is helpful

Thanks for your reply. After checking System>Admin>Login Screen the box for "Automatically login as" was already unchecked. However, this seemed to work for my last few boots. 

UPDATE: FIXED!
Go to Network Connections (icon, upper right)> right click> Edit Connections> Wireless tab > (Chose my wireless connection) > Edit > 
Check box for auto connect > in wireless security tab, entered my passphrase in the appropriate box > restart 

It saved it, and I was able to login at my next boot up.:popcorn:

---

