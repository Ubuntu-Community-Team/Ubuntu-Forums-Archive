---
title: "Are 0.23.1 autobuilds compatible with mythbuntu 9.10"
date: 2010-08-17
forum: Mythbuntu
---

### Post by utar on 2010-08-17
The subject says it all really!

I'm currently on autobuilds for 0.23 on mythbuntu 9.10.  After doing an update I noticed that the mythbuntu control centre was giving me a "Exception in applyStateToGUI of Plugin Repositories" so I did a "sudo dpkg-reconfigure mythbuntu-repos" and I noticed that 0.23.1 (and 0.24 were listed).

I actually thought that 0.23.1 and 0.24 were only supported on mythbuntu 10.04 so thought I would check before potentially wreaking my install!

Cheers.

---

### Post by tgm4883 on 2010-08-17
> **utar said:**
> The subject says it all really!

I'm currently on autobuilds for 0.23 on mythbuntu 9.10.  After doing an update I noticed that the mythbuntu control centre was giving me a "Exception in applyStateToGUI of Plugin Repositories" so I did a "sudo dpkg-reconfigure mythbuntu-repos" and I noticed that 0.23.1 (and 0.24 were listed).

I actually thought that 0.23.1 and 0.24 were only supported on mythbuntu 10.04 so thought I would check before potentially wreaking my install!

Cheers.

yea they work on 9.10. Interesting that you got that error though, can you start mythbuntu-control-centre from the command line and post the full error text

---

### Post by utar on 2010-08-17
Cheers, I will give 0.23.1 a go.  I thought I had read somewhere that only the version of Myth above the one that was shipped was supported.  I.e. 9.10 shipped with 0.22 and hence only up to 0.23 was supported.  I can't find where I read this now though.  In any case I was wrong.

Error below, it happened after a myth-repository update.  There seems to have been lots of these recently as an aside.


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 380, in refreshState
    plugin.applyStateToGUI()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 139, in applyStateToGUI
    self.repobox.set_active(self.versions.index(self.changes['WeeklyRepo']))
ValueError: list.index(x): x not in list
WARNING: There is no "Videos" Storage Group set so ONLY MythTV Frontend local paths for videos and graphics that are accessable from this MythTV Backend can be used.
no crontab for utar
/usr/bin/mythbuntu-control-centre:113: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()

```

---

### Post by tgm4883 on 2010-08-17
odd. What are the exact steps to reproduce that issue?

Also, what is the output of 
```
dpkg -l mythbuntu-repos
```

---

### Post by utar on 2010-08-17
Output of dpkg -l mythbuntu-repos:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.2-0ubuntu0+m Mythbuntu repos installer
```

The error appeared when I ran mythbuntu control centre straight after installing an update.  Apt log:

```
Log started: 2010-08-17  19:12:24
(Reading database ... 235494 files and directories currently installed.)
Preparing to replace mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100812002709 (using .../mythbuntu-repos_8.2-0ubuntu0+mythbuntu~auto20100817002634_all.deb) ...
Unpacking replacement mythbuntu-repos ...
Setting up mythbuntu-repos (8.2-0ubuntu0+mythbuntu~auto20100817002634) ...
OK
OK

```

I can't however say for certain that something else didn't caused it.

---

### Post by tgm4883 on 2010-08-17
> **utar said:**
> Output of dpkg -l mythbuntu-repos:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.2-0ubuntu0+m Mythbuntu repos installer
```

The error appeared when I ran mythbuntu control centre straight after installing an update.  Apt log:

```
Log started: 2010-08-17  19:12:24
(Reading database ... 235494 files and directories currently installed.)
Preparing to replace mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100812002709 (using .../mythbuntu-repos_8.2-0ubuntu0+mythbuntu~auto20100817002634_all.deb) ...
Unpacking replacement mythbuntu-repos ...
Setting up mythbuntu-repos (8.2-0ubuntu0+mythbuntu~auto20100817002634) ...
OK
OK

```

I can't however say for certain that something else didn't caused it.

Nope, looks like it was caused by mythbuntu-repos. So you can't reproduce the error?

What is the output of

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
cat /etc/default/mythbuntu-repos
```

---

### Post by utar on 2010-08-17
Well I get the error every time I run Mythbuntu Control Centre if that is what you mean about reproducing it?

cat /etc/apt/sources.list.d/mythbuntu-repos.list

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu karmic main
deb http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu karmic main
deb-src http://uk.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu karmic main

```

cat /etc/default/mythbuntu-repos

```
[cfg]
activateweekly = True
weeklylocation = UK
weeklyrepo = 0.23
testingppa = False
```

---

### Post by tgm4883 on 2010-08-17
Ah I see the issue. Let me try to fix that now.

---

### Post by tgm4883 on 2010-08-17
Ok, i've pushed the fix. It source packages will build it so it should be done in a few hours. Your system is still set to update to 0.23.0, which might be because of this error. Once the packages get build, you will have an upgrade to mythbuntu-repos that should fix this.

---

### Post by tgm4883 on 2010-08-17
Ok, looks like the latest builds are ready, should just be fixed via a regular apt-get update && apt-get upgrade.  Let me know if you are still experiencing the issue

---

### Post by utar on 2010-08-18
Thanks I will check when I get home tonight.

---

### Post by utar on 2010-08-18
Thanks the update worked.

Mythbuntu Control Centre is working again and I have upgraded to 0.23.1.

Many thanks for your help.

---

### Post by utar on 2010-08-18
Hmmm I think I spoke too soon about everything working.  Vdpau decoding has totally disappeared from 0.23.1.

Probably a problem for another thread though if I can't find a solution.

---

### Post by tgm4883 on 2010-08-18
> **utar said:**
> Hmmm I think I spoke too soon about everything working.  Vdpau decoding has totally disappeared from 0.23.1.

Probably a problem for another thread though if I can't find a solution.

Yea that would be for another thread since this one is regarding the -repos package

---

### Post by alien878 on 2010-10-16
I just upgraded to 10.10 and am experiencing this issue.  How was it fixed?

EDIT:  I was able to fix this by replacing 0.23 with 0.23.1 in the files.  Still, is there still something wrong to cause this?

Output of mythbuntu-control-center:
```
allen@violet:~$ sudo mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
no crontab for root
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 381, in refreshState
    plugin.applyStateToGUI()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 137, in applyStateToGUI
    self.repobox.set_active(self.versions.index(self.changes['WeeklyRepo']))
ValueError: list.index(x): x not in list
/usr/bin/mythbuntu-control-centre:126: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()
```Output of dpkg -l mythbuntu-repos:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.5-0ubuntu0+m Mythbuntu repos installer

```Content of /etc/default/mythbuntu-repos:
```
[cfg]
activateweekly = True
weeklylocation = DE
weeklyrepo = 0.23
testingppa = False

```content of /etc/apt/sources.list.d/mythbuntu-repos.list:
```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu maverick main
deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu maverick main
deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu maverick main


```

---

### Post by tgm4883 on 2010-10-16
> **alien878 said:**
> I just upgraded to 10.10 and am experiencing this issue.  How was it fixed?

EDIT:  I was able to fix this by replacing 0.23 with 0.23.1 in the files.  Still, is there still something wrong to cause this?

Output of mythbuntu-control-center:
```
allen@violet:~$ sudo mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
no crontab for root
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 381, in refreshState
    plugin.applyStateToGUI()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 137, in applyStateToGUI
    self.repobox.set_active(self.versions.index(self.changes['WeeklyRepo']))
ValueError: list.index(x): x not in list
/usr/bin/mythbuntu-control-centre:126: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()
```Output of dpkg -l mythbuntu-repos:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.5-0ubuntu0+m Mythbuntu repos installer

```Content of /etc/default/mythbuntu-repos:
```
[cfg]
activateweekly = True
weeklylocation = DE
weeklyrepo = 0.23
testingppa = False

```content of /etc/apt/sources.list.d/mythbuntu-repos.list:
```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu maverick main
deb http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu maverick main
deb-src http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu maverick main


```

After changing it from 0.23 to 0.23.1 in /etc/default/mythbuntu-repos do you still get the error when trying to launch mythbuntu-control-centre?

---

### Post by alien878 on 2010-10-17
> **tgm4883 said:**
> After changing it from 0.23 to 0.23.1 in /etc/default/mythbuntu-repos do you still get the error when trying to launch mythbuntu-control-centre?I changed it in both /etc/default/mythbuntu-repos and /etc/apt/sources.list.d/mythbuntu-repos.list.  Mythbuntu-control-center works fine, no errors.

I did just do a double upgrade 9.10-10.04-10.11.  Maybe something in the upgrade process messed up the files.

---

### Post by tgm4883 on 2010-10-17
> **alien878 said:**
> I changed it in both /etc/default/mythbuntu-repos and /etc/apt/sources.list.d/mythbuntu-repos.list.  Mythbuntu-control-center works fine, no errors.

I did just do a double upgrade 9.10-10.04-10.11.  Maybe something in the upgrade process messed up the files.

No, I think I know what happened. Looks like a legit bug. I don't think I accounted for when people upgrade distros that they might have versions selected that don't exist anymore. Can you file a bug on that, I'm working on some other stuff at the moment but don't want to forget about this as I'm sure more people will run into it.

---

