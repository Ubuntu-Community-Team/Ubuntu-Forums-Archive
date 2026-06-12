---
title: "Mediatomb in 9.10"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by Xavant on 2010-04-11
I just installed mediatomb so i can share files from my pc to ps3
when i try to access my slave hdd's i get this error msgs "Error: could not list directory /media/Geimsla 2 : Permission denied"  help would be appreciated thanks :)

---

### Post by Xavant on 2010-04-11
I forgot to put in that i used this tutorial in 8.04 and it wotked fine  [https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb) , but i cant find Gui text editor to change the .XML in 9.10 :/

---

### Post by arjuntank on 2010-04-11
$gksu gedit /etc/mediatomb/config.xml

doesnt work?

---

### Post by Xavant on 2010-04-11
ok, it worked, but i still get the error code when i try to acces my slave hdd's

---

### Post by arjuntank on 2010-04-11
so is that a system wide problem or you can't access them only on mediatomb?

---

### Post by Xavant on 2010-04-11
Only on mediatomb

---

### Post by dufftime on 2010-04-11
This is typically due to permissions.  Is your external drive world readable and executable?

[http://mediatomb.cc/dokuwiki/faq:faq](http://mediatomb.cc/dokuwiki/faq:faq)

---

