---
title: "Dynamic mount of Active Directory Share"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by ronw69 on 2012-02-10
I have many Xbuntu clients they log on to a Active directory network  with Likewise.  All of these clients could have any of 100 different  users log on to them at any time.  I need to map the users AD share  automatically on the desktop or in GVFS places.  I have tried using the  gvfs-mount command but it calls for entering the users name and  password. I have thought of creating a bash file and using the mount  command with the USER global variable but I am not aware of a global  variable for the password.

Please help there has to be a way to accomplish this it seems so simple.

---

### Post by ronw69 on 2012-02-16
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]I am redefining the question hoping that with this wording I will get an answer.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have many Ubuntu client computers they log on to a Active directory network with Likewise. All of these client computers could have any of 100 different users log on to them at any time. I am trying to have a connected share on the desktop or in GVFS places as soon as a new user logs, this share would be tied to their user name IE:(\\server\users\username). So in order to do this the authority given to the user at login from active directory should allow the login without having to re-login to the share. If there is no way to use this given authority then is there a way to capture the user name and password so that a BASH script could be written to automatically create this share?[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by nothingspecial on 2012-02-16
Just one thread for each problem please. Feel free to bump it every 24 hours or so.

Closed.

---

