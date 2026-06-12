---
title: "Mythbuntu Control Panel Hangs on Apply"
date: 2011-10-21
forum: Mythbuntu
---

### Post by GuiGuy on 2011-10-21
Any one else having problems with the Mythbuntu CP in 11.10? On my upgraded BE/FE it will hang whenever an attempt is made to change a setting that requires authentication :(

---

### Post by nickrout on 2011-10-22
> **GuiGuy said:**
> Any one else having problems with the Mythbuntu CP in 11.10? On my upgraded BE/FE it will hang whenever an attempt is made to change a setting that requires authentication :(

what is mythbuntu CP? Do you mean mythbuntu-control-centre?

---

### Post by GuiGuy on 2011-10-29
> **nickrout said:**
> what is mythbuntu CP? Do you mean mythbuntu-control-centre?

Yes I did.

Sorry about the delay in getting back here, but there have been problems.

Anyway, the issue is mythbuntu-bare:

>  mythbuntu-bare-console
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mythbuntu-bare-console (2.0) ...
start: Job failed to start
invoke-rc.d: initscript mythbuntu-bare-console, action "start" failed.
dpkg: error processing mythbuntu-bare-console (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythbuntu-bare-console


Attempting to apply mythbuntu-bare settings or any other control centre setting causes it to hang. 

I get the same error after purge > install so the issue is now probably beyond my level of understanding.

---

### Post by dangerous_d on 2011-11-11
I had a similar symptom and I tracked my problem down to bad permissions for the python scripts behind mythbuntu-bare.  They were not executable, which explains the "permission denied" message I kept seeing in one of the system log files.

Note: the snippet below is from AFTER I added execute permissions.  On my system I had to a+x the files in both directories.
/usr/share/mythbuntu-bare/bareclient/*
/usr/share/mythbuntu-bare/bareserver/*

```

Myth:~$ more /etc/init/mythbuntu-bare-console-processor.conf 
# Mythbuntu Bare Console service

description     "Mythbuntu Bare Server - Processor"
author          "Thomas Mashos <tgm4883@ubuntu.com>"

start on started mythbuntu-bare-console
stop on stopped mythbuntu-bare-console

exec /usr/share/mythbuntu-bare/bareserver/bareprocessor.py
respawn

```

```

Myth:~$ ls  -ltr /usr/share/mythbuntu-bare/bareclient/
total 48
-rwxr-xr-x 1 root root 1012 2011-09-06 12:36 update-task.py
-rwxr-xr-x 1 root root 2449 2011-09-06 12:36 updater.py
-rwxr-xr-x 1 root root 1730 2011-09-06 12:36 push_file.py
-rwxr-xr-x 1 root root 3367 2011-09-06 12:36 mythrestore.py
-rwxr-xr-x 1 root root 6590 2011-09-06 12:36 mythbareupdate.py
-rwxr-xr-x 1 root root 5179 2011-09-06 12:36 mythbackup.py
-rwxr-xr-x 1 root root 2116 2011-09-06 12:36 backup-task.py
-rwxr-xr-x 1 root root 4181 2011-11-05 02:14 mythbackup.pyc
-rwxr-xr-x 1 root root 2697 2011-11-05 02:14 mythrestore.pyc

```


Now I have to figure out why the 20111110 mythbuntu patches I installed yesterday are crashing my system with hardly a whisper in the log files (I think it's wlan0 related, stay tuned).

---

### Post by GuiGuy on 2011-11-11
> **dangerous_d said:**
> I had a similar symptom and I tracked my problem down to bad permissions for the python scripts behind mythbuntu-bare.  They were not executable, which explains the "permission denied" message I kept seeing in one of the system log files.

Thanks for the input. I had already reset the permissions to make the scripts executable but it hasn't helped.

In any case, every action in COntrol Center now hangs when apply is clicked and the confirmation dialog acknowledged.

I did a clean install but the problem persists so I'll pretend COntrol Center doesn't exist ;)


> 
Now I have to figure out why the 20111110 mythbuntu patches I installed yesterday are crashing my system with hardly a whisper in the log files (I think it's wlan0 related, stay tuned).

For all of 11.10's faults, and there are many IMO, this is the first time ever that at least one of my collection of USB Wireless N devices works more or less as it should (D-LINK DW140 mark 2). I looked at the update you mentioned. I haven't installed it yet so might wait for your report back? :) 

Thanks

---

