---
title: "[SOLVED] DVD::RIP Cluster Mode SSH"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by Son of Silas on 2007-12-05
Can anyone take me through (step by step) what I have to do to get SSH setup correctly so I can use DVD::RIP in cluster mode?

The instructions say
> Login as the user who will run the cluster control daemon (on the corresponding computer) and check if this user has a public key:

  ls -l ~/.ssh/identity.pub

If the file is not present execute this command:

  ssh-keygen

and follow its instructions but press enter if you are asked for a password!

Now add the content of your ~/.ssh/identity.pub file to the ~/.ssh/authorized_keys file on each transcode node. After this you should be able to login from the cluster control computer to the node without being prompted for a password

I don't have an "identity.pub" I have a "id_rsa.pub" and a "id_rsa". It also mentions a authorized_keys file but I don't have one? 

I really need a dummies 'how to on this'. All I want to do is use cluster mode, surely it can't be that hard?

---

### Post by Son of Silas on 2007-12-08
Worked it out myself and posted a 'HOW TO' here: _[Setup DVD::RIP SSH & NFS](http://ubuntuforums.org/showthread.php?p=3916736#post3916736)_

---

