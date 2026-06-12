---
title: "KWin package blocking updates"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2010-05-28
I've waited a little bit to see if this bug I have could be fixed, and I have reported it via Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/584672](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/584672)

I can't upgrade anything for KDE or FFMPEG for about a week now. Every time I do, this happens:

```
$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Resolving dependencies...
The following packages have been kept back:
  kdebase-workspace{a} kdebase-workspace-bin{a} kdebase-workspace-data{a} 
  kdebase-workspace-kgreet-plugins{a} kdm{a} ksysguard{a} 
  libsdl1.2debian{a} libsdl1.2debian-alsa{a} libxine1{a} libxine1-bin{a} 
  libxine1-console{a} libxine1-ffmpeg libxine1-misc-plugins{a} 
  libxine1-x{a} plasma-dataengines-addons{a} 
  plasma-dataengines-workspace{a} plasma-desktop{a} plasma-widgets-addons 
  plasma-widgets-workspace{a} 
The following NEW packages will be installed:
  libkwineffects1a{a} 
The following packages will be REMOVED:
  libkwineffects1{u} psfontmgr{u} 
The following packages will be upgraded:
  kde-window-manager 
1 packages upgraded, 1 newly installed, 2 to remove and 19 not upgraded.
Need to get 0B/1817kB of archives. After unpacking 69.6kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 113389 files and directories currently installed.)
Preparing to replace kde-window-manager 4:4.4.2-0ubuntu14 (using .../kde-window-manager_4%3a4.4.3-1ubuntu3_amd64.deb) ...
Unpacking replacement kde-window-manager ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.4.3-1ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/doc/kde/HTML/en/kcontrol/desktop/index.cache.bz2', which is also in package kdebase-workspace-data 4:4.4.2-0ubuntu14
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.4.3-1ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```
No matter of sudo apt-get clean will sort this out. However, updating using apt-get/KPackageKit will block KWin from upgrading. Anyone else having the same problem attempting to upgrade with aptitude, or if there is a fix for this problem?

Thanks in advance.

---

### Post by ranch hand on 2010-05-28
Anyone, now this is just my opinion, that uses packagekit, even spelled with a K, deserves what they get.

Install synaptic if you want a gui that works.

---

### Post by vikrant82 on 2010-05-28
Try force overwrite ?

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-window-manager_4%3a4.4.3-1ubuntu3_amd64.deb
sudo apt-get install -f
```

Have to do that with a lot of kde packages,

---

### Post by descendent87 on 2010-05-28
I had those updates about a week ago and just did an apt-get dist-upgrade and all went fine

---

### Post by cariboo on 2010-05-28
You should'nt be using dist-upgrade this early in the testing cycle.

```
sudo aptitude safe-upgrade
```

is the way to go, this way you don't get stuck with any partial upgrades.

---

### Post by xebian on 2010-05-28
> **ranch hand said:**
> Anyone, now this is just my opinion, that uses packagekit, even spelled with a K, deserves what they get.

Install synaptic if you want a gui that works.

I don't use it but this issue has nothing to do with any *packagekit* flavor - more on dependencies.

---

### Post by Reiger on 2010-05-28
Aptitude and apt-get do some things slightly differently. Perhaps:
```

sudo aptitude clean && sudo aptitude autoclean
sudo aptitude update && sudo aptitude safe-upgrade

```

---

### Post by tghe-retford on 2010-05-28
> **vikrant82 said:**
> Try force overwrite ?

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-window-manager_4%3a4.4.3-1ubuntu3_amd64.deb
sudo apt-get install -f
```

Have to do that with a lot of kde packages,
Thank you. That sorted out the problem with KWin. Just 19 blocked packages to wait on...

EDIT: libdirectfb-1.2.0 is blocking updates. I can upgrade but lose MPlayer or not upgrade and continue to have updates being blocked. Time for another bug report.

---

### Post by tghe-retford on 2010-05-28
> **cariboo907 said:**
> You should'nt be using dist-upgrade this early in the testing cycle.

```
sudo aptitude safe-upgrade
```

is the way to go, this way you don't get stuck with any partial upgrades.
I never used dist-upgrade when updating, always aptitude safe-upgrade after recommendations from other users on this forum.

---

### Post by seeker5528 on 2010-05-28
> **tghe-retford said:**
> I never used dist-upgrade when updating, always aptitude safe-upgrade after recommendations from other users on this forum.

Results may not always be identical, but 'aptitude safe-upgrade' should be more or less equivalent to 'apt-get upgrade' or to hitting the 'Mark All Upgrades' button in Synaptic if the 'Settings --> Preferences --> General --> System upgrade' option is set to 'Default Upgrade' instead of 'Smart Upgrade'.

I hate aptitude, so never use it, but with the others this means no packages will be installed that have new or changed dependencies, so you still end up with some you have to select manually, also doesn't do anything to prevent you from having issues with packages that try to over write files that are also in another package, except to the extent that in situations this problem arises there is a fair chance that dependencies changed.

Later, Seeker

---

