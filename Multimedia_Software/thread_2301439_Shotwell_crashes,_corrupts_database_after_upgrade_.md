---
title: "Shotwell crashes, corrupts database after upgrade to Wily"
date: 2015-11-02
forum: Multimedia Software
---

### Post by JanneM on 2015-11-02
As the title says, after update shotwell will crash or freeze when trying to use an external editor. After that, the resulting thumbnail will retain the old image proportions and rotation, and I am unable to change things like the "star" rating of the image any longer. The Launchpad bug entry is here: [https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1511914](https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1511914)

I'd very much like to fix this somehow. But a larger question for me is if Shotwell is even supported software any longer. My confidence in it has plummeted over the past year or so. Moving to a new machine is a dangerous mess (and I can no longer have Shotwell look for new images automatically as it tries to import all images again as duplicates). And now I'm stuck with no way to edit my images at all any longer.

Perhaps I should cut my losses, give up and use something else. The question is: Move to what? And how do I rescue whatever data I can from Shotwell? I have about 15k images, all tagged and sorted, and I really can't contemplate the idea of throwing away all that metadata.

---

### Post by Bucky Ball on 2015-11-02
*Thread moved to **Multimedia Software**.*

When you say an upgrade to 15.10, did you do a clean install or upgrade via the net from 15.04? If the latter, was Shotwell working fine in 15.04?

Post the terminal output of this command between code tags, please (see the last link in my signature):

```
nano /etc/apt/sources.list
```

Also, how did you install Shotwell? From the official repositories or is it left from a net upgrade? Have you done an update/upgrade since the OS upgrade?

These commands, one after the other with return between, please, and post any and all errors:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Reboot and check Shotwell.

---

### Post by JanneM on 2015-11-02
> **Bucky Ball said:**
> *Thread moved to **Multimedia Software**.*  When you say an upgrade to 15.10, did you do a clean install or upgrade via the net from 15.04? If the latter, was Shotwell working fine in 15.04?   Upgrade via net from 15.04. Shotwell worked fine in 15.04, this started happening immediately after upgrading to 15.10.  >  Post the terminal output of this command between code tags, please (see the last link in my signature):  ```
nano /etc/apt/sources.list
```  If you like, though it is pretty much the bog-standard Ubuntu repos. ```
 # deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid mai$  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to # newer versions of the distribution. deb http://jp.archive.ubuntu.com/ubuntu/ wily main restricted deb-src http://jp.archive.ubuntu.com/ubuntu/ wily main restricted  ## Major bug fix updates produced after the final release of the ## distribution. deb http://jp.archive.ubuntu.com/ubuntu/ wily-updates main restricted deb-src http://jp.archive.ubuntu.com/ubuntu/ wily-updates main restricted  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb http://jp.archive.ubuntu.com/ubuntu/ wily universe deb-src http://jp.archive.ubuntu.com/ubuntu/ wily universe deb http://jp.archive.ubuntu.com/ubuntu/ wily-updates universe deb-src http://jp.archive.ubuntu.com/ubuntu/ wily-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb http://jp.archive.ubuntu.com/ubuntu/ wily multiverse deb-src http://jp.archive.ubuntu.com/ubuntu/ wily multiverse deb http://jp.archive.ubuntu.com/ubuntu/ wily-updates multiverse deb-src http://jp.archive.ubuntu.com/ubuntu/ wily-updates multiverse  ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. deb http://jp.archive.ubuntu.com/ubuntu/ wily-backports main restricted univers$ deb-src http://jp.archive.ubuntu.com/ubuntu/ wily-backports main restricted uni$  deb http://security.ubuntu.com/ubuntu wily-security main restricted deb-src http://security.ubuntu.com/ubuntu wily-security main restricted deb http://security.ubuntu.com/ubuntu wily-security universe deb-src http://security.ubuntu.com/ubuntu wily-security universe deb http://security.ubuntu.com/ubuntu wily-security multiverse deb-src http://security.ubuntu.com/ubuntu wily-security multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. deb http://archive.canonical.com/ubuntu wily partner deb-src http://archive.canonical.com/ubuntu wily partner 
```  >  Also, how did you install Shotwell? From the official repositories or is it left from a net upgrade? Have you done an update/upgrade since the OS upgrade?   It's the officially provided version, as I stated. And yes, I stay up to date; this is the latest version, and all other software is up to date.  >  These commands, one after the other with return between, please, and post any and all errors:  ```
 sudo apt-get update sudo apt-get upgrade sudo apt-get dist-upgrade 
```  Reboot and check Shotwell.  No errors. One package (libavcodec-extra) kept back. And of course no change to Shotwell.  I did determine now that this happens specifically in the case when invoking the external editor on an image that does not already have an edited version. Create one by, for instance, doing a null edit in shotwell itself and I can use Gimp afterwards without issues.

---

