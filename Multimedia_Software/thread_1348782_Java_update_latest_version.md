---
title: "Java update latest version"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Cavsfan on 2009-12-07
I have Java 6 version 15 64 bit installed.

I downloaded and installed Java 64 bit jre-6u17-linux-x64.bin

Went to Java's version checker website and it said I still had 6.15 installed and there 
was an update.  The site mentioned to put it in /usr/local/ so when it installed, 
it put it in this folder **/usr/local/jre1.6.0_17/**

So, I went back and found some instructions that said to install 
it in **/usr/share/java/jre1.6.0_17** for it to be global.
The download and instructions are found _[here]("http://java.com/en/download/help/5000011400.xml")_
So I did that and it still says on the version checker page that I am on 6.15 still :confused:
The version checker site can be found [U][here]("http://java.com/en/download/help/testvm.xml")
[/U]Can some one please tell me what I am doing wrong?
Also does any one know how I get rid of the first 2 installations? If neither of them worked.
Thanks in advance!

PS I am going to reboot and see if that changes anything.

---

### Post by Cavsfan on 2009-12-07
Still the same version 6.15 instead of 6.17 after re-booting...

---

### Post by lavinog on 2009-12-07
try running this command in a terminal and see what you get
```

ls -l /usr/lib/mozilla/plugins/

```

you should see a line like this:
```

lrwxrwxrwx 1 root root      39 2009-11-13 19:13 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

```
then check that symlink:
```

ll /etc/alternatives/mozilla-javaplugin.so

```
most likely that will point to the old version.

---

### Post by ccleanerfan on 2009-12-07
```
ll /etc/alternatives/mozilla-javaplugin.so
ll: command not found


```

---

### Post by lavinog on 2009-12-07
sorry, ll is an alias for ls -l on my machine
```

ls -l /etc/alternatives/mozilla-javaplugin.so

```

---

### Post by Cavsfan on 2009-12-08
ls -l /usr/lib/mozilla/plugins/
```
total 364
-rw-r--r-- 1 root root   6120 2009-11-03 05:58 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 101536 2009-11-11 04:15 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 106240 2009-11-11 04:15 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  72816 2009-11-11 04:15 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  81336 2009-11-11 04:15 libtotem-narrowspace-plugin.so
```ls -l /etc/alternatives/mozilla-javaplugin.so

```
$ ls -l /etc/alternatives/mozilla-javaplugin.so
ls: cannot access /etc/alternatives/mozilla-javaplugin.so: No such file or directory
$
```There is no directory or file called mozilla-javaplugin.so in /etc/alternatives/
I manually checked.

Thanks!

---

### Post by lavinog on 2009-12-08
Did you manually install the previous version?
try
ls -l ~/.mozilla/plugins

---

### Post by Yellow Pasque on 2009-12-08
You're making it too hard. Just grab .debs from a PPA: [https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)

---

### Post by ccleanerfan on 2009-12-09
> **Temüjin said:**
> You're making it too hard. Just grab .debs from a PPA: [https://launchpad.net/~voronov84/+archive/andreyv]("https://launchpad.net/%7Evoronov84/+archive/andreyv")
Installs fine, doesn't work on Firefox 3.6 Beta 5 though.

---

### Post by Cavsfan on 2009-12-09
> **Temüjin said:**
> You're making it too hard. Just grab .debs from a PPA: [https://launchpad.net/~voronov84/+archive/andreyv]("https://launchpad.net/%7Evoronov84/+archive/andreyv")

Thanks, but I am trying to learn something. I am kind of a newbie and this should
have worked and I am trying to figure out and understand why it has not. I do 
appreciate you trying to make it easy though and I see 6.17 in that package, 
but don't see a key to add for it. I do not want to add unsigned software and have 
to OK that. Warnings are going off, sirens are screaming, and fireworks are being 
launched in the sky... (not really lol)
BTW, Java 6.15 works, but when I went to Sun Java site and it said there was an 
update for Karmic x64 (jre-6u17-linux-x64.bin). When I say it works, I mean a website 
displays an arrow with an F on it indicating flash.

> **lavinog said:**
> Did you manually install the previous version?
try
ls -l ~/.mozilla/plugins

I think I got version 6.15 from a Tutorial on adding flash to x64 systems.

The output of "ls -l ~/.mozilla/plugins" is
-rwxr-xr-x 1 cavsfan cavsfan 9560488 2009-07-18 00:04 libflashplayer.so

By the way does "~/.mozilla/plugins" mean a directory named mozilla in my home directory and the ~ sign means my home directory?

Thanks!

---

### Post by Cavsfan on 2009-12-09
I searched for javaplugin and found 7 places:

/etc/alternatives/xulrunner-1.9-javaplugin.so
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libjavaplugin_jni.so
/usr/lib/ure/lib/sunjavaplugin.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
/usr/local/jre1.6.0_17/lib/amd64/libjavaplugin_jni.so
/usr/share/java/jre1.6.0_17/lib/amd64/libjavaplugin_jni.so
/var/lib/dpkg/alternatives/xulrunner-1.9-javaplugin.so

I have FireFox version 3.5.5.

:confused: I am so confused!!  "calm down" I tell myself... LOL

Thanks for taking the time!

---

### Post by lavinog on 2009-12-09
> **Cavsfan said:**
> I searched for javaplugin and found 7 places:

/etc/alternatives/xulrunner-1.9-javaplugin.so
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libjavaplugin_jni.so
/usr/lib/ure/lib/sunjavaplugin.so
/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
/usr/local/jre1.6.0_17/lib/amd64/libjavaplugin_jni.so
/usr/share/java/jre1.6.0_17/lib/amd64/libjavaplugin_jni.so
/var/lib/dpkg/alternatives/xulrunner-1.9-javaplugin.so

I have FireFox version 3.5.5.

:confused: I am so confused!!  "calm down" I tell myself... LOL

Thanks for taking the time!
use ls -l to see if any of those are symlinks to the old version.
I am thinking the one in etc/alternatives is

---

### Post by Cavsfan on 2009-12-10
I had used Places > Search for Files to find these, so I used terminal to get into 
/etc/alternatives/ and then typed the "ls -l"

lrwxrwxrwx 1 root root  24 2009-12-02 16:17 xulrunner -> /usr/bin/xulrunner-1.9.1
lrwxrwxrwx 1 root root  49 2009-12-07 14:05 xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so

Does the fact that the 2 files point to another file mean they are symlinks?
I may indeed learn something here!

Thanks :)

---

### Post by lavinog on 2009-12-11
> **Cavsfan said:**
> 
Does the fact that the 2 files point to another file mean they are symlinks?
I may indeed learn something here!

Thanks :)
Yes, and sometimes symlinks can point to other symlinks, so things could get spaghetti like.

---

### Post by Cavsfan on 2009-12-13
Ho do I clear this up? Uninstall xulrunner? I am not sure I need it nor do I know if this 
would solve the version problem. I supposedly have the latest version installed, but it's just not being recognized.

---

### Post by lavinog on 2009-12-14
xulrunner is part of firefox.

see if this file points to anything: /usr/lib/xulrunner-addons/plugins/libjavaplugin.so

You should find the tutorial you followed, and see how it got installed.

---

### Post by Cavsfan on 2009-12-15
Thanks lavinog!
I searched the forum for "Update Java" (I think as I can't even remember now) and found this:
[U] [COLOR=DeepSkyBlue][http://ubuntuforums.org/showthread.php?t=1330992&highlight=java+update](http://ubuntuforums.org/showthread.php?t=1330992&highlight=java+update)[/COLOR]
[/U]It points to this site: [U][COLOR=Blue][http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)[/COLOR]
[/U]which is very good and will work with future versions (I bookmarked it for sure).
I did everything it said (32 bit directions are on the left and 64 bit directions are on 
the right). and viola, I am now cooking with gas on Java 6.17.
Although, the help:about (in Mozilla) still shows 6.15 (for some odd reason).
When I went to the version tester (also mentioned on the page) it said I was using 6.17!
These instructions deal with symbolics and everything!
Bookmark the above mentioned site (for the future)!

---

