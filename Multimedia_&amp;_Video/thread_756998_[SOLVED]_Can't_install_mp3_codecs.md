---
title: "[SOLVED] Can't install mp3 codecs"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by IHATEDLINK on 2008-04-16
heyy
I installed Ubuntu 7.10 like, TODAY and i can't get the mp3's codecs to work, here's my first try to get it working:

Clicked "SEARCH"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66149&stc=1&d=1208366899[/IMG]

Clicked "CONFIRM"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66150&stc=1&d=1208366899[/IMG]

Clicked "Close"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66151&stc=1&d=1208366899[/IMG]

I already installed Universe and Multiverse
Any help?
Thanks in advance

---

### Post by pytheas22 on 2008-04-16
What is the output if you type on the command line:

```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

### Post by IHATEDLINK on 2008-04-16
I get the following message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Synaptic doesn't work!!! What am i suposed to do now?

---

### Post by pytheas22 on 2008-04-16
Run the command:

```
sudo dpkg --configure -a
```

then try opening Synaptic again.  This should fix the problem and allow you to install the codecs.

---

### Post by IHATEDLINK on 2008-04-16
YAY, it works again!
THANK YOU FOR THAT!
I still can't download the codecs, i get the foloowing:

paco@paco-ubuntu:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                              Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages


Any ideas?

---

### Post by IHATEDLINK on 2008-04-16
Hey again
After fixing Symantic I tried downloading the package files from Package Manager and i got the following

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66164&stc=1&d=1208379630[/IMG]

Does it take so much to get a mp3 playing in Ubuntu?
I guess having the best OS available comes at it's price :(

---

### Post by pytheas22 on 2008-04-16
It looks like there might be some problem with the repositories, because Synaptic is saying that it can't locate needed packages.

Which version of Ubuntu are you using--Gutsy 7.10, Hardy 8.04, something else...?  And what kind of processor do you have (Intel 32-bit, AMD 32-bit, 64-bit, ppc...)?  In case you aren't sure, use the utility at System>Administration>System Monitor.

Also, please post the output of the command:

```
cat /etc/apt/sources.list
```

With that information maybe we can figure out why the package manager seems unable to find the packages it needs.

---

### Post by IHATEDLINK on 2008-04-16
Ubuntu Gutsy Gibson
32-bit Intel Pentium 4 CPU 1.80GHz

The output gave me this:

paco@paco-ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Thanks!

---

### Post by pytheas22 on 2008-04-16
This explains the problem--for some reason all of the repositories are disabled for you, hence Synaptic's inability to find the packages it wants.  It looks like maybe something weird happened and the installer disabled the repositories for some reason.

In any case, to solve this problem, do this:

In a terminal, type:

```
sudo gedit /etc/apt/sources.list
```

Then in the text editor that pops up, copy and paste the following content:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse restricted universe main
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
```

You can delete the stuff was originally in the file or you can leave it; it doesn't matter because it's all commented out and Synaptic will just ignore it.

Save the file and close the text editor.

Finally, open Synaptic again.  In the upper-left corner is a button with a blue arrow that says "Reload."  Click it, and try installing the mp3 codecs again.  Let me know if it works.

---

### Post by IHATEDLINK on 2008-04-17
IT WORKS AGAIN!!!
:D:D:D:D
Thanks a lot for your help!!

---

### Post by cornelius80 on 2008-04-24
Hi everyone,.. I had that same problem too.

So, I followed the details instructions carefully and it works for me too!

thank you all,
Cornelius
:guitar:

---

### Post by IHATEDLINK on 2008-04-25
glad my post helped, LOL
Don't forget to thank the helpers clicking on their the little star button!
they do a great job making linux easy for everyone

---

