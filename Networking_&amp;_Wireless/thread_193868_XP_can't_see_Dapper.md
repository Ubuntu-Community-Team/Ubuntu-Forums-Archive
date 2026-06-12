---
title: "XP can't see Dapper"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by gabbman on 2006-06-10
From my dapper desktop I can see, browse copy and past to and from my XP box.  
I have 'shared' my /home/gord folder, yet xp can not see my dapper box.
Samba and samba file share have both been installed.

---

### Post by user1397 on 2006-06-10
did you install firestarter?

---

### Post by gabbman on 2006-06-10
[QUOTE=erik1397]did you install firestarter?[/QUOTE]
If that's the firewall, NO.

---

### Post by user1397 on 2006-06-11
what does your samba conf file look like? try:
```
sudo gedit /etc/samba/smb.conf
```

---

### Post by gabbman on 2006-06-16
Is there not just a 'gui' way of doing this without editing files.  In a kde desktop it's a quick couple of clicks from the control panel.

---

