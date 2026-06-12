---
title: "Turning on the sound"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by JanvL on 2006-01-15
Hi all

It all depends whether your soundcard is detected OK.
After installing Ubuntu you should give user "root" a password
that you know, so you can enter your system as the superuser root.

Mind that you even have to allow that root enters the system in the Graphical
user environment, I know some oppose to it but I am lazy enough to
want to mouse-around even as root.

When you have the account root so that you can enter the system as root
in the grafical environment, then log in as root. If you hear your sound the card is OK.

Then go to "Systemtools" - "users and groups" select your user, choose
properties, choose the Tab "userrights" there the second choice is the
soundcard, and allow yourself to have some sound!

After that log off as root,
log of as the user that you changed it for and 
log on again,
then you will have your sound.

It sounds complicated, but it is not.

Jan

---

### Post by amohanty on 2006-01-15
Actually, just using (Gnome only) System->Administration->User and Groups (Enter your password for sudo op)->Select User->Click Properties->Goto User Privileges tab->Check Use AUdio Devices will do the same for you.

AM

---

