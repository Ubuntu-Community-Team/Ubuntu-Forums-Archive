---
title: "nm-applet won't start as normal user"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Twiggy794 on 2006-06-02
I've got network-manager-gnome installed, and my gnome session properties has 'nm-applet --sm-disable' in it, but everytime I load Gnome nm-applet doesn't start.  If I try to start it with ```
# sudo nm-applet
``` it works fines.  But when I try to start it manually with ```
# nm-applet --sm-disable
``` I get this error: ```
** (nm-applet:6933): WARNING **: 
<WARNING>	 nma_dbus_init (): nma_dbus_init() could not acquire its service.  
dbus_bus_acquire_service() says: 'Connection ":1.7" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" 
due to security policies in the configuration file'

``` Any ideas?

---

### Post by s31523 on 2006-06-02
I had a similar problem, maybe the same?  See my original post:
[http://www.ubuntuforums.org/showthread.php?t=185526&highlight=network+manager](http://www.ubuntuforums.org/showthread.php?t=185526&highlight=network+manager)

Hope this is it!

---

### Post by Twiggy794 on 2006-06-02
Already looked into that, this seems to be a permissions problem with dbus.

---

### Post by alecubero on 2006-08-05
to solve the problem posted in the last message you need to add the user who want to use NetworkManager to the group netdev, also the interfase needs to be set as auto in the /etc/network/interfase configuration file.
I solved this problem reading the info in /usr/share/doc/network-manager, there you'll find a complete explication.

---

### Post by Twiggy794 on 2006-08-06
I tried this, but it didn't help.  Though I had no netdev group so I created one.  Could you pass along the permissions for your netdev group?

---

### Post by poolee on 2006-08-21
Hello. Try this: 
```
sudo apt-get install --reinstall dbus dbus-1-utils
```

---

