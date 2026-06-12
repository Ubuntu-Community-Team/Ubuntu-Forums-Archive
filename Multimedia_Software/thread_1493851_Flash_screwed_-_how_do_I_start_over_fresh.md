---
title: "Flash screwed - how do I start over fresh?"
date: 2010-05-26
forum: Multimedia Software
---

### Post by MaindotC on 2010-05-26
I read on a forum post that the problem with clicking certain types of flash content was resolved by downloading and install the latest package of flash from adobe's site.

Well obviously that didn't really fix the problem.  I removed the flash install from the .deb package I downloaded from Adobe and wanted to start over.  I am having problems installing flashplugin-nonfree and flashplugin-installer due to conflicting packages.  How can I start over fresh as if flash was never installed and THEN install flashplugin-nonfree + it's dependencies without any problems?  Here's what happens when I try to remove and reinstall, among other things:
```

xk@xk:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.3kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 330983 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.45.2ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/19.5kB of archives.
After this operation, 188kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/19.5kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get remove adobe-flashplugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
xk@xk:~$ sudo apt-get remove flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330985 files and directories currently installed.)
Removing flashplugin-nonfree ...
xk@xk:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xk@xk:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nspluginwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 565kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330982 files and directories currently installed.)
Removing nspluginwrapper ...
Processing triggers for man-db ...
xk@xk:~$ sudo apt-get clean
xk@xk:~$ sudo apt-get update && sudo apt-get upgrade
xk@xk:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree nspluginwrapper
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 219kB of archives.
After this operation, 795kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse nspluginwrapper 1.2.2-0ubuntu6 [198kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse flashplugin-installer 10.0.45.2ubuntu1 [19.5kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse flashplugin-nonfree 10.0.45.2ubuntu1 [1,770B]
Fetched 219kB in 1s (122kB/s)                  
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 330955 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu6_amd64.deb) ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.45.2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/19.5kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get remove --purge flashplugin-nonfree adobe-flashplugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330985 files and directories currently installed.)
Removing flashplugin-nonfree ...
Setting up nspluginwrapper (1.2.2-0ubuntu6) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Auto-update plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
Auto-update plugins from /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
Auto-update plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins

xk@xk:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.3kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 330983 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.45.2ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get remove --purge flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330985 files and directories currently installed.)
Removing flashplugin-nonfree ...
xk@xk:~$ sudo apt-get remove --purge nspluginwrapper 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nspluginwrapper*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 565kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330982 files and directories currently installed.)
Removing nspluginwrapper ...
Processing triggers for man-db ...
xk@xk:~$ sudo apt-get update && sudo apt-get upgrade
xk@xk:~$ sudo apt-get install flashpl
flashplayer-mozilla    flashplugin-installer  
flashplugin            flashplugin-nonfree    
xk@xk:~$ sudo apt-get install flashpl
flashplayer-mozilla    flashplugin-installer  
flashplugin            flashplugin-nonfree    
xk@xk:~$ sudo apt-get install flashplayer-mozilla 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplayer-mozilla has no installation candidate
xk@xk:~$ sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/217kB of archives.
After this operation, 754kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 330955 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu6_amd64.deb) ...
dpkg: regarding .../flashplugin-installer_10.0.45.2ubuntu1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.45.2ubuntu1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xk@xk:~$ sudo apt-get remove --purge flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nspluginwrapper (1.2.2-0ubuntu6) ...
plugin dirs:
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Auto-update plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
Auto-update plugins from /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
Auto-update plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins

xk@xk:~$ sudo apt-get remove --purge nspluginwrapper 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nspluginwrapper*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 565kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 330982 files and directories currently installed.)
Removing nspluginwrapper ...
Processing triggers for man-db ...
xk@xk:~$

```

---

### Post by lovinglinux on 2010-05-26
Try this:

```
sudo dpkg -r adobe-flashplugin
```

Then Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by MaindotC on 2010-05-26
Well that would be nice but I can't seem to login to the Firefox sandbox to download it.  Man what a horrible idea to use Adobe's own package for THEIR OWN application. I can't believe what a mess this is.

---

### Post by lovinglinux on 2010-05-26
> **strAlan said:**
> Well that would be nice but I can't seem to login to the Firefox sandbox to download it.  Man what a horrible idea to use Adobe's own package for THEIR OWN application. I can't believe what a mess this is.

I'm the developer of FLASH-AID. It is basically a script launcher, that remove conflicting plugins and install the proper flash plugin.

The Automatic Install only works if you have an account at Mozilla, until they approve the extension. But you can get it from the Download link on my web site instead. You won't need an account at Mozilla then, since you download from my project repository.

---

### Post by MaindotC on 2010-05-26
WOw - FM - freaking magic!  Yes it did launch a script and I installed it per the suggested version.  Thank you so much for your help!  I'll be sure to examine your script to determine where I went wrong.  As soon as I get a job with my degree in IT instead of working at the grocery store I'll be sure to toss you a donation as well.  Thank you so much!

---

### Post by lovinglinux on 2010-05-26
> **strAlan said:**
> WOw - FM - freaking magic!  Yes it did launch a script and I installed it per the suggested version.  Thank you so much for your help!  I'll be sure to examine your script to determine where I went wrong.  As soon as I get a job with my degree in IT instead of working at the grocery store I'll be sure to toss you a donation as well.  Thank you so much!

You are welcome.

---

### Post by MaindotC on 2010-06-16
I was trying to watch the football highlights on fifa.com and of course they weren't working so I ran flash-aid again and I broke flash :(  Can you advise me on this output:
```
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.4kB of archives.
After this operation, 229kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 335267 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Finished! You can close this terminal. You must restart Firefox now

```

And of course no youtubes or anything work now :(

---

### Post by lovinglinux on 2010-06-16
> **strAlan said:**
> I was trying to watch the football highlights on fifa.com and of course they weren't working so I ran flash-aid again and I broke flash :(  Can you advise me on this output:
```
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.4kB of archives.
After this operation, 229kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.10.04.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 335267 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Finished! You can close this terminal. You must restart Firefox now

```

And of course no youtubes or anything work now :(

Try this:

```
sudo rm /var/lib/dpkg/info/flashplugin* 
sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```

Then run FLASH-AID again.

---

### Post by MaindotC on 2010-06-16
Thank you for the reply!  It didn't return any errors this time but my flash still isn't working for some reason.  

```

The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 41.0kB disk space will be freed.
(Reading database ... 335274 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 188kB disk space will be freed.
(Reading database ... 335271 files and directories currently installed.)
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/midbrowser/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/midbrowser' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceweasel/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceweasel' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceape/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceape' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/xulrunner/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/xulrunner' not empty so not removed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.4kB of archives.
After this operation, 229kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 335254 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.1) ...
Downloading...
--2010-06-16 09:26:50--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4739416 (4.5M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.53.64.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 72.0K 64s
    50K .......... .......... .......... .......... ..........  2%  145K 47s
   
(edited)

  4550K .......... .......... .......... .......... .......... 99% 3.75M 0s
  4600K .......... .......... ........                        100% 3.55M=4.1s

2010-06-16 09:26:55 (1.11 MB/s) - `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.1.53.64ubuntu0.10.04.1) ...
Finished! You can close this terminal. You must restart Firefox now.

```

This is after running flash-aid a 2nd time.

---

### Post by lovinglinux on 2010-06-16
> **strAlan said:**
> Thank you for the reply!  It didn't return any errors this time but my flash still isn't working for some reason.  

```

The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 41.0kB disk space will be freed.
(Reading database ... 335274 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 188kB disk space will be freed.
(Reading database ... 335271 files and directories currently installed.)
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/midbrowser/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/midbrowser' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceweasel/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceweasel' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceape/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/iceape' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/xulrunner/plugins' not empty so not removed.
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/xulrunner' not empty so not removed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.4kB of archives.
After this operation, 229kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 335254 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.53.64ubuntu0.10.04.1_amd64.deb) ...
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.1) ...
Downloading...
--2010-06-16 09:26:50--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4739416 (4.5M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.53.64.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 72.0K 64s
    50K .......... .......... .......... .......... ..........  2%  145K 47s
   
(edited)

  4550K .......... .......... .......... .......... .......... 99% 3.75M 0s
  4600K .......... .......... ........                        100% 3.55M=4.1s

2010-06-16 09:26:55 (1.11 MB/s) - `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.1.53.64ubuntu0.10.04.1) ...
Finished! You can close this terminal. You must restart Firefox now.

```

This is after running flash-aid a 2nd time.

Which browser you are using?

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by MaindotC on 2010-06-16
I believe this is what you're looking for:
```

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

```

That's supposed to say 10.1.53.64 isn't it?

---

### Post by lovinglinux on 2010-06-16
> **strAlan said:**
> I believe this is what you're looking for:
```

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

```

That's supposed to say 10.1.53.64 isn't it?

Yes.

Try this:

```
sudo apt-get purge adobe-flashplugin
sudo rm -f /usr/lib/adobe-flashplugin/libflashplayer.so

```

Then check the version again.

---

### Post by MaindotC on 2010-06-16
It works now!  Thank you so much!  Ok now let me see if I understand this.  In post #8, why did you have me remove those files?  It seems as though they are some sort of (aptly named) info files that dpkg checks to verify installed file versions, and removing them enabled dpkg to not be concerned with this information and thus proceed with the installation.

Then in #10 you showed me a good way to verify my flash version and it appears that Firefox was using the wrong version.  I ran the apt-get purge but apt said it wasn't installed, but I understand why you'd issue that command - to remove the flashplugin and anything associated with it, correct?

Then you had me remove libflashplayer.so.  I googled and read that this file is a shared object file and I know a little bit about development so I'm assuming this is some older or wrong version of file that the flashplugin needs to operate.  Is that correct?

Btw now I can view videos on fifa.com.  Thank you so much for your help and I look forward to your answers.  Please set up a donate link on your blog if you would find it appropriate.

---

### Post by lovinglinux on 2010-06-16
> **strAlan said:**
> It works now!  Thank you so much!  Ok now let me see if I understand this.  In post #8, why did you have me remove those files?  It seems as though they are some sort of (aptly named) info files that dpkg checks to verify installed file versions, and removing them enabled dpkg to not be concerned with this information and thus proceed with the installation.

Yes. There was a conflict with adobe-flashplugin package, which should have been uninstalled already when you used my extension, so deleting those files prevented the error and allowed to install flashplugin-nonfree, which is just a dummy package for flashplugin-installer. The package adobe-flashplugin is the flash installer from the partner repository and also the one installed when a deb file was downloaded from Adobe site, while flashplugin-installer is the flash installer from multiverse repository. It doesn't matter which one you use, as long as they are updated.

> **strAlan said:**
> Then in #10 you showed me a good way to verify my flash version and it appears that Firefox was using the wrong version.  I ran the apt-get purge but apt said it wasn't installed, but I understand why you'd issue that command - to remove the flashplugin and anything associated with it, correct?

Yes. The first command was probably unnecessary, because we had already removed the adobe-flashplugin info from dpkg but it doesn't hurt to run it. 

> **strAlan said:**
> Then you had me remove libflashplayer.so.  I googled and read that this file is a shared object file and I know a little bit about development so I'm assuming this is some older or wrong version of file that the flashplugin needs to operate.  Is that correct?

The file libflashplayer.so is in fact the flash plugin itself, which is a shared object. When you install adobe-flashplugin, the libflashplayer.so is saved inside /usr/lib/adobe-flashplugin/ while flashplugin-installer saves it inside /usr/lib/flashplugin-installer/, but symlinks are created in various places where Firefox can detect the plugin. Symlinks are small files that redirect to other files. Firefox was detecting a symlink to adobe-flashplugin/libflashplayer.so instead of flashplugin-installer/libflashplayer.so. So removing it manually allowed Firefox to detect the newest version.

Bottom line, what we did was to remove adobe-flashplugin manually, which was preventing flashplugin-installer to be installed and contained an old flash version. After that my extension was able to install flashplugin-installer, which has the newest version of flash.

> **strAlan said:**
> Btw now I can view videos on fifa.com.

You are welcome.

> **strAlan said:**
> Please set up a donate link on your blog if you would find it appropriate.

I don't think the forum admins will find that appropriate, since I post links to my blog all the time :)

But thanks for your support anyway.

---

### Post by MaindotC on 2010-06-17
> **lovinglinux said:**
> 
I don't think the forum admins will find that appropriate, since I post links to my blog all the time :)

But thanks for your support anyway.

I meant on your blog, not here on the forum.  Perhaps you don't need that support, or don't find it appropriate, but if you posted a paypal link on your blog I'd chip in.

---

### Post by lovinglinux on 2010-06-17
> **strAlan said:**
> I meant on your blog, not here on the forum.  Perhaps you don't need that support, or don't find it appropriate, but if you posted a paypal link on your blog I'd chip in.

I know you were talking about the blog. I was just worried that the moderators would not like it, since I post a lot of messages here in the forums with links to my blog. This could be interpreted as spam or something.

Anyway, I have added a donation button to my home page at [http://lovinglinuxblog.blogspot.com](http://lovinglinuxblog.blogspot.com) (I hope it works :))

Your contribution will be very much appreciated. It will help the development of my extensions.

---

### Post by MaindotC on 2010-06-17
Done.  Should be enough for for a rental and a nice warm tv dinner :p

---

### Post by lovinglinux on 2010-06-17
> **strAlan said:**
> Done.  Should be enough for for a rental and a nice warm tv dinner :p

Thank you very much. Your support is very welcome. Don't forget to subscribe to the RSS feed or Twitter to get informed about updates.

:popcorn:

---

### Post by Thanathos-ar on 2010-09-01
lovinglinux you are THE MAN!
Thanks!!!!!!!!!!!!!!!!!

Before I tried a lot of things, even your plugin, but nothing worked. I broke my flash several months ago making an upgrade of something, I don't remember...
Today I was fed up with the broken flash. Found this thread and voilá!

The sequence for me was:

```
sudo apt-get purge adobe-flashplugin
sudo rm -f /usr/lib/adobe-flashplugin/libflashplayer.so
sudo dpkg -r adobe-flashplugin
```

and then running your script, was enough to do the magic.
I wanted to let you know that your FLASH-AID plugin and your instructions were a great help to resolve my broken flash issue.

Thanks again!

---

### Post by lovinglinux on 2010-09-01
> **Thanathos-ar said:**
> lovinglinux you are THE MAN!
Thanks!!!!!!!!!!!!!!!!!

Before I tried a lot of things, even your plugin, but nothing worked. I broke my flash several months ago making an upgrade of something, I don't remember...
Today I was fed up with the broken flash. Found this thread and voilá!

The sequence for me was:

```
sudo apt-get purge adobe-flashplugin
sudo rm -f /usr/lib/adobe-flashplugin/libflashplayer.so
sudo dpkg -r adobe-flashplugin
```

and then running your script, was enough to do the magic.
I wanted to let you know that your FLASH-AID plugin and your instructions were a great help to resolve my broken flash issue.

Thanks again!

You are welcome. I'm glad you fixed it.

---

### Post by MaindotC on 2010-09-02
> **Thanathos-ar said:**
> lovinglinux you are THE MAN!
Thanks!!!!!!!!!!!!!!!!!


Throw the developer some money for a movie :D

---

