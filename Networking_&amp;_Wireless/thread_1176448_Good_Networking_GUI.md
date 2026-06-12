---
title: "Good Networking GUI?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by jmjohn on 2009-06-02
[solved]

Hey all,

I used to use the System -> Networking GUI interface for setting up different static network configurations and changing computer names, but that interface disappeared after Intrepid.

What GUI do people use to replace this?  

Thanks!

---

### Post by jmjohn on 2009-06-02
The network GUI was removed by default, but you can install it.

sudo apt-get install gnome-network-admin

Then, using the menus:
System -> Administration -> Network

And you can change the computer name via the GUI.

Also, more information about the proper way to do things here:
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
and more official links here:
[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)

---

