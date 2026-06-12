---
title: "Networking breezy to windows."
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by woedend on 2005-12-22
Hi guys, I've never networked before across computers.  Basically, I have 3 computers, a winxp, a win2000, and a breezy(well dapper but point taken).  I want to be able to share files through the router among computers - is that possible and if so can you point me in the right direction?  I'd also like to be able to use the printer on the win2000 machine.  Thanks a lot for any and all info to get me started.

---

### Post by darth_vector on 2005-12-22
hi,

you will want to look at installing samba if you want to share files between linux and windows. there are many howto's and a wiki entry on this. have a look around.

is the printer a network printer or is it connected to one of the machines? if it is a network printer then you should be able to share it without any hassles and without adding any software. if not, i think samba is probably your best bet again.

good luck! :)

---

### Post by woedend on 2005-12-22
thanks vector.  assuming i get samba set up, what about on the windows machines?

---

### Post by afhp on 2005-12-22
To put it simply, samba is a free implementation of what Windows uses for networking. In other words, once you get it up and running you'll see your Linux machines (1) from Windows, and your Windows machines from Linux.

(1) Samba comes in two parts: the client, and the server. 
If all you want is to "see" your Windows machine from your Linux one, the client is all you need. If you want the Windows machines to see the Linux one, you'll have to install and set up the samba server as well.

---

### Post by woedend on 2005-12-22
cool - using samba i can now access my own hard drive from the XP machine.  But for the life of me I cant figure out how to view the windows machine from here.  Is it all done in command line or is there a way I can access other machines files in nautilus?

---

### Post by woedend on 2005-12-22
ok good good.  closer now.  I can see all 3 computers from the 2000 machine, I can see the XP from my ubuntu, but I cannot see the 2000 from my ubuntu.  Kinda weird.  I set it all up right, I dont know if its not broadcasting right or im not picking it up right.  Im on the right path though.

---

