---
title: "no network notification for all users"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by ttremeth on 2010-09-09
I am a very new user of the netbook addition  10.04 I am not sure why but only the first user to logon gets the network notification icon. Is this normal, because on my eee pc 1000h all function keys work except the network function on subsequent logons.

---

### Post by grahammechanical on 2010-09-09
I can only give you a guess. I use a desktop machine and I am the only user.

It is possible that the other users on your machine are not allow network access.

Go to System >Administration>Users and Groups. Select each user in turn. Click on Advanced Settings. Look at User Privileges and see what your other Users are allow to do. You will need your login password to do this as this is an administrator privilege.

Or, Right click on the Network Manager icon. Select Edit connections. Select the connection method that is being used. Click Edit and make sure that Available to All Users is checked. You will need your login password to access the settings of the wireless connections. This is less secure than the other method.

This is the way the Linux and Ubuntu secure your computer and network access from unauthorised use.

I hope this helps    Regards

---

