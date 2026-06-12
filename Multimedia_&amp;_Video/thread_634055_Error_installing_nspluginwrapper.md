---
title: "Error installing nspluginwrapper"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by ganymede62 on 2007-12-07
Hello,

I think I messed up something.  After the upgrade to Gutzy I noticed that I can't watch Youtube anymore. I'm running 64-bit Kubuntu on an AMD X2. 

When trying to install nspluginwrapper I get this message:

 sudo aptitude install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  nspluginwrapper 
The following partially installed packages will be configured:
  flashplugin-nonfree 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives. After unpacking 377kB will be used.
Writing extended state information... Done
(Reading database ... 76716 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb) ...
dpkg: error processing /[B]var/cache/apt/archives/nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in [/B]package nspluginwrapper-i386
Errors were encountered while processing:
 /var/cache/apt/archives/nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on nspluginwrapper (>= 0.9.91.4-2ubuntu1); however:
  Package nspluginwrapper is not installed.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


Any help or ideas would be appreciated. 

Thank you.

---

### Post by ganymede62 on 2007-12-07
Bump. 

Sorry, I'm somewhat of a Ubuntu newbie here. Can anyone at least suggest some package utilities to try and fix this?

Thanks.

---

### Post by ganymede62 on 2007-12-09
Still stuck. 

It looks like my nspluginwrapper package is broken. Looking at a few other threads I tried to fix the package based on other recommendations but to no avail. 

I tried this:

It looks like the sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nspluginwrapper
The following NEW packages will be installed:
  nspluginwrapper
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/111kB of archives.
After unpacking 377kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 76965 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386
Errors were encountered while processing:


But no go.

Please help! I don't want to have to re-install from scratch.

---

### Post by wolfen69 on 2007-12-09
see this: [http://ubuntuforums.org/showpost.php?p=3916264&postcount=6](http://ubuntuforums.org/showpost.php?p=3916264&postcount=6)

there is a problem with flash right now. you also might want to check out the 64bit forum.

---

### Post by ganda99 on 2007-12-10
Thanks for the reply. I was starting to think I was posting to the wall. Even started to think I picked the wrong distro when I have up on Gentoo this year. 

Anyway, I saw the posts about the issue with the Flash package, however my issue seems to be with the  nspluginwrapper package which I can't install at all. 

There's not much to go on for error messages other than:

[B]dpkg: error processing /var/cache/apt/archives/nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386
Errors were encountered while processing:
 /var/cache/apt/archives/nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

Any advice would be greatly appreciated. 

Thanks again.

---

### Post by ganda99 on 2007-12-10
OK, I fixed it. 

I was playing with the "Manage Repositories" in adept_manager. I choose the "Officially Supported/Restricted Copywrite" box for 7.04 Feisty Fawn and reset. That later showed "nspluginwrapper-386" as being installed. I removed that then went back to "Manage Repositories" and unchecked option I chose earlier and reset. The I tried to install nspluginwrapper again and was successful. 

Must have been some conflict with the old and new distributions, I guess.

---

