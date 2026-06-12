---
title: "All config files need .conf? Wifi Help needed"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by JohnChir on 2010-10-26
[COLOR=#2a2a2a][SIZE=2]Ok so I got driver loaded with ndiswrapper, but my wireless network doesn't appear and when I do the ndiswrapper -l I'm getting this weird message (below) anyone know how to fix this? I ran some commands regarding blacklist to no avail. Thanks.[/SIZE][/COLOR] [COLOR=#2a2a2a][SIZE=2]john@Gameroom:~$ ndiswrapper -l[/SIZE][/COLOR][COLOR=#2a2a2a][SIZE=2]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.[/SIZE][/COLOR][COLOR=#2a2a2a][SIZE=2]netmw245 : driver installed[/SIZE][/COLOR][COLOR=#2a2a2a][SIZE=2] device (13B1:0029) present[/SIZE][/COLOR]

---

### Post by chili555 on 2010-10-26
> anyone know how to fix this?It's easy. Open a terminal and copy and paste:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

