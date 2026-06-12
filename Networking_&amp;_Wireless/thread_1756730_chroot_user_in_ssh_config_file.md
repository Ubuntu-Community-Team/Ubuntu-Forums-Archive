---
title: "chroot user in ssh config file"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-05-12
[SIZE=2]I was reading in: [/SIZE][SIZE=2]SSH The Secure Shell,The Definitive Guide. that in[/SIZE] the /etc/ssh/sshd_config file a user could be chrooted to their home folder by the command

chroot <username>

but it said it could only be used in SSH2. since the publication of said book (2001) and knowing that openSSH incorporated some SSH2 methodology, is this command usable in the current openSSH?

or is their another method used to achive this?

Many Thanks

---

### Post by Ceiber Boy on 2011-05-13
i Tryed placing this command in the /etc/ssh/sshd_config file and restarted the demon, from that it refused to let any ssh logins at all!

So i guess the short answer is NO!

---

### Post by kxmas on 2011-11-21
You should be able to apply the chroot to just one user if you combine it with the 'Match' argument.

```
man sshd_config
``` for details

---

### Post by vinterkind on 2012-03-16
more precisely you can match also a group.

That's what I've done:

1 create user (testuser) and group (eg remote)
2 setup jail (copy files and directories)
3 used "l2chroot" script for copying libraries
4 configured sshd_config as followed

```
match group remote
  ChrootDirectory /jail/home/testuser
```

And now I'm stuck at the following message while connecting -.-

```
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Write failed: Broken pipe
```

Any suggestions ?

---

### Post by vinterkind on 2012-03-16
ah sorry to meddle with them solved questions <.<

cheers,

---

