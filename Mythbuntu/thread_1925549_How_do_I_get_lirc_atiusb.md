---
title: "How do I get lirc_atiusb?"
date: 2012-02-14
forum: Mythbuntu
---

### Post by bensuffolk on 2012-02-14
I have installed a clean version of mythbuntu 64 bit version of 11.10 and have tried to setup my ATI Remote Wonder but it seems I am missing the lira_atiusb module :-

root@mythtv:/ modprobe lirc_atiusb
FATAL: Module lirc_atiusb not found.

I have seen various posts suggesting I need to get "lirc-modules-source" however that results in an error :-

root@mythtv:/# apt-get install lirc-modules-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lirc-modules-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lirc:i386 lirc

E: Package 'lirc-modules-source' has no installation candidate

If anybody can point me in the right direction I would be very grateful.

Regards

Ben

---

### Post by drmrgd on 2012-02-14
Based on the error message, it looks like the package "lirc-modules-source" has been replaced and is no longer available.  The package manager is suggesting the package lirc as a replacement.  Try:

```
sudo apt-get install lirc
```

I think that should fix it for you.

---

### Post by bensuffolk on 2012-02-15
HI,

Thanks for the idea, although I should probably have said I have lirc already installed (via the package) and the relevant module I need is not included in it for some reason.

Regards

Ben

---

### Post by drmrgd on 2012-02-15
> **bensuffolk said:**
> HI,

Thanks for the idea, although I should probably have said I have lirc already installed (via the package) and the relevant module I need is not included in it for some reason.

Regards

Ben

Hmmm...OK.  This is a bit out of my realm as I don't run Mythbuntu, and I don't have one of these remotes.  I did find, though, that the module is no longer available for some reason, and there is a bug report about it:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787742](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787742)

However, from a few posts here, I did find some potential information and workarounds, which may help depending on what you're trying to do:

[http://ubuntuforums.org/showthread.php?t=1743470](http://ubuntuforums.org/showthread.php?t=1743470)
[http://ubuntuforums.org/showthread.php?p=11451916](http://ubuntuforums.org/showthread.php?p=11451916)

Also found this on mythtvtalk.com, which may be relevant:

[http://www.mythtvtalk.com/how-i-got-my-ati-remote-work-ubuntu-11-10-a-15245/](http://www.mythtvtalk.com/how-i-got-my-ati-remote-work-ubuntu-11-10-a-15245/)

Sorry I couldn't help more!

---

### Post by bensuffolk on 2012-02-15
Thanks,

I'll have a good read though them. Its a shame really I had it all working on Mythdora, but it was a few years old and thought I should update to the latest mythtv, and mythdora has been dropped and mythbuntu looked like the best bet, but this looks like its going to be a lot of work just to get a remote working again :-(

Regards

Ben

---

