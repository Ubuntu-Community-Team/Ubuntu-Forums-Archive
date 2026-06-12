---
title: "Samba: Machine shows up in wrong workgroup??"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by nakko on 2006-07-07
I seek the aid of a guru!
My luvverly Dapper Drake machine shows up on my local network browser as being in the "Mshome" workgroup, not the one I set it to. I have it changed in /etc/samba/smb.conf to something else, "Mynet". "Mynet" is also what's shown when I go to "General Windows  sharing settings" and look in the "Domain / Workgroup" field.

Is there anywhere else other than /etc/samba/smb.conf where this info is coming from? How did I wind up on "Mshome"? I don't even have any other machines, say, running Windows, that are on Mshome. All my other machines on "Mynet" show up as such.
Pretty mysterious. :-?

---

### Post by scxtt on 2006-07-07
have you restarted samba after changing it?

```
sudo /etc/init.d/samba restart
```

---

### Post by nakko on 2006-07-07
I...  I think that did the trick! I guess I *assumed* I must have rebooted sometime recently, but uptime proves me wrong! Hey, all's well as ends well -- I guess I am still, after all this time, used to Winders needing to shut down to take a breath of fresh air every so often.

Cool! And thanks scxtt!

---

### Post by Scoee on 2008-01-04
Brilliant.

I'm new here, but you guys on these threads are amazing.

One question now though.

How do I conect to my ubuntu box, from an XP machine - It asks me to enter name and pasword, but then hangs and does nothing.

---

