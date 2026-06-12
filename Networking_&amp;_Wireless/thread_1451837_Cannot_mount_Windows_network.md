---
title: "Cannot mount Windows network"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2010-04-11
A few days ago I got this Ubuntu box (9.10) to connect to the Windows network in our house. Sharing printers and files. Life was good. 

But today, Places > Network > Workgroup tries to connect for about a minute then I get a "Unable to mount locations, Failed to retrieve share list from server" error.

Does anyone have any troubleshooting tips? The only thing I recall changing at around the same time was adding Wine.

---

### Post by Rocket J Squirrel on 2010-04-11
Following up, in Terminal I did:

```
smbclient -L //server -U user
``` and smbclient prompted me for the share password, thought about it for a few moments and returned:
```
error "nt_status_unsucessful" smbclient
```

The ip address of the Windows machine can be pinged from the Ubuntu machine, and it is accessible from any of the Windows machines on the network, so the problem is not with the machine or the network, it seems to be something that Ubuntu has gotten confused about. 

The following might be helpful:
```
$ smbd -V
Version 3.4.0
```
and, two days ago, I made the following changes in the /etc/samba/smb.conf in order to connect to the workgroup and control how this Ubuntu machine's shares appeared to the Windows machines:
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CCIRCLE

# server string is the equivalent of the NT Description field
   server string = my Samba Server (Ubuntu)
```
Neither of those seem like they could account for the problem, and after I made those changes and rebooted Ubuntu, the workgroup was accessible and everything worked fine for a couple days, then this sudden disconnect.

---

### Post by Rocket J Squirrel on 2010-04-11
Bump? I know it's rude to bump, but I know there's someone out there who can help.

---

### Post by Rocket J Squirrel on 2010-04-11
Oh, forgot to mention. From the Windows machines I can see the shared folder on the Ubuntu machine. But it ain't working the other way.

---

### Post by Iowan on 2010-04-11
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that might be helpful (if you haven't already seen it...).

---

### Post by Rocket J Squirrel on 2010-04-11
Hey -- did the stuff on the first page, rebooted Ubuntu, and Hey Presto! it works. :)

---

### Post by Iowan on 2010-04-12
:) Good to hear you got it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")!

---

