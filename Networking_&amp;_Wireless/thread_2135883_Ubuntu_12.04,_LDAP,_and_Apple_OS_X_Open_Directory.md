---
title: "Ubuntu 12.04, LDAP, and Apple OS X Open Directory"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by hateborne on 2013-04-15
Evening ladies/gents,

I have run into a bit a mess. I am trying to get three Ubuntu boxes to authenticate against an Apple OS X Open Directory (specifically 10.6.8). I am trying to see if it is possible to allow a networked user to log in one of the ubuntu boxes as himself/herself in the directory (i.e authenticate against). After numerous botched attempts, I am simply reinstalling the ubuntu box again (the system was installed, patched, restarted, and then hours poured into LDAP failings). This leads us to the present. Is it possible to do this with an ubuntu 12.04 system?

I would greatly appreciate any help or pointers. I have scoured through the guides below, but to no avail. I had the "**getent passwd**" and "**getent group**" pulling down a list of users, but I could not log in as any of them (either at login screen or via command line).

So...yeah....help please! Any generic configuration examples would be GREATLY appreciated. 

-Hate


[http://ubuntuforums.org/showthread.php?t=1059297&highlight=ldap](http://ubuntuforums.org/showthread.php?t=1059297&highlight=ldap)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
[http://askubuntu.com/questions/127389/how-to-configure-ubuntu-as-an-ldap-client](http://askubuntu.com/questions/127389/how-to-configure-ubuntu-as-an-ldap-client)
[https://help.ubuntu.com/community/OSXLDAPClientAuthentication](https://help.ubuntu.com/community/OSXLDAPClientAuthentication)

---

### Post by hateborne on 2013-04-18
Ok, I am able to pull down all the users via the "**getent passwd**" and "**getent shadow**". To facilitate the general combative nature of the Apple Open Directory, I created the full network path it cried about (_/Network/Servers/server.com/Volumes/nuser_hd/_), mounted the networked users directory to _/home/NUsers_, and then did a sym link to the end of the _/Network/Servers/server.com/Volumes/nuser_hd/_ so it would believe it to be correct.

If I manually mount the SMB share to the networked users folder with the credentials of the user, it will work fine. When I go to change users, I need to unmount the networked users and remount it as that user manually. Is there any way that I might be able to connect to this share and have the credentials change with the login, or possibly capture the login credentials and use them to manually mount?

```

sudo mount -t cifs //server.com/NUsers //home/NUsers -o username=hateborne,password=secrets
sudo ln -s /home/NUsers/ /Network/Servers/server.com/Volumes/nuser_hd/

```

So when logging in as "hateborne", it works great. When I go to log in as "santaclaus", it fails as it was mounted with my credentials and I don't have access to Santa's home directory. 

Any pointers, tips, or suggestions on where I should begin looking?


-Hate

---

