---
title: "Ubuntu Studio Error"
date: 2008-02-06
forum: Multimedia Production
---

### Post by tom_the_drummer on 2008-02-06
Hi guys,

When I boot into studio I get the following error message:

> There was an error starting the GNOME Setting Daemon.

Some things such as themes, sounds, or background settings may not work properly.

The last error message was:
Did not receive a reply. Possible causes include the remote application did not send a reply, the message bus secutiry policy blocked the reply, the reply timeout experied, or the network connection was broke.

GNOME will try to restart the Settings Daemon next time you log in

Any ideas?

Thank you muchly,


Tom

---

### Post by philc on 2008-02-06
The same thing happens to me maybe once every 10 logins. Unfortunately I don't know the cure, apart from logging out and logging back in again. It never happens a second time in a row for me.

---

### Post by wawarren on 2008-02-07
I used to have this problem in Ubuntu Studio 64 and I have completely resolved it.  However...  It's been a while and I forget exactly what I did :mad:

You can google for the contents of the message and a LOT of stuff comes up so I'm sure you can sift through most of it.  

I seem to remember it being related to a network config file of some sort, but I also remember reading about it being related to OSS sound being turned on.  

read this [https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381) and try the setting mentioned towards the bottom.  Adding "auto lo" to the file mentioned is what I did "*I think*"

---

### Post by d_in_Conduct on 2008-02-09
On my feisty system I found that the file /etc/interfaces was a little messed up.  

As root, open the file and look for duplicate entries, especially the ones starting with 'auto', or incomplete entries, or 'auto' entries in the wrong place.

---

