---
title: "How to file share between Ubuntu and W7"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by Bigneil on 2011-01-04
I'm struggling to file share between windows 7 desk top pc and Ubuntu 9.10 laptop. I posted the same question over on the W7 forum but i'm not making any headway yet. Have any of you guys had similar trouble file sharing and if so how did you solve the issue??

Thanks in advance   neil

---

### Post by Jose Catre-Vandis on 2011-01-04
Samba is your friend.

Check out the howto in the tutorials section by Stormbringer, works for me every time

---

### Post by anystupidname1 on 2011-01-04
Windows 7 comes with NFS tools too!

Looks like Jose wrote this: :p
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

Or SMB:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Bigneil on 2011-01-04
Thanks for your input guys i will read up on those links and report back on my progress. 

I just don't quite understand how file sharing all works. Until recently my desktop was dual booting 10.04 and XP and was i able to figure it out for both of them by bumbling about and following forum advice. But i have to admit, i am stumped by my new W7 machine, the networking seems to be dramatically different from what i have become used to.

---

### Post by Bigneil on 2011-01-04
ok, i have been mucking about with samba and have managed to get things working in reverse, in that i can use the desk top to access files on the laptop, but not the other way around. which is not useful as my aim is to be able to access files from the desk top with a laptop from anywhere in the house.  

I have been reading those links but,.. man i find it really hard to follow, there is just soooo much jargon. It's gonna take a while for me too google it all. lol


EDIT>>

Ok, ... with all the windows 7 file sharing stuff set to "YES" with the password for file sharing disabled. i still get asked for password by my 'Buntu box. I try typing in the password as provided by the windows box for "HOMEGROUP"  and nothing happens

---

### Post by PatchesTheCaveman on 2011-01-04
Hi Bigneil.  Happy New Year!

There is a bug in Samba that might be affecting you if you have Windows Live Essentials installed on your Windows system.  Microsoft sometimes installs this software as part of Windows Update, so you might not be aware you have this software.

To learn more and for a couple ways to fix it, see this thread:
[http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials](http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials)

---

### Post by Jose Catre-Vandis on 2011-01-04
> **anystupidname1 said:**
> Windows 7 comes with NFS tools too!

Looks like Jose wrote this: :p
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

Or SMB:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


Hmmm, proof of concept, ;), gave up when W7 came along as it was just too buggy for me at the time (actually worked quite well with XP). Had my trials with samba too, but now my server doles up nfs to my linux boxes and samba to the windows machines in the house (yes, I could use samba for both but I prefer nfs)

---

