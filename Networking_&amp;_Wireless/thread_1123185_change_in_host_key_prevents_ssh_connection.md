---
title: "change in host key prevents ssh connection"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Miles_Prower on 2009-04-11
Recently I installed centOS on an old junker so I could use it as an ftp server. I sped through the install, and missed some things, so I had to reinstall. After that, the machine I had been using to remote-administrate is couldn't connect to it via ssh anymore, giving this error:

```
taels@tornado:~$ ssh -l tails 192.168.1.XX
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
73:8c:45:e7:ac:d1:c5:34:5c:87:ce:5a:26:2e:90:43.
Please contact your system administrator.
Add correct host key in /home/taels/.ssh/known_hosts to get rid of this message.
Offending key in /home/taels/.ssh/known_hosts:3
RSA host key for 192.168.1.XX has changed and you have requested strict checking.
Host key verification failed.

```

I've tried editing /home/taels/.ssh/known hosts , but the file seems to be encryped, even when I use vi as root or with sudo. How can I add the correct host keys so that I can continue to use this server?

Thanks

---

### Post by Spider7 on 2009-04-12
if you can not find the key in the known_hosts file, you can remove/rename that file, and when you do ssh again, it should start from scratch, e.g. asking you whether you want to trust it, etc...

cheers.

---

### Post by drjonze on 2009-04-25
> **Spider7 said:**
> if you can not find the key in the known_hosts file, you can remove/rename that file, and when you do ssh again, it should start from scratch, e.g. asking you whether you want to trust it, etc...

cheers.

Thanks for the tip! I did new installs on both my machines and I could no longer connect them by ssh. This fixed it.

---

### Post by likebucks on 2009-08-30
Thank you - that worked like a charm!! :KS for you!

---

### Post by aussiedude on 2010-08-30
I just had this very problem. When I re-read the error message after reading this post I found error message  contained all I need for a more elegant solution.
Using the error provided by the op
Open a terminal window, at the prompt enter
```
nano /home/your_username/.ssh/known_hosts
```
move down to the 3rd line and press Ctrl+K to remove it. We know we have to remove the 3rd line (key) because the error message tells us "Offending key in /home/taels/.ssh/known_hosts:3"
Press Ctrl+O to save the file and Ctrl+X to exit nano
When you try connecting to the host this time it will ask if you trust the host, type yes and press Enter. The new key will be added to the known_hosts file
This is useful when you have a large number of hosts in the known_hosts file, if you just have 1 or 2, deleting the file might be the easier route.

Hope this helps someone else in the future

---

