---
title: "Setting up wireless at school."
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by phantommullet67 on 2011-01-05
Just got a my first netbook.  Came with windows 7 basic . . .decided i would try out the new netbook remix instead.  I have had some linux experience in the past, but i'm pretty darned rusty.  Currently, i have it installed on my flash drive to make sure I like it before I wipe my hard drive.  

I had no problem connecting to my wireless network at home, so there are no driver issues.  My school network has tutorials for setting it up on Window, mac, android, and iphone, but of course; NO LINUX.  Following are the instructions for setting it up on Windows 7 with screenshots.  I tried to get all the settings out of as I could, but I still can't get it to connect.  

[http://www.uc.edu/content/dam/uc/ucit/docs/helpdesk/SecurewirelessWindows7SetupInstructions.pdf](http://www.uc.edu/content/dam/uc/ucit/docs/helpdesk/SecurewirelessWindows7SetupInstructions.pdf)

Help would be appreciated, as the help desk knows nothing of Linux.

---

### Post by PatchesTheCaveman on 2011-01-05
In the *Wireless Security* tab of your wireless connection, set the following settings:

**Security:**  WPA & WPA2 Enterprise
**Authentication:**  Protected EAP (PEAP)
**Anonymous identity:**  *<leave blank>*
**CA certificate:**  *<leave at (None)>*
**PEAP version:**  Automatic
**Inner authentication:**  MSCHAPv2
**Username:**  *<your username>*
**Password:**  *<your password>*

That works at my university that has a similar setup.  You'll probably get a few CA certificate errors when you log in, which you can safely ignore.

---

### Post by phantommullet67 on 2011-01-06
those are the same settings i was using, but luckily it worked this time.  I think the only thing i did differently was telling it not to remember my name and password.

thanks.

---

