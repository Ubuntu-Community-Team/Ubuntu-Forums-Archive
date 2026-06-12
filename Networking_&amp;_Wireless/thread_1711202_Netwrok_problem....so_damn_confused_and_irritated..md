---
title: "Netwrok problem....so damn confused and irritated."
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by rakz on 2011-03-21
I want to configure pppoe settings in my ubuntu 10.10. i want a dialer like the windows one. Also tell me how to change the MAC address.

I tried all this things..but not worked...linux is such a command bitch

Pls help me ppl...pls

```
sudo pon dsl-provider
ping 4.2.2.1 -c5
ifconfig -a

gksudo gedit /etc/NetworkManager/nm-system-settings.conf
managed=true
man ifconfigman

sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet manual



```

---

### Post by rakz on 2011-03-21
Please anyone help !!

---

### Post by dineshs on 2011-03-21
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by rakz on 2011-03-24
Hey, I did the DSL connections but still i am not getting the DSL option in my NM :(

---

### Post by dineshs on 2011-03-25
Did you tick [COLOR="Blue"]Available to all users[/COLOR] while creating the connection?
What is the output of ```
sudo lshw -C network
```

---

