---
title: "auto dial kppp and novatel 760 broadband"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-03-31
I have a Novatel 760 broadband USB device and I use kppp to connect though it is extremely slow (ping takes 100ms).  What I need is a way to make kppp connect on reboot without any interaction from the user.  I have looked on the Internet, but I did not find anything useful.  

I am using kppp because I could not get gnome-ppp to connect and it does not seem to have the features of kppp.

---

### Post by Z.K. on 2011-03-31
> **Z.K. said:**
> I have a Novatel 760 broadband USB device and I use kppp to connect though it is extremely slow (ping takes 100ms).  What I need is a way to make kppp connect on reboot without any interaction from the user.  I have looked on the Internet, but I did not find anything useful.  

I am using kppp because I could not get gnome-ppp to connect and it does not seem to have the features of kppp.

Never mind, I figured it out.  I just added arguments to the autostart program like "kppp -c "connection name".  Now, when it boots, it dials out automatically.

:P

---

