---
title: "Keyring Manager"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by stretch427 on 2009-05-05
Whenever I start my computer the message comes up for me to enter a keyring password, which I do and it works fine. But first, I don't really know what it does, and second is there anyway to edit the /usr/bin/nm-applet file to make it accept the password automatically?

Just kind of an annoying start up thing. That's all.

Thanks!

---

### Post by cguy on 2009-05-07
Apparently you have a network connection which requires a password, which is stored in the keyring.

Because you use autologin, the keyring remains locked and that's why you get asked for the password.

THE SOLUTION: Edit your network connection so it's available to all users (you just have to tick a checkbox)




This bug is at least 3 years old so let's give it a cheer and a group hug. In only 4 years it will be school eligible :P

I wonder what's the lifespan record of a reported bug. :confused:

---

### Post by stretch427 on 2009-05-08
It actually was fixed with the upgrade to 9.04 but thank you for the response. Not sure if it was an automatic fix or just a weird coincidence. Either way it doesn't ask for a password prompt at startup so I'm happy.

---

### Post by cguy on 2009-05-09
Well, I run 9.04 and have (had) this problem, so either it's a coincidence for you or I am very unlucky (and so are many others)

---

### Post by stretch427 on 2009-05-12
Well do you still have that problem? Because now I think there is a check box that fixes that? Correct me if I'm wrong

---

### Post by cguy on 2009-05-12
> **cguy said:**
> Apparently you have a network connection which requires a password, which is stored in the keyring.

Because you use autologin, the keyring remains locked and that's why you get asked for the password.

**THE SOLUTION: Edit your network connection so it's available to all users (you just have to tick a checkbox)**




This bug is at least 3 years old so let's give it a cheer and a group hug. In only 4 years it will be school eligible :P

I wonder what's the lifespan record of a reported bug. :confused:

:)

One mod please add a poll to this thread:

> DO YOU THINK KEYRING ISSUES WILL BE SOLVED IN OUR LIFETIME?
-Yes
-No
-Maybe in 3 lifetimes
-Switch to KDE

Really, people, doesn't anyone at Gnome care about this? One can't use Evolution, Mail Notification, proper Network Configuration and many more beacause of this bug.
It's at least 3 years old for crying out loud!
The bug reports themselves are 3 years old.


NO, I don't want a null keyring password.
NO, I won't write the bug fix beacuse I don't have the skills to do it.
NO, I won't disable autologin. I want my computer to show the desktop and the desktop only.

---

### Post by pmla on 2009-07-07
lol...yes and it still goes on.

Sucks... I reading foruns dating 2007 :) with same problem

---

