---
title: "Unable to connect to internet after hibernation or suspend on karmic"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by zecthelion on 2009-12-30
Good evening,

I am a new Ubuntu user.  My wireless was working fine on Jaunty,  but ever since I upgraded to Karmic about a month ago, I have been having problems.  

I have an EEE PC, running the Netbook Remix.  The problem is that when my computer comes out of hibernation or suspension, it does not connect to the internet.  I use Wicd, and that shows "obtaining IP address" for about a minute before giving the error message "unable to get IP address," or something similar.  If I reboot the computer it connects immediately.  If i restart networking:
```
sudo /etc/init.d/networking restart
```It works.  It's just a bit of a pain.  I'm not sure what the problem is, and it seems  like there should be an easy fix to get it to automatically connect out of hibernation.  Can anyone help?  Please?

Thank you.

---

### Post by zecthelion on 2009-12-31
Pretty please?

---

### Post by mikeg113 on 2010-01-04
I'm having the same problem with my laptop on 9.10. I have to manually reconnect to my wireless network after hibernation.

---

### Post by leandromartinez98 on 2010-01-16
I have the same problem, but restarting the network from the 
command line does not work. I would like to know if there is
some way to fully restart the network services, including the
network manager.

Also I've filed a bug here, if you want to add some information:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/461250](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/461250)

---

### Post by Julita on 2010-02-07
Sometimes I have the same problem with my wireless on UNR 9.04, and the solution is

```
sudo killall NetworkManager
sudo NetworkManager
```
then it appears again.

---

