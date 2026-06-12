---
title: "WICD stopped working after update"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by david819 on 2008-12-06
Ok, I'm running 8.04 x86 on a presario f750.  It has an Atheros AR5007 internal wireless card.  The ONLY way I had found to get this wireless card to work is using: 

x86(no solutions for 64bit), 
ndiswrapper(couldn't get madwifi to work) 
wicd (if i remember correctly network manager could see but not connect)

A couple months ago update manager wanted to update WICD, and when it did (pay attention, this is where i made a huge mistake) it asked me about replacing a certain file that either I or another app had made a change to.  I was reading this at the same time I was blindly clicking OK.  Yeah, real smart.  So ever since then, I just can get it to connect without security, but not with security.  I have tried checking various settings, playing with I don't know how many different security setting combinations between my D-Link router and wicd.  

When I first boot the computer, WICD can see all the wireless networks, but not connect to mine.  after several minutes though, it suddenly goes blind and doesn't see them anymore.  If I log out and back in, it still does not see them, I have to reboot the computer.  If I set the router to "open system" I can use it just fine, but I cannot find a security setting that works.  If there is any information that would help someone help me, please let me know.  anything I can do to get this computer working wirelessly without my neighbors (apartments) logging on too would be nice.

Thanks in advance for any help received.

---

### Post by david819 on 2008-12-07
Posting at night didn't get me a lot of people reading the thread, maybe a bump in the middle of the day?  Could really use some help.  My only other option is (GASP) vista.  (dual booting)

---

### Post by kevdog on 2008-12-07
First of all are you sure your driver is working with encryption.

I would just verify this first before assuming the problem is wicd.  I have a link how to connect via the command line in my signature.  Take a look at it, and just make sure you can establish a manual connection at the command line -- not using wicd or network manager.  (This is really what they do in the background, so the process is the same -- really it is!).  That will help me know where you problem lies.

---

