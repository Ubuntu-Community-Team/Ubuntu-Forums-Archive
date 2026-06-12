---
title: "mythbackend crashes often"
date: 2008-02-08
forum: Mythbuntu
---

### Post by jjohns63 on 2008-02-08
I've got a pvr-350 and avermedia a180 and my backend crashes with no warning and seemingly at random. I managed to get it to restart by following this guide: [http://www.mythtv.org/wiki/index.php/Using_pcsk_to_Supervise_mythbackend](http://www.mythtv.org/wiki/index.php/Using_pcsk_to_Supervise_mythbackend)

Here's the pcsk log:

```
[2008-02-08 08:34:15] pcsk[4958]: Child process 4965 caught signal 11,, dumped core exited with 0 exit status. Runtime: 09:24:57
[2008-02-08 08:34:15] pcsk[4958]: Sleeping for 3 seconds..
[2008-02-08 08:34:18] pcsk[4958]: Spawning "/usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid" (pid =$
[2008-02-08 10:46:08] pcsk[4958]: Caught signal 15, terminating..
[2008-02-08 10:46:08] pcsk[4958]: Killing child 7525 with signal 15..
[2008-02-08 10:46:12] pcsk[4958]: Child process 7525 caught signal 15, exited with 0 exit status. Runtime: 02:11:54
[2008-02-08 10:46:12] pcsk[4958]: Exiting.
[2008-02-08 10:49:42] pcsk[4964]: Starting pcsk v0.0.5(rev0).
[2008-02-08 10:49:42] pcsk[4964]: Spawning "/usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid" (pid =$
[2008-02-08 11:02:18] pcsk[4964]: Child process 4967 caught signal 11,, dumped core exited with 0 exit status. Runtime: 00:12:36
[2008-02-08 11:02:18] pcsk[4964]: Sleeping for 3 seconds..
[2008-02-08 11:02:21] pcsk[4964]: Spawning "/usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid" (pid =$
[2008-02-08 14:21:07] pcsk[4964]: Child process 5991 caught signal 11,, dumped core exited with 0 exit status. Runtime: 03:18:46
[2008-02-08 14:21:07] pcsk[4964]: Sleeping for 3 seconds..
[2008-02-08 14:21:10] pcsk[4964]: Spawning "/usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid" (pid =$
[2008-02-08 16:02:59] pcsk[4964]: Caught signal 15, terminating..
[2008-02-08 16:02:59] pcsk[4964]: Killing child 6735 with signal 15..
[2008-02-08 16:02:59] pcsk[4964]: Child process 6735 caught signal 15, exited with 0 exit status. Runtime: 01:41:49
[2008-02-08 16:02:59] pcsk[4964]: Exiting.
[2008-02-08 16:04:38] pcsk[4993]: Starting pcsk v0.0.5(rev0).
[2008-02-08 16:04:38] pcsk[4993]: Spawning "/usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid" (pid =$
```

Now I know the lines where it uses signal 15 are normal kills such as rebooting. It's the signal 11 that causes the crash. There's nothing in the backend logs at the same time. Any ideas?

---

### Post by superm1 on 2008-02-08
There is a bug in the -fixes branch when using one of these tools to watch over mythbackend.  Don't do it until you switch to trunk.  They have a tendency to kill the process in -fixes.

---

### Post by jjohns63 on 2008-02-08
Sorry, but i'm not sure what that means or how to change it. I am using SVN branch: branches/release-0-20-fixes (found out through mythbackend --version) but how could I change that?

Sorry but I don't really know a whole lot about what I'm doing.

If it helps I attached the crash file created by apport.

---

### Post by superm1 on 2008-02-09
For now don't use a service like monit.  One 0.21 is released, you can start using it.

---

### Post by djkmyth on 2008-03-13
Hi jjohns63,

You are getting the exact same problem I have, hence I used pcsk to fix it.  Well, not really fix, more work around.

For comparison, I have a Hauppauge NOVA-T-500 dual tuner, Kubuntu 7.04 (Feisty), x86_64 version (AMD), so it doesn't seem to be hardware-specific.

Like you, I'm just waiting for an updated version that will hopefully be fixed.  (Also, I'm looking forward to the new version that allows multiple streams on the same channel to be recorded at once).

I'm glad somebody found the guide useful!

DJKMyth

---

