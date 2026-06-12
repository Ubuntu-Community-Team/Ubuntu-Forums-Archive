---
title: "Trying to set up Samba fileserver, prompted repeatedly for password"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by rsp385 on 2009-08-29
Hi all,

I'm trying to set up my Ubuntu machine (Jaunty 64-bit) as a Samba file server, which I intend to use to back up some files from my Windows machine.  I've looked at a few guides, most of which give roughly the same installation procedures (e.g. [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu)).

After following those steps, I can see the Ubuntu machine in my workgroup from Windows, and when I try to connect to it (e.g. "\\machinename\username") I get prompted for the password.  However, entering my username and password just gives me another prompt, and another, etc.  If I look in /var/log/samba, I see a log for the client machine that has a lot of stuff like this:

```
[2009/08/29 00:57:03,  0] smbd/service.c:make_connection_snum(740)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2009/08/29 01:03:54,  0] smbd/service.c:make_connection_snum(996)
  Can't become connected user!
[2009/08/29 01:03:54,  0] smbd/service.c:make_connection_snum(996)
  Can't become connected user!
[2009/08/29 01:03:54,  0] smbd/service.c:make_connection_snum(996)
  Can't become connected user!
[2009/08/29 01:03:54,  0] smbd/service.c:make_connection_snum(996)
  Can't become connected user!
[2009/08/29 01:03:54,  0] smbd/service.c:make_connection_snum(996)
  Can't become connected user!
[2009/08/29 01:04:02,  0] smbd/service.c:make_connection_snum(740)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

```

Anyone know what I'm doing wrong?  As far as I can tell, I've followed the setup steps verbatim.

Thanks!

---

### Post by Iowan on 2009-08-30
What did you put in */etc/samba/smbusers*for the line: ```
<username> = “<username>”
``` The username map connects unix (linux) usernames with Windows usernames (example [here)]("http://ubuntuforums.org/showpost.php?p=7828117&postcount=4") - but the linux user must exist. Did you create a linux and Samba user account?

---

### Post by rsp385 on 2009-08-30
Assuming my username on the Linux machine is "jdoe" and my username on the Windows machine is "John Doe", I've tried all of the following configurations now:

```
jdoe = "jdoe"
jdoe = "John Doe"
jdoe = John Doe
jdoe = jdoe
John Doe = jdoe
"John Doe" = jdoe
```

Yes, I've used *smbpasswd -a* and yes, I've checked and re-checked my password.  What am I missing here?

---

### Post by rsp385 on 2009-08-30
Ah ha.  I realized I hadn't uncommented all of the following lines in */etc/samba/smb.conf* (I was missing the *[homes]* line):

```
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes] 
comment = Home Directories             
browseable = yes
```

Problem solved.  Thanks for your help and sorry for wasting your time. :)

---

### Post by Iowan on 2009-08-31
Good news! Are you aware that the [SOLVED] feature has returned? (Under Thread Tools)

---

### Post by rsp385 on 2009-08-31
Now I am!  Thanks again.

---

