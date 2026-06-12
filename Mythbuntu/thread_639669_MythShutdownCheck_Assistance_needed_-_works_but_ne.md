---
title: "MythShutdownCheck Assistance needed - works but needs refining"
date: 2007-12-13
forum: Mythbuntu
---

### Post by kyfehr on 2007-12-13
Hello,

So after finally getting my motherboard to do the whole shutdown wake up thing.. I need help with the script for **pre-shutdown check**. Can't find my answer online.. or don't know what to find exactly

The script is called and all is working.. but I don't want to check for a user logged in otherwise I need to physically go and log off the computer, which doesn't help me. But I want to know how to change the script to just check if a program like transcode or commercial flagging is running.. basically checking the job queue.. 

I know this is part of the Trunk.. but I am running 0.20.fixes

Any help would be great cause I really want the energy savings from the auto off :)

Thanks in advance

---

### Post by tohc1 on 2007-12-14
Not sure if I've misunderstood your question but I just use the mythshutdown command for the check.

This can check to see if the backend is a recording/ in a wakeup period/commerical flagging etc. Can't remmeber the exact command but ```
mythshutdown --help
``` should tell you.

---

### Post by kyfehr on 2007-12-14
Thanks tohc1, 

I will try that when I get home :)

---

### Post by majoridiot on 2007-12-18
if the MythShutdownCheck script you are referring to is from this guide:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

and your only concern is that your backend not shutdown while doing mythtv
business, then simply remove that script from the backend setup.  mythtv should
not shutdown while transcoding, etc.

that script was added only to check for other logins or whatever the user
might have added themselves and was only called *after* mythtv was
finished any processes and was ready to shut down.

---

### Post by gregshldn on 2008-08-12
Hi

I wrote variation of MythShutdownCheck to check whether Firefox is running.   If it is, shutdown is deferred until the next timed check by mythtv.   If there are no instance of Firfox, the PC is shutdown.  My first bash script by the way... woo hoo.
> 
#
# MythShutdownCheck
#
# checks to see if any other user is
# logged in before idle shutdown
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#

if ps -C firefox | grep firefox -c -q; then exit 1; else exit 0; fi

Of course for other apps, just change firefox for you app name as appears in the list produces by the ps command in the shell.

---

### Post by gregshldn on 2008-08-16
This version gives you 30 seconds to stop Myth's auto-shutdown (if firefox is not running).   Hope this is useful to someone.

```
#
# MythShutdownCheck
#
# checks to see if any other user is
# logged in before idle shutdown
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#

if ps -C firefox | grep firefox -c -q; then
	exit 1
else
	xmessage shutdown in 30 secounds -buttons OK:0,STOP:2 -timeout 30
	u=$?
	if [ "$u" == "2" ]; then
		exit 1
	else
		exit 0
	fi
fi
```

---

### Post by majoridiot on 2008-08-16
> **gregshldn said:**
> This version gives you 30 seconds to stop Myth's auto-shutdown (if firefox is not running).   Hope this is useful to someone.

```
#
# MythShutdownCheck
#
# checks to see if any other user is
# logged in before idle shutdown
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#

if ps -C firefox | grep firefox -c -q; then
	exit 1
else
	xmessage shutdown in 30 secounds -buttons OK:0,STOP:2 -timeout 30
	u=$?
	if [ "$u" == "2" ]; then
		exit 1
	else
		exit 0
	fi
fi
```

these might be useful to others, so thank you for sharing them...

however, i suggest starting a new little section of the ACPI Wake wiki
for this sorta thing... that way the info is right there when folks are 
setting it up.

unfortunately, people only tend to look here when they have problems. ;)

thanks again for sharing these!

---

### Post by gregshldn on 2008-08-17
OK, thanks.   This is where I was looking (and in the Wiki) so that makes sense in all directions.

---

