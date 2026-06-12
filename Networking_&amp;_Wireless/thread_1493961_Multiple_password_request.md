---
title: "Multiple password request"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by Zrc on 2010-05-26
I've a script that sends via scp another script to a remote host and next runs it via ssh to finally recover a result file from the remote host using scp again. Something like this:

scp script root@remoteHost:.
...
ssh root@remoteHost /bin/bash script
...
scp root@remoteHost:file .

The problem is that it requires remote host root password three times and it's a little bit annoying.

Is there a simple solution to do this with only one password request?

The function of the script is to configure rsa keys on a remote client automatically (In fact, file is the client id_rsa.pub), then keys are not a solution.

---

