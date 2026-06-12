---
title: "Data transfer options"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by fatherwilliam on 2009-09-21
I'm running Xubuntu 9.04, and I just signed up with nexx.com as a web host.  Nexx.com provides limited ssh account access, and I am trying to find the best way to interact with this host.

I am able to ssh into the account.
I am able to sftp into the account and transfer files

However, when I try to use scp, I am prompted for a password, and the connection just hangs.  No timeout, no transfer, nothing.

Similarly, if I try to use rsync -e ssh, I am prompted for a password, but the connection hangs and no data is transferred.

I thought that scp was indistinguishable to the server from a normal ssh session, so I was surprised to see that all my attempts to scp failed.

Has anyone else used hosts like this?  Any ideas on the best way to keep the remote host in sync with local files?

ftp access is provided, but I would really like some way to sync files.  As far as I know, there is no rsync type utility that uses ftp.

I understand that this is not directly about ubuntu, but since my power on the remote host is very limited, I am probably looking for some kind of solution I can implement on my local machine.

Any suggestions are welcome.  Thanks.

---

### Post by fatherwilliam on 2009-09-21
I have come up with a couple of solutions so far:

lftp has a mirror option, and it doesn't seem to do full incremental transfers, but it looks like it is able to only transfer only the files that have been modified.

I installed sshfs, and if I can mount the remote drive locally, so I should be able to do an rsync on my local machine.

I'll give these methods a try...

---

