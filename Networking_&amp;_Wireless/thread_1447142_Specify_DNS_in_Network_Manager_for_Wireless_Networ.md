---
title: "Specify DNS in Network Manager for Wireless Network"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Garibaldi3489 on 2010-04-05
I'm having a strange DNS problem with my wireless network at home. If I connect to the wireless network by default, Network Manager assigns my router and modem's IP addresses as the two DNS for the wireless connection. This causes my browser to behave very sluggishly as it tries to resolve the host from these (incorrect) DNS. If I go into Network Manager and manually put in my ISP's DNS:
[[IMG]http://img688.imageshack.us/img688/6498/63381928.png[/IMG]](http://img688.imageshack.us/i/63381928.png/)
it then adds those lines to /etc/resolv.conf however it still keeps my router and modem's DNS in /etc/resolv.conf as well:
```
nameserver 192.168.2.1 # router
nameserver 192.168.1.254 # modem
nameserver 68.94.156.1 # good ISP DNS 1
nameserver 68.94.157.1 # good ISP DNS 2

```

How can I force only the two ISP DNS that I manually enter into Network Manager to show up in /etc/resolv.conf? So far I've been manually commenting out the router and modem nameservers but that is not a permanent solution. Also, all other wireless networks work fine.

Thanks!

---

### Post by duanedesign on 2010-04-05
You may take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=191239"). It is a few years old but might be of some help.

Also [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/12252") provides some additional info and workarounds.

best of luck

---

### Post by Iowan on 2010-04-05
Hey, I remember that thread...
In a nutshell, if you get address by DHCP, you can edit */etc/dhcp/dhclient.conf*. If you use ***prepend*** the nameservers will appear *before* the nameservers offered by the DHCP server. If you ***supercede***, they will *replace* the nameservers offered by the DHCP server.

---

### Post by Garibaldi3489 on 2010-04-07
Thanks - I've added a supercede rule to my /etc/dhcp3/dhclient.conf and my /etc/resolv.conf is only reporting the correct DNS now! I'm guessing that this will affect any other wireless networks that I connect to though, right?

---

### Post by Iowan on 2010-04-07
> **Garibaldi3489 said:**
> I'm guessing that this will affect any other wireless networks that I connect to though, right?I suspect that's correct... :(
Would a manually configured address (connection) work at home? It'd need to be outside the DHCP range. Manual configuration *shouldn't* get DNS from DHCP server, so only what you specify *should* appear. that wouldn't affect other wireless networks - but would require you to select which connection to use.

---

