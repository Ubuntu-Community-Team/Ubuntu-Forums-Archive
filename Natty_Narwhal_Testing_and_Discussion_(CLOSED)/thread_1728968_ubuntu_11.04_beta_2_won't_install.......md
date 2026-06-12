---
title: "ubuntu 11.04 beta 2 won't install......"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tszkitc on 2011-04-14
It freeze at the "Preparing to install Ubuntu" .

Can one gone through the same experiences?

Thanks.

---

### Post by uRock on 2011-04-14
Moved to Natty Narwhal Testing & Discussion.

---

### Post by tszkitc on 2011-04-14
> **tszkitc said:**
> It freeze at the "Preparing to install Ubuntu" .

Can one gone through the same experiences?

Thanks.

I had no problem to install Ubuntu 10.10

---

### Post by 5149.5 on 2011-04-14
It worked fine for me. I was only doing an upgrade though.

---

### Post by cariboo on 2011-04-14
The beta hasn't been officially released yet, there may be changes to the iso before it's released.

---

### Post by nilarimogard on 2011-04-14
The beta2 ISO worked just fine for me in VirtualBox.

---

### Post by KegHead on 2011-04-14
Hi!


Some info please:

Is this a fresh install?

How much ram do you have onboard?

Are you using a cd or USB stick?

KegHead

---

### Post by tszkitc on 2011-04-14
> **tszkitc said:**
> I had no problem to install Ubuntu 10.10

4GB ram
one 250gb hdd
one 1500gb hdd
intel 5200cpu
8800gt display card
I got no problem with all other Linux distro including
OpenSUSE 11,4

---

### Post by tszkitc on 2011-04-14
> **KegHead said:**
> Hi!


Some info please:

Is this a fresh install?

How much ram do you have onboard?

Are you using a cd or USB stick?

KegHead

I use a DVD rewritable.
Fresh install? I use the dvd to boot and would like to erase
everything on HDD......

---

### Post by tszkitc on 2011-04-14
> **tszkitc said:**
> I use a DVD rewritable.
Fresh install? I use the dvd to boot and would like to erase
everything on HDD......


Same as I do with all other distro......

---

### Post by KegHead on 2011-04-14
Hi!

I can't determine if this is a new install or are you using another version? (like 10.04 or 10.10) And are upgrading.

11.04 is brand new and is in the testing stage. (beta)

It might be best to try to install 10.10

BTW-how did you burn your iso?

KegHead

---

### Post by Cenotaph on 2011-04-14
Same thing is happening to me... Thought I would reinstall the system from scratch and it just doesn't do anything at preparing to install, I hit next, everything is greyed out but nothing happens. I'm using a USB drive created through USB creator.

---

### Post by Cenotaph on 2011-04-14
okay, i just tried a third time and this time it got past that stage after i changed a partition's file system in my hdd, could this be related to the bug the installer had before beta where it ubiquity would crash if there was free space on disk or something like that?

---

### Post by tszkitc on 2011-04-15
> **Cenotaph said:**
> okay, i just tried a third time and this time it got past that stage after i changed a partition's file system in my hdd, could this be related to the bug the installer had before beta where it ubiquity would crash if there was free space on disk or something like that?

I use my whole drive 250gb for linux.
There is only ubunt 10.10 on it.
I tried install other distro and all works.

---

### Post by KegHead on 2011-04-15
Hi!

**Use this with extreme caution to upgrade;**

sudo apt-get update && sudo apt-get dist-upgrade

11.04 is in the beta stage, there may be many errors, you could lose your files and need to reinstall your current distro.

Back up your files.

KegHead

---

