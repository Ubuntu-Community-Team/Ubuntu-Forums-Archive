---
title: "openLDAP, gnome problems"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by n3ocort3x on 2013-01-20
Hey community :)

I try since 2 days to get an openLDAP server working and it works partly... but I run into a few problems and I hope some of you pro´s can help me with my problems.

Just for information:
 I setup an openLDAP Server on Ubuntu 12.04 LTS with [THIS ]("http://www.ryazkhan.net/?show=ldap12")tutorial. Everthing works as it should. I can connect via SSH (locally) without errors. I reboot the machine and the new name shows up on welcome screen (gnome) with the right name (added in LDAP). And here comes the problem:

I enter the password for the newly added LDAP user the screen goes black for 3 seconds and then I´m back to the welcome screen.

If i try to start the x server in my working ssh session i get this:

> xauth:  timeout in locking authority file /profiles/testuser/.Xauthority
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
No protocol specified
No protocol specified
xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error


I really hope someone is able to help me (It´s for a project in evening school) Thanks in advance. I also tried [THIS]("https://help.ubuntu.com/community/LDAPClientAuthentication") tutorial

---

### Post by luvshines on 2013-01-21
Are you able to login to non-LDAP user ?

For the LDAP user part, most likely missing home directory could be an issue.
Do any of the user you are trying have their home directory(as defined on LDAP) present on the server ?
If not, then just for testing, say your username is 'xyz'. Define /home/xyz as the home directory for this user on LDAP.
Then create /home/xyz on the server and chown /home/xyz for xyz```
sudo mkdir -p /home/xyz
sudo chown xyz /home/xyz
```

Then try to login

---

### Post by n3ocort3x on 2013-01-21
thanks for your reply, allready did taht. my ldap user has a seperate homedirectory (I´ve created one). I tried again the whole day to get it working but nothing I do results in success.

---

