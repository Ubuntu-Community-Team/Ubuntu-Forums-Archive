---
title: "Connect to server(ssh) takes me to root folder"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by bnilsson on 2010-09-14
Dear all,

When I use the function "Connect to server" / ssh and leave the "folder" field empty and log in, I am taken to the file system root level (/) on the remote system..!! Is this behaviour really the intention?
I am really surprised, I would expect to automatically end up in my own home folder on the remote server.

Is there any way to avoid this, except entering "/home/myname" in the folder field? I tried $HOME, ~/, ~, but I got error messages on all.

It is not always obvious where your own home folder is in the remote file system, it might not even be a unix.

I should mention that when I do a command line sftp connection (sftp name@host) to the same server it works as I would expect.  So this sftp GUI must do it differently? 

BN

---

### Post by SilviuJ on 2011-04-29
Sorry to bring up an old thread, but I am having the exact same problem.

Does anyone know a fix to this?

Thank you

---

