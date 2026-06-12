---
title: "Could not calculate the upgrade"
date: 2010-12-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Penguin360 on 2010-12-10
When I tried to upgrade Ubuntu 10.10 to 11.04 Alpha 1 this morning, I got an error saying "Could not calculate the upgrade". Here is some more information.

An unresolvable problem occurred while calculating the upgrade.
Can not mark 'ubuntu-desktop' for upgrade
This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I searched the forum but could not find much information. Do I need to do a clean install of 11.04?

Thanks,

---

### Post by Penguin360 on 2010-12-10
Just found this in the sticky post:


**How can I upgrade to Natty?**

There's basically no point in upgrading to Natty at this point. It exists as a release in the archive, but isn't open for development, the Debian auto-sync hasn't started, and you can't really do anything useful. Unless you're a toolchain hacker or have special interest in a particular Debian sync issue, it's going to stay this way until after UDS.

So I guess I have to do a clean install.

---

### Post by dino99 on 2010-12-10
clean the cache:

sudo rm /var/cache/apt/archives/*

you might check your sources.list to work only with genuine natty repo then update/upgrade.

---

### Post by Jay Car on 2010-12-10
I don't know if this pertains to the problem you've found.  However, I was going to start testing Natty this week (my first experience with an Alpha version!), but was advised to wait until this weekend, due to this current issue: [http://ubuntuforums.org/showthread.php?t=1641151](http://ubuntuforums.org/showthread.php?t=1641151)

My next attempt will be Sunday.  I'm looking forward to it.

---

### Post by Penguin360 on 2010-12-10
> **dino99 said:**
> clean the cache:

sudo rm /var/cache/apt/archives/*

you might check your sources.list to work only with genuine natty repo then update/upgrade.

Cleaning the cache worked like a charm, thank you dino99.

Now the upgrade is running, but I got an error saying cannot install Python2.7-minimal though the installation is still going. Is it going to be a problem?

---

### Post by dino99 on 2010-12-10
hey, you are in testing jam, so if you cant swim in the dark without breathing, maybe its too scary for you :(

Read the Sticky threads may help

---

### Post by Penguin360 on 2010-12-10
> **dino99 said:**
> hey, you are in testing jam, so if you cant swim in the dark without breathing, maybe its too scary for you :(

Read the Sticky threads may help

Hehe, I am learning that kind of skill, and besides, with so many experienced Ubuntu users like you around, I don't feel too scary.

About 30 minutes remaining until the upgrade is finished. I have my fingers crossed...

Thanks,

---

