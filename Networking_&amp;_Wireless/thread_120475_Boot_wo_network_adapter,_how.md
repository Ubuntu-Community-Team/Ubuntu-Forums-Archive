---
title: "Boot w/o network adapter, how?"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2006-01-21
Hi all. I want my PC to boot with the adapter eth0 switched off on boot. I would like to be able to have an icon or something to start and stop networking, just like in KDE, where I had a little plug in the system tray, and when I clicked on it, my PC connected to the internet and when I clicked again, the connection was closed. I am using GNOME. Is there something similar? How could I achieve this?

---

### Post by ubuntuuser on 2006-01-23
Anyone got an idea?

---

### Post by ashrack on 2006-01-23
use [this guide]("http://ubuntuforums.org/showthread.php?t=89491&highlight=boot") to disable NETWORK from booting up.
and then once in desktop create a luncher with the code:
```
/etc/init.d/networking start
```

---

### Post by healychan on 2006-01-23
Modify your /etc/network/interfaces file

Remove the line "auto eth0" will disable eht0 when start up

---

### Post by Lambert on 2006-01-23
healychain is correct, just simply remove the auto eth0 line from the interfaces file.

I don't know of an applet that does what you want but you could write a simple script that brings up and activates the interface and another that reverses this. Then add a custom application launcher applet to the panel that runs the scripts.

I'm not that good with scripts but believe something like this would work. Maybe somebody else can help out here or know of something better.
```

#!/bin/bash

ifconfig eth0 up
wait 2
dhclient eth0

``` 
Put it in a folder of your choice, change the permissions of it then right click on panel, add to panel, custom application launcher.

Repat only make script look like this

```

#!/bin/bash

ifconfig eth0 down

```

---

### Post by ubuntuuser on 2006-01-24
Thanks to you all.

---

