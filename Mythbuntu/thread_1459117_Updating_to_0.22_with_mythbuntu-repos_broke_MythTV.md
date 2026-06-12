---
title: "Updating to 0.22 with mythbuntu-repos broke MythTV"
date: 2010-04-21
forum: Mythbuntu
---

### Post by andrewc6l on 2010-04-21
This evening I decided to upgrade my elderly Mythbuntu 9.04 release by installing the mythbuntu-repos.deb from [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds). After selecting 0.22 and updating via aptitude, I ran into errors upgrading:

```
Current status: 8 updates [+8], 25920 new [+8].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  libmyth-perl{a} mythtv-backend{a} mythtv-common{a} mythtv-frontend{a} 
  mythtv-themes{a} mythtv-transcode-utils{a} 
The following packages will be upgraded:
  mythflix mythgame 
2 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/304kB of archives. After unpacking 32.8kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 207263 files and directories currently installed.)
Preparing to replace mythflix 0.21.0+fixes21768-0ubuntu0+mythbuntu3 (using .../mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb) ...
Unpacking replacement mythflix ...
dpkg: error processing /var/cache/apt/archives/mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/netflix-bg.png', which is also in package mythtv-common
Preparing to replace mythgame 0.21.0+fixes21768-0ubuntu0+mythbuntu3 (using .../mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb) ...
Unpacking replacement mythgame ...
dpkg: error processing /var/cache/apt/archives/mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/game-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb
 /var/cache/apt/archives/mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

Starting mythfrontend now causes a seg fault. The back end appears to be running.

Any idea what went wrong, and (more importantly) how to fix it?

---

### Post by xinix on 2010-04-21
Try uninstalling your mythtv packages (at-least your plugins) and re-installing with the new ones.> 
The following packages have been kept back:
  libmyth-perl{a} mythtv-backend{a} mythtv-common{a} mythtv-frontend{a} 
  mythtv-themes{a} mythtv-transcode-utils{a} 
The following packages will be upgraded:
  mythflix mythgame 

As you can see from this a good number of your mythtv packages were not upgraded. I'm going to guess that it is because some files in a newer package are trying to overwrite files that used to be installed by a different package.
> 
 trying to overwrite `/usr/share/mythtv/themes/default-wide/game-ui.xml', which is also in package mythtv-common

---

### Post by superm1 on 2010-04-21
> **andrewc6l said:**
> This evening I decided to upgrade my elderly Mythbuntu 9.04 release by installing the mythbuntu-repos.deb from [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds). After selecting 0.22 and updating via aptitude, I ran into errors upgrading:

```
Current status: 8 updates [+8], 25920 new [+8].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  libmyth-perl{a} mythtv-backend{a} mythtv-common{a} mythtv-frontend{a} 
  mythtv-themes{a} mythtv-transcode-utils{a} 
The following packages will be upgraded:
  mythflix mythgame 
2 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/304kB of archives. After unpacking 32.8kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 207263 files and directories currently installed.)
Preparing to replace mythflix 0.21.0+fixes21768-0ubuntu0+mythbuntu3 (using .../mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb) ...
Unpacking replacement mythflix ...
dpkg: error processing /var/cache/apt/archives/mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/netflix-bg.png', which is also in package mythtv-common
Preparing to replace mythgame 0.21.0+fixes21768-0ubuntu0+mythbuntu3 (using .../mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb) ...
Unpacking replacement mythgame ...
dpkg: error processing /var/cache/apt/archives/mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/game-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mythflix_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb
 /var/cache/apt/archives/mythgame_0.22.0+fixes23766-0ubuntu0+mythbuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

Starting mythfrontend now causes a seg fault. The back end appears to be running.

Any idea what went wrong, and (more importantly) how to fix it?

Try apt-get dist-upgrade instead, it should have resolved that mythtv-common is so important for this to work out properly.

---

### Post by andrewc6l on 2010-04-22
Thanks to both of you! I tried dist-upgrade first, but aptitude still had trouble figuring out how to resolve the conflict between the old mythtv-common and the new mythflix package. So... I held my breath, removed mythtv-common, and reinstalled mythtv.

Luckily, it recognized that my database already existed. (whew!) That gave my a working frontend and backend whose schemas myth was able to upgrade; afterwards I installed mythtv-plugins and things appear to be back to normal.

Thanks again!

---

### Post by superm1 on 2010-04-22
> **andrewc6l said:**
> Thanks to both of you! I tried dist-upgrade first, but aptitude still had trouble figuring out how to resolve the conflict between the old mythtv-common and the new mythflix package. So... I held my breath, removed mythtv-common, and reinstalled mythtv.

Luckily, it recognized that my database already existed. (whew!) That gave my a working frontend and backend whose schemas myth was able to upgrade; afterwards I installed mythtv-plugins and things appear to be back to normal.

Thanks again!

Definitely not the first time i've seen aptitude resolve the upgrade weirdly.  Honestly, apt-get's resolver is a bit more sane than aptitude's quite often...

---

