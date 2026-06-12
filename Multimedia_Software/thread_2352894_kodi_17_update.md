---
title: "kodi 17 update"
date: 2017-02-16
forum: Multimedia Software
---

### Post by valotker on 2017-02-16
**hi!!**
[COLOR=#ff0000]first, sorry about my English.[/COLOR]

second,
update kodi is failed.
I try with terminal, with Ubuntu software updater, with synaptic & try to read in google about same problem, but nothing. 

here what I am get (half of it):

```
Unpacking kodi (2:18.0~git20170216.0200-a1bf5b1-0xenial) ...
dpkg: error processing archive /var/cache/apt/archives/kodi_2%3a18.0~git20170216.0200-a1bf5b1-0xenial_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/16x16/apps/kodi.png', which is also in package kodi-data 15.2+dfsg1-3ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kodi_2%3a18.0~git20170216.0200-a1bf5b1-0xenial_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[B]thanks for the help.
beni.[/B]

---

### Post by QIII on 2017-02-16
There is absolutely no reason to apologize about your English.  Do as well as you can and we will try to help.  If language becomes a barrier, we'll see if we can find you another resource.

I have moved your post to Multimedia Software for a better fit with the subject.

Welcome to the Forums!

---

### Post by valotker on 2017-02-16
thank you my friend.

---

### Post by #&amp;thj^% on 2017-02-16
How did you install version17 on Xenial? 
If you had a link to post here... that would be good, or any instructions that you followed.

---

### Post by valotker on 2017-02-16
[http://linuxg.net/install-kodi-stable-on-ubuntu/](http://linuxg.net/install-kodi-stable-on-ubuntu/)
 
From here.
And from kodi website.

---

### Post by #&amp;thj^% on 2017-02-16
I'm afraid a outside PPA is going to be a challenge to solve here.
If it were me... I would revert my system back to a better state.
That would be via:
```
sudo apt remove kodi*
```
Followed by
```
sudo ppa-purge ppa:team-xbmc/ppa
```
This program disables a PPA from your Software Sources and reverts your
 system back to the official Ubuntu packages. You can use this to return your
 system to normal after testing a new version from a PPA.
Now see if the package manager is happy with:
```
sudo apt update && sudo apt full-upgrade
```
Now I say this with no promise you will have a working system...[COLOR=#ff0000]**in fact I highly discourage this**[/COLOR]...but you could try to force the package with:
```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install kodi`
```
**To be clear I assume no responsibility if that breaks your system.**
Again If it were me... I would revert my system back to a better state.

---

### Post by valotker on 2017-02-17
I think you were right.
I don't do nothing and now it work.
I think it's  related to the country and maybe them fix the update.

Thank you very much my friend!!!!

---

