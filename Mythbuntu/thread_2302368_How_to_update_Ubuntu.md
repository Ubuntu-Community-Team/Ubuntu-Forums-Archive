---
title: "How to update Ubuntu?"
date: 2015-11-09
forum: Mythbuntu
---

### Post by skyemoor on 2015-11-09
Started with a fresh build of Mythbuntu 14.04.2 32 bit on a Dell Inspiron Mini dual boot with Win7. Installed easily, configured without a hitch, and pretty much ran right out of the box. Was able to make 2 short successful recording, and everything but uPnP seemed to be working. Software Updater gave notification of new components, so I loaded those. Afterwards, could not record (but could playback, and Live TV). I could click on the program I wanted to record, but there was not change on the screen except for yellow text at the top right that said "Not Recording".

I then loaded the MythTV package from the .27 Repository. Same issues, not able to record or uPnP, but can playback and do LiveTV.

There was then one more Software Updater notification about new packages, and it asked for a reboot afterward, but there was no change in function or issues. 

There is a Mythsocket issue where it then adds a local backend, then connects back to the Master backend. Over and over.

Pastebin of mythbackend.log; [http://pastebin.com/eHzL7HRz](http://pastebin.com/eHzL7HRz)

Pastebin of mythfrontend: [http://pastebin.com/sbvVHDUk](http://pastebin.com/sbvVHDUk)

Should I just revert back to the 14.04.2 Mythbuntu and use miniDNLA for UPnP?

---

### Post by TheFu on 2015-11-09
Don't know anything about  myth, but every week, I run 2 commands on all my ubuntu-server systems.
```
sudo apt-get update
sudo apt-get upgrade
```

These update packages for a system that is currently under support. This should be universal for any debian-based distro.

Of course, daily backups are also a requirement, so if anything too terrible happens, falling back to the most recent backup is needed.  That happens about once every 3 years and never when it is convenient.

[http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) has a few more details and recommended steps.  For a media server, I wouldn't use dist-upgrade as the article recommends. There are reasons.

---

### Post by Bucky Ball on 2015-11-09
I do as TheFu (hey, that rhymes!) but add this after them:

```
sudo apt-get dist-upgrade
```

This WON'T upgrade the release to a newer one.

---

### Post by TheFu on 2015-11-09
No need to do both **upgrade** and **dist-upgrade**. Dist-upgrade does everything upgrade does plus more. If you want to stay on the same kernel line DO NOT USE dist-upgrade. Doing so will change a 5yr supported LTS 14.04.1 release into a much less supported 14.04.2 or 14.04.3 release (until Aug 2016 only).  
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) shows clearer how long the different 14.04 releases are supported.  It is a huge gotcha that many long-time Ubuntu users misunderstand.

**If you want 5 years of support on  the 14.04 release, only 14.04.1 provides it, not 14.04.2 or 14.04.3 or 14.04.4 (if released).**

This doesn't matter if you run non-LTS releases, unless you manually build kernel modules.  Some of my hardware needs manually built drivers, which is the only reason I care.

---

### Post by MoebusNet on 2015-11-10
@skymoor - Since you only have 2 short recordings, I think I would just back up (or don't) the recordings and start over with mythbutu. For clarification, Ubuntu (Mythbuntu) 14.04, 14.04.1, 14.04.2, 14.04.3 are all 'Trusty Tahr' LTS. The major difference between them is that each newer 'point' release includes all the updated and current packages but none of the outdated packages from the previous 'point' release (ie, 14.04 vs 14.04.1, 14.04.1 vs 14.04.2, etc.). This is mainly to avoid having to install an iso image then update several hundreds of megabytes of packages; instead you install the OS with all current packages as of release date. This saves bandwidth for you and the mirrors.

I believe I would make sure I have the latest iso for mythbuntu to install from; if it is problematic you can try an earlier version.

Since I don't use UPnP, I can't advise you; mine is just a combined FE/BE.

---

### Post by MoebusNet on 2015-11-10
@skymoor - Just a thought, but it occurs to me that since you can play etc your previous recordings but not record new ones, is it possible that you have an issue with your tuner(s)? Can you watch Live TV, pause Live TV, etc? I have had configuration changes that were messed up after package upgrades, so before you reinstall you might want to check _all_ of your configuration settings just as though you were setting up Myth from scratch - you may catch a configuration mistake. Just sayin'... :)

---

