---
title: "Dial-Up Permission"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by Weta on 2006-05-04
Hello

I have set-up new users on our home computer, and given them all access to all user privileges except executing system administration tasks (admin).  The problem is, they cannot connect to Internet through modem devices - even though I have ticked this box (through the Users and Group tool).  The users are all members of the dialout group.  We use a softmodem, with licenced Linuxant software.  The modem connection is ppp0.  The wiki DialupModemHowto doesn't appear to help here (but I could be wrong).  I'd be grateful if anyone was able to suggest how I could give the new users access to the use the modem, without the wider system administration privileges.    Thank you.

---

### Post by towsonu2003 on 2006-05-04
No replies here yet, so just wanna give an idea, though I donno how to do that. Someone after me (who knows this) can pick up (please). 

Have a look at visudo and sudo documentations (man and online) to see how to give administrative permissions to users via sudo, but only to use "wvdial" (tool for dialing out). I believe this can be done, but I donno how to get there :) I think you can give passwordless sudo access to wvdial as well. 

doing this, if user types "sudo wvdial" it will work, but "sudo gedit" or similar won't work (will give "permission denied"). 

Let us know how it goes, and I'll add it to the wiki.

---

