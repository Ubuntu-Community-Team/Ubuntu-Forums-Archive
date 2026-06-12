---
title: "core dumped"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Ituxlinux on 2007-11-06
Hi there;

I'm having serious problems with firefox.  It crashes NOT only when I try to view a youtube video, but sometimes when I open a link in a new tab.

Here is what I got when I open fron command line
```

itux@ubuntu704laptop:~$ firefox
Segmentation fault (core dumped)
itux@ubuntu704laptop:~$

```

I did remove the flash pluging, 
```
 rm ~/.mozilla/plugins/libflashplayer.so

```
and added a new flash
```
sudo apt-get -y install flashplugin-nonfree
```

Any idea what i"core dumped" means

---

### Post by Ituxlinux on 2007-11-07
BTW I just discovered I have the same problem in two different laptops, one with ubuntu 7.04 and the other one with 7.10 updated from 7.04

I also remember that the problem started last week after a recommended update, before that firefox was working fine.

Any ideas??

---

### Post by erginemr on 2007-11-07
"Core dump" means the crash information (content of the memory) has been written to a file after a program crashes. This file, although pretty useless for a standard end user, can be scrutinized by a programmer to identify the reason for the crash.

---

### Post by erginemr on 2007-11-07
Do you happen to remember which package did you update last week?

Or to find it out, you can check out the installed packages from Synaptic - > File Menu -> History.

---

### Post by Ituxlinux on 2007-11-08
Hi there;

Thanks for the hint. Well I started to have problen after the following update
```

Upgraded the following packages:
bsdutils (1:2.12r-17ubuntu2) to 1:2.12r-17ubuntu2.1
firefox (2.0.0.6+1-0ubuntu1) to 2.0.0.8+1nobinonly-0ubuntu1
firefox-gnome-support (2.0.0.6+1-0ubuntu1) to 2.0.0.8+1nobinonly-0ubuntu1
libkonq4 (4:3.5.6-0ubuntu20.4) to 4:3.5.6-0ubuntu20.7
libnspr4 (2:1.firefox2.0.0.6+1-0ubuntu1) to 2:1.firefox2.0.0.8+1nobinonly-0ubuntu1
libnss3 (2:1.firefox2.0.0.6+1-0ubuntu1) to 2:1.firefox2.0.0.8+1nobinonly-0ubuntu1
libssl0.9.8 (0.9.8c-4ubuntu0.1) to 0.9.8c-4ubuntu0.2
mount (2.12r-17ubuntu2) to 2.12r-17ubuntu2.1
mozilla-thunderbird (1.5.0.13-0ubuntu0.7.04) to 1.5.0.13+1.5.0.14b-0ubuntu0.7.04
openssl (0.9.8c-4ubuntu0.1) to 0.9.8c-4ubuntu0.2
util-linux (2.12r-17ubuntu2) to 2.12r-17ubuntu2.1
util-linux-locales (2.12r-17ubuntu2) to 2.12r-17ubuntu2.1

```

So FF 2.0.0.6+1 was working fine, I guess.

Is there is something else I can do to solve the crash problem, I will appreciate the help.

---

### Post by erginemr on 2007-11-08
It is not advisable to downgrade firefox of course due to security reasons. But I have also upgraded it to 2.0.0.8 and am running it fine without any issues. I think I have uninstalled firefox-gnome-support, it may be this package which is the culprit. 

Or the installed firefox extensions check for the updates from time to time, and definitely after a version upgrade. An extension for say, downloading youtube videos can cause such a crash.

If I were in your boots, I would try to isolate the problem by first disabling all extensions and trying to visit youtube and other sites. If you still happen to experience crashes, I would uninstall firefox-gnome-support package above to see what happens.

Good Luck!

P.S. What is the meaning of the latin phrase in your signature?

---

