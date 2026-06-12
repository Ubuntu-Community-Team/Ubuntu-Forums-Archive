---
title: "Flash player installation pain"
date: 2009-07-15
forum: Multimedia Software
---

### Post by theumang on 2009-07-15
This is the error I get when I choose one of the options from the plugin suggester on firefox.

I am running 9.04 (installed 4 hours ago) on a amd proc pc

---

### Post by x33a on 2009-07-15
try
```
sudo aptitude install flashplugin-nonfree
```
in a terminal.

---

### Post by theumang on 2009-07-15
Thanx for that Quick response!

umang@ubuntu:~$ sudo aptitude install flashplugin-nonfree
[sudo] password for umang: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
umang@ubuntu:~$

---

### Post by x33a on 2009-07-15
yes, please first close synaptic or add/remove if you have opened it. then try this again.

---

### Post by vinutux on 2009-07-15
Close all other apt-get gui's - Add/remove, Update manager, Synaptic and terminals with apt-get.

Then retry....

---

### Post by theumang on 2009-07-15
Ahhaaa..
its @ 38% as I type

EDIT:

Done.... works like charm, thanx **x33a** :KS & **vinutux** :KS
This friendly community ensures that I stay here for quite some time now.

---

### Post by vinutux on 2009-07-15
okey mark thead as SOLVED..

---

### Post by lovinglinux on 2009-07-15
You might also want to remove other flash plugins, to avoid conflicts, with this command:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by igorzwx on 2009-07-15
no problems, nothing to dramatize

make this:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

and relax.

It works even for Ubuntu 8.04,
but other Medi-repos should be enabled.

---

### Post by theumang on 2009-07-15
Hey... iDunno how to mark the thread title as solved... I tried looking for that option, Tried editing the thread, unable to rename the title :(

---

### Post by vinutux on 2009-07-15
> **theumang said:**
> Hey... iDunno how to mark the thread title as solved... I tried looking for that option, Tried editing the thread, unable to rename the title :(

**Thread tools->mark this thread solved**

.

---

### Post by theumang on 2009-07-15
Oh Nice.... but I am having an issue now :(

when I try to install anything from synaptic or terminal commands, the following error appears : 

No apport report written because MaxReports is reached already
                                                       
Setting up unrar (1:3.8.5-1) ...

Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
 mozilla-plugin-gnash
 swfdec-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is when I tried installing a rar extractor with the command :
sudo apt-get install unrar

---

### Post by theumang on 2009-07-15
> **lovinglinux said:**
> You might also want to remove other flash plugins, to avoid conflicts, with this command:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
```
I tried that.... error :

umang@ubuntu:~$ sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash swfdec-mozilla
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 541kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133021 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing swfdec-mozilla ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
dpkg: error processing swfdec-mozilla (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
 swfdec-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't think I am made for Ubuntu, I am just an Epic fail!

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> I tried that.... error :

umang@ubuntu:~$ sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash swfdec-mozilla
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 541kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133021 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing swfdec-mozilla ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
dpkg: error processing swfdec-mozilla (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
 swfdec-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't think I am made for Ubuntu, I am just an Epic fail!

It's because you have 4 packages not fully installed or removed, so they are messing with the other attempts of installing stuff. Run the command below to fix this:

```
dpkg --configure -a
```

Then:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by theumang on 2009-07-15
> **lovinglinux said:**
> It's because you have 4 packages not fully installed or removed, so they are messing with the other attempts of installing stuff. Run the command below to fix this:

```
dpkg --configure -a
```

Then:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```
Just > dpkg --configure -a dint work, It came up with dpkg: requested operation requires superuser privilege
So I put the word prefixed it with sudo.

then tried the 5 commands
Now I ended up with the following :
Errors were encountered while processing:
 flashplugin-installer
 mozilla-plugin-gnash
 swfdec-mozilla
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> Just  dint work, It came up with dpkg: requested operation requires superuser privilege
So I put the word prefixed it with sudo.

then tried the 5 commands
Now I ended up with the following :
Errors were encountered while processing:
 flashplugin-installer
 mozilla-plugin-gnash
 swfdec-mozilla
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Try 

```
sudo dpkg --configure unrar
```

if that doesn't work, try

```

sudo apt-get purge unrar
```

Then

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by theumang on 2009-07-15
I have posted terminal activity for the steps you suggested in the last post.

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> I have posted terminal activity for the steps you suggested in the last post.


I have found the solution.

First paste the output of this command:

```
ls -l /var/lib/dpkg/alternatives/*flash*
```

---

### Post by theumang on 2009-07-15
> umang@ubuntu:~$ ls -l /var/lib/dpkg/alternatives/*flash*
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/iceape-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/iceweasel-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/midbrowser-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
-rw-r--r-- 1 root root 0 2009-07-15 12:23 /var/lib/dpkg/alternatives/xulrunner-flashplugin

Too mucha garbage, eh ?

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> Too mucha garbage, eh ?

Run this:

```
sudo rm -f /var/lib/dpkg/alternatives/firefox-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/iceape-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/iceweasel-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/midbrowser-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/mozilla-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/xulrunner-flashplugin 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by theumang on 2009-07-15
I believe we missed the rm command for gnash...

Posting few parts where the word error comes up

> umang@ubuntu:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133677 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash


> umang@ubuntu:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32ncurses5 nspluginwrapper ia32-libs libc6-i386 lib32gcc1 lib32asound2
  flashplugin-installer lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133677 files and directories currently installed.)
Removing flashplugin-nonfree ...
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/1766B of archives.
After this operation, 41.0kB of additional disk space will be used.
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 133675 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.22.87ubuntu2_amd64.deb) ...
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Setting up flashplugin-nonfree (10.0.22.87ubuntu2) ...
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133677 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ 

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> I believe we missed the rm command for gnash...

Posting few parts where the word error comes up


Try this:

```
sudo rm -f /var/lib/dpkg/alternatives/firefox-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/iceape-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/iceweasel-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/midbrowser-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/mozilla-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
sudo rm -f /var/lib/dpkg/alternatives/xulrunner-flashplugin 
sudo dpkg --configure mozilla-plugin-gnash
sudo apt-get autoremove
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by theumang on 2009-07-15
I did not do the last two as they have a loooooooooong activity listed & do not have nething to do with gnash..

Other than that, everything is here :

> umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/firefox-flashplugin
[sudo] password for umang: 
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/iceape-flashplugin
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/iceweasel-flashplugin
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/midbrowser-flashplugin
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/mozilla-flashplugin
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
umang@ubuntu:~$ sudo rm -f /var/lib/dpkg/alternatives/xulrunner-flashplugin 
umang@ubuntu:~$ sudo dpkg --configure mozilla-plugin-gnash
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
umang@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133677 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin

I really appreciate your patience **lovinglinux**
Its about 3:15 in the early morning where I am...
We are missing something...
Do you need something else so that you could research on it ?

I'd Like go to bed once I respond to your next reply.

Getting a flashplayer & unrar work is so tedious...

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> I did not do the last two as they have a loooooooooong activity listed & do not have nething to do with gnash..

Other than that, everything is here :



I really appreciate your patience **lovinglinux**
Its about 3:15 in the early morning where I am...
We are missing something...
Do you need something else so that you could research on it ?

I'd Like go to bed once I respond to your next reply.

Getting a flashplayer & unrar work is so tedious...

Last try :)

```
sudo apt-get purge gnash-common gnash mozilla-plugin-gnash
```

---

### Post by theumang on 2009-07-15
Last try... for now :)

> umang@ubuntu:~$ sudo apt-get purge gnash-common gnash mozilla-plugin-gnash
[sudo] password for umang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnash* gnash-common* mozilla-plugin-gnash*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 7819kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133677 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing gnash ...
Removing gnash-common ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing gnash-common (--purge):
 subprocess post-removal script returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 mozilla-plugin-gnash
 gnash-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


no rm command... yet ?
you are the boss, am going to sleep btw, will check this space tomorrow, obviously, rofl

I am going to have these commands as a Nightmare now, lol..

---

### Post by lovinglinux on 2009-07-15
> **theumang said:**
> Last try... for now :)



no rm command... yet ?
you are the boss, am going to sleep btw, will check this space tomorrow, obviously, rofl

I am going to have these commands as a Nightmare now, lol..

Good sleep :)

---

### Post by SyanTK on 2009-07-16
Adding some fuel to the fire here... or fire to the fuel :(

I somehow managed to google myself all the way to this post! Yay!

I have the exact same problem with Gnash.. I just want it to go away!!

Anyway.. I've gone through all the steps as well and nothing worked.

The only diff is that am running on a PS3 system.

Ill check back to see how this progresses.

---

### Post by lovinglinux on 2009-07-16
> **SyanTK said:**
> Adding some fuel to the fire here... or fire to the fuel :(

I somehow managed to google myself all the way to this post! Yay!

I have the exact same problem with Gnash.. I just want it to go away!!

Anyway.. I've gone through all the steps as well and nothing worked.

The only diff is that am running on a PS3 system.

Ill check back to see how this progresses.

Check this discussion [http://ubuntuforums.org/showthread.php?t=1075776](http://ubuntuforums.org/showthread.php?t=1075776)

---

### Post by theumang on 2009-07-16
Hey!

when I tried ls -l /var/lib/dpkg/alternatives/*flash* from that thread... I get
ls: cannot access /var/lib/dpkg/alternatives/*flash*: No such file or directory

How do I install phimBHflashplugin so that I could leave it there ?
Hang on, does that mean I am getting the error just because I do not have that dir et al ?

---

### Post by theumang on 2009-07-17
> **theumang said:**
> Hey!

when I tried ls -l /var/lib/dpkg/alternatives/*flash* from that thread... I get
ls: cannot access /var/lib/dpkg/alternatives/*flash*: No such file or directory

How do I install phimBHflashplugin so that I could leave it there ?
Hang on, does that mean I am getting the error just because I do not have that dir et al ?
Bump

---

### Post by lovinglinux on 2009-07-17
> **theumang said:**
> Bump

Probably because you don't have any flash related files inside it.

What is your current situation?

Try again

```
sudo dpkg --configure -a
```

Then 

```
sudo apt-get purge gnash gnash-common mozilla-plugin-gnash
```

---

### Post by theumang on 2009-07-17
This is what I got

> umang@ubuntu:~$ sudo dpkg --configure -a
umang@ubuntu:~$ sudo apt-get purge gnash gnash-common mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134813 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by theumang on 2009-07-17
I got this Red circle with a - sign in it by the clock.
The update manager suggests me to install gnash & gnash-common
I Tried installing both of them, got an error : 
You have 1 broken package on your system!
Use the "Broken" filter to locate it.

---

### Post by lovinglinux on 2009-07-17
> **theumang said:**
> I got this Red circle with a - sign in it by the clock.
The update manager suggests me to install gnash & gnash-common
I Tried installing both of them, got an error : 
You have 1 broken package on your system!
Use the "Broken" filter to locate it.

I wish there was a command like *sudo apt-get send-to-hell mozilla-plugin-gnash* :)

---

### Post by lovinglinux on 2009-07-17
I've found a solution:

```
sudo aptitude download mozilla-plugin-gnash
```

```
sudo dpkg --force-overwrite --install mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb
```

```
sudo apt-get purge mozilla-plugin-gnash
```

```

sudo apt-get install flashplugin-nonfree
```

```
sudo rm mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb
```

---

### Post by theumang on 2009-07-18
Remember ? I told U that I have an amd proc ?
Unsure that i386.deb could help...

> umang@ubuntu:~$ sudo aptitude download mozilla-plugin-gnash
[sudo] password for umang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe mozilla-plugin-gnash 0.8.5-0ubuntu1 [40.8kB]
Fetched 40.8kB in 1s (24.0kB/s)              
umang@ubuntu:~$ sudo dpkg --force-overwrite --install mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb
dpkg: error processing mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb
umang@ubuntu:~$ sudo apt-get purge mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 gnash-common libboost-thread1.34.1 gnash
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-plugin-gnash*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... y
134901 files and directories currently installed.)
Removing mozilla-plugin-gnash ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)
umang@ubuntu:~$ sudo rm mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb
rm: cannot remove `mozilla-plugin-gnash_0.8.5-0ubuntu1_i386.deb': No such file or directory


---

### Post by lovinglinux on 2009-07-18
> **theumang said:**
> Remember ? I told U that I have an amd proc ?
Unsure that i386.deb could help...

:oops: sorry. 

Download from [http://packages.ubuntu.com/search?searchon=names&keywords=mozilla-plugin-gnash](http://packages.ubuntu.com/search?searchon=names&keywords=mozilla-plugin-gnash)

---

### Post by x33a on 2009-07-18
> **theumang said:**
> Remember ? I told U that I have an amd proc ?
Unsure that i386.deb could help...

afaik, i386 debs work just fine on amd 32 bit, but for 64 bit you need, amd specific packages. correct me if i am wrong.

---

