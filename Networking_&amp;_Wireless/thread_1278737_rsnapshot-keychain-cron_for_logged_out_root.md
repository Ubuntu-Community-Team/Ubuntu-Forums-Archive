---
title: "rsnapshot-keychain-cron for logged out root"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by neilevan814 on 2009-09-29
I have been struggling with this for days now.  I have rsnapshot for localhost running just fine with cron, but from the research I have done, when cron makes a call to a service that requires a log in, for example rsync over ssh..no default shell is given so I found to use the bash variable ENV=/root/.bashrc in a shell script run at cmd_preexec  in the rsnapshot.conf.  

my shell script reads 
#!/bin/bash
ENV=/root/.bashrc
source /root/.keychain/neil-htpc-sh

I used this same script with a test cron job run under root when I was logged out of root to try a simple rsync command and it worked great, the only difference is that cron was pointed directly to my shell script and the rsync command was also included in that.

For rsnapshot, the crontabs point to rsnapshot hourly, daily, weekly,monthly on separate lines, the rsnapshot starts and the cmd_preexec statement should be performed right before rsync starts.

Does anyone have any experience with this set up?

SOLVED:
Hi, I have been trying to get rsnapshot to run with keychain under cron for root when logged out.  

For me adding 
source /root/.keychain/<host>-sh
to cmd_preexec in the rsnapshot.conf did not work
What has finally worked for me which works remotely and locally is:
under cron run a command pointing to shell scripts for hourly daily weekly and monthly rsnapshots

my script is for hourly backups is hourly.sh
#!/bin/bash
ENV=/root/.bashrc
source /root/.keychain/<host>-sh
rsnapshot hourly

the reason why this was needed is because cron for ssh doesn't enter a shell to perform it's function, so before rsnapshot begins you must point the process into a shell or you get an annoying and failing error 255 stating rsync couldn't ssh(or something like that).  Then just re comment the cmd_preexec line in the rsnapshot.conf

---

### Post by acy76 on 2010-01-19
I was getting a similar error due to failed ssh logins and found the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1059461&highlight=rsnapshot") (see post #4).

I think your solution is likely accomplishing the same thing, i.e. passing the proper credentials to ssh, but this one is a bit easier. You can call rsnapshot directly from cron without an intermediate script using this method.

---

