---
title: "any type of network gui?"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by opfeld on 2012-07-14
Is there any type of GUI that will walk me through settings up a simple network between two linux computers connected via cat5 cable and router?  I have been trying ssh and samba and I haven't gotten anywhere

---

### Post by Cheesehead on 2012-07-14
A network to do what?

For example, if all you want to do is move files from A to B once, ssh is perfectly good for that.
However, if one is a webserver visible to the internet, the setup is quite different.

---

### Post by bobmct on 2012-07-14
One thing you might want to look into is a program called "webmin" which provides a web based interface to your system configuration.  You can view/download it from [www.webmin.com](www.webmin.com) and it works like a charm.  In most cases even better than the provided gnome/kde config programs.

Good luck :D

---

### Post by Kirk Schnable on 2012-07-14
> **opfeld said:**
> Is there any type of GUI that will walk me through settings up a simple network between two linux computers connected via cat5 cable and router?  I have been trying ssh and samba and I haven't gotten anywhere

It sounds like you're trying to move files from one Ubuntu computer to another.

You can do so with an SSH server.  Simply install the SSH server from apt.

```
apt-get install openssh-server
```

On the client computer, you should be able to open your file manager (Nautilus) (go into your Home folder, or any other folder).

Hit CTRL+L, this will make the "Location" an editable text box.

Type:
```
ssh://ip.of.your.pc
```

If you don't know the IP of your PC, you can get it by running:
```
ifconfig
```

It should prompt for username and password after you hit enter.

Kirk

---

