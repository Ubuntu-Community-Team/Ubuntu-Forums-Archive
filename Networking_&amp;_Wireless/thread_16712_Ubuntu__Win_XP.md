---
title: "Ubuntu \ Win XP"
date: 2005-02-23
forum: Networking &amp; Wireless
---

### Post by faze on 2005-02-23
i want to set \svr in my root to sahred on the network and let anyone on teh network or on the ubuntu have full permissions to this folder mostly between my win xp pc to drop mp3s onto the ubuntu pc i cnat figure out how to do this pleae help  ](*,)

is there a gui way to do this or only via terminal if its by terminal i ahve no idea how to do it im a complete n00b to linux

---

### Post by bored2k on 2005-02-23
[QUOTE=faze]i want to set \svr in my root to sahred on the network and let anyone on teh network or on the ubuntu have full permissions to this folder mostly between my win xp pc to drop mp3s onto the ubuntu pc i cnat figure out how to do this pleae help  ](*,)

is there a gui way to do this or only via terminal if its by terminal i ahve no idea how to do it im a complete n00b to linux[/QUOTE]

#sudo chmod 777 /svr ??

---

### Post by alastair on 2005-02-23
I think this is a Samba question?

You will want to install samba and samba-doc.

Then take a look at the docs - there are some pretty good "getting started" guides on how to do simple sharing.

---

### Post by Buffalo Soldier on 2005-02-23
Go to [http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking) it has guides on how to:
[list=1]
[*] configure network connections?
[*] change computer name?
[*] change computer descriptions?
[*] change computer Domain/Workgroup?
[*] access network folder without mounting?
[*] mount/unmount network folder manually?
[*] mount/unmount network folder manually, and allow all users to read/write?
[*] mount network folder on boot-up?
[*] mount network folder on boot-up, and allow all users to read/write?
[/list]

---

