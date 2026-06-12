---
title: "Videos choppy, tried installing ununtu-restricted-extras, error code"
date: 2013-04-18
forum: Multimedia Software
---

### Post by StealthMode on 2013-04-18
I have been trying to get my flash videos to work, as they have been choppy for about a week or so. Not sure what I blew up, but something changed. I tried using Synaptic to install flashplugin-installer and its dependent packages. I run into an error code that mentions flashplugin-nonfree. 

```
Errors were encountered while processing: flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can someone help me. I have even tried removing flashplugin-nonfree as root and still can't get rid of it.

---

### Post by StealthMode on 2013-04-20
Anyone? Is this a flash problem perhaps? Or something else? I'm pretty sure I have the restricted repository installed.

EDIT: Just tried installing ubuntu-restricted-extras and this is what I got for results

```
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) .../var/lib/dpkg/info/flashplugin-nonfree.postinst: 38: cd: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by claracc on 2013-04-21
flashplugin-installer is in conflict with flashplugin-nonfree.

So, uninstall flashplugin-nonfree and install flashplugin-installer

---

### Post by StealthMode on 2013-04-21
I can't uninstall flashplugin-nonfree. I tried through synaptic to mark for complete removal, and it wouldn't work. Then I tried to mark flashplugin-installer for installation, which would automatically uninstall nonfree, and it gave me this error:
```
(Reading database ... 640508 files and directories currently installed.)Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 38: cd: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

EDIT: I have tried sudo apt-get install adobe-flashplugin with these results: 
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,729 kB of archives.
After this operation, 18.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package adobe-flashplugin.
(Reading database ... 640731 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.280-0precise1_i386.deb) ...
Selecting previously unselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.280-0precise1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 38: cd: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up adobe-flashplugin (11.2.202.280-0precise1) ...
No apport report written because MaxReports is reached already
                                                              update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
Setting up adobe-flash-properties-gtk (11.2.202.280-0precise1) ...
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also tried sudo apt-get remove --purge flashplugin-nonfree with these results: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 168 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 640746 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then I entered: sudo dpkg -l| grep flash with these results:
```
ii  adobe-flash-properties-gtk                11.2.202.280-0precise1                                     GTK+ control panel for Adobe Flash Player plugin version 11
ii  adobe-flashplugin                         11.2.202.280-0precise1                                     Adobe Flash Player plugin version 11
pF  flashplugin-nonfree                       10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 Adobe Flash Player plugin installer

```

And finally I entered: sudo dpkg -P flashplugin-nonfree with these results: 
```
(Reading database ... 640746 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
```

I was following instructions from another thread, and it seems that the things that worked for others have not worked for me. Any ideas anyone?

EDIT 2: Ok, just tried this: sudo dpkg -r --force-remove-reinstreq flashplugin-nonfree  per instructions from the bottom of this page [http://ubuntuforums.org/showthread.php?t=1352683&page=2](http://ubuntuforums.org/showthread.php?t=1352683&page=2) , and still no luck! Turns out I got the same result as the person on page 3. 
```
(Reading database ... 640746 files and directories currently installed.)Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
```

---

### Post by StealthMode on 2013-04-23
Bump, please can someone help?

---

### Post by StealthMode on 2013-04-25
Anyone?

---

### Post by claracc on 2013-04-26
> **StealthMode said:**
> Anyone?

Have you tried the ways to remove flashplugin-non free given in this thread?: [http://ubuntuforums.org/showthread.php?t=1352683&page=2](http://ubuntuforums.org/showthread.php?t=1352683&page=2)

---

### Post by StealthMode on 2013-04-26
yes, I followed the same thread and posted my results in my super long post.

---

### Post by dentaku65 on 2013-04-26
Try
```
sudo dpkg --force-all -P flashplugin-nonfree
```

---

### Post by StealthMode on 2013-04-26
Ok did that and this here is the result. (I wish I better understood what it's trying to tell me!) 

```
sudo dpkg --force-all -P flashplugin-nonfree[sudo] password for lex-luthor: 
(Reading database ... 640727 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

```

---

### Post by dentaku65 on 2013-04-26
Are you using Iceape browser?
If not try:
```
sudo update-alternatives --remove-all iceape-flashplugin
```

Then:
```
sudo apt-get install aptitude
sudo aptitude reinstall flashplugin-nonfree

```

Please post the content:
```
ls -al /var/lib/dpkg/info/adob*
```
and
```
ls -al /var/lib/dpkg/info/flash*
```

---

### Post by StealthMode on 2013-04-26
No, I'm not using Iceape. I'm using Chrome. I will run these codes and edit this post shortly.

Ok, here we go.
```
lex-luthor@lexluthor:~$ sudo update-alternatives --remove-all iceape-flashplugin[sudo] password for lex-luthor: 
update-alternatives: error: no alternatives for iceape-flashplugin.

```

```
sudo apt-get install aptitudeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.46.1 libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libcwidget3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,785 kB of archives.
After this operation, 8,351 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 i386 1.46.1-7ubuntu3 [39.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 i386 0.5.16-3.1ubuntu1 [392 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main aptitude i386 0.6.6-1ubuntu1.1 [2,353 kB]
Fetched 2,785 kB in 5s (536 kB/s)     
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 640728 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_i386.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_i386.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1.1_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 38: cd: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1.1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo aptitude reinstall flashplugin-nonfreeThe following packages will be REINSTALLED:
  flashplugin-nonfree 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 38: cd: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         

```

```
 ls -al /var/lib/dpkg/info/adob*ls: cannot access /var/lib/dpkg/info/adob*: No such file or directory
```

```
ls -al /var/lib/dpkg/info/flash*-rwxr-xr-x 1 root root 1394 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.config
-rw-r--r-- 1 root root  706 Apr 14 22:51 /var/lib/dpkg/info/flashplugin-nonfree.list
-rw-r--r-- 1 root root  241 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.md5sums
-rwxr-xr-x 1 root root 4781 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.postinst
-rwxr-xr-x 1 root root  206 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.postrm
-rwxr-xr-x 1 root root 3279 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.prerm
-rw-r--r-- 1 root root 8183 Jul 12  2008 /var/lib/dpkg/info/flashplugin-nonfree.templates

```

Seems like no matter what I try to install, it keeps puking on the flashplugin-nonfree package. I can't seem to force remove it either.

---

### Post by dentaku65 on 2013-04-27
Try:
```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree*
```
```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

But are you sure aboute Iceape?
In one of your previous post I read:
> Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.


---

### Post by StealthMode on 2013-04-29
Here is what I got: 
```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree*rm: cannot remove `/var/lib/dpkg/info/flashplugin-nonfree*': No such file or directory
```

```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
(Reading database ... 
dpkg: warning: files list file for package `flashplugin-nonfree' missing, assuming package has no files currently installed.
(Reading database ... 640847 files and directories currently installed.)
Removing flashplugin-nonfree ...

```

Seems like maybe that worked...? Should I now try installing flashplugin-installer?

---

### Post by StealthMode on 2013-04-29
Looks like it might have finally worked. I'm going to install flashplugin-installer and give YouTube a shot. Are there any other plugins or packages that might help video playback?

EDIT: I have NO idea why my machine was mentioning IceApe. I don't have IceApe installed, that I'm aware of. I have FireFox and Chrome, and I usually use Chrome.

---

### Post by StealthMode on 2013-04-29
ARGH, video still doesn't work properly. Still choppy. Could it be some other kind of problem, unrelated to plugins? I know it's not my internet connection.

---

### Post by StealthMode on 2013-04-29
I solved my problem. Thanks dentaku65 for helping me get rid of flashplugin-nonfree, I finally found the solution to my problem here. 

[http://askubuntu.com/questions/142662/how-to-solve-jitter-or-stutter-playback-via-chrome-flash-plugin](http://askubuntu.com/questions/142662/how-to-solve-jitter-or-stutter-playback-via-chrome-flash-plugin)

This only worked finally after uninstalling flashplugin-nonfree. Thanks again!

---

### Post by claracc on 2013-04-30
> **StealthMode said:**
> I solved my problem. Thanks dentaku65 for helping me get rid of flashplugin-nonfree, I finally found the solution to my problem here. 

[http://askubuntu.com/questions/142662/how-to-solve-jitter-or-stutter-playback-via-chrome-flash-plugin](http://askubuntu.com/questions/142662/how-to-solve-jitter-or-stutter-playback-via-chrome-flash-plugin)

This only worked finally after uninstalling flashplugin-nonfree. Thanks again!

Please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

