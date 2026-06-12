---
title: "Windows disconnect from Samba share"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by Kryten68 on 2009-01-11
Hi everybody!

I'm a relative newbie with Linux, even more so with Samba. I'm having a particular problem with Samba - actually, I kind of suspect the problem is not with Samba, but with Windows, but more on that in a moment...

My home network consists of the following:
1 Windows Vista box (my wife's)
1 Windows XP box (mine)
1 Ubuntu 7.10 server (operating as a file, backup, web, and subversions server)

Two other computers are connected to the network from time to time:
1 Windows XP laptop (mine, connected only occasionally)
My brother-in-law's XP laptop (which he brings over from time-to-time when he's home from grad school).

I'm using Samba to operate the file server. I have a couple of shares set up:

"Shared Files" - contains family photos & videos, some music files, and miscellaneous stuff that anyone on the network can access

"Web Server" - which is just a share of my Apache www directory, so I can easily maintain web sites I'm working on

"Backup" - a read-only share of the backup files (which are backed up nightly onto an external hard drive from the windows PCs & the other shares using rsync)

"Confidential" - a password-protected read/write share that contains stuff my wife & I don't want others to see - banking info, mainly, along with some business related stuff of mine & my wife's.

The problem is this: I want the windows machines to prompt for a password when accessing the "Confidential" share. They do this the first time, but then they maintain the connection so that subsequent access does not require a password. I guess this would work very well in an environment where the users log off regularly, but we don't. The pcs generally stay on 24/7.

What I would like it to do is this: after about 30 minutes of inactivity (ie. no open files), disconnect completely from the share. If the user wants to go back later, ask for the password again.

I've played with Samba options like "deadtime", but I realize that that's not doing what I want. After some time fiddling around, I realized that what's probably happening is that the Windows PCs are saving the user/password info & reconnecting to the share as needed.

Can anyone confirm that that's what's happening?

Does anyone have any suggestions on how to change that behaviour?

Thanks

---

### Post by uzi09 on 2009-05-08
Hey, sorry for a late reply.

How are you connecting to the server? If you're mapping the drives or if you're connecting from the run dialog with "\\server" a cool command can help disconnect drives for you:
```

net use * /d

```
This basically disconnects from all network drives, prompting for confirmation for each one.
Don't want a confirmation (say in case of a script)?
```

net use * /d /yes

```

Now it's just a matter of getting a batch file to run at a particular interval. 

Hopefully this should get you going in the right direction.

---

