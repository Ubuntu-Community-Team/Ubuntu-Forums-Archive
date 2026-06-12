---
title: "verizon wireless on 8.1"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by bounce. on 2009-04-10
It seems that it is possible to get the verizon wireless modem to work in ubuntu, but I don't quite know where to start.
In this thread [http://ubuntuforums.org/archive/index.php/t-1024653.html](http://ubuntuforums.org/archive/index.php/t-1024653.html) it seems that set-up is fairly automatic (last post by don1500).

Perhaps it's not working for me as I'm using the xubuntu version? My network connections doesn't have verizon as a provider.

I would much appreciate it if anyone could help, or at least point me in the right direction.

Details:
The device is UM150, and seems to show up on my machine's usb as
```
Bus 003 Device 002: ID 106c:3711 Curitel Communications, Inc.
```
I'm running the stable version (8.10?) with xubuntu

---

### Post by bounce. on 2009-04-11
Definitely nothing to do with xubuntu. I switched to the gnome desktop and it uses the same network application, with no way to add wireless broadband for verizon.

---

### Post by bounce. on 2009-04-11
The closest I've gotten yet is using wvdial, and following instructions found here: [http://forums.fedoraforum.org/archive/index.php/t-195453.html](http://forums.fedoraforum.org/archive/index.php/t-195453.html)

It is possible that I'm not getting a signal, would the following be the error one would expect?
```

--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> The PPP daemon has died. (exit code = 19)
```

I used the following, which seem to be accurate.
Username = vzw
Password = <my 10 digit number>@vzw3g.com
Phone: *99#          (also used #777)

Anyone have any suggestions?

Thanks.

---

