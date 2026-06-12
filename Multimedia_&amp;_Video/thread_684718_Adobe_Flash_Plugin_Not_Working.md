---
title: "Adobe Flash Plugin Not Working"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by sportman1280 on 2008-02-01
I have the nonfree adobe flash 9 plugin installed, however websites are still saying i dont have flash installed.  Any ideas on steps to take?

---

### Post by jan quark on 2008-02-01
try my guide it should work

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by GreenMeanie on 2008-02-01
If using firfox just goto youtube and when the popup comes on the screen install it that way.

---

### Post by sportman1280 on 2008-02-01
that method doesnt work because its already installed....

---

### Post by wolfen69 on 2008-02-01
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by jcrosbie on 2008-02-02
Hi,

I've been following some of the threads on the forum with interest (vids on YouTube not playing, problem with flash plugin) I downloaded the flash-plugin from the Adobe site directly as a tarball.  I un-installed gnash beforehand.  It worked fine.  I can view vids on YouTube now.

---

### Post by amlucent23 on 2008-02-02
I think you have the same problem as I do.. It seems to me (could be wrong) that the ftp site is dishing out a corrupt version of flash and it wont install correctly...

run 

sudo apt-get purge flashplugin-nonfree

sudo apt-get clean

then reinstall the plugin and watch the out put very carefully and see if it looks like this (see attached) in the end.

---

### Post by RomeReactor on 2008-02-02
> **amlucent23 said:**
> I think you have the same problem as I do.. It seems to me (could be wrong) that the ftp site is dishing out a corrupt version of flash and it wont install correctly...

run 

sudo apt-get purge flashplugin-nonfree

sudo apt-get clean

then reinstall the plugin and watch the out put very carefully and see if it looks like this (see attached) in the end.

Hi. This problem has been discussed many times, and it's directly related to [this bug]("http://ubuntuforums.org/showthread.php?t=636397"). To get Flash working, download one of the following packages:

* [flashplugin-nonfree for Ubuntu 7.10 32-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")
* [flashplugin-nonfree for Ubuntu 7.10 64-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

Close Firefox, and double-click the package to install. Make sure gnash is not installed:
```
sudo aptitude remove --purge gnash mozilla-plugin-gnash
```

---

### Post by Shrek X on 2008-02-02
Hot damn, I have been fighting this one for 2 days with no results, your fix did it!  


> **RomeReactor said:**
> Hi. This problem has been discussed many times, and it's directly related to [this bug]("http://ubuntuforums.org/showthread.php?t=636397"). To get Flash working, download one of the following packages:

* [flashplugin-nonfree for Ubuntu 7.10 32-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")
* [flashplugin-nonfree for Ubuntu 7.10 64-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

Close Firefox, and double-click the package to install. Make sure gnash is not installed:
```
sudo aptitude remove --purge gnash mozilla-plugin-gnash
```

---

### Post by Sproid on 2008-02-04
Hi, I want to say I've been fighting flash for so many days and thanx to you I now can see every page using flash correctly. But as was to good to be true, and now I try to install limewire and frostwire and both have incompatibility with the version of flash  I have installed, the one you suggest. Any idea to solve or other thread regarding this new problem? But thank you again for posting the info of the bug and the solution.

(I have an HP 6710b notebook with Ubuntu 7.10 64bit)

---

### Post by RomeReactor on 2008-02-04
Hi. I don' t use LimeWire or FrostWire, but as far as I know they don't use Flash--though they both use Java, so the problem might be the Java version. Please post the error message that you're getting, or launch either one from the terminal (Applications->Accessories->Terminal):
```
limewire
```
or:
```
frostwire
```
and if they leave error messages in the terminal, please post the output they leave there.

---

