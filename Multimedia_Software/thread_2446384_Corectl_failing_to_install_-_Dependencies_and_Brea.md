---
title: "Corectl failing to install - Dependencies and Breaks"
date: 2020-06-29
forum: Multimedia Software
---

### Post by backspin on 2020-06-29
When installing corectl it is failing to install due to the following dependencies. What's weird is that it talks of "breaks", and I don't know what that means?  What is the best way to clear this problem?

davidc502@Ryzen-3900x:/mnt/md0$ sudo apt install corectrl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 **gsettings-desktop-schemas : Breaks: mutter (< 3.31.4) but 3.28.4-0ubuntu18.04.2 is to be installed**              <--------------------------------------------------------
 **libgirepository-1.0-1 : Breaks: python-gi (< 3.34.0-4~) but 3.26.1-2ubuntu1 is to be installed   **                 <---------------------------------------------------------------
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


Thanks,

David

---

### Post by Bashing-om on 2020-06-29
backspin; Hello -

Not enough information to say.
I get:
> 
sysop@x1804mini:~$ apt show corectrl
N: Unable to locate package corectrl
N: Unable to locate package corectrl
E: No packages found


So,
what release are you working with ?
where did you get corectrl ? ( sudo apt install corectrl ??)
What kernel is corectrl built for ?

Installing something from upstream ?

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by backspin on 2020-06-29
Release Ubuntu 18.04 LTS
davidc502@Ryzen-3900x:/mnt/md0$ uname -a
Linux Ryzen-3900x 5.7.1-050701-generic #202006071230 SMP Sun Jun 7 12:32:55 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

To get corectrl -   Add the [Ernst ppa-mesarc]("https://launchpad.net/~ernstp/+archive/ubuntu/mesarc") PPA    Here is the repo -   [https://gitlab.com/corectrl/corectrl](https://gitlab.com/corectrl/corectrl)

My Radeon RX 5700XT arrived and I installed the latest drivers, and they work fine, but the drivers, as they are, do not push the gpu at all. I need something that will drive the gpu the way that I want and it looks like corectl is the answer. corectl basically replaces the windows version of AMD's Wattman. 

Hope that helps.

David

---

### Post by Bashing-om on 2020-06-29
backspin;

Humm ....

System fully updated ?
```

sudo apt update
sudo apt upgrade

```

Else I do suggest that you contact the PPA maintainer, Ernst Sjöstrand,  with this issue as it is not an official ubuntu packaging issue.
as:
> 
You have searched for packages that names contain gsettings-desktop-schemas in suite(s) bionic-backports, all sections, and all architectures.

Sorry, your search gave no results
 
the required package(s) versions do not appear to be available in our repo.

[INDENT][INDENT]these things happen
[/INDENT][/INDENT]

---

### Post by backspin on 2020-06-29
I went ahead and upgraded, and was a bit of a mistake.  Seems the new gpu driver won't install because it is expecting packages that aren't there, but yet I can install 18.04 no problem, so I feel like the system is quasi updated. 

when I try to install corectl it fails for the same reason. I guess it will be time to do a clean install and see what happens. 

Will also try and contact the PPA maintainer as well.

---

