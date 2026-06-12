---
title: "[SOLVED] Crontab bug"
date: 2008-06-25
forum: Mythbuntu
---

### Post by doogy2004 on 2008-06-25
I have installed Ubuntu 8.04 Server then I installed mythbuntu-desktop.  After I installed the Mythbuntu package crontab jobs no longer run.

When I open webmin and go to "Scheduled Cron Jobs" the columns are supposed to be as follows:  User, Active?, Command, Move

However after installing the Mythbuntu package webmin shows the following columns:  Active?, Command, Move

The user column goes missing and crontab jobs do not run anymore.

Any suggestions?

Thanks in advance

The reason that I need the crontab jobs to run is so that I can auto update my video library with the following command: ```
mythbackend --upnprebuild
```

---

### Post by doogy2004 on 2008-06-26
bump

I'm currently testing the problem in a VM to verify what is happening.

---

### Post by uopjohnson on 2008-06-26
webmin adds and extra variable here.  What happens if you open a terminal and run```
crontab -e
``` should open the crontab for your user in vi.  Is there anything listed there?  

Add a line like:
```
* * * * *  /bin/echo "working" >> /tmp/crontest.txt
```
then:
```
tail -f /tmp/crontest.txt
```
and see if it is working.

---

### Post by doogy2004 on 2008-06-26
I figured out why webmin is not showing the user column, I only had one user (root) using cron/crontab.  As soon as I setup another user's crontab, the user column is shown.

Currently I have a fresh install of Ubuntu 8.04 LTS Server.  I just tried the following:

> **uopjohnson said:**
> webmin adds and extra variable here.  What happens if you open a terminal and run```
crontab -e
``` should open the crontab for your user in vi.  Is there anything listed there?  

Add a line like:
```
* * * * *  /bin/echo "working" >> /tmp/crontest.txt
```
then:
```
tail -f /tmp/crontest.txt
```
and see if it is working.

Using these instructions work on a clean install of the Server version.

I then ran the command:```
sudo apt-get install mythbuntu-desktop
```
I restarted the VM for good measure.

I tried the above again, worked fine. Then I tried the same with ```
sudo crontab -e
``` and it worked, in the VM.

I then tried the above instructions again on the computer I'm having trouble with using ```
crontab -e
``` worked however when I did ```
sudo crontab -e
``` it did not work.

I'm gonna try to reinstall again and see what happens.

Thanks for the response.

---

### Post by KillerKiwi on 2008-06-29
try [gnome-schedule]("apt:gnome-schedule")

---

### Post by doogy2004 on 2008-06-29
I did a clean install on my server again and now everything is working.  Strange.  Anyway, Thanks to all those involved.

---

