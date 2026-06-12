---
title: "Cannot uninstall MPD"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by billynomates on 2008-04-08
I've been having problems with mpd so I figured the easiest way to fix it would be to uninstall it completely and then reinstall it.

Only problem is, when I try to uninstall it in Synaptic, I get this:
```
E: mpd: subprocess pre-removal script returned error exit status 1

```

And if I try to do it in a terminal, I get this:
```

mike@mike:~$ sudo apt-get remove mpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  mpd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 479kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 156124 files and directories currently installed.)
Removing mpd ...
 * Stopping Music Player Daemon mpd                                      [fail] 
invoke-rc.d: initscript mpd, action "stop" failed.
dpkg: error processing mpd (--remove):
 subprocess pre-removal script returned error exit status 1
action: abort-remove not supported
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike:~$ 

```

What's going on? Any ideas?

---

### Post by TenPlus1 on 2008-04-08
You could always try going into the System Monitor and removing MPD from the list manually, either by ending the process' or killing them...  THEN trying to uninstall it...

---

### Post by billynomates on 2008-04-08
Thanks for your reply!
There are no MPD-related processes in System Monitor. I even tried rebooting and it still doesn't work. MPD isn't in my startup sessions either.

---

### Post by booljayj on 2008-04-09
I am also having this problem. Bump.

---

### Post by senab on 2008-04-11
I'm also having this problem

---

### Post by bluebyt on 2008-04-15
> **TenPlus1 said:**
> You could always try going into the System Monitor and removing MPD from the list manually, either by ending the process' or killing them...  THEN trying to uninstall it...

I killed MPD process, but I am still unable to uninstall it???

---

### Post by jpmontalbo on 2008-04-17
I had the same exact issue and I got the same errors as well. This is how I got it to uninstall.

```
sudo rm /var/lib/dpkg/info/mpd.*
```

afterwards run

```
sudo apt-get autoremove --purge mpd
```

I uninstalled because mpd refused to run even when I did

```
sudo /etc/init.d/mpd start
```

I even checked mpd.log to see if it would give me an exact error but no success. I really wanted to use Sonata with Hardy Heron Beta.

---

### Post by daengbo on 2008-04-17
Have you tried removing from the command line using
sudo apt-get remove mpd
or
sudo aptitude remove mpd
??

This works for me with no issues. If it doesn't work for you, you will have a better output of the error which you can post.

---

### Post by billynomates on 2008-04-19
Thanks for your help, but I fixed it by reinstalling Ubuntu, haha.

---

### Post by vanadium on 2008-04-19
For those who have problems with mpd but do not really want to remove it or reinstall Ubuntu ;) : delete the file /var/lib/mpd/state  It seems that this file can become corrupt and prevent mpd from being loaded. After that, see wether the problem is solved by starting the mpd daemon again: "sudo mpd".

---

### Post by rjmdomingo2003 on 2008-05-28
> **jpmontalbo said:**
> I had the same exact issue and I got the same errors as well. This is how I got it to uninstall.

```
sudo rm /var/lib/dpkg/info/mpd.*
```

afterwards run

```
sudo apt-get autoremove --purge mpd
```

I uninstalled because mpd refused to run even when I did

```
sudo /etc/init.d/mpd start
```

I even checked mpd.log to see if it would give me an exact error but no success. I really wanted to use Sonata with Hardy Heron Beta.

This worked for me! Thanks a bunch!:KS

---

