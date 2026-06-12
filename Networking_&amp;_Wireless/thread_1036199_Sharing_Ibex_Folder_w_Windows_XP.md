---
title: "Sharing Ibex Folder w/ Windows XP"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by PPPP on 2009-01-10
Has sharing been changed in Ibex?  I don't remember it being this difficult...here's what I've tried:

Right clicked on folder, go to Share tab, check "Share This Folder" and clicked "Create Share".  But then I get this message:

"net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. No such group."

Then I tried System -> Adminstration -> Samba.  I added the folder I wanted to share.  In Windows Explorer, I typed in my IP address and it says it can't be found?

I've also checked if samba is running:
sudo /etc/init.d/samba status
 * nmbd is running.
 * smbd is running.

Does anyone have any idea?  :confused:

---

### Post by PPPP on 2009-01-10
Oh one more thing to add.  I'm able to ping my IP from XP.

---

### Post by PPPP on 2009-01-13
Can anyone point me to the right direction?

---

### Post by Iowan on 2009-01-13
Well, it took me awhile to discover what [SID]("http://www.webopedia.com/TERM/S/SID.html") means. I presume the XP user has an account both on Ubuntu AND Samba?

---

