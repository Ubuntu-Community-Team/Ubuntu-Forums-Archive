---
title: "How do I assign group on new files?"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by Nebulus on 2006-05-07
I have set up a machine with Ubuntu (called "Ubuntubox") and made a usergroup (called "family") and created users for all family members (called "Peter" and "Ann").

Now I want Ann and Peter to be able to share files on Ubuntubox (via ssh and/or winscp).

All files are placed  in /srv/share.

My problem is that when Peter uploads a file it gets user/group peter/peter and Ann cannot access the file before it gets "chgrp family".

Is it possible to make this work without intervention?
I am thinking usermasks or something like that but I really have no clue of how to set this up.

---

### Post by gborzi on 2006-05-07
Perhaps you can do it by using family as the primary (or main) group for Peter and Ann. In gnome System -> Administration -> Users and Groups, click on the user you want to modify, Properties -> Advanced -> Main group .

---

### Post by souki on 2006-05-07
[quote=Nebulus]My problem is that when Peter uploads a file it gets user/group peter/peter and Ann cannot access the file before it gets "chgrp family".

Is it possible to make this work without intervention?
I am thinking usermasks or something like that but I really have no clue of how to set this up.[/quote] 

you can add the +s flag to the group owner:
```
chgrp family /your/share
chmod g+srwX /your/share
```

---

### Post by Nebulus on 2006-05-07
[QUOTE=souki]you can add the +s flag to the group owner:
```
chgrp family /your/share
chmod g+srwX /your/share
```[/QUOTE]

That was exactly what I was looking for.

Thanks.

---

### Post by Nebulus on 2006-05-07
[QUOTE=gborzi]Perhaps you can do it by using family as the primary (or main) group for Peter and Ann. [/QUOTE]

Thanks for the reply. Knew that one already but it would not make things work the way I wanted as I might want to make more shares in the future "owned" by other usergroups than "family"

---

