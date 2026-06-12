---
title: "Not mounting directory with winbind"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by oj0kksn5 on 2011-01-18
Hello,

I have been battering my head with this for about a month now so gonna see if anyone else knows something else to try.

I am trying to get a ubuntu machine (client) onto a windows active directory (domain) this i have done and you can login using winbind to the client desktop no problems however i dont want the domain users' home directories on the client machine so i have set up a ubuntu server (samba) to hold the home directories now so far i have been able to set up a share which both windows and linux can read and write to with no passwords needed, and if i have modified the /etc/fstab file on the client to mount the samba share on startup however if i login as a domain user it fails to create a home directory on the share with the following error:

*"/mnt/home/admin2" does not exist*

now the main question is this in fstab i have used a cred file stored in /usr/share/.smbcred which should be accessible by all users right? i know i can put the creds into the fstab file but i can't find how and it is just failing to mount when i try so if you know how i will try that, also does fstab run before or after the home directory is created as if it runs after then the cred file is working but the home directory is looking at a location which hasnt been mounted yet or if fstab runs before then the location is not mounting right (hoping for second one :D)

Sorry for the massive description.

if you need any log files please let me know and ill post them.

[Client]
Ubuntu 10.04 desktop

[Samba Server]
Ubuntu 8.04 LTS Server

[Windows Active Directory]
Windows server 2003

Thanks

---

### Post by oj0kksn5 on 2011-01-24
Anyone??

---

