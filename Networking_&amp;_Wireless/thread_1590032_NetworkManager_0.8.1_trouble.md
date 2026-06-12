---
title: "NetworkManager 0.8.1 trouble"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by exFalso on 2010-10-07
Hey there, linux newbie here.

I've seen NetworkManager 0.8.1 has command line support, so I figured I'd upgrade it. I compiled it from source(NetworkManager and nm-applet), and it seems to run fine(no error messages when it starts up, and it displays all nearby wireless networks), however when I try to connect to any network it says 
Error: Connection activation failed: No user settings service available

Any ideas?

thanks
exFalso

---

### Post by P4man on 2010-10-07
Just a wild guess.. you need to run it with admin privileges? Try putting "sudo" in front of your command.

---

### Post by exFalso on 2010-10-07
> **P4man said:**
> Just a wild guess.. you need to run it with admin privileges? Try putting "sudo" in front of your command.
NetworkManager runs by default with root priviliges. Running nm-applet with sudo gives same error...

---

