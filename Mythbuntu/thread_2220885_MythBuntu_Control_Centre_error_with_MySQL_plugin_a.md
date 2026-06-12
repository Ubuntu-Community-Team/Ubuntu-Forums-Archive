---
title: "MythBuntu Control Centre error with MySQL plugin after 14.04 upgrade"
date: 2014-04-29
forum: Mythbuntu
---

### Post by RichardK3 on 2014-04-29
Just upgraded to 14.04LTS.  When I try to use MCC, I'm getting this error:

Exception in compareState of plugin MySQL
    Disabling Plugin

This has been reported as a bug here:

[https://www.mail-archive.com/mythbuntu-bugs@lists.launchpad.net/msg08628.html](https://www.mail-archive.com/mythbuntu-bugs@lists.launchpad.net/msg08628.html)

Just thought I'd post here, and ask if anyone has a solution....

---

### Post by dannyboy79 on 2014-05-03
i too am getting the same error. I upgraded my server from 12.04.4 to 14.04 and when I do a restore of my backup file mythtv can't connect to the database. and when I try to use various commands for updating the mythtv mysql  user password i get an error about not selecting a database. Please help I have been at this for 12 hours now trying to get my mythtv server back up and running.

---

### Post by dannyboy79 on 2014-05-09
it's as if my mythbuntu control centre app is useless due to this reoccuring error. pretty much anything I try to change using MCC i get errors so I've given up on it. My mythtv install is fine it's just frustrating that MCC isn't working. Here's some screeenshots of the errors.

[IMG]https://lh4.googleusercontent.com/-pEOym65R0kE/U2xbTED_z2I/AAAAAAAACsA/iNfDc5Eywso/s800/mythbuntu_mysql_error.png[/IMG]
[IMG]https://lh5.googleusercontent.com/-PZx8K8N2fT4/U2xbTImE4jI/AAAAAAAACsA/hmp2gx1vxNA/s800/mythbuntu_repositories_error.png[/IMG]
[IMG]https://lh4.googleusercontent.com/-yLwRxZUBtqQ/U2xbTVwCTEI/AAAAAAAACsA/02ofqYlKtgs/s800/mythbuntu_python_error.png[/IMG]

---

### Post by Al_Vampyre on 2014-05-09
Yeah, I can confirm I'm getting this as well

---

### Post by nonsense.junk on 2014-05-11
This error is stopping me from turn on the Enabling the mysql service on ethernet interfaces under the mysql tab.  Every time I choose to Enable, the setting never holds.  So my external frontends can't connect to the primary backend.  

Any one know how to enable this service via commandline/terminal?  I have been looking over the internet and have found nothing on how to do it outside of MCC.

---

### Post by dannyboy79 on 2014-05-12
yes, open up your my.cnf file located within /etc/mysql/ directory and set the bind-address to the external IP of your server (ie: 192.168.1.10) OR others have suggested that commenting out the bind-address line works as well. This will make mysql listen for connections from other sources besides localhost, then just make sure that your permissions are correct. Here's a good guide, it should still be applicable [http://emmanuelcontreras.com/content/how-setting-multiple-remote-frontend-mythtv-backend](http://emmanuelcontreras.com/content/how-setting-multiple-remote-frontend-mythtv-backend)

---

### Post by dannyboy79 on 2014-05-17
i am wondering why we haven't seen the developer of mythbuntu-control-centre pop in here yet? I thought I saw tgm.... post in another mythbuntu thread

---

### Post by tgm4883 on 2014-05-18
> **dannyboy79 said:**
> i am wondering why we haven't seen the developer of mythbuntu-control-centre pop in here yet? I thought I saw tgm.... post in another mythbuntu thread

This is a known issue, which you can help fix. The fix has been committed and is in proposed, it just needs tested and then replying to that bug report with the results.

[https://bugs.launchpad.net/mythbuntu/+bug/1316905](https://bugs.launchpad.net/mythbuntu/+bug/1316905)

---

### Post by khPWXxF on 2014-05-20
I tried to include this bug-fix but failed. I'm a novice at this so please be gentle!
I followed  [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

```
ls -l /etc/apt
total 52
drwxr-xr-x 2 root root  4096 May  8 13:27 apt.conf.d
-rw-r--r-- 1 root root    61 May 20 19:11 preferences
-rw-r--r-- 1 root root    62 May 20 19:07 preferences~
drwxr-xr-x 2 root root  4096 Apr 10 14:04 preferences.d
-rw-rw-r-- 1 root root  3032 May 20 19:25 sources.list
drwxr-xr-x 2 root root  4096 Apr 10 14:04 sources.list.d
-rw-rw-r-- 1 root root  3126 May 20 19:25 sources.list.save
-rw------- 1 root root    40 Apr 18 00:33 trustdb.gpg
-rw-r--r-- 1 root root 12926 Apr 18 00:33 trusted.gpg
drwxr-xr-x 2 root root  4096 Apr 10 14:04 trusted.gpg.d

```

```
phil@Mythtv:~$ cat /etc/apt/preferences
Package: *
Pin: release a=trusty-proposed
Pin-Priority: 400

```

Ubuntu software centre had these ticked:
- important security updates (trusty security)
- Recommended updates (trusty updates)
- unsupported updates (trusty backports)

Is that last one okay? 

  I added:
- Pre-released updates (trusty proposed)

```
phil@Mythtv:~$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms nvidia-prime
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  apport apport-gtk apport-noui gtk2-engines-pixbuf ifupdown libcgmanager0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libsdl1.2debian openssh-client openssh-server openssh-sftp-server python3-apport python3-problem-report
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst libgtk2.0-common [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst gtk2-engines-pixbuf [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgtk2.0-bin [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgtk2.0-0 [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libsdl1.2debian [1.2.15-8ubuntu1] (1.2.15-8ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst ifupdown [0.7.47.2ubuntu4] (0.7.47.2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libcgmanager0 [0.24-0ubuntu5] (0.24-0ubuntu6 Ubuntu:14.04/trusty-updates [amd64])
Inst openssh-sftp-server [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst openssh-server [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst openssh-client [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-problem-report [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport-gtk [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport-noui [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk2.0-common (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk2.0-0 (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gtk2-engines-pixbuf (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk2.0-bin (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsdl1.2debian (1.2.15-8ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf ifupdown (0.7.47.2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcgmanager0 (0.24-0ubuntu6 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-client (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-sftp-server (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-server (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-problem-report (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport-gtk (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport-noui (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])

```


I expected no upgrades to be listed, but carried on regardless:


```
phil@Mythtv:~$ sudo aptitude -t trusty-proposed
sudo: aptitude: command not found

```

Any pointers appreciated.

Phil

---

### Post by tgm4883 on 2014-05-20
> **khPWXxF said:**
> I tried to include this bug-fix but failed. I'm a novice at this so please be gentle!
I followed  [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

```
ls -l /etc/apt
total 52
drwxr-xr-x 2 root root  4096 May  8 13:27 apt.conf.d
-rw-r--r-- 1 root root    61 May 20 19:11 preferences
-rw-r--r-- 1 root root    62 May 20 19:07 preferences~
drwxr-xr-x 2 root root  4096 Apr 10 14:04 preferences.d
-rw-rw-r-- 1 root root  3032 May 20 19:25 sources.list
drwxr-xr-x 2 root root  4096 Apr 10 14:04 sources.list.d
-rw-rw-r-- 1 root root  3126 May 20 19:25 sources.list.save
-rw------- 1 root root    40 Apr 18 00:33 trustdb.gpg
-rw-r--r-- 1 root root 12926 Apr 18 00:33 trusted.gpg
drwxr-xr-x 2 root root  4096 Apr 10 14:04 trusted.gpg.d

```

```
phil@Mythtv:~$ cat /etc/apt/preferences
Package: *
Pin: release a=trusty-proposed
Pin-Priority: 400

```

Ubuntu software centre had these ticked:
- important security updates (trusty security)
- Recommended updates (trusty updates)
- unsupported updates (trusty backports)

Is that last one okay? 

  I added:
- Pre-released updates (trusty proposed)

```
phil@Mythtv:~$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms nvidia-prime
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  apport apport-gtk apport-noui gtk2-engines-pixbuf ifupdown libcgmanager0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libsdl1.2debian openssh-client openssh-server openssh-sftp-server python3-apport python3-problem-report
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst libgtk2.0-common [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst gtk2-engines-pixbuf [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgtk2.0-bin [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgtk2.0-0 [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libsdl1.2debian [1.2.15-8ubuntu1] (1.2.15-8ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst ifupdown [0.7.47.2ubuntu4] (0.7.47.2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libcgmanager0 [0.24-0ubuntu5] (0.24-0ubuntu6 Ubuntu:14.04/trusty-updates [amd64])
Inst openssh-sftp-server [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst openssh-server [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst openssh-client [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-problem-report [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport-gtk [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst apport-noui [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk2.0-common (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk2.0-0 (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gtk2-engines-pixbuf (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk2.0-bin (2.24.23-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsdl1.2debian (1.2.15-8ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf ifupdown (0.7.47.2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcgmanager0 (0.24-0ubuntu6 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-client (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-sftp-server (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-server (1:6.6p1-2ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-problem-report (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport-gtk (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf apport-noui (2.14.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])

```


I expected no upgrades to be listed, but carried on regardless:


```
phil@Mythtv:~$ sudo aptitude -t trusty-proposed
sudo: aptitude: command not found

```

Any pointers appreciated.

Phil

You should just be able to activate the proposed repo, do an "apt-get update", then do an "apt-get install mythbuntu-common"

---

### Post by dannyboy79 on 2014-05-20
he apparently doesn't want to activate the proposed repo and have other software be upgraded which is why he's trying to use pinning but it appears to not be working. 


here's a tip though, before enabling the proposed repo, did you ensure your system was all up to date? ```
sudo apt-get update && apt-get upgrade
```
once it's all up to date, then you know for sure that IF a package is going to be upgraded after you enable the -proposed repo, you know it's from the proposed repo.
If you want to use aptitude as it shows in the example of seeing what will be upgraded from the proposed repo, you need to install aptitude as it doesn't come pre-installed ubuntu.
```
sudo apt-get install aptitude
```

---

### Post by khPWXxF on 2014-05-21
Thanks for your replies.  Apologies to all that I seem to have diverted this thread from MCC to a repo tutorial.  It will be a few days before I can find time to swap disks and play again but:
 
Yes, I had upgraded software before trying it (the software updater had just run).  I was aware that other items from proposed might get included but I wasn’t aware that ‘pinning’ was the mechanism - I was just following the recipe in launchpad bugs but perhaps too blindly.
 
> You should just be able to activate the proposed repo, do an "apt-get update", then do an "apt-get install mythbuntu-common"
 
I’ll try that but would you clarify:
 
Why will it choose mythbuntu-common from the proposed repo rather than the normal one?  Because of the repo priority in /usr/apt/preferences or because of higher version numbers on the package?   If the latter, do I need the preferences file at all (none existed before)?
 
How do I subsequently prevent other ‘proposed’ items being included by sudo apt-get update && sudo apt-get upgrade. 
 
If I subsequently remove the repo and apt-get upgrade, will the package revert?
 
Thanks again for your help.
Phil

---

### Post by dannyboy79 on 2014-05-21
> **khPWXxF said:**
> 
Why will it choose mythbuntu-common from the proposed repo rather than the normal one?  Because of the repo priority in /usr/apt/preferences or because of higher version numbers on the package?   If the latter, do I need the preferences file at all (none existed before)?
it will choose the latest version of software, which just so happens to be within the -proposed repository. The only reason you need the preferences file is if you don't want ALL packages to be upgraded from the -proposed repo.
 
> **khPWXxF said:**
> 
How do I subsequently prevent other ‘proposed’ items being included by sudo apt-get update && sudo apt-get upgrade. that's done with the preferences file just as it stated in the link you had provided in an earlier post. but apparently the pinning process you followed didn't work since you were still getting packages that were going to upgrade. i am not sure, maybe your preferences file isn't formatted correctly. I have never used the preferences file, when I enable proposed, i just let it upgrade all my software.
 > **khPWXxF said:**
> 
If I subsequently remove the repo and apt-get upgrade, will the package revert?
 
Thanks again for your help.
Philaccording to tgm it will not downgrade it.

---

### Post by tgm4883 on 2014-05-21
> **dannyboy79 said:**
> it will choose the latest version of software, which just so happens to be within the -proposed repository. The only reason you need the preferences file is if you don't want ALL packages to be upgraded from the -proposed repo.
 
that's done with the preferences file just as it stated in the link you had provided in an earlier post. but apparently the pinning process you followed didn't work since you were still getting packages that were going to upgrade. i am not sure, maybe your preferences file isn't formatted correctly. I have never used the preferences file, when I enable proposed, i just let it upgrade all my software.
 yes, i believe it will downgrade it because to the system, that's the latest version available.

No, it will not downgrade the package. Otherwise, you would never be able to install a deb that wasn't in the repo.

---

### Post by gga96 on 2014-05-21
[FONT=Times New Roman]I tried tmg...  suggestion 
> 
    sudo apt-get update                   
    sudo  apt-get install mythbuntu-common

but it did NOT change the  MCC>MySQL behavior.[/FONT]

Edit: Sorry I was at the end of page one when I posted this reply.

---

### Post by RichardK3 on 2014-05-22
> **gga96 said:**
> [FONT=Times New Roman]I tried tmg...  suggestion 

but it did NOT change the  MCC>MySQL behavior.[/FONT]

Edit: Sorry I was at the end of page one when I posted this reply.

It didn't fix it for me, either.  I think I had the test code installed correctly, since "mythbuntu-common" shows version 0.74.

---

### Post by tgm4883 on 2014-05-23
Can someone run mythbuntu-control-centre from a terminal, reproduce the error, then post the messages from the terminal here?

---

### Post by RichardK3 on 2014-05-23
> **tgm4883 said:**
> Can someone run mythbuntu-control-centre from a terminal, reproduce the error, then post the messages from the terminal here?


```
richard@MythTV:~$ mythbuntu-control-centre
WARNING: Error importing plugin bare_console
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/MythbuntuControlCentre/plugin.py", line 56, in reload_plugins
    __import__(plugin, None, None, [''])
  File "/usr/share/mythbuntu/plugins/python/bare_console.py", line 29, in <module>
    import gobject
ImportError: No module named 'gobject'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 193, in compareState
    SELVER = self.convertVersion(self.repobox.get_active_text())
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 185, in convertVersion
    if VERSION.endswith(".x"):
AttributeError: 'NoneType' object has no attribute 'endswith'
richard@MythTV:~$ 

```

---

### Post by tgm4883 on 2014-05-23
> **RichardK3 said:**
> ```
richard@MythTV:~$ mythbuntu-control-centre
WARNING: Error importing plugin bare_console
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/MythbuntuControlCentre/plugin.py", line 56, in reload_plugins
    __import__(plugin, None, None, [''])
  File "/usr/share/mythbuntu/plugins/python/bare_console.py", line 29, in <module>
    import gobject
ImportError: No module named 'gobject'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 193, in compareState
    SELVER = self.convertVersion(self.repobox.get_active_text())
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 185, in convertVersion
    if VERSION.endswith(".x"):
AttributeError: 'NoneType' object has no attribute 'endswith'
richard@MythTV:~$ 

```

That is a different bug. Can you file a bug report for it at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)

---

### Post by RichardK3 on 2014-05-23
> **tgm4883 said:**
> That is a different bug. Can you file a bug report for it at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)

Done.  Bug # 1322746

---

### Post by mike_d2 on 2014-05-27
I am new to Mythbuntu, and am also experiencing this error. I have some previous linux experience, but not a ton. I am using a HDHHomerun Prime with 3 tuners. I have installed 14.04, and updated. I have gone all the way through setup of mythtv, and everything seems to be working great, channel's download from Schedulesdirect, I can tune channels with the HDHomerun GUI, and I can "sudo service mythtv-backend status" and see that the backend is up and running, except I cannot connect to the backend from my XBMC Gotham (wincrap) frontend. After going through several different forums, I find myself here, being unable to connect to mysql server as well. I think. I followed the above link and commented out the 127.0.0.1 line in the my.cnf file, and I believe I also have successfully changed the login password for mysql to "mythtv" and "mythtv", and enabled remote connections. I can also see the mysql service as up and running. But for some reason I am still unable to connect. I am having a hard time enabling the proposed repository. I am trying to follow your instructions, but is there any way someone can post a line by line of what to type and which packages to select etc. and I can hope that works. Or if anyone in here happens to have any suggestions I have been at this for 15 hours now. And I am not very good with linux, I'm not a total n00b, but I'm lost with this network tuner and myth / mysql configuration.

---

### Post by khPWXxF on 2014-05-27
Thanks for your help and patience everyone.  MCC is now working.
 
Mike_d2
You mention two quite separate issues.  MCC should now be fixed if you start a terminal session and do the following it should work:
 
```
sudo apt-get update
sudo apt-get upgrade
exit
```
 
As for the frontend, did you try running mythtv frontend before trying XBMC?
> I believe I also have successfully changed the login password for mysql to "mythtv" and "mythtv",
 
Ouch!  I hope you mean that you did this in XBMC setup rather than with mysql commands.
 
On a ‘clean’ installation the password for the database is a random string and is held in ~/.mythtv/config.xml as well as inside the database.  To see it do
 
```
cat ~/.mythtv/config.xml
```
 
It should be same in /home/mythtv/.mythtv/config.xml - one or both of those files may be a link (to I think /etc/mythtv/config.xml).  Mythtv frontend and backend both consult that in order to access the database.  XBMC will have its own mechanism for remembering the password.
 
If you really did change the mysql password then all mythtv components will fail.
 
So, the password inside the database, the config.xml files and the value you put in XBMC setup should all match.  Which ones don’t?
 
Of course, you may have other compatibility issues as well.
 
Phil

---

### Post by mike_d2 on 2014-05-27
Thanks [**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453") for the quick reply, and helping me with what I'm sure are pretty dumb questions. Did a fresh install, and "sudo apt-get update"in then a "sudo apt-get upgrade", (Got a weird message about Samba, so I chose "Keep old version" but everything else went fine). Now it seems as though MySql, and the Mythtv-backend are both up and running as they should be. I have not touched the mysql password. So you are saying do NOT change it from it's random generated password? Or if I do just to make sure that I change it in both places ?

---

### Post by khPWXxF on 2014-05-27
Yes, Samba always has thrown oddities in upgrades for me too.
 
Personal choice:  Leave the database password and the config.xml files well alone.  I prefer mythtv frontend for viewing TV recordings with just the occasional DVD but if you do want XBMC then insert the password into it at appropriate point in its installation/configuration.  Not sure whether you'll hit other issues though.

I'm not saying that changing password and config.xml file(s) won't work - it might but I'm a coward and would avoid any manual database changes if possible.

This thread has come a long way from its original topic so if you have other XBMC/Myth queries then a new thread might be preferable.

Regards

Phil

---

### Post by RichardK3 on 2014-05-29
Based on replies to the bug report from Thomas Mashos, I have resolved the errors.


First, I removed mythbuntu-bare-console in Synaptic.  That didn't (by itself) eliminate the error in MythBuntu backup, when invoked from MCC.


Next, I opened MCC and navigated to "repositories".   The menu under "Select which version..." was blank, so apparently no version was selected.  (Should I have needed to do this manually?)  I selected 0.27, and clicked "Refresh available repositories", and replied to the subsequent messages.  Then I ran "Software Updater", and some MythBuntu and MythTV updates were installed.


After that completed, I ran both a backup and a MySQL optimize within MCC without encountering the prior errors.


Thanks , Thomas!!

---

### Post by dannyboy79 on 2014-06-01
it's not fixed for me. i just tried using MCC to setup backing up my database and it just crashes MCC repeatedly. just an FYI. i use mythconverg_backup.pl via my crontab but wanted to point this out so it can get fixed.

UPDATE: i ran mythbuntu-control-centre from the terminal to see what it returned as i was trying to add the backup schedule and here's the terminal output as well as the dialog box that appeared.

terminal
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu-bare.py", line 388, in schedule_setter
    self.schedule_label_sent.set_text("Scheduled backup will be set to run daily at "+texthour+":"+textminute)
TypeError: Can't convert 'NoneType' object to str implicitly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

picture
[IMG]https://lh4.googleusercontent.com/-k744Flk4xq4/U4rIGkF7TYI/AAAAAAAACu4/6tjQ7lhF3PY/s644/mcc_error.png[/IMG]

---

