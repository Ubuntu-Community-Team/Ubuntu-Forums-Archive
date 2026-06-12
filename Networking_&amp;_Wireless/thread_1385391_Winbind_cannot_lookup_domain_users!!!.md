---
title: "Winbind cannot lookup domain users!!!"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by pieter96 on 2010-01-19
hi,

ubuntu 8.04 is running fine in our network with xp clients and samba 3.0.28

we would like to give remote acces by VPN on their desktop and PPTP on our server.

so I installed winbind and also joined the domain.

but I cannot get winbind to authenticate my remote (samba) users.

does anyone know how to do this ?

here are some error messages

 > [SIZE=2][COLOR=Black][FONT=Verdana]domein winbindd[8136]:   idmap_init: Ignoring domain INTRANET2[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=Black][COLOR=blue][FONT=Verdana]Winbindd lookupname failed to resolve INTRANET2+vpn into a SID! [/FONT][/COLOR][/COLOR][/SIZE]
[SIZE=2][COLOR=Black][FONT=Verdana]Error looking up domain users[/FONT][/COLOR][/SIZE]  [COLOR=Black][FONT=Verdana][SIZE=2]create_builtin_users: Failed to create Users[/SIZE][/FONT][/COLOR]


I hope someone can help me 

thanx !

Pieter

---

