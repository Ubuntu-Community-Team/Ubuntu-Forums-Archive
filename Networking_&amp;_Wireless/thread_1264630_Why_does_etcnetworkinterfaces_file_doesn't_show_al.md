---
title: "Why does /etc/network/interfaces file doesn't show all the interfaces.??"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-09-12
My /etc/network/interfaces file looks like this..

```

auto lo
iface lo inet loopback


```

My Internet connection is working properly... but I am a little confused about the way my network connections and interfaces are stored..

I used to think that they were saved in this file..
but apparently this doesn't seem right now..

any suggestions..

---

### Post by dbalascak on 2009-09-12
It all depends which network manager you are using. If you are using the network manager that is in the dropdown System-> Administration-> Network to config your interfaces then */etc/network/interfaces* file*/etc/network/interfaces* file will be populated.  If you are using NetworkManager, that is the icon on your toolbar, then the network config data is stored in files under */etc/NetworkManager/system-connections*.  The config data must be in only one place. If you put it in both you may experience problems with your network.  If you right click on the NetworkManager icon and select Edit Connections there should be only one entry per interface.

---

### Post by shredder12 on 2009-09-12
I think you are talking about some other version..
I am sorry I didn't mention, I am using Jaunty.

and in Jaunty the network manager is also provided in system->preferences->network ....
so the icon and this are both the same thing...

I got the information about the network settings I have done on the eth0 interface in
/etc/NetworkManager/system-connections folder
but still couldn't find the configuration file for my wireless network..

---

### Post by dbalascak on 2009-09-12
Using the same version.
```

$ ls /etc/NetworkManager/system-connections
Autoeth0  AutoTheWirelessLink


$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

```

---

### Post by shredder12 on 2009-09-12
mine shows

```
ls /etc/NetworkManager/system-connections

shared internet connection
```

this "shared internet connection" is the one I use for providing Internet connection to my Desktop...

I might have not mentioned that I get Internet access on eth1 through wireless..
and I can't see its configuration file anywhere

---

### Post by lswb on 2009-09-12
You will probably be surprised to know that Network Manager uses the gconf database to store your wireless network settings as well as some other information.

---

### Post by shredder12 on 2009-09-12
kk.. i got it..
i can now see all of the ever established wireless connections..
I then modified one of the wireless connections through the network manager and checked the option "available to all users"
this led to the creation of that wireless connections's configuration file  in /etc/NetworkManager/system-connections

So, i guess that's it.. 
By the way..  did all the previous versions of Network managers used to do the same or is this something new..

---

