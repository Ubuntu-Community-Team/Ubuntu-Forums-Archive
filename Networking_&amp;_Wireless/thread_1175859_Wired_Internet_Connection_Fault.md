---
title: "Wired Internet Connection Fault"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by John C 1989 on 2009-06-01
A week in to the Ubuntu experience and I am enjoying the system, yet finding problems I have no idea on correcting.
 
My wired Internet connection has stopped working. I have connected the router to my xp laptop and it is working fine, So I have ruled out technical issues with the router. I suspect it is related to anti virus software I installed.
 
Last night I installed a ClamTK virus scanner. It seemed to be working fine alongside firefox yet today when I boot up the machine It will not let me connect to the net. 
I have searched through add/remove program to find clamTK to uninstall it, but I cant find it to remove.
 
Help would be great.
 
Kind regards,
John

---

### Post by MichaelSammels on 2009-06-01
To remove ClamTK try this in Terminal:

```
sudo apt-get remove clamtk
```

Perhaps the software is blocking access to the net? (Which is more a firewall issue).

---

### Post by Iowan on 2009-06-01
You can check under */etc/init.d* to see if there's a link for that program, stop it, then restart/retry the networking.
Otherwise, you might check System>Preferences>Startup Programs

Oops, duplicate post

---

### Post by Iowan on 2009-06-01
You can check under */etc/init.d* to see if there's a link for that program, stop it, then restart/retry the networking.
Otherwise, you might check System>Preferences>Startup Programs to see if you can de-activate it... and worry about uninstalling it later (if deactivating it doesn't work).

---

### Post by John C 1989 on 2009-06-02
I have removed the clamTK software from my system, with the command"sudo apt-get remove clamtk". However I still can not access the internet. 
 
I have used the Ubuntu built in help. When I try to ping Ubuntu.com, I get an error message saying I cant connect to Ubuntu.com. A problem with the DNS so says the self help.
 
When I put in the network address as 91.189.94.2.9. It tries to ping but the 5 packets fail.

---

### Post by Iowan on 2009-06-02
Have you checked the network settings? **ifconfig -a**, contents of */etc/resolv.conf*...

---

