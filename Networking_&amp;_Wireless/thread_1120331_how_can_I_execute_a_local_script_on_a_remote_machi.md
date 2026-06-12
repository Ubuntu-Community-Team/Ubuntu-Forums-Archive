---
title: "how can I execute a local script on a remote machine via ssh?"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by duffrecords on 2009-04-08
I'm trying to write a script to save myself some keystrokes at work.  We frequently push content from a development server to a live server and it usually involves logging into each, making an archive of the dev files, backing up any live files that will be overwritten, transferring the archive to the live machine with scp or wget, uncompressing it and setting the correct permissions, and deleting the archive.

I could easily write a script on my local machine that would fully automate the procedure with commands in this form:```
ssh -l <user> <host> "<command> && <command> && <command>"
```But I want to make it interactive on the local side.  For example, I'd like to write some logic so that conditions such as "No such file or directory" would pause the script and prompt the user to make a decision.  Or if elevated privileges were needed, I'd want to prompt the user for a password, rather than use a locally-cached password (bad idea) or RSA authentication (better idea, but I'd still prefer human intervention).  So I don't want it to be 100% automated, just mostly automated except for specific cases.

The other issue I have with the method above is that executing a remote command, prompting the local user for input, and then executing another remote command based on that input would involve two login authentications.  That's secure, of course, but it seems like one extra step and I'm picky about writing very lean, efficient code.  Is there a way to create an SSH tunnel to a machine, run an interactive script locally that executes commands remotely, and then close the tunnel once everything is complete?

---

### Post by duffrecords on 2009-06-14
bump

---

