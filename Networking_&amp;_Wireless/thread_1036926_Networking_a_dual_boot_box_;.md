---
title: "Networking a dual boot box ;|"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by ultratek on 2009-01-11
i have searched a lot of places and joined chat rooms  looking for a resolution:
i have my pc which has a dual boot, vista and ubuntu. can a network see a dual boot system or do i have to adjust some file? (like my oldest brothers vista laptop see my dualboot system?)
my middle brothers pc has just ubuntu and my oldest brothers pc can see it in the entire network as an icon. however both me and my middle brother from our ubuntu cannot see windows (my dad and oldest brothers pcs).
and me and my middle brother cannot see each others ubuntu under network in the file browser.

all systems can ping each other and we all can transfer files if i connect using ip we just have the problems of the systems not loading under our network neighborhoods so to say...

one other problem... my middle brothers unbuntu when seen from xp or vista cannot be logged into(to the share) when you enter his user name and pwd for.
we are all on the same workgroup name
can anyone help me?
thanks=)

---

### Post by ultratek on 2009-01-11
anyone have any ideas?
thank you for your help=)

---

### Post by superprash2003 on 2009-01-12
well for that you need to add a samba user and place it in the /etc/samba/smbusers file.. read step 2 of this [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) ..create a user with whichever username and password you wish to enter to connect to the shares..

---

