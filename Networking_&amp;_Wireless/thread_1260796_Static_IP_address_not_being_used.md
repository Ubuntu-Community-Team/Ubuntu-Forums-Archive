---
title: "Static IP address not being used"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by rabinski on 2009-09-08
Hello another Ubuntu noob signing in.

I have a wired connection using a static ip address setup through Network Manager 10.1.1.11 but when I do an 'ip address show' it reports 10.1.1.136

Any ideas no how to get it to use 10.1.1.11

Thanks

---

### Post by aiharak on 2009-09-08
try assigning a static ip address through the router's configuration menu

---

### Post by rabinski on 2009-09-08
I realy dont want to touch the router as its working fine and managed by a 3rd party.

---

### Post by Iowan on 2009-09-08
**ifconfig -a** will probably show the same results. Do you have multiple configurations via NM - or did you modify **Auto eth0**?

---

### Post by demiurg on 2009-09-08
I would advise you to avoid using network manager. It is not stable enough and there is no reason whatsoever to use it with wired network cards.

---

### Post by Iowan on 2009-09-09
I must be one of the lucky ones - Jaunty's Network Manager seems to work MUCH better than the two previous versions.  It handles my Wi-Fi and wired access without problems (so far), but I've yet to set up a secure wireless link at home.

---

### Post by uylug on 2009-09-09
Have you tried configuring your interfaces by editing your /etc/network/interfaces file?

---

### Post by dbalascak on 2009-09-09
There are 2 places where network interface config data is kept with a default install. 
1) */etc/network/interfaces*. 
2) */etc/NetworkManager/system-connections/*AUTOXXYYZZ 
If you are using NetworkManager ( the icon on your task bar) to do your configuration then */etc/networks/interfaces* should be fairly clean, like this. 
```


auto lo
iface lo inet loopback


```

To disable the NetworkManager and use the */etc/network/interfaces* file, set the following in the */etc/NetworkManager/nm-system-settings.conf*. NOTE If you do this, it clears resolv.conf.
```

[ifupdown]
managed=false

```

Keep only one of the two areas populated with config info. I too have found NetworkManager to be stable.  I have configured  WEP keys in Network Manager.

---

