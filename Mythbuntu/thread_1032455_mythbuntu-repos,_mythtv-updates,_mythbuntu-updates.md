---
title: "mythbuntu-repos, mythtv-updates, mythbuntu-updates - Questions or Issues"
date: 2009-01-06
forum: Mythbuntu
---

### Post by tgm4883 on 2009-01-06
Updated builds of MythTV are available by installing the mythbuntu-repos package. This thread is for questions, issues, etc about the mythbuntu-repos package or the build process itself. This is not the place to post bugs about mythtv or other related plugins.

For 12.04 and future releases this functionality if built in. You can enable it from the Mythbuntu Control Centre on the repos tab.

For releases prior to 12.04, please go to [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) for more information and to download the Mythbuntu Repos package.

---

### Post by Nikas on 2009-01-07
0.22-trunk

[http://uk.weeklybuilds.mythbuntu.org/mythbuntu-trunk-0.22/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://uk.weeklybuilds.mythbuntu.org/mythbuntu-trunk-0.22/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

The us-mirror does not give the 404 but no updates found.

---

### Post by superm1 on 2009-01-07
Unfortunately it looks we need to discontinue trunk 0.22 builds for hardy.  hardy doesn't have a new enough qt4 for them to work :(

---

### Post by tgm4883 on 2009-01-07
> **Nikas said:**
> 0.22-trunk

[http://uk.weeklybuilds.mythbuntu.org/mythbuntu-trunk-0.22/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://uk.weeklybuilds.mythbuntu.org/mythbuntu-trunk-0.22/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

The us-mirror does not give the 404 but no updates found.

Thats my bad.  Hardy will not get 0.22 because of the QT4 requirement.  Sorry about that.  I've updated the OP and the webpage.

---

### Post by Nikas on 2009-01-07
> **tgm4883 said:**
> Thats my bad.  Hardy will not get 0.22 because of the QT4 requirement.  Sorry about that.  I've updated the OP and the webpage.

Oh. Ok.. i cant use Intrepid. My server just locks up with newer kernels. Thanks for 0.21-fixes. ;-)

---

### Post by Erast on 2009-01-10
Have the changes for VDPAU (Nvidia Pure Video) been backported to 0.21 ? 

Regards,

Erast

---

### Post by superm1 on 2009-01-10
No, they haven't and likely won't be anytime soon... Still evolving, unstable etc.

---

### Post by joshoekstra on 2009-01-13
Well according to the devs it won't be backported...
It will be one of the features of .22(which hopefully won't take too long)

---

### Post by jyavenard on 2009-01-20
Where are the sources of the trunk packages located?

Unfortunately, the last release 19693 won't start on my machine and keep core-dumping...

So I'd like to get the sources and recompile them myself...

Edit: Found it on the UK mirror, for some reason, it isn't available on the US one
Thank you!
Jean-Yves

---

### Post by tgm4883 on 2009-01-21
19639 starts fine on my 8.10 system.  Can you post the terminal output when you try to start it?  Are you on hardy or intrepid?

---

### Post by jyavenard on 2009-01-27
It was segfaulting as soon as I started.

Sorry, I can't provide a capture, I simply downloaded the package, updated the source to a new revision and it started right away.

BTW, I have completed ported VDPAU support to 0.21-fixes..
Available there:
[http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)
along with Ubuntu packages ...

Works great for me at least :)

---

### Post by superm1 on 2009-01-27
> **jyavenard said:**
> It was segfaulting as soon as I started.

Sorry, I can't provide a capture, I simply downloaded the package, updated the source to a new revision and it started right away.

BTW, I have completed ported VDPAU support to 0.21-fixes..
Available there:
[http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)
along with Ubuntu packages ...

Works great for me at least :)
woah neat!

I'll have to give this a shot on my box now....

---

### Post by mbobak on 2009-01-29
Works great for me!

Thanks!

-Mark

---

### Post by xinix on 2009-01-30
So I just switched to the 0.21+fixes+VDPAU and video looks great!  I have a huge problem with this though;  transitions in the menu are painfully sloooooooow (20+ seconds).  I'm using the 180.22 driver from the repo. Any suggestions would be greatly appreciated

Thanks!

Edit:  fixed the transition problem by changing the transitions to QT.

Now that I set video render to VDPAU Mythtv crashes as soon as it tries to play a video.

---

### Post by jyavenard on 2009-01-30
> **xinix said:**
> So I just switched to the 0.21+fixes+VDPAU and video looks great!  I have a huge problem with this though;  transitions in the menu are painfully sloooooooow (20+ seconds).  I'm using the 180.22 driver from the repo. Any suggestions would be greatly appreciated

Thanks!

Edit:  fixed the transition problem by changing the transitions to QT.

Now that I set video render to VDPAU Mythtv crashes as soon as it tries to play a video.

Hi

What video card do you have ?
Prior to using Qt for display rendering, was VDPAU working ?

Jean-Yves

---

### Post by xinix on 2009-01-30
It's a 6200,  I just read up on the compatible cards and they start with the series 8xxx cards.  I think thats my problem.  When I first got this installed it didn't occur to me that I had to change things to VDPAU.  I just started playing a show and the picture was better than before, I assumed that it was working.  Then I realized that VDPAU was an option to enable and found it crashes my system.

---

### Post by jyavenard on 2009-01-30
> **xinix said:**
> It's a 6200,  I just read up on the compatible cards and they start with the series 8xxx cards.  I think thats my problem.  When I first got this installed it didn't occur to me that I had to change things to VDPAU.  I just started playing a show and the picture was better than before, I assumed that it was working.  Then I realized that VDPAU was an option to enable and found it crashes my system.

Yes, the VDPAU build isn't for you...

The 6200 won't handle the VDPAU features incorporated in my patches.. 

For the picture to be better, you would have to use the new OpenGL rendering and de-interlacer, the vdpau patches includes Mark Kendall OpenGL patches, made huge improvements there... If you check my repository, I have older packages without VDPAU but with the OpenGL fixes only

I'm surprised that using VDPAU crashes your system however, it should just default to xv or opengl if vdpau isn't available...

Jean-Yves

---

### Post by Nikas on 2009-02-03
I'm trying to use trunk with 8.10 (VirtualBox)

It's not working.
I can post my apt-get output but it's in swedish.
Stuff about broken-pipe.. 
How can i get the output in english?

Edit:
Got it (US-mirror. The UK-mirror are giving some other error message, PGP-error or something):
```
root@mythtv-test:/var/log# LC_ALL=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk19789-0ubuntu0+mythbuntu1) but 0.21.0+fixes18722-0ubuntu1 is installed
  mythtv-database: Depends: mythtv-common (= 0.21.0+trunk19789-0ubuntu0+mythbuntu1) but 0.21.0+fixes18722-0ubuntu1 is installed
  mythtv-frontend: Depends: mythtv-common (= 0.21.0+trunk19789-0ubuntu0+mythbuntu1) but 0.21.0+fixes18722-0ubuntu1 is installed
  mythtv-transcode-utils: Depends: mythtv-common (= 0.21.0+trunk19789-0ubuntu0+mythbuntu1) but 0.21.0+fixes18722-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
root@mythtv-test:/var/log# LC_ALL=C apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  mytharchive-data mythcontrols mythflix mythgallery mythgame mythmusic
  mythnews mythtv-common
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0B/23.2MB of archives.
After this operation, 4293kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 106992 files and directories currently installed.)
Preparing to replace mythtv-common 0.21.0+fixes18722-0ubuntu1 (using .../mythtv-common_0.21.0+trunk19789-0ubuntu0+mythbuntu1_all.deb) ...
Unpacking replacement mythtv-common ...
dpkg: error processing /var/cache/apt/archives/mythtv-common_0.21.0+trunk19789-0ubuntu0+mythbuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default/controls-ui.xml', which is also in package mythcontrols
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mytharchive-data 0.21.0+fixes18722-0ubuntu1 (using .../mytharchive-data_0.21.0+trunk19693-0ubuntu0+mythbuntu1_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk19693-0ubuntu0+mythbuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mytharchive-ui.xml', which is also in package mythtv-common
Preparing to replace mythcontrols 0.21.0+fixes18722-0ubuntu1 (using .../mythcontrols_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythcontrols ...
dpkg: error processing /var/cache/apt/archives/mythcontrols_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/controls-ui.xml', which is also in package mythtv-common
Preparing to replace mythflix 0.21.0+fixes18722-0ubuntu1 (using .../mythflix_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythflix ...
dpkg: error processing /var/cache/apt/archives/mythflix_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/netflix-ui.xml', which is also in package mythtv-common
No apport report written because MaxReports is reached already
                                                              Preparing to replace mythgallery 0.21.0+fixes18722-0ubuntu1 (using .../mythgallery_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythgallery ...
dpkg: error processing /var/cache/apt/archives/mythgallery_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/gallery-ui.xml', which is also in package mythtv-common
No apport report written because MaxReports is reached already
                                                              Preparing to replace mythgame 0.21.0+fixes18722-0ubuntu1 (using .../mythgame_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythgame ...
dpkg: error processing /var/cache/apt/archives/mythgame_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/game-ui.xml', which is also in package mythtv-common
No apport report written because MaxReports is reached already
                                                              Preparing to replace mythmusic 0.21.0+fixes18722-0ubuntu1 (using .../mythmusic_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythmusic ...
dpkg: error processing /var/cache/apt/archives/mythmusic_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mm_waiting.png', which is also in package mythtv-common
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mythnews 0.21.0+fixes18722-0ubuntu1 (using .../mythnews_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb) ...
Unpacking replacement mythnews ...
dpkg: error processing /var/cache/apt/archives/mythnews_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/news-ui.xml', which is also in package mythtv-common
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-common_0.21.0+trunk19789-0ubuntu0+mythbuntu1_all.deb
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk19693-0ubuntu0+mythbuntu1_all.deb
 /var/cache/apt/archives/mythcontrols_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
 /var/cache/apt/archives/mythflix_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
 /var/cache/apt/archives/mythgallery_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
 /var/cache/apt/archives/mythgame_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
 /var/cache/apt/archives/mythmusic_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
 /var/cache/apt/archives/mythnews_0.21.0+trunk19693-0ubuntu0+mythbuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mythtv-test:/var/log# 
```

---

### Post by thewOndErEr57 on 2009-02-12
For what it's worth xinix,

I have done some naive tests on VDPAU, and I must say that, despite some recent critisism in the direction of the nvidia team, VDPAU support is excellent news, and the tests show this.
From 29% CPU usage down to 2% with VDPAU.

If you're tempted, I would recommend spending a bit of money to buy the Geforce 8 or higher card that has VDPAU support.

See the results here:
[VDPAU benchmarks]("http://linuxsoftwareblog.com/blog/?p=58")

---

### Post by keimol on 2009-02-22
Topic mentions Jaunty builds but it seems they are not available?

---

### Post by andyrm on 2009-02-22
I'm new to Mythbuntu but not a linux newbie. I'm trying to update Intrepid with svn-0.22 build. I followed the directions on the auto-builds page. I also uninstalled all myth apps before following the instructions. apt-get upgrade always seems to pull the svn-0.21 trunk instead of the 0.22 trunk. How can i fix that. I'm a Slackware user so I'm just getting use to Ubuntu.

---

### Post by superm1 on 2009-02-22
The builds are labeled as 0.21+trunkXYZ

This is because 0.22 is not actually released yet.  So it's "0.21" + "all the trunk stuff after 0.21"

---

### Post by andyrm on 2009-02-22
> **superm1 said:**
> The builds are labeled as 0.21+trunkXYZ

This is because 0.22 is not actually released yet.  So it's "0.21" + "all the trunk stuff after 0.21"

I'm trying to to use the 0.22 svn buid. My backend which runs on BlueWhite64 is on the svn-0.22 build. All of my frontends are on the same build. I'm considering moving to Mythbuntu so that's why I need to use the 0.22 svn release. Is there a way to easily compile from the source code in Mythbuntu.

---

### Post by keimol on 2009-02-22
> **keimol said:**
> Topic mentions Jaunty builds but it seems they are not available?
Also, I should mention that I'm interested in the trunk builds. Bleeding edge FTW.

---

### Post by tgm4883 on 2009-02-22
> **andyrm said:**
> I'm trying to to use the 0.22 svn buid. My backend which runs on BlueWhite64 is on the svn-0.22 build. All of my frontends are on the same build. I'm considering moving to Mythbuntu so that's why I need to use the 0.22 svn release. Is there a way to easily compile from the source code in Mythbuntu.

Until upstream actually makes a branch for 0.22, there will not be a 0.22 package.  There is however, a 0.21+trunk branch which is what you are looking for.  As superm1 said, it is called that because upstream has not made a separate branch for 0.22 yet.  What you are using on BlueWhite64 has an (IMO) incorrect version number.  Until upstream makes a new branch for 0.22, there is no 0.22, it is just trunk.

---

### Post by andyrm on 2009-02-22
> **tgm4883 said:**
> Until upstream actually makes a branch for 0.22, there will not be a 0.22 package.  There is however, a 0.21+trunk branch which is what you are looking for.  As superm1 said, it is called that because upstream has not made a separate branch for 0.22 yet.  What you are using on BlueWhite64 has an (IMO) incorrect version number.  Until upstream makes a new branch for 0.22, there is no 0.22, it is just trunk.

My mistake, I't trying to get the trunk and even though the url leads you to believe that I'm getting the mythtv trunk, I get the 0.21 fixes. I've been running on the trunk since October. It's been pretty good. My database and all my recordings are in the database used by trunk so I can't go back without lots of pain and possibly loosing all of my recordings. Is there an easy way for me to build from source in Mythbuntu. I've been running Slackware since it's inception and I know my way around that environment. I just need a few pointers for the Ubuntu environment. 

I'm considering migrating to Ubuntu for all my 7 workstations and servers. this is just the first step.

---

### Post by grytpype on 2009-03-03
> **keimol said:**
> Topic mentions Jaunty builds but it seems they are not available?

Right, where are the .21-fixes for Jaunty?

---

### Post by Nikas on 2009-03-11
> **grytpype said:**
> Right, where are the .21-fixes for Jaunty?

No .21-fixes for hardy for a long time either..

---

### Post by Nikas on 2009-03-13
Got some fixes today but...

```
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What now?!

---

### Post by superm1 on 2009-03-13
> **Nikas said:**
> Got some fixes today but...

```
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

```What now?!
<shrug>

OK, well the build problems were sorted out, that's why these suddenly showed up.

Try this:

```
apt-get -f install
```

If that doesn't do the trick, can you modify /var/lib/dpkg/info/mythtv-backend.postinst

and add a
```
set -x
```

Near the top (but after #!/bin/sh)

Try an apt-get -f install again after you make that change.  Please post the output here so we can debug it and get that fixed.

---

### Post by Nikas on 2009-03-13
> **superm1 said:**
> <shrug>

OK, well the build problems were sorted out, that's why these suddenly showed up.

Try this:

```
apt-get -f install
```

If that doesn't do the trick, can you modify /var/lib/dpkg/info/mythtv-backend.postinst

and add a
```
set -x
```

Near the top (but after #!/bin/sh)

Try an apt-get -f install again after you make that change.  Please post the output here so we can debug it and get that fixed.

Did not work. :( (edit: solution after the paste)

> root@mythtv:/home/niklas# LC_ALL=C apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-xml libgeoip1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-backend (0.21.0+fixes20205-0ubuntu0+mythbuntu1) ...
+ [ ! -e /dev/.devfsd ]
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/mythtv-backend.postinst co                                                                             nfigure 0.21.0+fixes19878-0ubuntu0+mythbuntu1
+ [ ! -e /dev/.devfsd ]
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ db_get mythtv/create_v4l_devs
+ _db_cmd GET mythtv/create_v4l_devs
+ IFS=  printf %s\n GET mythtv/create_v4l_devs
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ cd /dev
+ MAKEDEV v4l
udev active, devices will be created in /dev/.static/dev/
+ [ -d /var/log/mythtv ]
+ dpkg-statoverride --list /var/log/mythtv
+ chown mythtv:mythtv /var/log/mythtv
+ chmod 2775 /var/log/mythtv
+ [ -d /var/lib/mythtv/recordings ]
+ dpkg-statoverride --list /var/lib/mythtv/recordings
+ chown mythtv:mythtv /var/lib/mythtv/recordings
+ chmod 2775 /var/lib/mythtv/recordings
+ [ -d /var/cache/mythtv ]
+ dpkg-statoverride --list /var/cache/mythtv
+ chown mythtv:mythtv /var/cache/mythtv
+ chmod 2775 /var/cache/mythtv
+ [ -z 0.21.0+fixes19878-0ubuntu0+mythbuntu1 ]
+ [ -x /etc/init.d/mythtv-backend ]
+ update-rc.d mythtv-backend defaults 24 16
+ which invoke-rc.d
+ [ -x /usr/sbin/invoke-rc.d ]
+ invoke-rc.d mythtv-backend start
 * MythTV server already started; use restart instead.
invoke-rc.d: initscript mythtv-backend, action "start" failed.
+ exit 1
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); how                                                                             ever:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+m                                                                             ythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mythtv:/home/niklas#

[B]Edit:
I had to kill mythtv-backend myself. Worked just fine after that![/B]

Great work btw! :)

---

### Post by superm1 on 2009-03-13
> **Nikas said:**
> Did not work. :( (edit: solution after the paste)



[B]Edit:
I had to kill mythtv-backend myself. Worked just fine after that![/B]

Great work btw! :)
OK, well you still might have unearthed a bug here if the postinst can't run with mythtv-backend running.  Can you please file a bug on:

[https://bugs.launchpad.net/ubuntu/+source/mythtv](https://bugs.launchpad.net/ubuntu/+source/mythtv)

so that we can track this and it doesn't get forgotten?

---

### Post by movieman on 2009-03-14
Same problem here, and shutting down the backend and then running apt-get -f install resolved it.

However, I still got a whole load of errors from rm, mknod and makedev complaining about a read-only file system:


Setting up mythtv-backend (0.21.0+fixes20205-0ubuntu0+mythbuntu2) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `video0-': Read-only file system
mknod: `video0-': Read-only file system
makedev video0 c 81 0 root video 0660: failed
rm: cannot remove `video0-': Read-only file system
rm: cannot remove `radio0-': Read-only file system
mknod: `radio0-': Read-only file system
makedev radio0 c 81 64 root video 0660: failed

(etc)

I tried going to /dev/.static/dev and creating a file there, and it is indeed a read-only file system.

---

### Post by syphr42 on 2009-03-15
I've been getting tons of those "read-only file system" errors when updating mythtv-backend for months now. I'm running 8.10, but all of my systems are upgrades from 8.04 (if that matters). I have been ignoring it though because it doesn't seem to affect anything.

---

### Post by movieman on 2009-03-15
> **syphr42 said:**
> I'm running 8.10, but all of my systems are upgrades from 8.04 (if that matters).

Mine was a fresh 8.10 install a couple of months ago.

---

### Post by jyavenard on 2009-03-16
> **superm1 said:**
> 

Try an apt-get -f install again after you make that change.  Please post the output here so we can debug it and get that fixed.

Hi

The issue is with what's automatically added to mythtv-backend.postinst by dh_install

# Automatically added by dh_installinit
if [ -x "/etc/init.d/mythtv-backend" ]; then
        update-rc.d mythtv-backend defaults 24 16 >/dev/null
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d mythtv-backend start || exit $?
        else
                /etc/init.d/mythtv-backend start || exit $?
        fi
fi

the mythtv-backend startup script does an exit 1 when started and the mythbackend daemon has already been started.

It would need to be a "restart" there instead of a "start"

The work-around right now is to do /etc/init.d/mythtv-backend stop before running apt or synaptic

In debian/rules, dh_installinit -a -r -- defaults 24 16, should be changed to:
dh_installinit -a -R -- defaults 24 16

so it will restart mythbackend rather than simply start it.
Jean-Yves

---

### Post by dsegel on 2009-03-16
> **movieman said:**
> 
I tried going to /dev/.static/dev and creating a file there, and it is indeed a read-only file system.

Try doing this before you upgrade:

mount -o remount,rw /dev/.static/dev /dev/.static/dev/

You need to specify it like that because it's not in fstab.

---

### Post by dazzed and confussed on 2009-03-16
I can't seem to get this working.

I've tried to stop the Backend with 
sudo /etc/init.d/mythtv-backend stop

~$ sudo LC_ALL=C apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-backend (0.21.0+fixes20205-0ubuntu0+mythbuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-backend
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've tried $ sudo gedit /var/lib/dpkg/info/mythtv-backend.postinst
and adding set -x (As below)

#!/bin/sh

set -x

case "$1" in
    configure)
        if [ ! -e /dev/.devfsd ]; then
            . /usr/share/debconf

Still the same error message.
Can anyone give me some advice.

---

### Post by jyavenard on 2009-03-17
> **dazzed and confussed said:**
> 
dpkg (subprocess): unable to execute post-installation script: Exec format error

You've screwed up something here ; like installing a package for the wrong architecture.

I would uninstall the package completely and install it again .

Make sure mythtbackend isn't running in the mean time

---

### Post by movieman on 2009-03-22
While I was updating today, I noticed an error message about an invalid mysql admin password; any idea where the installer is getting that password from, so I can figure out what's wrong?

---

### Post by superm1 on 2009-03-22
> **movieman said:**
> While I was updating today, I noticed an error message about an invalid mysql admin password; any idea where the installer is getting that password from, so I can figure out what's wrong?
Yeah, when that happens, run:

dpkg-reconfigure mythtv-database

It will ask you for the root mysql password which you can then enter.

---

### Post by movieman on 2009-03-22
Thanks!

---

### Post by Nikas on 2009-03-24
> **superm1 said:**
> Yeah, when that happens, run:

dpkg-reconfigure mythtv-database

It will ask you for the root mysql password which you can then enter.

I did use that command but got "Failed to connect to database (incorrect admin password)" when running the update.

---

### Post by superm1 on 2009-03-24
> **Nikas said:**
> I did use that command but got "Failed to connect to database (incorrect admin password)" when running the update.
Well then i'd make sure you have the root password set right.  Run this to reset it:

dpkg-reconfigure mysql-server-5.0

---

### Post by Nikas on 2009-03-24
> **superm1 said:**
> Well then i'd make sure you have the root password set right.  Run this to reset it:

dpkg-reconfigure mysql-server-5.0

How do you mean right?
I have changed the root password to my own.

---

### Post by superm1 on 2009-03-24
> **Nikas said:**
> How do you mean right?
I have changed the root password to my own.
If this is the case, then the packaging for when you run dpkg-reconfigure mythtv-database should be handling this case properly.  If it's not, then you might have unearthed a bug.

Do you by chance use any non alpha numeric characters in your password?  That's the only thing I could think that would be causing breakage with it.

---

### Post by Nikas on 2009-03-24
> **superm1 said:**
> If this is the case, then the packaging for when you run dpkg-reconfigure mythtv-database should be handling this case properly.  If it's not, then you might have unearthed a bug.

Do you by chance use any non alpha numeric characters in your password?  That's the only thing I could think that would be causing breakage with it.

Just a-z 0-9..

---

### Post by superm1 on 2009-03-24
> **Nikas said:**
> Just a-z 0-9..
Well could you set your root password to something more common temporarily and try it with that?  If that doesn't work properly, then open up a bug (and mention the common password you were trying with) and we'll carry on debugging there.

---

### Post by joshoekstra on 2009-03-27
Hmmm, I get a second set of packages for update today, the SVN-numbers have gone from 20273 to 20274. I like regular updates, but is this supposed to happen? ;)
All packages seem to be working fine, so I'm not complaining. Just an observation.

---

### Post by Nikas on 2009-03-29
> **joshoekstra said:**
> Hmmm, I get a second set of packages for update today, the SVN-numbers have gone from 20273 to 20274. I like regular updates, but is this supposed to happen? ;)
All packages seem to be working fine, so I'm not complaining. Just an observation.

Yes. It's more like daily builds now. ;-)

---

### Post by tgm4883 on 2009-03-29
> **joshoekstra said:**
> Hmmm, I get a second set of packages for update today, the SVN-numbers have gone from 20273 to 20274. I like regular updates, but is this supposed to happen? ;)
All packages seem to be working fine, so I'm not complaining. Just an observation.

> **Nikas said:**
> Yes. It's more like daily builds now. ;-)

We were having some issues with some of the builds, and in order to rebuild them, we have to rebuild everything (not just the part that failed).  This seems to have been worked out now though.

---

### Post by superm1 on 2009-03-29
It's because there has been a concerted effort to fix a lot of things about the trunk build (plugins etc).   Everything should be working now...

(Famous Last Words)

---

### Post by Nikas on 2009-03-29
I cant get trunk to work with mythbuntu 8.10..(something fails when running apt-get upgrade) haven't tried lately but i will try again in my virtual machine tonight.

---

### Post by jyavenard on 2009-03-31
Just a quick question..

Was trying the Mythbuntu 9.04-beta CD.

Is there a way to force the installation of a frontend when the backend or mysql database can't be reached?

I wanted to test installing on a USB flash drive while offline and I couldn't.

Must install a full backend+frontend instead.

There should be a way to allow installation, even if it can't contact the mysql database.

Thanks
Jean-Yves

---

### Post by superm1 on 2009-03-31
> **jyavenard said:**
> Just a quick question..

Was trying the Mythbuntu 9.04-beta CD.

Is there a way to force the installation of a frontend when the backend or mysql database can't be reached?

I wanted to test installing on a USB flash drive while offline and I couldn't.

Must install a full backend+frontend instead.

There should be a way to allow installation, even if it can't contact the mysql database.

Thanks
Jean-Yves
Hi Jean:

Starting at RC this will be doable.  If your backend isn't contactable because of a wireless network or what not, then start up in Live mode rather than install mode to be able to contact the wireless network.

---

### Post by Nikas on 2009-04-04
I cant get trunk to work with 8.10.
Clean install via VirtualBox:

```
root@mythtv-test:/home/niklas# LC_ALL=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
  linux-restricted-modules-generic mythcontrols mythflix mythgallery
  mythgame mythmovies mythmusic mythnews mythphone mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils mythvideo mythweather
The following packages will be upgraded:
  mytharchive-data
1 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
184 not fully installed or removed.
Need to get 0B/13.4MB of archives.
After this operation, 582kB of additional disk space will be used.
Do you want to continue [Y/n]? Y     
(Reading database ... 91054 files and directories currently installed.)
Preparing to replace mytharchive-data 0.21.0+fixes18722-0ubuntu1 (using .../mytharchive-data_0.21.0+trunk20300-0ubuntu0+mythbuntu1_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20300-0ubuntu0+mythbuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mytharchive-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20300-0ubuntu0+mythbuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mythtv-test:/home/niklas# 
```

How should i add trunk with a clean install?
Do i have to start with update and upgrade before i add the trunk repo or something?
Should i use dist-upgrade?

---

### Post by endemoniada on 2009-04-05
Following a update to Jaunty beta, I tried to add the weekly builds to my repos list and hit a problem, I`ve installed the deb package twice and both times it`s trying to connect to the PPA repo, even though I chose the UK server on the first try & US on the second (doing a complete purge removal of the package between tries)

> W: Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/ppa/ubuntu/dists/jaunty/Release.gpg](http://weeklybuilds.mythbuntu.org/mythbuntu/ppa/ubuntu/dists/jaunty/Release.gpg)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

W: Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://weeklybuilds.mythbuntu.org/mythbuntu/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

is there a way of fixing this manually, without having to go through the rigmarole of removing the package & reinstalling i.e manually editing the lines in etc/apt/sources.list

What was wrong with the old way of doing things using terminal entries to add entries/gpg key etc

---

### Post by wombo on 2009-04-05
> **Nikas said:**
> How should i add trunk with a clean install?
Do i have to start with update and upgrade before i add the trunk repo or something?
Should i use dist-upgrade?

When I installed it I installed mythbuntu 9.04.
Skipped the Mythtv setup bit
Rebooted
Updated the base Operating system
Then added trunk.

---

### Post by tgm4883 on 2009-04-06
> **endemoniada said:**
> Following a update to Jaunty beta, I tried to add the weekly builds to my repos list and hit a problem, I`ve installed the deb package twice and both times it`s trying to connect to the PPA repo, even though I chose the UK server on the first try & US on the second (doing a complete purge removal of the package between tries)



is there a way of fixing this manually, without having to go through the rigmarole of removing the package & reinstalling i.e manually editing the lines in etc/apt/sources.list

What was wrong with the old way of doing things using terminal entries to add entries/gpg key etc

Ok, first, thats not the PPA.  The PPA address looks like [http://ppa.launchpad.net/mythbuntu/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu/ppa/ubuntu)  The address that you posted is to the US repo.  The US (and UK) repos mirror from the PPA, that is why there is PPA in that link.

It would appear that the weekly builds repo server is down.  It is not responding to pings.  In the words of superm1 "so that likely means that an army of little children attacked the datacentre with plastic sporks and succeeded".  Our suggestion is to either wait for the server to come back up, or switch to the PPA.

There is nothing wrong with the weekly-build package.  It has been tested and works great.  It is easier for users to install and configure this package (and reconfigure to change between repos).  This package also installs the GPGKEY, so thats another step the user doesn't need to do anymore.  If you want to change between repos, instead of purging and reinstalling the package, do "dpkg-reconfigure mythbuntu-weekly".  If you wish to not use the package, you can still manually add the repos to your sources.list and manually add the GPGKEY.  I'll leave you to find out how to do that on your own though.

---

### Post by Nikas on 2009-04-06
> **wombo said:**
> When I installed it I installed mythbuntu 9.04.
Skipped the Mythtv setup bit
Rebooted
Updated the base Operating system
Then added trunk.

As i did then... clean install... :/
I will give 9.04 a try.

---

### Post by tgm4883 on 2009-04-06
The US repo is back up, not sure whats going on with the UK repo though.

---

### Post by joshoekstra on 2009-04-17
Any reason why the latest mythweb-package makes a redirect to mythweb?
I answerred no on the question if the machine is only used with mythweb, still it overwrote the existing index.html and made a redirect-rule or something.

---

### Post by superm1 on 2009-04-17
> **joshoekstra said:**
> Any reason why the latest mythweb-package makes a redirect to mythweb?
I answerred no on the question if the machine is only used with mythweb, still it overwrote the existing index.html and made a redirect-rule or something.
Last week's package made that change, the latest package will ask if it's okay to do add such a rule and do it more nicely (via vhosts)

---

### Post by joshoekstra on 2009-04-17
Hmmm, how do I point it back to the original solution I had before?
I was using and index.html in the /var/www before and that seems to have been overwritten as well, even putting in a dummy that says hello doesn't get seen and redirects automatically to mythweb.

---

### Post by Nikas on 2009-04-26
Cant get trunk to work with 8.10 or 9.04:

apt-get upgrade
```
root@mythtv-test:/etc/apt/sources.list.d# LC_ALL=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythcontrols mythgallery mythmovies mythmusic mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils mythvideo mythweather
The following packages will be upgraded:
  mytharchive-data
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
16 not fully installed or removed.
Need to get 0B/13.5MB of archives.
After this operation, 582kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 91052 files and directories currently installed.)
Preparing to replace mytharchive-data 0.21.0+fixes19556-0ubuntu8 (using .../mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mythnative-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

apt-get dist-upgrade
```
root@mythtv-test:/etc/apt/sources.list.d# LC_ALL=C apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  mythcontrols
The following NEW packages will be installed:
  gstreamer0.10-plugins-good gstreamer0.10-x libmyth-0.22-0 libphonon4
  libqt4-opengl libqt4-webkit nvidia-180-libvdpau phonon
  phonon-backend-gstreamer
The following packages will be upgraded:
  mytharchive-data mythgallery mythmovies mythmusic mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils mythvideo mythweather
13 upgraded, 9 newly installed, 1 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B/44.5MB of archives.
After this operation, 51.3MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
Failed to connect to database (incorrect admin password)
(Reading database ... 91052 files and directories currently installed.)
Preparing to replace mytharchive-data 0.21.0+fixes19556-0ubuntu8 (using .../mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mythnative-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

You can see "Failed to connect to database (incorrect admin password)" too. Brand new and clean install (9.04).
Should i do upgrade or dist-upgrade btw? Packages are being held back if i don't use dist-upgrade.

---

### Post by superm1 on 2009-04-26
> **Nikas said:**
> Cant get trunk to work with 8.10 or 9.04:

apt-get upgrade
```
root@mythtv-test:/etc/apt/sources.list.d# LC_ALL=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythcontrols mythgallery mythmovies mythmusic mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils mythvideo mythweather
The following packages will be upgraded:
  mytharchive-data
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
16 not fully installed or removed.
Need to get 0B/13.5MB of archives.
After this operation, 582kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 91052 files and directories currently installed.)
Preparing to replace mytharchive-data 0.21.0+fixes19556-0ubuntu8 (using .../mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mythnative-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```apt-get dist-upgrade
```
root@mythtv-test:/etc/apt/sources.list.d# LC_ALL=C apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  mythcontrols
The following NEW packages will be installed:
  gstreamer0.10-plugins-good gstreamer0.10-x libmyth-0.22-0 libphonon4
  libqt4-opengl libqt4-webkit nvidia-180-libvdpau phonon
  phonon-backend-gstreamer
The following packages will be upgraded:
  mytharchive-data mythgallery mythmovies mythmusic mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils mythvideo mythweather
13 upgraded, 9 newly installed, 1 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B/44.5MB of archives.
After this operation, 51.3MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
Failed to connect to database (incorrect admin password)
(Reading database ... 91052 files and directories currently installed.)
Preparing to replace mytharchive-data 0.21.0+fixes19556-0ubuntu8 (using .../mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb) ...
Unpacking replacement mytharchive-data ...
dpkg: error processing /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/mythnative-ui.xml', which is also in package mythtv-common
Errors were encountered while processing:
 /var/cache/apt/archives/mytharchive-data_0.21.0+trunk20445-0ubuntu0+mythbuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```You can see "Failed to connect to database (incorrect admin password)" too. Brand new and clean install (9.04).
Should i do upgrade or dist-upgrade btw? Packages are being held back if i don't use dist-upgrade.
I think this is an order-of-operations kind of bug. (Still a bug tho)

If you try to do:

apt-get install mythtv mytharchive mytharchive-data
apt-get dist-upgrade

I bet it will work.  If so, can try to put a fix in the next set of weeklies to force that order with the file that got moved to mytharchive-data.

---

### Post by Nikas on 2009-04-26
I did a new install.
Used only dist-upgrade and it worked.

---

### Post by Nikas on 2009-04-29
> **superm1 said:**
> Unfortunately it looks we need to discontinue trunk 0.22 builds for hardy.  hardy doesn't have a new enough qt4 for them to work :(

Still no new QT4 or is it not possible for Hardy?

---

### Post by tgm4883 on 2009-04-29
> **Nikas said:**
> Still no new QT4 or is it not possible for Hardy?

AFAIK, The newer version of QT4 isn't likely to be backported to hardy.  Backports 

From [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
> Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

Based on this, I don't think QT4 is eligible for a backport.  This means hardy will not get MythTV 0.22 (Officially anyway).

---

### Post by Daminator on 2009-05-01
None of the Jaunty repositories seem to be working for me. Are they all broken? All was fine with the Intrepid ones before I upgraded to 9.04

Damian

---

### Post by joshoekstra on 2009-05-04
> **Daminator said:**
> None of the Jaunty repositories seem to be working for me. Are they all broken? All was fine with the Intrepid ones before I upgraded to 9.04

Damian
Did you try these:

deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main

These seem to be fine for me :)

---

### Post by BassKozz on 2009-05-09
Auto-Builds seems to be down...
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) -> links to -> [http://www.mythbuntu.org/Temp%20Unavailable](http://www.mythbuntu.org/Temp%20Unavailable)
> **joshoekstra said:**
> Did you try these:

deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main

These seem to be fine for me :)

When adding this to my "Third-Party Software Sources" do I need to add both the deb & deb-src (deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main & deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main) or just the first one?

---

### Post by joshoekstra on 2009-05-09
> **BassKozz said:**
> Auto-Builds seems to be down...
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) -> links to -> [http://www.mythbuntu.org/Temp%20Unavailable](http://www.mythbuntu.org/Temp%20Unavailable)


When adding this to my "Third-Party Software Sources" do I need to add both the deb & deb-src (deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main & deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main) or just the first one?

Just the first one should be ok as well :)

---

### Post by tgm4883 on 2009-05-10
> **BassKozz said:**
> Auto-Builds seems to be down...
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) -> links to -> [http://www.mythbuntu.org/Temp%20Unavailable](http://www.mythbuntu.org/Temp%20Unavailable)


When adding this to my "Third-Party Software Sources" do I need to add both the deb & deb-src (deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main & deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main) or just the first one?

This is fixed now, you can grab the new package

---

### Post by tgm4883 on 2009-05-10
also, 

```
http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu
```

is the wrong link now, please use the package

---

### Post by Daminator on 2009-05-10
is the 'testing' ppa safe to use, or is that for trunk? I only ever used the more stable build with weekly fixes. Myth seems to need enough work as it is without using 'testing' bleeding edge packages before they are ready.

---

### Post by tgm4883 on 2009-05-10
> **Daminator said:**
> is the 'testing' ppa safe to use, or is that for trunk? I only ever used the more stable build with weekly fixes. Myth seems to need enough work as it is without using 'testing' bleeding edge packages before they are ready.

The testing PPA does not contain MythTV packages.  It instead contains things like updated packages of MythExport, MythNetTV, and such.  It will also contain new packages that aren't in the repos yet such as (eventually) MythFeed and MythBoinc.

---

### Post by Daminator on 2009-05-10
That sounds great!

Can those things then be added using the Mythbuntu Control Panel? If not, how do you know what to add and how to use them? Excuse me if this is all realy straight forward, but I'd never heard of this side of mythbuntu before! Obviously been using it for a couple of years without knowing about extra features!

Cheers
Damian

---

### Post by tgm4883 on 2009-05-11
> **Daminator said:**
> That sounds great!

Can those things then be added using the Mythbuntu Control Panel? If not, how do you know what to add and how to use them? Excuse me if this is all realy straight forward, but I'd never heard of this side of mythbuntu before! Obviously been using it for a couple of years without knowing about extra features!

Cheers
Damian

Sorry, that cannot be added from MCC.  In the next release of MCC, you will be able to activate these repos though, but in order to know what is in that repo (that you haven't already got installed) you will have to check the PPA.  Eventually, we may have a page on mythbuntu.org that has this information available.

If the testing PPA contains new versions of software you already have installed (ie. MythNetTV, MythExport, etc) then just and apt-get update and apt-get upgrade will suffice.

---

### Post by oobe-feisty on 2009-05-12
.

---

### Post by joshoekstra on 2009-05-14
> **joshoekstra said:**
> Did you try these:

deb [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu) jaunty main

These seem to be fine for me :)
Should have been:
deb [http://ppa.launchpad.net/mythbuntu/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu/ppa/ubuntu) jaunty main

Sorry for the confusion.

---

### Post by pigah on 2009-05-14
I just tried upgrading to trunk and having problems like Nikas with database password.  I dpkg-reconfigured both mysql-server-5.0 and mythtv-database to have the same password.  

dpkg-reconfigure mysql-server-5.0 seems to work but gives the following warning: 
"090514 11:54:37 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576"

dpkg-reconfigure mythtv-database exits with:

"Failed to create or modify database (incorrect admin username/password?)"

When I look at the mythbackend logs there is this nugget:

```

2009-05-14 11:50:55.300 mythbackend version: trunk [Unknown] www.mythtv.org
2009-05-14 11:50:55.317 Using runtime prefix = /usr
2009-05-14 11:50:55.320 Empty LocalHostName.
2009-05-14 11:50:55.321 Using localhost value of mythtv
2009-05-14 11:50:55.374 New DB connection, total: 1
2009-05-14 11:50:55.408 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:55.411 Closing DB connection named 'DBManager0'
2009-05-14 11:50:55.414 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:55.441 Current Schema Version: 1224
2009-05-14 11:50:55.442 Database schema is old. Waiting to see if DB is being upgraded.
2009-05-14 11:50:56.444 New DB connection, total: 2
2009-05-14 11:50:56.447 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:56.458 Current Schema Version: 1224
2009-05-14 11:50:57.470 Current Schema Version: 1224
2009-05-14 11:50:58.482 Current Schema Version: 1224
2009-05-14 11:50:59.492 Current Schema Version: 1224
2009-05-14 11:51:00.501 Current Schema Version: 1224
2009-05-14 11:51:00.504 Timed out waiting.
2009-05-14 11:51:00.544 Database backup script does not exist: /usr/share/mythtv/mythconverg_backup.pl
2009-05-14 11:51:00.561 Backing up database to file: '/var/lib/mythtv/recordings/mythconverg-1224-20090514115100.sql'
2009-05-14 11:51:00.613 DBUtil Error: Error backing up database: 'mysqldump --defaults-extra-file='/tmp/mythtv_db_backup_conf_RApObJ' --host='localhost' --user='root' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick 'mythconverg' > '/var/lib/mythtv/recordings/mythconverg-1224-20090514115100.sql' 2>/dev/null' (512)
2009-05-14 11:51:00.705 Console is non-interactive, can't prompt user...
2009-05-14 11:51:00.708 Upgrading.
2009-05-14 11:51:00.710 Newest Schema Version : 1232
2009-05-14 11:51:00.724 Upgrading to schema version 1225
2009-05-14 11:51:00.726 DB Error (Performing database upgrade): 
Query was: CREATE TABLE bad_people AS SELECT * FROM people; 
Error was: Driver error was [2/1050]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'bad_people' already exists
 
new version: 1225
2009-05-14 11:51:00.728 Database Schema upgrade FAILED, unlocking.
2009-05-14 11:51:00.732 Couldn't upgrade database to new schema

```

---

### Post by tgm4883 on 2009-05-14
> **joshoekstra said:**
> Should have been:
deb [http://ppa.launchpad.net/mythbuntu/ppa/ubuntu](http://ppa.launchpad.net/mythbuntu/ppa/ubuntu) jaunty main

Sorry for the confusion.

No.  This is also an incorrect link.  Please use the Mythbuntu Repos package located at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) 

The package there will allow you to select which Mythbuntu repos to install.

---

### Post by Daminator on 2009-05-14
The repros package only seems to allow you to select once.

I have tried running it from the web site a second time and it doesn't ask me which option I want to choose. If the program is installed somewhere, I can't find it.

Damian

---

### Post by tgm4883 on 2009-05-14
> **Daminator said:**
> The repros package only seems to allow you to select once.

I have tried running it from the web site a second time and it doesn't ask me which option I want to choose. If the program is installed somewhere, I can't find it.

Damian

From the website

> Mythbuntu Repos - This program will install and configure the weekly build repo for you. Just install this program and it will ask you which version you want to use (-fixes or -trunk), and which repo you want to use (US, UK, or PPA). During install you will also be asked if you would like the -testing PPA activated. **If you already have the Mythbuntu Repos package installed and would like to activate the weekly builds repo, from a command line just do 'dpkg-reconfigure mythbuntu-repos'** 

I'll edit that line so it's a little more clear.

---

### Post by Neon Dusk on 2009-05-14
If you need to get the source pacakges for weekly fixes-0.21 is a case of manually adding 'deb-src [http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu](http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu) jaunty main'?

---

### Post by Dubstar_04 on 2009-05-15
The weekly builds packaged seems to be messed up in Jaunty. it seems that the repos are unavailable.

---

### Post by tgm4883 on 2009-05-15
> **Dubstar_04 said:**
> The weekly builds packaged seems to be messed up in Jaunty. it seems that the repos are unavailable.

Are you talking about the weekly builds package, or the new Mythbuntu Repos package?  We recently switched everything to a single account in launchpad, so you may have to install the new Mythbuntu Repos package.

---

### Post by jyavenard on 2009-05-23
Hi

I've noticed the the mythbuntu package mythtv-backend installs compressed version (gzip) of all the perl scripts. Making them pretty much useless as-is.

this is due to calling dh_compress in debian/rules

The package really shouldn't compress any perl or python scripts.

Could change that to dh_compress -X.pl -X.py

---

### Post by lionsnob on 2009-07-05
Hello,

I've noticed that the changes for the July 3rd build for trunk has mismatched versions for mythtv-backend and mythtv-backend-master and thus dependency issues.  I tried downloading the older debs for mythtv-backend but still no avail.  I just got a brand new backend server that I'm trying to transfer my HD-PVR and new HDHomeRun to :)

The two versions are 20745 and 20784.  Any ideas?  Should I just wait another week and see what happens?

---

### Post by tgm4883 on 2009-07-05
> **lionsnob said:**
> Hello,

I've noticed that the changes for the July 3rd build for trunk has mismatched versions for mythtv-backend and mythtv-backend-master and thus dependency issues.  I tried downloading the older debs for mythtv-backend but still no avail.  I just got a brand new backend server that I'm trying to transfer my HD-PVR and new HDHomeRun to :)

The two versions are 20745 and 20784.  Any ideas?  Should I just wait another week and see what happens?

I'm not at home, but let me try to ping someone and get a rebuild.

---

### Post by Daviey on 2009-07-05
> **lionsnob said:**
> Hello,

The two versions are 20745 and 20784.  Any ideas?  Should I just wait another week and see what happens?


Hi, pushing a manual build now.  Hopefully this should resolve the issue.  should hit the mirrors within the next 2 hours or so.

I will watch the build records, and hopefully that should resolve the matter.

Thanks.

---

### Post by awaterson on 2009-07-06
HI have just tried to upgrade to trunk20789 but mythtv-common does not seam to have been built and even then there are only amd64 packages available.  Was there a problem with the build this week?

---

### Post by tgm4883 on 2009-07-06
I believe there was a change upstream that broke some things.

---

### Post by foxjones on 2009-07-06
Hi,

unfortunately the Version conflict is still here, using 

[http://ppa.launchpad.net/mythbuntu/trunk-0.22/](http://ppa.launchpad.net/mythbuntu/trunk-0.22/)

apt says:
```
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
  mythtv-frontend: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
  mythtv-transcode-utils: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
E: Broken packages
```

Greetings,
fox

---

### Post by tgm4883 on 2009-07-06
> **foxjones said:**
> Hi,

unfortunately the Version conflict is still here, using 

[http://ppa.launchpad.net/mythbuntu/trunk-0.22/](http://ppa.launchpad.net/mythbuntu/trunk-0.22/)

apt says:
```
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
  mythtv-frontend: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
  mythtv-transcode-utils: Depends: mythtv-common (= 0.21.0+trunk20789-0ubuntu0+mythbuntu3) but 0.21.0+trunk20745-0ubuntu0+mythbuntu3 is to be installed
E: Broken packages
```

Greetings,
fox

Yep, the breakages that we are seeing have resulted in builds failing. It may have to wait until friday to get sorted.

---

### Post by awaterson on 2009-07-06
sounds fine when using the trunk stuff there is always the possiblity of this happening. Will wait and try on Friday again.  Thanks for the quick response.

---

### Post by jyavenard on 2009-07-07
I would hold off on any trunk update for the time being. ffmpeg just got updated and many things aren't right yet ...

it's likely going to take a little while for things to go back to normal

---

### Post by rtrevor on 2009-07-07
> **jyavenard said:**
> I would hold off on any trunk update for the time being. ffmpeg just got updated and many things aren't right yet ...


I've been having a few issues with specific audio codecs (DTS audio) from previous trunk builds... will be interesting to see if the new version of ffmpeg fixes this (once stabilised):

[http://ubuntuforums.org/showthread.php?t=1205992](http://ubuntuforums.org/showthread.php?t=1205992)

---

### Post by lionsnob on 2009-07-07
> **tgm4883 said:**
> I'm not at home, but let me try to ping someone and get a rebuild.

Thanks for your help!  We'll see how it goes on Friday.

---

### Post by lionsnob on 2009-07-09
> **lionsnob said:**
> Thanks for your help!  We'll see how it goes on Friday.

Looks like its fixed now - version 20830 is listed for all of the modules.  Thanks for clearing this up!

---

### Post by iamretr0 on 2009-07-13
> **pigah said:**
> I just tried upgrading to trunk and having problems like Nikas with database password.  I dpkg-reconfigured both mysql-server-5.0 and mythtv-database to have the same password.  

dpkg-reconfigure mysql-server-5.0 seems to work but gives the following warning: 
"090514 11:54:37 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576"

dpkg-reconfigure mythtv-database exits with:

"Failed to create or modify database (incorrect admin username/password?)"

When I look at the mythbackend logs there is this nugget:

```

2009-05-14 11:50:55.300 mythbackend version: trunk [Unknown] www.mythtv.org
2009-05-14 11:50:55.317 Using runtime prefix = /usr
2009-05-14 11:50:55.320 Empty LocalHostName.
2009-05-14 11:50:55.321 Using localhost value of mythtv
2009-05-14 11:50:55.374 New DB connection, total: 1
2009-05-14 11:50:55.408 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:55.411 Closing DB connection named 'DBManager0'
2009-05-14 11:50:55.414 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:55.441 Current Schema Version: 1224
2009-05-14 11:50:55.442 Database schema is old. Waiting to see if DB is being upgraded.
2009-05-14 11:50:56.444 New DB connection, total: 2
2009-05-14 11:50:56.447 Connected to database 'mythconverg' at host: localhost
2009-05-14 11:50:56.458 Current Schema Version: 1224
2009-05-14 11:50:57.470 Current Schema Version: 1224
2009-05-14 11:50:58.482 Current Schema Version: 1224
2009-05-14 11:50:59.492 Current Schema Version: 1224
2009-05-14 11:51:00.501 Current Schema Version: 1224
2009-05-14 11:51:00.504 Timed out waiting.
2009-05-14 11:51:00.544 Database backup script does not exist: /usr/share/mythtv/mythconverg_backup.pl
2009-05-14 11:51:00.561 Backing up database to file: '/var/lib/mythtv/recordings/mythconverg-1224-20090514115100.sql'
2009-05-14 11:51:00.613 DBUtil Error: Error backing up database: 'mysqldump --defaults-extra-file='/tmp/mythtv_db_backup_conf_RApObJ' --host='localhost' --user='root' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick 'mythconverg' > '/var/lib/mythtv/recordings/mythconverg-1224-20090514115100.sql' 2>/dev/null' (512)
2009-05-14 11:51:00.705 Console is non-interactive, can't prompt user...
2009-05-14 11:51:00.708 Upgrading.
2009-05-14 11:51:00.710 Newest Schema Version : 1232
2009-05-14 11:51:00.724 Upgrading to schema version 1225
2009-05-14 11:51:00.726 DB Error (Performing database upgrade): 
Query was: CREATE TABLE bad_people AS SELECT * FROM people; 
Error was: Driver error was [2/1050]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'bad_people' already exists
 
new version: 1225
2009-05-14 11:51:00.728 Database Schema upgrade FAILED, unlocking.
2009-05-14 11:51:00.732 Couldn't upgrade database to new schema

```


I have this identical problem.  Is there a solution?

---

### Post by Observer64 on 2009-07-16
I use the weekly builds packages for 0.21-fixes under Intrepid. Could the following patch please be integrated into these builds?

[http://cvs.mythtv.org/trac/changeset/17172](http://cvs.mythtv.org/trac/changeset/17172)

It fixes a problem with input groups where one input shares a card with another input which is not in the same group. For example, using firewire capture with s-video/composite capture to a PVR-150. In this setup, the analog tuner is not part of that input group, but if the analog tuner is busy, then the firewire tuner is marked busy as well.

-Ray

---

### Post by tgm4883 on 2009-07-16
> **Observer64 said:**
> I use the weekly builds packages for 0.21-fixes under Intrepid. Could the following patch please be integrated into these builds?

[http://cvs.mythtv.org/trac/changeset/17172](http://cvs.mythtv.org/trac/changeset/17172)

It fixes a problem with input groups where one input shares a card with another input which is not in the same group. For example, using firewire capture with s-video/composite capture to a PVR-150. In this setup, the analog tuner is not part of that input group, but if the analog tuner is busy, then the firewire tuner is marked busy as well.

-Ray

You should ask upstream first. We try to keep as close to the official tree as we can.

---

### Post by Observer64 on 2009-07-16
> **tgm4883 said:**
> You should ask upstream first. We try to keep as close to the official tree as we can.

I have made posts to the mythtv-users and mythtv-dev mailing lists with almost no response. I have tried contacting Daniel K using the email address he uses on the list -- at the suggestion of the community -- also with no response.

I would really like to keep one source from clobbering recordings on the other, and input groups is supposed to be the way to do it.

If someone here has the ear of one of the source managers, your help is greatly appreciated.

If it wasn't so darn convenient to use the weekly build packages, I'd just roll it myself and be done with it. But it shouldn't have to be that way.

-Ray

---

### Post by tgm4883 on 2009-07-17
> **Observer64 said:**
> I have made posts to the mythtv-users and mythtv-dev mailing lists with almost no response. I have tried contacting Daniel K using the email address he uses on the list -- at the suggestion of the community -- also with no response.

I would really like to keep one source from clobbering recordings on the other, and input groups is supposed to be the way to do it.

If someone here has the ear of one of the source managers, your help is greatly appreciated.

If it wasn't so darn convenient to use the weekly build packages, I'd just roll it myself and be done with it. But it shouldn't have to be that way.

-Ray

I'll have our lead dev take a look at it, but usually we try not to stray from upstream unless it's pretty important.

---

### Post by Observer64 on 2009-07-26
Thank you. And as I mentioned before, if someone here could convince someone in charge of the upstream to integrate that patch, it would be appreciated.

-Ray

---

### Post by tgm4883 on 2009-07-28
> **Observer64 said:**
> Thank you. And as I mentioned before, if someone here could convince someone in charge of the upstream to integrate that patch, it would be appreciated.

-Ray

Ok, we aren't going to apply that patch here. My suggestion would be to go to #mythtv-users on freenode and ask there about the patch. You may have to wait around for someone in charge to see it and comment on it.

---

### Post by HW_Hack on 2009-08-02
I just skimmed thru these - lots of info here. I would suggest a simple simple build status indicator be added to the very first post (or somewhere). Just something that give a very terse status for Hardy, Intrepid, Jaunty ...  I know these things can take on a life of their own but even if updated twice a month would great.

Hardy - Very stable. Current issues: Backend:zzz xxx, Install:yyy
Mythbuntu Build: 11111111  MythTV Ver: 0.xx  Last Build:07-22-09

where zzz xxx yyy are just terms you could use in a search to find more info

---

### Post by mbobak on 2009-08-15
Current weekly build broken?

I just updated my weekly build, hoping an intermittent lockup would go away....and it appears to have broken Myth entirely.

I'm getting:
Protocol version mismatch (frontend=46,backend=45)

Now, that's pretty self-explanatory, I see the problem.  I just don't know how to fix it.  Is there a workaround?

I checked to make sure that all myth packages, including frontend and backend, are at the same version.  According to synaptic, all things Myth are at 0.21.0-trunk21261.  And, it seems that's the latest.  Doing sudo apt-get update && sudo apt-get dist-upgrade tells me there are 0 packages to be updated.

So, is mythbuntu weekly broken till next week?  Anyone know of a workaround?

Thanks,

-Mark

---

### Post by jyavenard on 2009-08-15
Upgrade both the mythtv frontends and the backends.

Restart all of them.. you obviously upgraded your frontend but not your backend.

---

### Post by superm1 on 2009-08-15
Doesn't look broken (unless you're on hardy, are you?)

[https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22](https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22)

---

### Post by mabene on 2009-08-17
With revision 21318 DVB-S2 (s2api) support is finally available in mythtv trunk. To actually make this work mythtv must be compiled either with kernel headers >= 2.6.29 or with dvb headers from a recent v4l hg repository.
 
Is there any chance to get mythbuntu weekly builds with this feature?
 
Thanks, Martin

---

### Post by RTucker on 2009-08-30
Ok, I'm trying to upgrade my single combined backend/frontend to 0.22. I've installed the mythbuntu-repos package and ran through it to add the trunk and PPA repos. After which I ran:

```
apt-get update
apt-get upgrade
```Restarted the system and then:
```
apt-get update
apt-get distupgrade
```A lot of packages were updated including a new kernel image, and the mythtv packages. The trouble is that I still don't have 0.22... I definitely selected -trunk (I've checked it 3 times), but for some reason its still 0.21.

The system was originally installed with Hardy, though it has been updated to jaunty for quite a while (and is definitely using the jaunty repos).

Any idea whats going on and how I can get 0.22?

---

### Post by tgm4883 on 2009-08-30
> **RTucker said:**
> Ok, I'm trying to upgrade my single combined backend/frontend to 0.22. I've installed the mythbuntu-repos package and ran through it to add the trunk and PPA repos. After which I ran:

```
apt-get update
apt-get upgrade
```Restarted the system and then:
```
apt-get update
apt-get distupgrade
```A lot of packages were updated including a new kernel image, and the mythtv packages. The trouble is that I still don't have 0.22... I definitely selected -trunk (I've checked it 3 times), but for some reason its still 0.21.

The system was originally installed with Hardy, though it has been updated to jaunty for quite a while (and is definitely using the jaunty repos).

Any idea whats going on and how I can get 0.22?

It might be the naming system that is being used. Post the output of

```
dpkg -l mythtv
```

---

### Post by jyavenard on 2009-08-31
Hi

mythtv provide three set of themes upstream.
The ones that are included in mythtv source code, and which are found in the package mythtv-common

The ones found in trunk/myththemes directory and provided by the various mythtv-themes meta package

And finally 3rd party themes found in trunk/themes which currently aren't packaged directly, but instead are packaged individually using various sources, each with their own versioning.

I've created packages for those ones:
mythtv-themes-extra

source can be found there:
[http://www.avenard.org/files/ubuntu-repos/trunk/myththemes-extra_0.22.0+trunk-21556-0ubuntu1.tar.gz](http://www.avenard.org/files/ubuntu-repos/trunk/myththemes-extra_0.22.0+trunk-21556-0ubuntu1.tar.gz)

And include the following themes:
blootube/
ProjectGrayhem-OSD/
blootubelite-wide/
Graphite/
ProjectGrayhem-wide/
blootube-osd/
neon-wide/
blootube-wide/
ProjectGrayhem/

Would be great if those themes were provided by mythbuntu ...

---

### Post by RTucker on 2009-08-31
Ok, dpkg -l mythtv says:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-============================
ii  mythtv                   2:0.21.0+fixes-21583-ope A personal video recorder application (client and server)
```

---

### Post by tgm4883 on 2009-08-31
> **RTucker said:**
> Ok, dpkg -l mythtv says:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-============================
ii  mythtv                   2:0.21.0+fixes-21583-ope A personal video recorder application (client and server)
```

Ok, it looks as though the trunk build is older than the fixes build. There have been some issues building trunk the last couple weeks. I'll poke the maintainer again and see whats up. 

Latest fixes release
```
mythtv - 0.21.0+fixes21556-0ubuntu0+mythbuntu3 
```

Latest trunk release
```
mythtv - 0.21.0+trunk21261-0ubuntu0+mythbuntu3 
```

---

### Post by tgm4883 on 2009-09-02
Ok, the builds are working again. Please try to update again.

---

### Post by movieman on 2009-09-04
So for the third day in a row the update-manager is telling me that there's a new version of MythTV to install: is this true or is something screwed up here?

---

### Post by tgm4883 on 2009-09-05
> **movieman said:**
> So for the third day in a row the update-manager is telling me that there's a new version of MythTV to install: is this true or is something screwed up here?

It's actually correct. At least up until release, we will be doing daily builds of trunk.

---

### Post by RTucker on 2009-09-12
Ok, so I just tried to upgrade again and still don't have trunk...

during the upgrade I could see it downloading packages marked 0.22, and a bunch of lines such as:

```
Preparing to replace mythtv-themes 0.21.0+trunk21261-0ubuntu0+mythbuntu3 (using .../mythtv-themes_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb) ...
```but there were also lines referencing 0.21, like:

```
Preparing to replace mythvideo 2:0.21.0+fixes-svn20752-jya-0ubuntu0 (using .../mythvideo_2%3a0.21.0+fixes-svn21591-jya-0ubuntu0_i386.deb) ...
```after a reboot apt-get shows no updates are available, but dpkg -l mythtv shows:

```
mythtv                                 2:0.21.0+fixes-21583-openglvdpau2-nv18
```I've gone through ```
sudo dpkg-reconfigure mythbuntu-repos
``` again, and its definitely set to trunk...

Sorry about the slow response, but this system is "in production" during the week, so I can only do major tinkering on the weekends :)

EDIT: Here is the full list...
```

||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  mythtv                                 2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (client and server)
ii  mythtv-backend                         2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (server)
ii  mythtv-backend-master                  2:0.21.0+fixes-21583-openglvdpau2-nv18 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                          2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (common data)
ii  mythtv-database                        2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (database)
un  mythtv-doc                             <none>                                 (no description available)
ii  mythtv-frontend                        2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (client)
ii  mythtv-status                          0.7.3-2ubuntu2                         Show the status of a MythTV backend
ii  mythtv-theme-blootube                  1:0.21.0-0ubuntu1                      The Blootube MythTV theme
ii  mythtv-theme-blootube-osd              1:0.21.0-0ubuntu2                      The Blootube MythTV OSD
ii  mythtv-theme-blootube-wide             1:0.21.0-0ubuntu1                      The Blootube MythTV theme (widescreen)
ii  mythtv-theme-blootubelite-wide         1:0.21.0-0ubuntu1                      The Blootube Lite MythTV theme (widescreen)
ii  mythtv-theme-glass-wide                0.20080908-0ubuntu2                    The Glass MythTV theme (widescreen)
ii  mythtv-theme-gray-osd                  0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Gray-OSD MythTV Theme
ii  mythtv-theme-isthmus                   0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Isthmus MythTV Theme
ii  mythtv-theme-iulius                    0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Iulius MythTV Theme
ii  mythtv-theme-iulius-osd                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Iulius-OSD MythTV Theme
ii  mythtv-theme-metallurgy-osd            1.0-0ubuntu1                           The Metallurgy MythTV OSD theme
ii  mythtv-theme-metallurgy-wide           1.0-0ubuntu1                           The Metallurgy MythTV theme (widescreen)
ii  mythtv-theme-minimalist-wide           0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Minimalist Wide MythTV Theme
ii  mythtv-theme-mythbuntu                 0.20080421                             default MythTV theme used in Mythbuntu
ii  mythtv-theme-mythcenter                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The MythCenter MythTV Theme
ii  mythtv-theme-mythcenter-wide           0.22.0~trunk21783-0ubuntu0~mythbuntu1  The MythCenter Wide MythTV Theme
ii  mythtv-theme-neon-wide                 1:0.21.0-0ubuntu4                      The Neon MythTV theme (widescreen)
ii  mythtv-theme-projectgrayhem            1:0.21.0-0ubuntu1                      The Project Grayhem MythTV theme
ii  mythtv-theme-projectgrayhem-osd        1:0.21.0-0ubuntu2                      The Project Grayhem MythTV OSD
ii  mythtv-theme-projectgrayhem-wide       1:0.21.0-0ubuntu2                      The Project Grayhem MythTV theme (widescreen)
ii  mythtv-theme-retro                     0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Retro MythTV Theme
ii  mythtv-theme-retro-osd                 0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Retro-OSD MythTV Theme
ii  mythtv-theme-titivillus                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Titivillus MythTV Theme
ii  mythtv-theme-titivillus-osd            0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Titivillus-OSD MythTV Theme
ii  mythtv-themes                          0.22.0~trunk21783-0ubuntu0~mythbuntu1  Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                 2:0.21.0+fixes-21583-openglvdpau2-nv18 Utilities used for transcoding MythTV tasks

```

---

### Post by mbobak on 2009-09-12
Did something break?  I've been running the -trunk weekly builds for the past several weeks, and today, when I tried to update, I got the following errors:
```
mjb@jupiter:~$ sudo apt-get  dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.22.0~trunk21783-0ubuntu0~mythbuntu1) but 0.22.0~trunk21739-0ubuntu0~mythbuntu1 is installed
  mythtv-database: Depends: mythtv-common (= 0.22.0~trunk21783-0ubuntu0~mythbuntu1) but 0.22.0~trunk21739-0ubuntu0~mythbuntu1 is installed
  mythtv-frontend: Depends: mythtv-common (= 0.22.0~trunk21783-0ubuntu0~mythbuntu1) but 0.22.0~trunk21739-0ubuntu0~mythbuntu1 is installed
  mythtv-transcode-utils: Depends: mythtv-common (= 0.22.0~trunk21783-0ubuntu0~mythbuntu1) but 0.22.0~trunk21739-0ubuntu0~mythbuntu1 is installed
E: Unmet dependencies. Try using -f.
mjb@jupiter:~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  mythtv-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
34 not fully installed or removed.
Need to get 0B/7286kB of archives.
After this operation, 2658kB disk space will be freed.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 151638 files and directories currently installed.)
Preparing to replace mythtv-common 0.22.0~trunk21739-0ubuntu0~mythbuntu1 (using .../mythtv-common_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb) ...
Unpacking replacement mythtv-common ...
dpkg: error processing /var/cache/apt/archives/mythtv-common_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/MythCenter-wide/title/title_dvd.png', which is also in package mythtv-theme-mythcenter-wide
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-common_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone have an idea what's going on here?

-Mark

---

### Post by mbobak on 2009-09-12
So, I opened a bug on the dependency problem described above.

Superm1 closed and said "This bug was fixed in the package mythtv - 0.22.0~trunk21785-0ubuntu2".

Ok.....except, even after doing 'apt-get update', doing 'apt-get dist-upgrade' does not try to install 21785.  I seem to be stuck on 21783.  So, how do I get the latest package w/ the fix in it?

Thanks,

-Mark

---

### Post by superm1 on 2009-09-12
> **mbobak said:**
> So, I opened a bug on the dependency problem described above.

Superm1 closed and said "This bug was fixed in the package mythtv - 0.22.0~trunk21785-0ubuntu2".

Ok.....except, even after doing 'apt-get update', doing 'apt-get dist-upgrade' does not try to install 21785.  I seem to be stuck on 21783.  So, how do I get the latest package w/ the fix in it?

Thanks,

-Mark
Hi Mark:

That's on the karmic archive, you'll see new (automatic) builds for it on intrepid and jaunty tomorrow.

---

### Post by superm1 on 2009-09-12
> **RTucker said:**
> Ok, so I just tried to upgrade again and still don't have trunk...

during the upgrade I could see it downloading packages marked 0.22, and a bunch of lines such as:

```
Preparing to replace mythtv-themes 0.21.0+trunk21261-0ubuntu0+mythbuntu3 (using .../mythtv-themes_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb) ...
```but there were also lines referencing 0.21, like:

```
Preparing to replace mythvideo 2:0.21.0+fixes-svn20752-jya-0ubuntu0 (using .../mythvideo_2%3a0.21.0+fixes-svn21591-jya-0ubuntu0_i386.deb) ...
```after a reboot apt-get shows no updates are available, but dpkg -l mythtv shows:

```
mythtv                                 2:0.21.0+fixes-21583-openglvdpau2-nv18
```I've gone through ```
sudo dpkg-reconfigure mythbuntu-repos
``` again, and its definitely set to trunk...

Sorry about the slow response, but this system is "in production" during the week, so I can only do major tinkering on the weekends :)

EDIT: Here is the full list...
```

||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  mythtv                                 2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (client and server)
ii  mythtv-backend                         2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (server)
ii  mythtv-backend-master                  2:0.21.0+fixes-21583-openglvdpau2-nv18 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                          2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (common data)
ii  mythtv-database                        2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (database)
un  mythtv-doc                             <none>                                 (no description available)
ii  mythtv-frontend                        2:0.21.0+fixes-21583-openglvdpau2-nv18 A personal video recorder application (client)
ii  mythtv-status                          0.7.3-2ubuntu2                         Show the status of a MythTV backend
ii  mythtv-theme-blootube                  1:0.21.0-0ubuntu1                      The Blootube MythTV theme
ii  mythtv-theme-blootube-osd              1:0.21.0-0ubuntu2                      The Blootube MythTV OSD
ii  mythtv-theme-blootube-wide             1:0.21.0-0ubuntu1                      The Blootube MythTV theme (widescreen)
ii  mythtv-theme-blootubelite-wide         1:0.21.0-0ubuntu1                      The Blootube Lite MythTV theme (widescreen)
ii  mythtv-theme-glass-wide                0.20080908-0ubuntu2                    The Glass MythTV theme (widescreen)
ii  mythtv-theme-gray-osd                  0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Gray-OSD MythTV Theme
ii  mythtv-theme-isthmus                   0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Isthmus MythTV Theme
ii  mythtv-theme-iulius                    0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Iulius MythTV Theme
ii  mythtv-theme-iulius-osd                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Iulius-OSD MythTV Theme
ii  mythtv-theme-metallurgy-osd            1.0-0ubuntu1                           The Metallurgy MythTV OSD theme
ii  mythtv-theme-metallurgy-wide           1.0-0ubuntu1                           The Metallurgy MythTV theme (widescreen)
ii  mythtv-theme-minimalist-wide           0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Minimalist Wide MythTV Theme
ii  mythtv-theme-mythbuntu                 0.20080421                             default MythTV theme used in Mythbuntu
ii  mythtv-theme-mythcenter                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The MythCenter MythTV Theme
ii  mythtv-theme-mythcenter-wide           0.22.0~trunk21783-0ubuntu0~mythbuntu1  The MythCenter Wide MythTV Theme
ii  mythtv-theme-neon-wide                 1:0.21.0-0ubuntu4                      The Neon MythTV theme (widescreen)
ii  mythtv-theme-projectgrayhem            1:0.21.0-0ubuntu1                      The Project Grayhem MythTV theme
ii  mythtv-theme-projectgrayhem-osd        1:0.21.0-0ubuntu2                      The Project Grayhem MythTV OSD
ii  mythtv-theme-projectgrayhem-wide       1:0.21.0-0ubuntu2                      The Project Grayhem MythTV theme (widescreen)
ii  mythtv-theme-retro                     0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Retro MythTV Theme
ii  mythtv-theme-retro-osd                 0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Retro-OSD MythTV Theme
ii  mythtv-theme-titivillus                0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Titivillus MythTV Theme
ii  mythtv-theme-titivillus-osd            0.22.0~trunk21783-0ubuntu0~mythbuntu1  The Titivillus-OSD MythTV Theme
ii  mythtv-themes                          0.22.0~trunk21783-0ubuntu0~mythbuntu1  Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                 2:0.21.0+fixes-21583-openglvdpau2-nv18 Utilities used for transcoding MythTV tasks

```
What's apt-cache policy mythtv-common look like?

My guess is that you've got some other third party repos involved that added an epoch mistakenly.  I really hope someone didn't try to go and add an epoch like that...

---

### Post by RTucker on 2009-09-12
By the looks of [http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/](http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/) there is no package for 21785 yet...

Though I guess the dependency problem might explain why mine wont go from 21583 to 21783... maybe...

---

### Post by RTucker on 2009-09-12
apt-cache policy mythtv-common says:

```

  Installed: 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0
  Candidate: 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0
  Version table:
 *** 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
        100 /var/lib/dpkg/status
     2:0.21.0+fixes-21349-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-21228-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-21211-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20918-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20787-openglvdpau2-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20769-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20752-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20722-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20674-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20667-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20651-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20635-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20607-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20607-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20600-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20573-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20555-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     0.22.0~trunk21783-0ubuntu0~mythbuntu1 0
        500 http://ppa.launchpad.net jaunty/main Packages
     0.21.0+fixes19961-0ubuntu8 0
        500 http://archive.ubuntu.com jaunty/multiverse Packages
```

Aside from mythbuntu-repos I have the standard:
```

# deb cdrom:[Mythbuntu 8.04 i386]/ hardy main restricted universe
deb http://archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
# deb http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu jaunty main # disabled on upgrade to jaunty
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
# deb-src http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu jaunty main # disabled on upgrade to jaunty

# deb http://packages.medibuntu.org/ hardy free non-free
deb http://packages.medibuntu.org/ jaunty free non-free

```

plus the 3rd party:
```

deb http://www.avenard.org/files/ubuntu-repos jaunty release

```

---

### Post by mbobak on 2009-09-12
> **superm1 said:**
> Hi Mark:

That's on the karmic archive, you'll see new (automatic) builds for it on intrepid and jaunty tomorrow.

Ah, ok, thanks Mario.

-Mark

---

### Post by superm1 on 2009-09-12
> **RTucker said:**
> apt-cache policy mythtv-common says:

```

  Installed: 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0
  Candidate: 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0
  Version table:
 *** 2:0.21.0+fixes-21583-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
        100 /var/lib/dpkg/status
     2:0.21.0+fixes-21349-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-21228-openglvdpau2-nv180-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-21211-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20918-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20787-openglvdpau2-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20769-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     2:0.21.0+fixes-20752-openglvdpau2-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20722-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20674-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20667-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20651-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20635-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20607-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20607-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20600-openglvdpau-0ubuntu3 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20573-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     1:0.21.0+fixes-20555-openglvdpau-0ubuntu0 0
        500 http://www.avenard.org jaunty/release Packages
     0.22.0~trunk21783-0ubuntu0~mythbuntu1 0
        500 http://ppa.launchpad.net jaunty/main Packages
     0.21.0+fixes19961-0ubuntu8 0
        500 http://archive.ubuntu.com jaunty/multiverse Packages
```Aside from mythbuntu-repos I have the standard:
```

# deb cdrom:[Mythbuntu 8.04 i386]/ hardy main restricted universe
deb http://archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
# deb http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu jaunty main # disabled on upgrade to jaunty
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
# deb-src http://ppa.launchpad.net/mythbuntu-testing/ppa/ubuntu jaunty main # disabled on upgrade to jaunty

# deb http://packages.medibuntu.org/ hardy free non-free
deb http://packages.medibuntu.org/ jaunty free non-free

```plus the 3rd party:
```

deb http://www.avenard.org/files/ubuntu-repos jaunty release

```
Well it looks like avenard messed up on his third party repo and introduced an epoch.  You'll have to use synaptic and the setting to pick a specific version (ctrl-e) to get the right packages.

---

### Post by RTucker on 2009-09-12
Ok, so what do I force to 0.22? Is it just the mythtv package, or do I have to go through all the installed packages and change each one?

I just forced mythtv-frontend to 0.22 and synaptic wants to uninstall basically all other mythtv related packages as a result, is that normal? Should I let it?

...there seems to be all kinds of dependency issues going on, including qt, I think I'll wait for 21785 tomorrow and go from there instead...

---

### Post by RTucker on 2009-09-12
So 21818 is now avaliable, but I still have dependency issues and upgrading certain packages to 0.22 still makes synaptic want to remove basically all of mythtv (which may be related)...

I think I've traced it back to libqt4-webkit not installing because:
```

libqt4-webkit:
  Depends: libqt4-network (=4.5.0-0ubuntu4.1) but 4.5.0-0ubuntu4.2 is to be installed
  Depends: libqtcore4 (=4.5.0-0ubuntu4.1) but 4.5.0-0ubuntu4.2 is to be installed
  Depends: libqtgui4 (=4.5.0-0ubuntu4.1) but 4.5.0-0ubuntu4.2 is to be installed

```

and libqt4-opengl because:
```

libqt4-opengl:
  Depends: libqtcore4 (=4.5.0-0ubuntu4.1) but 4.5.0-0ubuntu4.2 is to be installed
  Depends: libqtgui4 (=4.5.0-0ubuntu4.1) but 4.5.0-0ubuntu4.2 is to be installed

```

Strangely all the libqt4 packages which are installed are version 4.5.0-0ubuntu4.2, but the packages I don't have installed say the latest version is 4.5.0-0ubuntu4.1.

---

### Post by jwbrown77 on 2009-09-13
Anyone seen this using mythvideo after upgrading to 0.22?

2009-09-12 23:38:04.855 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-09-12 23:38:05.845 Loading window theme from /usr/share/mythtv/themes/Graphite/video-ui.xml
2009-09-12 23:38:05.848 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythtv/var/lib/mythtv/videos/)
2009-09-12 23:38:05.903 New DB connection, total: 2
2009-09-12 23:38:05.903 Connected to database 'mythconverg' at host: localhost
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv.
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv


Exiting... (End of file)

------

Trying to run the command manually from a terminal works fine:

mplayer-vdpau /var/lib/mythtv/videos/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv

It seems like it's trying to stream over a localhost socket instead of playing the file directly off the filesystem?  I couldn't find a setting to change this behavior.

---

### Post by kmitche on 2009-09-13
> **jwbrown77 said:**
> Anyone seen this using mythvideo after upgrading to 0.22?

2009-09-12 23:38:04.855 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-09-12 23:38:05.845 Loading window theme from /usr/share/mythtv/themes/Graphite/video-ui.xml
2009-09-12 23:38:05.848 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythtv/var/lib/mythtv/videos/)
2009-09-12 23:38:05.903 New DB connection, total: 2
2009-09-12 23:38:05.903 Connected to database 'mythconverg' at host: localhost
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv.
No stream found to handle url myth://Videos@127.0.0.1:6543/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv


Exiting... (End of file)

------

Trying to run the command manually from a terminal works fine:

mplayer-vdpau /var/lib/mythtv/videos/Movies/Alien (1979) (Director's Cut)/Alien (1979).mkv

It seems like it's trying to stream over a localhost socket instead of playing the file directly off the filesystem?  I couldn't find a setting to change this behavior.

I finally got it working Friday, after playing with it for several days. As soon as I got the directories set correctly it works. I can even get a Mac frontend to connect. This is the guide I followed. Rereading it carefully helped! 

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

---

### Post by jwbrown77 on 2009-09-13
Changing the storage group path to another directory seems to have fixed it.  Thanks for the tip.

---

### Post by whistlerxj on 2009-09-14
Hi 
I would like to know what I can do to manually upgrade my database schema.

I turned on mythbuntu-repos -trunk. 
ran apt-get update / dist-upgrade

then:
mythtv-setup gives me a warning that it couldn't back up my database and that it wants to upgrade the schema from 1215 to 1244

I get an error in dpkg-reconfigure mysql-server-5.0:
error 126 - incorrect key file for table /tmp/#sql<random#>.MYI; try to repair it.

So, since that file only exists while the dpkg is running I don't know what to do.

---

### Post by Nikas on 2009-09-14
> **whistlerxj said:**
> Hi 
I would like to know what I can do to manually upgrade my database schema.

I turned on mythbuntu-repos -trunk. 
ran apt-get update / dist-upgrade

then:
mythtv-setup gives me a warning that it couldn't back up my database and that it wants to upgrade the schema from 1215 to 1244

I get an error in dpkg-reconfigure mysql-server-5.0:
error 126 - incorrect key file for table /tmp/#sql<random#>.MYI; try to repair it.

So, since that file only exists while the dpkg is running I don't know what to do.

Try:
```
mysqlcheck -Arao -u mythtv -pyour_db_password
```
NO space between -p and your db-password. :-)
You can find the password in /etc/mythtv/mysql.txt

---

### Post by movieman on 2009-09-25
Is something up with the mythbuntu server? For the last few days the update-manager has been complaining that it can't download from weeklybuilds.mythbuntu.org.

---

### Post by kilowhisky on 2009-09-25
> **movieman said:**
> Is something up with the mythbuntu server? For the last few days the update-manager has been complaining that it can't download from weeklybuilds.mythbuntu.org.

Yea its been broke for me for quite a few days. Just switched to the PPA server and it seems to not give the error but its not showing any updates either. There should be a new weekly fix because i haven't updated in over a week.

---

### Post by discoverpc on 2009-09-26
Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/Release.gpg](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/Release.gpg)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

W: Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

still down ?
do we have an ETA for the server to be back online?

---

### Post by mitchell2345 on 2009-09-27
> **discoverpc said:**
> Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/Release.gpg](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/Release.gpg)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

W: Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to weeklybuilds.mythbuntu.org:80 (130.133.35.11). - connect (111 Connection refused)

still down ?
do we have an ETA for the server to be back online?

I see the exact same thing.  I changed from US to UK by running sudo dpkg-reconfigure mythbuntu-repos and these servers are up.

Mitchell

---

### Post by discoverpc on 2009-09-27
i just updated the /etc/apt/sourcelist.d/mythbu$ to the uk and it does work.

so it looks like the us server is down then.

---

### Post by mbobak on 2009-09-28
So, question:

When Myth 0.22 is released, what will be the migration path to switch off the weekly builds and onto the standard Ubuntu Myth repo?  Will these two sync up, in terms of the versions they provide, at least for a time?  That would allow for a smooth transition.....

Anticipating 0.22 and Ubuntu 9.10.....

-Mark

---

### Post by tgm4883 on 2009-09-28
> **mbobak said:**
> So, question:

When Myth 0.22 is released, what will be the migration path to switch off the weekly builds and onto the standard Ubuntu Myth repo?  Will these two sync up, in terms of the versions they provide, at least for a time?  That would allow for a smooth transition.....

Anticipating 0.22 and Ubuntu 9.10.....

-Mark

The trunk-022 PPA will follow Mythtv 22-fixes. There will be a new PPA for trunk (called 0.23).

MythTV 0.22 will not be backported to 9.04 or previous. There will be no automatic switch back to the standard repos.

---

### Post by RTucker on 2009-10-01
superm, tgm, any ideas re my posts here [http://ubuntuforums.org/showpost.php?p=7937925&postcount=131](http://ubuntuforums.org/showpost.php?p=7937925&postcount=131)?

---

### Post by tgm4883 on 2009-10-01
> **RTucker said:**
> superm, tgm, any ideas re my posts here [http://ubuntuforums.org/showpost.php?p=7937925&postcount=131](http://ubuntuforums.org/showpost.php?p=7937925&postcount=131)?

You should just be able to add the trunk repo from mythbuntu-repos and then apt-get update then apt-get upgrade

---

### Post by RTucker on 2009-10-02
I know what *should* happen :P

The trouble is, as superm1 helped me figure out, a third party repo has introduced an epoch on my mythtv packages. As suggested I went in to synaptic and used 'Ctrl-e' to force the packages to the 0.22 in the mythbuntu weekly repos, but when I do this I have the problem I mentioned in the posts I linked to.

---

### Post by tgm4883 on 2009-10-02
> **RTucker said:**
> I know what *should* happen :P

The trouble is, as superm1 helped me figure out, a third party repo has introduced an epoch on my mythtv packages. As suggested I went in to synaptic and used 'Ctrl-e' to force the packages to the 0.22 in the mythbuntu weekly repos, but when I do this I have the problem I mentioned in the posts I linked to.

Ah thats right. hmm. yea you may want to force all the mythtv packages to 0.22 and see what happens. Disable that other repo though.

---

### Post by theSeekerr on 2009-10-04
Hi,

I just upgraded to 0.22-trunk on my Jaunty installation, and as far as that box is concerned, everything works fine.

However, the reported protocol version is 50, while every other available 0.22 frontend (including a fresh compile from SVN) expects version 48.

What's going on?

---

### Post by tgm4883 on 2009-10-04
> **theSeekerr said:**
> Hi,

I just upgraded to 0.22-trunk on my Jaunty installation, and as far as that box is concerned, everything works fine.

However, the reported protocol version is 50, while every other available 0.22 frontend (including a fresh compile from SVN) expects version 48.

What's going on?

Thats odd. What is the output of dpkg -l mythtv* on that box and your other boxes.

---

### Post by theSeekerr on 2009-10-04
My Jaunty box is running trunk 22179. Weirdly, a fresh build from SVN is reporting 21995, so there's my problem.

---

### Post by Nikas on 2009-10-10
I want to change to trunk.

I need to run apt-get dist-upgrade to get "mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-transcode-utils openbox".

apt-get upgrade will only give me:
"libmyth-perl libmyth-python mythtv-doc mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius mythtv-theme-iulius-osd
  mythtv-theme-minimalist-wide mythtv-theme-mythcenter mythtv-theme-mythcenter-wide mythtv-theme-retro mythtv-theme-retro-osd mythtv-theme-titivillus
  mythtv-theme-titivillus-osd mythtv-themes mythweb nvidia-180-modaliases"

Should i go with upgrade first and then dist-upgrade or should i do dist-upgrade only?

---

### Post by tgm4883 on 2009-10-10
> **Nikas said:**
> I want to change to trunk.

I need to run apt-get dist-upgrade to get "mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-transcode-utils openbox".

apt-get upgrade will only give me:
"libmyth-perl libmyth-python mythtv-doc mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius mythtv-theme-iulius-osd
  mythtv-theme-minimalist-wide mythtv-theme-mythcenter mythtv-theme-mythcenter-wide mythtv-theme-retro mythtv-theme-retro-osd mythtv-theme-titivillus
  mythtv-theme-titivillus-osd mythtv-themes mythweb nvidia-180-modaliases"

Should i go with upgrade first and then dist-upgrade or should i do dist-upgrade only?

Odd, did you do an apt-get update

---

### Post by Nikas on 2009-10-10
> **tgm4883 said:**
> Odd, did you do an apt-get update

Yes.
I have installed the updates but mythtv are unable to upgrade my database... so i cant use .22.

Its discussed here:
[http://www.gossamer-threads.com/lists/mythtv/users/399413](http://www.gossamer-threads.com/lists/mythtv/users/399413)

I'm having problems with the "oldrecorded"-table.
I have tried all the suggestions here [http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding](http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding) without success. :-(

I dont want to loose oldrecorded. 9000 recordings.

---

### Post by mythding on 2009-10-15
I am getting a "could not download all repository indexes" message for the weekly trunk-0.22 update. I am on 9.04 and I have been running trunk for a couple of months now and upgrading weekly went fine. Is this permanent or temporary? I did notice the the mythtv devs have started a 0.22-fixes branch. Does this have anything to do with it?  Can I do something to fix it or should I just sit and wait for things to get sorted out?

Edit: These are the US weekly builds.
Edit 2: When I switch to the ppa builds I get "Partial Upgrade" Warning and won't let me upgrade "mythtv, mythtv-backend, mythtv-common, mythtv-database, mythtv-frontend, mythtv-transcode-utils"

---

### Post by tgm4883 on 2009-10-15
> **mythding said:**
> I am getting a "could not download all repository indexes" message for the weekly trunk-0.22 update. I am on 9.04 and I have been running trunk for a couple of months now and upgrading weekly went fine. Is this permanent or temporary? I did notice the the mythtv devs have started a 0.22-fixes branch. Does this have anything to do with it?  Can I do something to fix it or should I just sit and wait for things to get sorted out?

Edit: These are the US weekly builds.
Edit 2: When I switch to the ppa builds I get "Partial Upgrade" Warning and won't let me upgrade "mythtv, mythtv-backend, mythtv-common, mythtv-database, mythtv-frontend, mythtv-transcode-utils"

Don't use the US repo for now. Use either the PPA or UK. The partial upgrade warning might be because things are currently building. So try back later.

:EDIT:

Check here [https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22](https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22)

As long as all the version numbers match there it should be fine. Myththemes shouldn't matter.

---

### Post by mythding on 2009-10-15
I've been trying since last night. Just tried right now with the same issue. It looks like they built just fine at the PPA about 18 hours ago. I am currently running version 22240 of both front and backends.

Thank you.

---

### Post by tgm4883 on 2009-10-15
Odd, why won't it let you upgrade?

---

### Post by mythding on 2009-10-15
Got tired of it and used Synaptic instead of update manager and that got the job done. Hopefully that did not screw anything up.

---

### Post by Dubstar_04 on 2009-11-03
Any news on the 0.22 rc2 build?

---

### Post by pootle1 on 2009-11-04
I've just added [http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu](http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu) as part of a new karmic build, but when I try and install a mythbackend it fails as the version of 

mythtv-backend is fixes22722

but the version of mythtv-common is fixes22705

and it throws a wobbly.

Am I missing another repo or something?

I've tried against the UK servers and the master servers - they are the same.

---

### Post by joshoekstra on 2009-11-04
Na, common is last to come in, as far as I know the mythbuntu guys use the PPA-buildservice and I suspect it being slow because of the last release....

---

### Post by novellahub on 2009-11-13
> **tgm4883 said:**
> Don't use the US repo for now. Use either the PPA or UK. The partial upgrade warning might be because things are currently building. So try back later.

:EDIT:

Check here [https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22](https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22)

As long as all the version numbers match there it should be fine. Myththemes shouldn't matter.

I am getting the partial upgrade message currently using the PPA or US repositories. 

0.22.0+fixes22722-0ubuntu0+mythbuntu3
0.22.0+fixes22814-0ubuntu0+mythbuntu3

Is there a issue with the last build?

---

### Post by tgm4883 on 2009-11-13
> **novellahub said:**
> I am getting the partial upgrade message currently using the PPA or US repositories. 

0.22.0+fixes22722-0ubuntu0+mythbuntu3
0.22.0+fixes22814-0ubuntu0+mythbuntu3

Is there a issue with the last build?

It looks like everything built correctly about 4 hours ago. You can check the builds on the PPA here [https://launchpad.net/~mythbuntu/+archive/trunk-0.22](https://launchpad.net/~mythbuntu/+archive/trunk-0.22)

Have you done an apt-get update recently?

---

### Post by Neon Dusk on 2009-11-14
It looks like the packaging of the nvidia driver has changed which will cause the partial upgrade message.

See post from jyavenard [post=8316310]here[/post] for the correct upgrade order.

---

### Post by novellahub on 2009-11-15
> **Neon Dusk said:**
> It looks like the packaging of the nvidia driver has changed which will cause the partial upgrade message.

See post from jyavenard [post=8316310]here[/post] for the correct upgrade order.

Thank you!  I got past the partial upgrade error message by running this first:

```

sudo apt-get install libvdpau1

```

Then I was able to run the update manager successfully  without any messages.

---

### Post by rodercot on 2009-11-19
Hey all,

 I am using the US autobuilds repo and all my machines are 8.10 with version .22 I just updated to 22589 I believe.

 All my machines are keeping the mythtv-themes held back. Is there a reason or is it because the themes that are working are being updated individually. 

 Can some point me to a post or info on which directory and files I need to keep theme info in that I have customized so it does not get upgraded overwritten with the weekly builds.
 
 thanks,

 Dave

---

### Post by kilowhisky on 2009-12-07
I looked through this thread but i still didn't find an answer. Is there a fix for the partial upgrade problem yet?  I've had it for months and I'm almost afraid to do an update because it could break my whole machine.

---

### Post by novellahub on 2009-12-07
> **kilowhisky said:**
> I looked through this thread but i still didn't find an answer. Is there a fix for the partial upgrade problem yet?  I've had it for months and I'm almost afraid to do an update because it could break my whole machine.

See post 166 above.

---

### Post by kilowhisky on 2009-12-07
> **novellahub said:**
> See post 166 above.

That is not my issue. I have an error with the nvidia 190 libdvpau and it keeps saying that mythtv packages are being held back.

---

### Post by tgm4883 on 2009-12-08
> **kilowhisky said:**
> That is not my issue. I have an error with the nvidia 190 libdvpau and it keeps saying that mythtv packages are being held back.

Do an apt-get -s dist-upgrade, then post the output here.

---

### Post by Neon Dusk on 2009-12-31
I've been using the auto-builds and nvidia-graphics-drivers-190 (190.42) successfully for a number of months. 

However it looks like the nvidia drivers have now been updated to 190.53 and when I try an update I get the error 'nvidia-glx-190: Depends: libvdapu but it is not installable'

---

### Post by Neon Dusk on 2009-12-31
Today's build of nvidia-graphics-drivers-190 has fixed the issue.

Thanks.

---

### Post by novellahub on 2010-01-01
I am getting the partial upgrade error again in the update manager.  Here is the output of sudo apt-get -s dist-upgrade below.  Any ideas?  I am using the PPA non testing mythbuntu repo.

```

novellahub@mythtvmaster:~/Desktop$ sudo apt-get -s dist-upgrade
[sudo] password for novellahub: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libmyth-perl
The following NEW packages will be installed:
  libmythtv-perl
The following packages will be upgraded:
  apparmor apparmor-utils apport apport-gtk firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support gstreamer0.10-alsa
  gstreamer0.10-plugins-base gtk2-engines-pixbuf jockey-common jockey-gtk
  libapparmor-perl libapparmor1 libgail-common libgail18 libglib2.0-0
  libglib2.0-data libgstreamer-plugins-base0.10-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libmyth-0.22-0 libmyth-python libpython2.6 libvdpau1
  mytharchive mytharchive-data mythgallery mythmovies mythmusic mythtv
  mythtv-backend mythtv-backend-master mythtv-common mythtv-database
  mythtv-frontend mythtv-theme-blootube-osd mythtv-theme-blueosd
  mythtv-theme-graphite mythtv-theme-iulius-osd mythtv-theme-metallurgy
  mythtv-theme-mono-osd mythtv-theme-mythbuntu mythtv-theme-projectgrayhem-osd
  mythtv-theme-retro-osd mythtv-theme-titivillus-osd mythtv-themes
  mythtv-transcode-utils mythvideo mythweather mythweb python-apport
  python-problem-report python2.6 python2.6-minimal rsyslog upstart
  xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
61 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Inst mythtv-common [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst libvdpau1 [0.2-0ubuntu1~ppa2] (0.3-2~ppa1 0.22:9.10/karmic)
Inst libmyth-0.22-0 [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-transcode-utils [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-backend [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic) []
Remv libmyth-perl [0.22.0+fixes22957-0ubuntu0+mythbuntu3] []
Inst libmythtv-perl (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst upstart [0.6.3-10] (0.6.3-11 Ubuntu:9.10/karmic-updates)
Conf upstart (0.6.3-11 Ubuntu:9.10/karmic-updates)
Inst mythtv-database [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-frontend [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-backend-master [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst libpython2.6 [2.6.4-0ubuntu2] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst python2.6 [2.6.4-0ubuntu2] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst python2.6-minimal [2.6.4-0ubuntu2] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf python2.6-minimal (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst libglib2.0-0 [2.22.2-0ubuntu1] (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libglib2.0-data [2.22.2-0ubuntu1] (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst rsyslog [4.2.0-2ubuntu5] (4.2.0-2ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst apparmor [2.3.1+1403-0ubuntu27.2] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst libapparmor1 [2.3.1+1403-0ubuntu27.2] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst libapparmor-perl [2.3.1+1403-0ubuntu27.2] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst apparmor-utils [2.3.1+1403-0ubuntu27.2] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst python-problem-report [1.9.3-0ubuntu4.1] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst python-apport [1.9.3-0ubuntu4.1] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst apport [1.9.3-0ubuntu4.1] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst apport-gtk [1.9.3-0ubuntu4.1] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst firefox-3.5-branding [3.5.5+nobinonly-0ubuntu0.9.10.1] (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates) []
Inst libgail-common [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst libgail18 [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst libgtk2.0-common [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst gtk2-engines-pixbuf [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst libgtk2.0-0 [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst xulrunner-1.9.1-gnome-support [1.9.1.5+nobinonly-0ubuntu0.9.10.1] (1.9.1.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates) []
Inst xulrunner-1.9.1 [1.9.1.5+nobinonly-0ubuntu0.9.10.1] (1.9.1.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates) []
Inst firefox-3.5-gnome-support [3.5.5+nobinonly-0ubuntu0.9.10.1] (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates) []
Inst firefox-3.5 [3.5.5+nobinonly-0ubuntu0.9.10.1] (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Inst firefox [3.5.5+nobinonly-0ubuntu0.9.10.1] (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Inst libgstreamer-plugins-base0.10-0 [0.10.25-2ubuntu1.1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-alsa [0.10.25-2ubuntu1.1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-plugins-base [0.10.25-2ubuntu1.1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst jockey-gtk [0.5.5-0ubuntu2] (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst jockey-common [0.5.5-0ubuntu2] (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst libgtk2.0-bin [2.18.3-1ubuntu2] (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst libmyth-python [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mytharchive-data [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mytharchive [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythgallery [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythmovies [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythmusic [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-blootube-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-blueosd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-graphite [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-iulius-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-metallurgy [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-mono-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-mythbuntu [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-projectgrayhem-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-retro-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-theme-titivillus-osd [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythtv-themes [1:0.22.0+fixes22957-0ubuntu0+mythbuntu3] (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythvideo [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythweather [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Inst mythweb [0.22.0+fixes22957-0ubuntu0+mythbuntu3] (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-common (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf libvdpau1 (0.3-2~ppa1 0.22:9.10/karmic)
Conf libmyth-0.22-0 (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-transcode-utils (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf libmythtv-perl (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-backend (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-database (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-frontend (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-backend-master (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf python2.6 (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libpython2.6 (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libglib2.0-0 (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libglib2.0-data (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf rsyslog (4.2.0-2ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf apparmor (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf libapparmor1 (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf libapparmor-perl (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf apparmor-utils (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf python-problem-report (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf python-apport (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf apport (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf apport-gtk (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-common (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-0 (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf xulrunner-1.9.1 (1.9.1.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf firefox-3.5 (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf firefox-3.5-branding (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf libgail18 (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libgail-common (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf gtk2-engines-pixbuf (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf xulrunner-1.9.1-gnome-support (1.9.1.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf firefox-3.5-gnome-support (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf firefox (3.5.6+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf libgstreamer-plugins-base0.10-0 (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-alsa (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-plugins-base (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf jockey-common (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf jockey-gtk (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-bin (2.18.3-1ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libmyth-python (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mytharchive-data (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mytharchive (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythgallery (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythmovies (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythmusic (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-blootube-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-blueosd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-graphite (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-iulius-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-metallurgy (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-mono-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-mythbuntu (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-projectgrayhem-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-retro-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-theme-titivillus-osd (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythtv-themes (1:0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythvideo (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythweather (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)
Conf mythweb (0.22.0+fixes23034-0ubuntu0+mythbuntu3 0.22:9.10/karmic)

```

---

### Post by tgm4883 on 2010-01-01
Looks to me as if a package got renamed 

> The following packages will be REMOVED:
  libmyth-perl
The following NEW packages will be installed:
  libmythtv-perl

---

### Post by novellahub on 2010-01-02
> **tgm4883 said:**
> Looks to me as if a package got renamed

Do I need to manually remove libmyth-perl first before I do the next update?

Here is a reference of the change:

[http://bazaar.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes/revision/236](http://bazaar.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes/revision/236)

---

### Post by tgm4883 on 2010-01-02
> **novellahub said:**
> Do I need to manually remove libmyth-perl first before I do the next update?

Here is a reference of the change:

[http://bazaar.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes/revision/236](http://bazaar.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes/revision/236)

No. This is where a better understanding of upgrades/dist-upgrades and apt-get come in handy. "apt-get upgrade" will upgrade the packages you have installed, but not install any new required packages (so if a packages has a new dependency that you don't have installed, it gets held back). "apt-get dist-upgrade" will upgrade your packages and install/remove anything that needs to be done in order to upgrade your packages. This can be bad in some instances as if not all of the dependencies can be met, then  it will remove those packages and any package that depends on them. This is where -s comes in. Adding a -s after apt-get will run it in simulation mode. Where it will show you what is happening without making any changes to your computer. So what you need to do is run "apt-get -s dist-upgrade" and make sure it isn't going to do anything you don't want it to do (like removing all your packages). Once you verify that is fine, do "apt-get dist-upgrade" to actually do it this time.

---

### Post by Archmage on 2010-01-23
I'm using this repro:

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list 
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu karmic main
deb http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu karmic main
```

And after the today update I'm unable to search for TV-Shows in Mythvideo. Is there a way to fix this? Yesterday it was working flawless.

---

### Post by russell5 on 2010-03-09
I updated to the weekly builds. and am having two issues

Mythweb playing recordings via flash doesnt seems to work for me. 
Any shows recorded before i upgraded to weekly builds still work. But any shows recorded after upgrade gives this error. 
303: failed to load a resource failed to load esources error #2124

anyone else having this issue?

My other issue is nuvexport. 

It wont install from apt-get because 
nuvexport: Depends: libmyth-perl but it is not going to be installed

I know its now called libmythtv-perl but how can i get nuvexport installed.

---

### Post by Archmage on 2010-04-10
> **Archmage said:**
> And after the today update I'm unable to search for TV-Shows in Mythvideo. Is there a way to fix this? Yesterday it was working flawless.

Sorry for the late reply - I did forget this completely.

It seems it was just a hiccup - it works flawless later.

---

### Post by dannyboy79 on 2010-04-23
i would like to point out that I am running lucid (all up to date as of this morning) and when I run the sudo dpkg-reconfigure mythbuntu-repos command, the debconf screen that appears has 2 of the same .23 choices. which one is trunk and which one is more stable? Heres a pic also,

[[IMG]http://img144.imageshack.us/img144/3020/screenshotqqt.png[/IMG]](http://img144.imageshack.us/i/screenshotqqt.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

sorry for posting full size pic but I never know which option to use from imageshack. I tried direct link but when I used ubuntuforums attach imae option, it actually doesn't work (for me anyways) so if anyone can enlighten me as to how to only paste a link to the pic I will not post the full pic next time

---

### Post by tgm4883 on 2010-04-23
> **dannyboy79 said:**
> i would like to point out that I am running lucid (all up to date as of this morning) and when I run the sudo dpkg-reconfigure mythbuntu-repos command, the debconf screen that appears has 2 of the same .23 choices. which one is trunk and which one is more stable? Heres a pic also,

[[IMG]http://img144.imageshack.us/img144/3020/screenshotqqt.png[/IMG]](http://img144.imageshack.us/i/screenshotqqt.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

sorry for posting full size pic but I never know which option to use from imageshack. I tried direct link but when I used ubuntuforums attach imae option, it actually doesn't work (for me anyways) so if anyone can enlighten me as to how to only paste a link to the pic I will not post the full pic next time

It's the same. Pick either

---

### Post by Archmage on 2010-07-19
10.04 - I notice two problems. Myth-Repro will give me two syntax errors and one illegal character. And Mythvideo seems to stop working since the latest update. (If you press Enter/Confirm in your Mythfrontend to go into Mythvideo nothing will happening.)

---

### Post by tgm4883 on 2010-07-19
What syntax errors? I don't see any and can't confirm unless you tell me what is happening, and what version of mythbuntu-repos you have

---

### Post by Archmage on 2010-07-19
With the latest update Mythvideo is again working. I'll look later into the problem with the myth-repro.

---

### Post by Archmage on 2010-07-20
> **tgm4883 said:**
> What syntax errors? I don't see any and can't confirm unless you tell me what is happening, and what version of mythbuntu-repos you have

[http://ppa.launchpad.net/mythbuntu/repos/ubuntu/](http://ppa.launchpad.net/mythbuntu/repos/ubuntu/) lucid/main mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100720002540

(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |

deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main

Kindly tell me, if you need any additional information.

---

### Post by tgm4883 on 2010-07-20
> **Archmage said:**
> [http://ppa.launchpad.net/mythbuntu/repos/ubuntu/](http://ppa.launchpad.net/mythbuntu/repos/ubuntu/) lucid/main mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100720002540

(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |

deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main

Kindly tell me, if you need any additional information.

Yea, what are you doing to reproduce those errors?

---

### Post by Archmage on 2010-07-20
Each time I'm installing a new version of myth-repro I got the following message:

```
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
```

---

### Post by tgm4883 on 2010-07-20
> **Archmage said:**
> Each time I'm installing a new version of myth-repro I got the following message:

```
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
```

Ah ok, so it's just when you install a new version of mythbuntu-repos, not when you are getting a new version of mythtv, and not when you are reconfiguring the mythbuntu-repos package.

---

### Post by tgm4883 on 2010-07-20
Odd, I am completely unable to reproduce the issue. Try this


```
apt-get purge mythbuntu-repos
```

Then try reinstalling mythbuntu-repos

---

### Post by Archmage on 2010-07-20
I guess this screwed up even more. :(

```
sudo dpkg-reconfigure mythbuntu-repos 
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
OK
OK
```

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

---

### Post by tgm4883 on 2010-07-20
> **Archmage said:**
> I guess this screwed up even more. :(

```
sudo dpkg-reconfigure mythbuntu-repos 
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
OK
OK
```

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

Wow, that is really weird. You purged mythbuntu-repos before reinstalling?

---

### Post by Archmage on 2010-07-20
> **tgm4883 said:**
> Wow, that is really weird. You purged mythbuntu-repos before reinstalling?

Yes, I did. After purging I even can't install mythbuntu-repos via apt-get, because they are complete away. I have to go to [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu) to install it again.

There is a new version out there. After a "sudo aptitude -r safe-upgrade"

I got the following:

```
Aktueller Status: 1 Aktualisierung [+1].
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig
Die folgenden Pakete werden aktualisiert:
  mythbuntu-repos 
1 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
Muss 10,8kB an Archiven herunterladen. Nach dem Entpacken werden 0B zusätzlich belegt sein.
Wollen Sie fortsetzen? [Y/n/?] y
Schreibe erweiterte Statusinformationen... Fertig
Hole:1 http://ppa.launchpad.net/mythbuntu/repos/ubuntu/ lucid/main mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100721002528 [10,8kB]
10,8kB wurden in 0s heruntergeladen (13,4kB/s)
Vorkonfiguration der Pakete ...
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(Lese Datenbank ... 183773 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von mythbuntu-repos 8.0-0ubuntu0+mythbuntu~auto20100720002540 (durch .../mythbuntu-repos_8.0-0ubuntu0+mythbuntu~auto20100721002528_all.deb) ...
Entpacke Ersatz für mythbuntu-repos ...
Richte mythbuntu-repos ein (8.0-0ubuntu0+mythbuntu~auto20100721002528) ...
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
OK
OK

Paketlisten werden gelesen... Fertig             
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig

Aktueller Status: 0 Aktualisierungen [-1], 8 Neue [-2].
```

And again a "cat /etc/apt/sources.list.d/mythbuntu-repos.list" is showing:

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

I'll edit it back to get it showing again the right ones.

Before I forget it - I'm using the 64-bit version.
Linux olds 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

---

### Post by tgm4883 on 2010-07-21
Very odd. I wonder if it is a language thing.


Can you add 

```
set -x
```

to the top of 

```
/var/lib/dpkg/info/mythbuntu-repos.postinst
```

Then do a dpkg-reconfigure on it again and post the output

---

### Post by tgm4883 on 2010-07-21
Can you also paste the output of

```
cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
```

And what options are you given for version numbers in mythbuntu-repos

---

### Post by Archmage on 2010-07-21
> **tgm4883 said:**
> Can you add 

```
set -x
```

to the top of 

```
/var/lib/dpkg/info/mythbuntu-repos.postinst
```

Then do a dpkg-reconfigure on it again and post the output

sudo dpkg-reconfigure mythbuntu-repos
```
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
[: 110: =: unexpected operator
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ /usr/bin/apt-key del EEED06D0
+ true
+ /usr/bin/apt-key del 1504888C
OK
+ rm /etc/apt/sources.list.d/mythbuntu-repos.list
+ lsb_release -c -s
+ release=lucid
+ cut -f 2
+ grep lucid
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ BLD1=
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ weeklyactive=true
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ mythversion=0.23.0+fixes24158-0ubuntu2 | h,
+ db_get mythbuntu-repos/repolocation
+ _db_cmd GET mythbuntu-repos/repolocation
+ IFS=  printf %s\n GET mythbuntu-repos/repolocation
+ IFS=
 read -r _db_internal_line
+ RET=US
+ return 0
+ repolocation=US
+ db_get mythbuntu-repos/testing
+ _db_cmd GET mythbuntu-repos/testing
+ IFS=  printf %s\n GET mythbuntu-repos/testing
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ testingactive=true
+ CONFIGFILE=/etc/default/mythbuntu-repos
+ [ -x /usr/bin/apt-key ]
+ /usr/bin/apt-key add /usr/share/keyrings/mythbuntu-ppa-keyring.gpg
OK
+ echo deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
+ echo [cfg]
+ version=0.23.0+fixes24158-0ubuntu2 | h,
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.21 ]
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.22 ]
+ [ US = PPA ]
+ tr “[:upper:]” “[:lower:]”
+ echo US
+ smrepolocation=us
+ [ us = de ]
+ repo=us.autobuilds.mythbuntu.org
+ [ true = true ]
+ echo activateweekly = True
+ echo weeklylocation = US
+ echo weeklyrepo = 0.23.0+fixes24158-0ubuntu2 | h,
+ echo deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ echo deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ [ true = true ]
+ echo deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo testingppa = True
+ exit 0
```


> **tgm4883 said:**
> Can you also paste the output of

```
cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
```

cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
```
MYTHTV_RELEASE	0.23
repos	DE, FR, UK, US, PPA
replacements	AU, AF, EU, AS, NA, SA
```


> **tgm4883 said:**
> And what options are you given for version numbers in mythbuntu-repos

First Page
The Auto Builds Repo will contain updated MythTV software built frequently from upstream. (such as mythtv-frontend and mythtv-backend).
Would you like to activate the Auto Builds updates?                                                                <Ja>                                             <Nein>     

Second Page
This is the location of the repository you want to use. Please choose one that is closer to you. If you don't know, please choose PPA.
Which repo would you like to use?
DE
FR
UK
US
PPA

Third Page
The testing PPA will often contain updated software or software that is not yet in the Ubuntu repos. It will not contain MythTV packages, but instead will contain software such as MythExport or new versions of Mythbuntu-Control-Centre.
Would you like to activate the testing PPA?

Fourth Page
Please use a package manager to finish updating.
To complete the transition to auto-builds, please open update-manager (or synaptic) and click Check (or Reload) and then install updates as you normally would.

And that is all.

---

### Post by tgm4883 on 2010-07-21
Ok, I see where the issue is, not sure how to fix it yet.

What language is your system in?

What is the output of the following commands

```
lsb_release -c -s

```

```

cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db | grep lucid | cut -f 2
```

```

echo $LANG

```

---

### Post by Archmage on 2010-07-22
Thanks for trying to help me. I appreciate your work.

lsb_release -c -s
```
lucid
```

cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db | grep lucid | cut -f 2
```

```
No result at all - keep in mind that the file only has this entries:
```
MYTHTV_RELEASE	0.23
repos	DE, FR, UK, US, PPA
replacements	AU, AF, EU, AS, NA, SA
```

echo $LANG
```
de_DE.UTF-8
```

---

### Post by tgm4883 on 2010-07-22
"Removed because command is not necessary"

---

### Post by tgm4883 on 2010-07-22
Hmm, apparently it's coming from higher up. You can remove set -x from sudo nano /var/lib/dpkg/info/mythbuntu-repos.postinst

Can you add 

```
set -x
LANG=C
```

to the top of

```
sudo nano /var/lib/dpkg/info/mythbuntu-repos.config
```

and then do 

```
dpkg-reconfigure mythbuntu-repos
```

Also, what is the output of 

```
apt-cache madison mythtv | grep "multiverse Packages" | sed -rne 's/1://;s/^mythtv: | *.........(.*).............-.*/\1/p'

```

---

### Post by Archmage on 2010-07-22
> **tgm4883 said:**
> ```
set -x
LANG=C
```
```
sudo nano /var/lib/dpkg/info/mythbuntu-repos.config
```
```
dpkg-reconfigure mythbuntu-repos
```

Result
```
+ LANG=C
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ db_version 2.0
+ _db_cmd VERSION 2.0
+ IFS=  printf %s\n VERSION 2.0
+ IFS=
 read -r _db_internal_line
+ RET=2.0
+ return 0
+ db_capb backup
+ _db_cmd CAPB backup
+ IFS=  printf %s\n CAPB backup
+ IFS=
 read -r _db_internal_line
+ RET=multiselect escape backup
+ return 0
+ sed -rne s/1://;s/^mythtv: | *.........(.*).............-.*/\1/p
+ grep multiverse Packages
+ apt-cache madison mythtv
+ BLD1=0.23.0+fixes24158-0ubuntu2 | h
+ awk {printf "%04s\n", $0}
+ bc
+ echo 0.23.0+fixes24158-0ubuntu2 | h + 0.01
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ BLD2=
+ cut -f 2
+ grep MYTHTV_RELEASE
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ RVER=0.23
+ db_subst mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ _db_cmd SUBST mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ _db_cmd SUBST mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ _db_cmd SUBST mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=  printf %s\n SUBST mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/mythversion RVERSION 0.23
+ _db_cmd SUBST mythbuntu-repos/mythversion RVERSION 0.23
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion RVERSION 0.23
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_fset mythbuntu-repos/mythversion seen false
+ _db_cmd FSET mythbuntu-repos/mythversion seen false
+ IFS=  printf %s\n FSET mythbuntu-repos/mythversion seen false
+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ cut -f 2
+ grep repos
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ REPOS=DE, FR, UK, US, PPA
+ db_subst mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ _db_cmd SUBST mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ IFS=  printf %s\n SUBST mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_fset mythbuntu-repos/repolocation seen false
+ _db_cmd FSET mythbuntu-repos/repolocation seen false
+ IFS=  printf %s\n FSET mythbuntu-repos/repolocation seen false
+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ CONFIG=/etc/default/mythbuntu-repos
+ [ -e /etc/default/mythbuntu-repos ]
+ sed -n -e s/^\(str  *\)\?activateweekly = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/weekly True
+ _db_cmd SET mythbuntu-repos/weekly True
+ IFS=  printf %s\n SET mythbuntu-repos/weekly True
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?weeklyrepo = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ _db_cmd SET mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=  printf %s\n SET mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?weeklylocation = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/repolocation US
+ _db_cmd SET mythbuntu-repos/repolocation US
+ IFS=  printf %s\n SET mythbuntu-repos/repolocation US
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?testingppa = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/testing True
+ _db_cmd SET mythbuntu-repos/testing True
+ IFS=  printf %s\n SET mythbuntu-repos/testing True
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ STATE=1
+ LASTSTATE=7
+ [ 1 != 0 -a 1 -le 7 ]
+ db_input high mythbuntu-repos/weekly
+ _db_cmd INPUT high mythbuntu-repos/weekly
+ IFS=  printf %s\n INPUT high mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=2
+ [ 2 != 0 -a 2 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_input high mythbuntu-repos/mythversion
+ _db_cmd INPUT high mythbuntu-repos/mythversion
+ IFS=  printf %s\n INPUT high mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=30 question skipped
+ return 30
+ true
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=3
+ [ 3 != 0 -a 3 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ bc
+ echo if(0.23.0+fixes24158-0ubuntu2 | h,<=0.23)r=0;if(0.23.0+fixes24158-0ubuntu2 | h,>0.23)r=1;r
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ [ = 1 ]
[: 1: =: unexpected operator
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=4
+ [ 4 != 0 -a 4 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ bc
+ echo if(0.23.0+fixes24158-0ubuntu2 | h,<=0.23)r=0;if(0.23.0+fixes24158-0ubuntu2 | h,>0.23)r=1;r
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ [ = 1 ]
[: 1: =: unexpected operator
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=5
+ [ 5 != 0 -a 5 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_input high mythbuntu-repos/repolocation
+ _db_cmd INPUT high mythbuntu-repos/repolocation
+ IFS=  printf %s\n INPUT high mythbuntu-repos/repolocation
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=6
+ [ 6 != 0 -a 6 -le 7 ]
+ db_input high mythbuntu-repos/testing
+ _db_cmd INPUT high mythbuntu-repos/testing
+ IFS=  printf %s\n INPUT high mythbuntu-repos/testing
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=7
+ [ 7 != 0 -a 7 -le 7 ]
+ db_input high mythbuntu-repos/complete
+ _db_cmd INPUT high mythbuntu-repos/complete
+ IFS=  printf %s\n INPUT high mythbuntu-repos/complete
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=8
+ [ 8 != 0 -a 8 -le 7 ]
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ exit 0
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ /usr/bin/apt-key del EEED06D0
+ true
+ /usr/bin/apt-key del 1504888C
OK
+ rm /etc/apt/sources.list.d/mythbuntu-repos.list
+ lsb_release -c -s
+ release=lucid
+ cut -f 2
+ grep lucid
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ BLD1=
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ weeklyactive=true
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ mythversion=0.23.0+fixes24158-0ubuntu2 | h,
+ db_get mythbuntu-repos/repolocation
+ _db_cmd GET mythbuntu-repos/repolocation
+ IFS=  printf %s\n GET mythbuntu-repos/repolocation
+ IFS=
 read -r _db_internal_line
+ RET=US
+ return 0
+ repolocation=US
+ db_get mythbuntu-repos/testing
+ _db_cmd GET mythbuntu-repos/testing
+ IFS=  printf %s\n GET mythbuntu-repos/testing
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ testingactive=true
+ CONFIGFILE=/etc/default/mythbuntu-repos
+ [ -x /usr/bin/apt-key ]
+ /usr/bin/apt-key add /usr/share/keyrings/mythbuntu-ppa-keyring.gpg
OK
+ echo deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
+ echo [cfg]
+ version=0.23.0+fixes24158-0ubuntu2 | h,
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.21 ]
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.22 ]
+ [ US = PPA ]
+ tr “[:upper:]” “[:lower:]”
+ echo US
+ smrepolocation=us
+ [ us = de ]
+ repo=us.autobuilds.mythbuntu.org
+ [ true = true ]
+ echo activateweekly = True
+ echo weeklylocation = US
+ echo weeklyrepo = 0.23.0+fixes24158-0ubuntu2 | h,
+ echo deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ echo deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ [ true = true ]
+ echo deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo testingppa = True
+ exit 0
```

That again trash the /etc/apt/sources.list.d/mythbuntu-repos.list
```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```


> **tgm4883 said:**
> ```
apt-cache madison mythtv | grep "multiverse Packages" | sed -rne 's/1://;s/^mythtv: | *.........(.*).............-.*/\1/p'

```

Result
```
0.23.0+fixes24158-0ubuntu2 | h
```

---

### Post by tgm4883 on 2010-07-23
> **Archmage said:**
> Result
```
+ LANG=C
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ db_version 2.0
+ _db_cmd VERSION 2.0
+ IFS=  printf %s\n VERSION 2.0
+ IFS=
 read -r _db_internal_line
+ RET=2.0
+ return 0
+ db_capb backup
+ _db_cmd CAPB backup
+ IFS=  printf %s\n CAPB backup
+ IFS=
 read -r _db_internal_line
+ RET=multiselect escape backup
+ return 0
+ sed -rne s/1://;s/^mythtv: | *.........(.*).............-.*/\1/p
+ grep multiverse Packages
+ apt-cache madison mythtv
+ BLD1=0.23.0+fixes24158-0ubuntu2 | h
+ awk {printf "%04s\n", $0}
+ bc
+ echo 0.23.0+fixes24158-0ubuntu2 | h + 0.01
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ BLD2=
+ cut -f 2
+ grep MYTHTV_RELEASE
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ RVER=0.23
+ db_subst mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ _db_cmd SUBST mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion choices 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ _db_cmd SUBST mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ _db_cmd SUBST mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=  printf %s\n SUBST mythbuntu-repos/trunkwarning2 FVERSION 0.23.0+fixes24158-0ubuntu2 | h
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_subst mythbuntu-repos/mythversion RVERSION 0.23
+ _db_cmd SUBST mythbuntu-repos/mythversion RVERSION 0.23
+ IFS=  printf %s\n SUBST mythbuntu-repos/mythversion RVERSION 0.23
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_fset mythbuntu-repos/mythversion seen false
+ _db_cmd FSET mythbuntu-repos/mythversion seen false
+ IFS=  printf %s\n FSET mythbuntu-repos/mythversion seen false
+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ cut -f 2
+ grep repos
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ REPOS=DE, FR, UK, US, PPA
+ db_subst mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ _db_cmd SUBST mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ IFS=  printf %s\n SUBST mythbuntu-repos/repolocation repos DE, FR, UK, US, PPA
+ IFS=
 read -r _db_internal_line
+ RET=0
+ return 0
+ db_fset mythbuntu-repos/repolocation seen false
+ _db_cmd FSET mythbuntu-repos/repolocation seen false
+ IFS=  printf %s\n FSET mythbuntu-repos/repolocation seen false
+ IFS=
 read -r _db_internal_line
+ RET=false
+ return 0
+ CONFIG=/etc/default/mythbuntu-repos
+ [ -e /etc/default/mythbuntu-repos ]
+ sed -n -e s/^\(str  *\)\?activateweekly = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/weekly True
+ _db_cmd SET mythbuntu-repos/weekly True
+ IFS=  printf %s\n SET mythbuntu-repos/weekly True
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?weeklyrepo = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ _db_cmd SET mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=  printf %s\n SET mythbuntu-repos/mythversion 0.23.0+fixes24158-0ubuntu2 | h,
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?weeklylocation = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/repolocation US
+ _db_cmd SET mythbuntu-repos/repolocation US
+ IFS=  printf %s\n SET mythbuntu-repos/repolocation US
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?testingppa = \(.*\)$/\2/gp; /etc/default/mythbuntu-repos
+ db_set mythbuntu-repos/testing True
+ _db_cmd SET mythbuntu-repos/testing True
+ IFS=  printf %s\n SET mythbuntu-repos/testing True
+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ STATE=1
+ LASTSTATE=7
+ [ 1 != 0 -a 1 -le 7 ]
+ db_input high mythbuntu-repos/weekly
+ _db_cmd INPUT high mythbuntu-repos/weekly
+ IFS=  printf %s\n INPUT high mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=2
+ [ 2 != 0 -a 2 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_input high mythbuntu-repos/mythversion
+ _db_cmd INPUT high mythbuntu-repos/mythversion
+ IFS=  printf %s\n INPUT high mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=30 question skipped
+ return 30
+ true
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=3
+ [ 3 != 0 -a 3 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ bc
+ echo if(0.23.0+fixes24158-0ubuntu2 | h,<=0.23)r=0;if(0.23.0+fixes24158-0ubuntu2 | h,>0.23)r=1;r
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ [ = 1 ]
[: 1: =: unexpected operator
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=4
+ [ 4 != 0 -a 4 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ bc
+ echo if(0.23.0+fixes24158-0ubuntu2 | h,<=0.23)r=0;if(0.23.0+fixes24158-0ubuntu2 | h,>0.23)r=1;r
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
+ [ = 1 ]
[: 1: =: unexpected operator
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=5
+ [ 5 != 0 -a 5 -le 7 ]
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ [ true = true ]
+ db_input high mythbuntu-repos/repolocation
+ _db_cmd INPUT high mythbuntu-repos/repolocation
+ IFS=  printf %s\n INPUT high mythbuntu-repos/repolocation
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=6
+ [ 6 != 0 -a 6 -le 7 ]
+ db_input high mythbuntu-repos/testing
+ _db_cmd INPUT high mythbuntu-repos/testing
+ IFS=  printf %s\n INPUT high mythbuntu-repos/testing
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=7
+ [ 7 != 0 -a 7 -le 7 ]
+ db_input high mythbuntu-repos/complete
+ _db_cmd INPUT high mythbuntu-repos/complete
+ IFS=  printf %s\n INPUT high mythbuntu-repos/complete
+ IFS=
 read -r _db_internal_line
+ RET=question will be asked
+ return 0
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ STATE=8
+ [ 8 != 0 -a 8 -le 7 ]
+ db_go
+ _db_cmd GO 
+ IFS=  printf %s\n GO 
+ IFS=
 read -r _db_internal_line
+ RET=ok
+ return 0
+ exit 0
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ /usr/bin/apt-key del EEED06D0
+ true
+ /usr/bin/apt-key del 1504888C
OK
+ rm /etc/apt/sources.list.d/mythbuntu-repos.list
+ lsb_release -c -s
+ release=lucid
+ cut -f 2
+ grep lucid
+ cat /usr/share/mythbuntu/plugins/mythbuntu-repos.db
+ BLD1=
+ db_get mythbuntu-repos/weekly
+ _db_cmd GET mythbuntu-repos/weekly
+ IFS=  printf %s\n GET mythbuntu-repos/weekly
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ weeklyactive=true
+ [ true = true ]
+ db_get mythbuntu-repos/mythversion
+ _db_cmd GET mythbuntu-repos/mythversion
+ IFS=  printf %s\n GET mythbuntu-repos/mythversion
+ IFS=
 read -r _db_internal_line
+ RET=0.23.0+fixes24158-0ubuntu2 | h,
+ return 0
+ mythversion=0.23.0+fixes24158-0ubuntu2 | h,
+ db_get mythbuntu-repos/repolocation
+ _db_cmd GET mythbuntu-repos/repolocation
+ IFS=  printf %s\n GET mythbuntu-repos/repolocation
+ IFS=
 read -r _db_internal_line
+ RET=US
+ return 0
+ repolocation=US
+ db_get mythbuntu-repos/testing
+ _db_cmd GET mythbuntu-repos/testing
+ IFS=  printf %s\n GET mythbuntu-repos/testing
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ testingactive=true
+ CONFIGFILE=/etc/default/mythbuntu-repos
+ [ -x /usr/bin/apt-key ]
+ /usr/bin/apt-key add /usr/share/keyrings/mythbuntu-ppa-keyring.gpg
OK
+ echo deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
+ echo [cfg]
+ version=0.23.0+fixes24158-0ubuntu2 | h,
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.21 ]
+ [ 0.23.0+fixes24158-0ubuntu2 | h, = 0.22 ]
+ [ US = PPA ]
+ tr “[:upper:]” “[:lower:]”
+ echo US
+ smrepolocation=us
+ [ us = de ]
+ repo=us.autobuilds.mythbuntu.org
+ [ true = true ]
+ echo activateweekly = True
+ echo weeklylocation = US
+ echo weeklyrepo = 0.23.0+fixes24158-0ubuntu2 | h,
+ echo deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ echo deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
+ [ true = true ]
+ echo deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
+ echo testingppa = True
+ exit 0
```

That again trash the /etc/apt/sources.list.d/mythbuntu-repos.list
```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```




Result
```
0.23.0+fixes24158-0ubuntu2 | h
```

Ok, thats definitly where it is breaking then. That should be returning 0.23.

What is the output of

```
apt-cache madison mythtv
```

---

### Post by Archmage on 2010-07-23
apt-cache madison mythtv
```
mythtv | 0.23.0+fixes25396-0ubuntu0+mythbuntu2 | http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu/ lucid/main Packages
    mythtv | 0.23.0+fixes24158-0ubuntu2 | http://apt-proxy-server.home/ubuntu/ lucid/multiverse Packages
    mythtv | 0.23.0+fixes25396-0ubuntu0+mythbuntu2 | http://weeklybuilds.mythbuntu.org/mythbuntu/0.23/ubuntu/ lucid/main Sources
```

---

### Post by Archmage on 2010-08-05
The version from today is doing the same. :(

```

Richte mythbuntu-repos ein (8.0-0ubuntu0+mythbuntu~auto20100805002724) ...
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: illegal character: |
OK
OK

```

```

cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main

```

---

### Post by tgm4883 on 2010-08-05
Yea that got built as a result of fixing another issue. I'll have this issue fixed in about a week when I can push another change to -repos. I'm have another project I need to get finished by feature freeze on Aug 12th. Stick with me and I'll get that issue fixed. Unfortuntly I can't fix it right now as it will require some reengineering of how we pull the version information since we need to account for point releases now (eg. 0.23.1)

---

### Post by Archmage on 2010-08-06
Of course. Do your important projects first. I can life with rewriting the /etc/apt/sources.list.d/mythbuntu-repos.list each time. As long as I know that a fix will come in the near future.

Thanks for your work and take your time. :D

---

### Post by jms-ubuntu-en on 2010-08-08
I edited mythbuntu-repos's apt sources for version 0.23.1 and for me *"apt-cache madison mythtv"* outputs:

```
    mythtv | 0.23.1+fixes25586-0ubuntu0+mythbuntu2 | http://ppa.launchpad.net/mythbuntu/0.23.1/ubuntu/ lucid/main Packages
    mythtv | 0.23.0+fixes24158-0ubuntu2 | http://ubuntu.trumpetti.atm.tut.fi/ubuntu/ lucid/multiverse Packages
    mythtv | 0.23.1+fixes25586-0ubuntu0+mythbuntu2 | http://ppa.launchpad.net/mythbuntu/0.23.1/ubuntu/ lucid/main Sources
```

The problem is that mythbuntu-repos don't have version 0.23.1 included and it overwrites my editions every time. For now I put the package mythbuntu-repos on hold...

---

### Post by epi 1:10,000 on 2010-08-08
Why are the .24 packages all out of sync? Mythweb is version 25575, Myhtv-common front and back are 25588, and the theme are 25106, ect.   Is this supposed to work?  My test rig has multiple problems now.  I'm just playing around and testing but I am new to this.  Am I doing something wrong?   Should I just compile and install everything from scratch instead of using the repo's for testing?

---

### Post by tgm4883 on 2010-08-08
> **jms-ubuntu-en said:**
> I edited mythbuntu-repos's apt sources for version 0.23.1 and for me *"apt-cache madison mythtv"* outputs:

```
    mythtv | 0.23.1+fixes25586-0ubuntu0+mythbuntu2 | http://ppa.launchpad.net/mythbuntu/0.23.1/ubuntu/ lucid/main Packages
    mythtv | 0.23.0+fixes24158-0ubuntu2 | http://ubuntu.trumpetti.atm.tut.fi/ubuntu/ lucid/multiverse Packages
    mythtv | 0.23.1+fixes25586-0ubuntu0+mythbuntu2 | http://ppa.launchpad.net/mythbuntu/0.23.1/ubuntu/ lucid/main Sources
```

The problem is that mythbuntu-repos don't have version 0.23.1 included and it overwrites my editions every time. For now I put the package mythbuntu-repos on hold...

If you are manually editing your apt sources, why do you keep reconfiguring mythbuntu-repos. All you need to do is edit the sources. The -repos package will be updated soon enough.

---

### Post by tgm4883 on 2010-08-08
> **epi 1:10,000 said:**
> Why are the .24 packages all out of sync? Mythweb is version 25575, Myhtv-common front and back are 25588, and the theme are 25106, ect.   Is this supposed to work?  My test rig has multiple problems now.  I'm just playing around and testing but I am new to this.  Am I doing something wrong?   Should I just compile and install everything from scratch instead of using the repo's for testing?

Mythtv and myththemes are both 25588, mythplugins are older because right now they are failing to build. Sometimes things break in trunk, so you either A) should just wait it out, or B) not run the development version of mythtv

---

### Post by jms-ubuntu-en on 2010-08-09
> **tgm4883 said:**
> If you are manually editing your apt sources, why do you keep reconfiguring mythbuntu-repos. All you need to do is edit the sources. The -repos package will be updated soon enough.
Thanks for the info. This is not an issue any more as I put package mythbuntu-repos on hold. Until then mythbuntu-repos got an update  every day as well as overwrited apt sources without any manual mythbuntu-repos reconfiguring. Now I have installed version:

```
hi  mythbuntu-repos    8.0-0ubuntu0+mythbuntu~auto20100808002702    Mythbuntu repos installer
```

---

### Post by Archmage on 2010-08-17
The latest version of mythbuntu-repos didn't make any error message while upgrading it.

```
Richte mythbuntu-repos ein (8.2-0ubuntu0+mythbuntu~auto20100817002640) ...
OK
OK
```

But the file /etc/apt/sources.list.d/mythbuntu-repos.list is still messed up after upgrading it.

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

---

### Post by tgm4883 on 2010-08-17
> **Archmage said:**
> The latest version of mythbuntu-repos didn't make any error message while upgrading it.

```
Richte mythbuntu-repos ein (8.2-0ubuntu0+mythbuntu~auto20100817002640) ...
OK
OK
```

But the file /etc/apt/sources.list.d/mythbuntu-repos.list is still messed up after upgrading it.

```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.0+fixes24158-0ubuntu2 | h,/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

Can you do a 'dpkg-reconfigure mythbuntu-repos' and see if it is still messed up?

---

### Post by Archmage on 2010-08-18
> **tgm4883 said:**
> Can you do a 'dpkg-reconfigure mythbuntu-repos' and see if it is still messed up?

It's **NOT** messed up after the commando!

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

I'm curios waiting for the next version of the mythbuntu-repos to see what is happing than. But so far so good. :)

---

### Post by tgm4883 on 2010-08-19
> **Archmage said:**
> It's **NOT** messed up after the commando!

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu lucid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb-src http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu lucid main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu lucid main
```

I'm curios waiting for the next version of the mythbuntu-repos to see what is happing than. But so far so good. :)

Ok, it shouldn't be messed up from now on. I changed how the versions were figured out, instead of doing math on it, it pulls a list from the web

---

### Post by bgiannes on 2010-08-20
Mythbuntu repos installer is fixed for me with todays update

---

### Post by jms-ubuntu-en on 2010-08-30
After today's updates I couldn't launch frontend any more, error message:
```
Error: MythTV database has newer TV schema (1263) than expected (1254).
```


```
ii  libmyth-0.23-0                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           Common library code for MythTV and add-on mo
ii  libmyth-python                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A python library to access some MythTV featu
ii  libmythtv-perl                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A PERL library to access some MythTV feature
ii  mythbuntu-3rd-party-frontends                     1-0ubuntu1+mythbuntu~lucid                      Mythbuntu 3rd Party Frontends Installer
ii  mythbuntu-common                                  0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre                          0.62-0ubuntu1                                   Mythbuntu Configuration Application
hi  mythbuntu-repos                                   8.2-0ubuntu0+mythbuntu~auto20100819002723       Mythbuntu repos installer
ii  mythmusic                                         0.23.1+fixes25975-0ubuntu0+mythbuntu2           Music add-on module for MythTV
ii  mythtv                                            0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-backend                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (serve
ii  mythtv-common                                     0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (commo
ii  mythtv-database                                   0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (datab
ii  mythtv-doc                                        0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (docum
ii  mythtv-frontend                                   0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-status                                     0.9.2-3                                         Show the status of a MythTV backend
ii  mythtv-theme-arclight                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The arclight MythTV Theme
ii  mythtv-theme-blootube-osd                         1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                              1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The blueosd MythTV Theme
ii  mythtv-theme-childish                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The childish MythTV Theme
ii  mythtv-theme-graphite                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The graphite MythTV Theme
ii  mythtv-theme-iulius-osd                           1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy                           1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu                            1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd                   1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd                            1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd                       1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The titivillus-osd MythTV Theme
ii  mythtv-themes                                     1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         Themes for MythTV
ii  mythtv-transcode-utils                            0.23.1+fixes25975-0ubuntu0+mythbuntu2           Utilities used for transcoding MythTV tasks
ii  mythvideo                                         0.23.1+fixes25975-0ubuntu0+mythbuntu2           A generic video player frontend module for M
ii  mythweather                                       0.23.1+fixes25975-0ubuntu0+mythbuntu2           Weather add-on module for MythTV
ii  mythweb                                           0.23.1+fixes25975-0ubuntu0+mythbuntu2           Web interface add-on module for MythTV

```

Any idea what happened? I was in a hurry to start a recording so I just edited mythconverg's settings table's DBSchemaVer 1263 -> 1254 and after that frontend started properly...

---

### Post by tgm4883 on 2010-08-30
> **jms-ubuntu-en said:**
> After today's updates I couldn't launch frontend any more, error message:
```
Error: MythTV database has newer TV schema (1263) than expected (1254).
```


```
ii  libmyth-0.23-0                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           Common library code for MythTV and add-on mo
ii  libmyth-python                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A python library to access some MythTV featu
ii  libmythtv-perl                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A PERL library to access some MythTV feature
ii  mythbuntu-3rd-party-frontends                     1-0ubuntu1+mythbuntu~lucid                      Mythbuntu 3rd Party Frontends Installer
ii  mythbuntu-common                                  0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre                          0.62-0ubuntu1                                   Mythbuntu Configuration Application
hi  mythbuntu-repos                                   8.2-0ubuntu0+mythbuntu~auto20100819002723       Mythbuntu repos installer
ii  mythmusic                                         0.23.1+fixes25975-0ubuntu0+mythbuntu2           Music add-on module for MythTV
ii  mythtv                                            0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-backend                                    0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (serve
ii  mythtv-common                                     0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (commo
ii  mythtv-database                                   0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (datab
ii  mythtv-doc                                        0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (docum
ii  mythtv-frontend                                   0.23.1+fixes25975-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-status                                     0.9.2-3                                         Show the status of a MythTV backend
ii  mythtv-theme-arclight                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The arclight MythTV Theme
ii  mythtv-theme-blootube-osd                         1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                              1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The blueosd MythTV Theme
ii  mythtv-theme-childish                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The childish MythTV Theme
ii  mythtv-theme-graphite                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The graphite MythTV Theme
ii  mythtv-theme-iulius-osd                           1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy                           1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                             1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu                            1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd                   1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd                            1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd                       1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         The titivillus-osd MythTV Theme
ii  mythtv-themes                                     1:0.23.1+fixes25975-0ubuntu0+mythbuntu2         Themes for MythTV
ii  mythtv-transcode-utils                            0.23.1+fixes25975-0ubuntu0+mythbuntu2           Utilities used for transcoding MythTV tasks
ii  mythvideo                                         0.23.1+fixes25975-0ubuntu0+mythbuntu2           A generic video player frontend module for M
ii  mythweather                                       0.23.1+fixes25975-0ubuntu0+mythbuntu2           Weather add-on module for MythTV
ii  mythweb                                           0.23.1+fixes25975-0ubuntu0+mythbuntu2           Web interface add-on module for MythTV

```

Any idea what happened? I was in a hurry to start a recording so I just edited mythconverg's settings table's DBSchemaVer 1263 -> 1254 and after that frontend started properly...

You ran trunk/0.24 somewhere in your environment at some point. You can either completely upgrade to trunk, or restore the database from a previous backup. I don't recommend changing the DBSchemaVer in the database though. You should have a backup of the database from when the upgrade took place.

---

### Post by red321 on 2010-08-31
Trunk daily builds seem to have stuck at 25893

---

### Post by tgm4883 on 2010-08-31
> **red321 said:**
> Trunk daily builds seem to have stuck at 25893

Trunk builds do fail from time to time. Looks to be just mythplugins.

---

### Post by brian_hammerhead on 2010-09-19
I am kind of a novice so please excuse me if I have posted this in the wrong area.

I am running Mythbuntu 10.04 and have activated auto-builds so that the fixes appear as update packages in the Update Manager (I am sure that I am not saying this correctly, but hopefully you know what I mean).  Over the past few months I have been applying fixes upgrades and for the most part all has been reasonably good.  However, a few weeks ago, one of the updates stopped at a window and asked me for the mysql userid and password.  I now believe that I know which userid and password it wanted, but at the time I thought it wanted by myth userid and password.  At any rate, I typed in three wrong userids and passwords.  The install script just continued on.  When I looked in the "verbose" install log screen, it said something like "couldn't update the mysql tables and you should run some kind of command".  Before I could copy the text with the command, the update finished and the install log screen went away.

I searched all over my hard drive to see if the install log was written somewhere, but I couldn't find it.

I am currently on fixes-s25362 according to the System Info screen in Myth TV.

Up until today I haven't noticed any significant weirdness with not having the database updated, but I am sure that something will break soon.  Today I tried adding a new video and for some weird reason when I scanned for new titles, it added two entries for the new video.  I am not sure if this is because the database didn't update.

Q:  Does anyone know what I should do to make sure that the mysql database structure is in sync with my version of Mythbuntu?


Thanks very much in advance!

---

### Post by superm1 on 2010-09-19
> **brian_hammerhead said:**
> I am kind of a novice so please excuse me if I have posted this in the wrong area.

I am running Mythbuntu 10.04 and have activated auto-builds so that the fixes appear as update packages in the Update Manager (I am sure that I am not saying this correctly, but hopefully you know what I mean).  Over the past few months I have been applying fixes upgrades and for the most part all has been reasonably good.  However, a few weeks ago, one of the updates stopped at a window and asked me for the mysql userid and password.  I now believe that I know which userid and password it wanted, but at the time I thought it wanted by myth userid and password.  At any rate, I typed in three wrong userids and passwords.  The install script just continued on.  When I looked in the "verbose" install log screen, it said something like "couldn't update the mysql tables and you should run some kind of command".  Before I could copy the text with the command, the update finished and the install log screen went away.

I searched all over my hard drive to see if the install log was written somewhere, but I couldn't find it.

I am currently on fixes-s25362 according to the System Info screen in Myth TV.

Up until today I haven't noticed any significant weirdness with not having the database updated, but I am sure that something will break soon.  Today I tried adding a new video and for some weird reason when I scanned for new titles, it added two entries for the new video.  I am not sure if this is because the database didn't update.

Q:  Does anyone know what I should do to make sure that the mysql database structure is in sync with my version of Mythbuntu?


Thanks very much in advance!
My guess here is that a mysql upgrade happened around the same time as this other upgrade you did, causing it to not be running while the scripts were trying to probe the database.  The database updates would have happened next time the backend ran though anyhow.  If there are no (visible) issues, I wouldn't worry too much.  If this happens again however with the next set of autobuilds, it'd be good if you can file a bug so we can help figure out what exactly is going on that's broken ([http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu))

---

### Post by Neon Dusk on 2010-09-22
It looks like the packages for mythplugins 0.24 (amd64) have failed to build the past couple of days

---

### Post by superm1 on 2010-09-22
> **Neon Dusk said:**
> It looks like the packages for mythplugins 0.24 (amd64) have failed to build the past couple of days

According to [https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages](https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages) they've been building, they're just lagging behind because of a lot of activity on the amd64 PPA builder's

---

### Post by Neon Dusk on 2010-09-22
The plugins seem to be stuck at 0.24.0~trunk26419

```

sudo apt-cache policy mythnetvision
mythnetvision:
...
Candidate: 0.24.0~trunk26419-0ubuntu0~mythbuntu1

```

while everything else is at 0.24.0~trunk26433
```

sudo apt-cache policy mythtv-frontend
mythtv-frontend:
...
Candidate: 0.24.0~trunk26433-0ubuntu0~mythbuntu1

```

From [https://edge.launchpad.net/~mythbuntu/+archive/0.24/+builds?build_text=mythplugins&build_state=all](https://edge.launchpad.net/~mythbuntu/+archive/0.24/+builds?build_text=mythplugins&build_state=all) it looks like the last build was 20 Sept

---

### Post by tgm4883 on 2010-09-22
> **Neon Dusk said:**
> The plugins seem to be stuck at 0.24.0~trunk26419

```

sudo apt-cache policy mythnetvision
mythnetvision:
...
Candidate: 0.24.0~trunk26419-0ubuntu0~mythbuntu1

```

while everything else is at 0.24.0~trunk26433
```

sudo apt-cache policy mythtv-frontend
mythtv-frontend:
...
Candidate: 0.24.0~trunk26433-0ubuntu0~mythbuntu1

```

From [https://edge.launchpad.net/~mythbuntu/+archive/0.24/+builds?build_text=mythplugins&build_state=all](https://edge.launchpad.net/~mythbuntu/+archive/0.24/+builds?build_text=mythplugins&build_state=all) it looks like the last build was 20 Sept

I see whats causing the issue, but i'm not sure how to fix it quite yet.

---

### Post by LowSky on 2010-09-26
The mythbuntu website seems to be down. Is there anywhere else to grab the autobuild package?

---

### Post by superm1 on 2010-09-26
> **LowSky said:**
> The mythbuntu website seems to be down. Is there anywhere else to grab the autobuild package?

For now, u can grab it from the PPA at [https://edge.launchpad.net/~mythbuntu/+archive/repos](https://edge.launchpad.net/~mythbuntu/+archive/repos)

---

### Post by wombo on 2010-09-26
Hey guys looks like at least Mythweb did not build last night for trunk.

---

### Post by superm1 on 2010-09-27
> **wombo said:**
> Hey guys looks like at least Mythweb did not build last night for trunk.

There was an upstream problem with the python bindings causing the FTBFS.  Tonight's builds should be good.

---

### Post by jimmyoo0 on 2010-10-08
Im having a problem upgrading from 0.23.1 to 0.24, in the Mythbuntu Control Center gui under repository's it only lists 0.22, 0.23 and 0.23.1, so i went in to 
```
sudo dpkg-reconfigure mythbuntu-repos
```That all goes smoothly giving me the options of 0.23, 0.23.1 and 0.24. Then i get to this screen (as in attachment) where it asks me for a password but i cant see what the password is i presume it should be where the space is inbetween the words "enter  below" on the start of the forth line.

There is something weird going on can anyone shed some light on this? thanks

Im running 9.10

---

### Post by tgm4883 on 2010-10-08
> **jimmyoo0 said:**
> Im having a problem upgrading from 0.23.1 to 0.24, in the Mythbuntu Control Center gui under repository's it only lists 0.22, 0.23 and 0.23.1, so i went in to 
```
sudo dpkg-reconfigure mythbuntu-repos
```That all goes smoothly giving me the options of 0.23, 0.23.1 and 0.24. Then i get to this screen (as in attachment) where it asks me for a password but i cant see what the password is i presume it should be where the space is inbetween the words "enter  below" on the start of the forth line.

There is something weird going on can anyone shed some light on this? thanks

Im running 9.10

Couple issues.

MythTV 0.24 isn't available on 9.10. You can't update to it with the Mythbuntu repos because we don't provide builds for it. There would be nothing to download.

In that respect the MCC plugin is working correctly. The debconf portion is busted (since it is showing you 0.24 as an option). I've looked at the code and see where it was broke. It should be fixed in tomorrows build of mythbuntu-repos.

This probably isn't what you wanted to hear, but the only way you are going to get 0.24 (which BTW isn't released yet) from mythbuntu-repos is to upgrade to at least 10.04.

---

### Post by sharkcohen on 2010-10-09
Just a quick question: I'm interested in trying out .24.  If I upgrade, will I have to reconfigure my backend?

---

### Post by tgm4883 on 2010-10-09
> **sharkcohen said:**
> Just a quick question: I'm interested in trying out .24.  If I upgrade, will I have to reconfigure my backend?

I'm not sure. I don't run 0.24. You won't have to completely reconfigure it as the database would be upgraded and any settings would be in the database. If there are any new settings you would need to configure the backend in order to configure them (obviously).

Note that you cannot go back to a previous version with backing up and restoring your database.

---

### Post by joshoekstra on 2010-10-13
Is there a page where I can see which patches other than the ones already committed upstream are being added?
The reason I'm asking is because I seem to be affected by the bug mentioned here:
[http://svn.mythtv.org/trac/ticket/8526](http://svn.mythtv.org/trac/ticket/8526)
The ticket has some patches, but I'm not sure if they are applied here like other patches or not?

Thanks in advance,

---

### Post by tgm4883 on 2010-10-13
> **joshoekstra said:**
> Is there a page where I can see which patches other than the ones already committed upstream are being added?
The reason I'm asking is because I seem to be affected by the bug mentioned here:
[http://svn.mythtv.org/trac/ticket/8526](http://svn.mythtv.org/trac/ticket/8526)
The ticket has some patches, but I'm not sure if they are applied here like other patches or not?

Thanks in advance,

We don't include too many patches downstream. What we do add you can see at the following links

## Mythtv fixes and trunk
[http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/files/head:/debian/patches/](http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/files/head:/debian/patches/)
[http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-fixes/files/head:/debian/patches/](http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-fixes/files/head:/debian/patches/)

## Mythplugins fixes and trunk
[http://bazaar.launchpad.net/~mythbuntu/mythplugins/mythplugins-trunk/files/head:/debian/patches/](http://bazaar.launchpad.net/~mythbuntu/mythplugins/mythplugins-trunk/files/head:/debian/patches/)
[http://bazaar.launchpad.net/~mythbuntu/mythplugins/mythplugins-fixes/files/head:/debian/patches/](http://bazaar.launchpad.net/~mythbuntu/mythplugins/mythplugins-fixes/files/head:/debian/patches/)

---

### Post by the_crowbar on 2010-10-13
The patches from Myth ticket 8526 do not appear to be applied to mythbuntu package based on svn 26766. I am able to cleanly apply the patches to the mythbunut package source. I was having some trouble with using debuild under my normal environment. With help from superm1 on IRC I now have the package building with the patches from ticket 8526. Here is a quick howto:

1) Setup a pbuilder environment. [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) Make sure you read about half way down about enabling the universe repo.

2) create a directory to store the mythtv source code. Change into that directory. My command was: mkdir /usr/src/mythtv-0.24-26766 (you may have to use sudo to create a directory under /usr/src and then chown it to you account) and then:
cd /usr/src/mythtv-0.24-26766

3) apt-get source mythtv (this requires that you have a deb-src repository setup for mythtv. mine looks like this: 
deb-src [http://uk.autobuilds.mythbuntu.org/mythbuntu/0.24/ubuntu](http://uk.autobuilds.mythbuntu.org/mythbuntu/0.24/ubuntu) lucid main )

4) The apt-get source command above will download the mythtv source code into a directory below the current one. Change into that directory.
My command was: 
cd mythtv-0.24.0~trunk26766

5) Change to the debian/patches directory and save any patches you want to apply to Myth int this directory. My command was: 
cd debain/patches

6) Add the patch file names to the series file. I did an echo <patch_file_name> >> series

7) Change back to the source directory from the apt-get source command. 
My command was:
 cd ../..

8) Build a .dsc file for pbuilder with:
debuild -S -sa -us -uc

9) Build package with:
pbuilder. sudo pbuilder build *.dsc

10) Wait... The finished package will appear in /var/cache/pbuilder/result

Hopefully you can get your own package built.

---

### Post by joshoekstra on 2010-10-16
Thanks for the howto, but I noticed the patches got applied upstream(r26827) and built by fixes.
I'&#314;l save this little howto though, might come in handy :)

---

### Post by ubf583 on 2010-11-14
Does anyone know if 0.24 is available on the autobuilds?  I am trying to upgrade to 0.24 from 0.23.1 provided by JYA but even after deleting the JYA repositories and enabling the autobuilds Update Manager never finds the 0.24 packages?  TIA.

---

### Post by superm1 on 2010-11-14
> **ubf583 said:**
> Does anyone know if 0.24 is available on the autobuilds?  I am trying to upgrade to 0.24 from 0.23.1 provided by JYA but even after deleting the JYA repositories and enabling the autobuilds Update Manager never finds the 0.24 packages?  TIA.

0.24 is available on auto-builds:
[http://www.mythbuntu.org/mythtv/0.24](http://www.mythbuntu.org/mythtv/0.24)

You can check out the builds at [https://launchpad.net/~mythbuntu/+archive/0.24](https://launchpad.net/~mythbuntu/+archive/0.24)

If they're not showing up as updates, try switching to the "PPA" repository in MCC.  If they're still not showing up, try looking in synaptic to see if the version number on jya's repo is conflicting.

---

### Post by Nikas on 2010-11-14
> **ubf583 said:**
> Does anyone know if 0.24 is available on the autobuilds?  I am trying to upgrade to 0.24 from 0.23.1 provided by JYA but even after deleting the JYA repositories and enabling the autobuilds Update Manager never finds the 0.24 packages?  TIA.

It's available...
I also want to change from JYA's repo but i dont know how.

I have tried to switch to PPA with dkpg-reconfigure mythbuntu-repos selecting 0.24 and PPA but they still dont show up as updates..

---

### Post by tgm4883 on 2010-11-14
As mentioned before, it is because JYA's version numbers are considered "larger" than ours. I would attempt going into synaptic and forcing the version from our PPA

---

### Post by Nikas on 2010-11-14
> **tgm4883 said:**
> As mentioned before, it is because JYA's version numbers are considered "larger" than ours. I would attempt going into synaptic and forcing the version from our PPA

Which packages should i attempt to force?

---

### Post by tgm4883 on 2010-11-14
Any myth* package

---

### Post by Nikas on 2010-11-14
> **tgm4883 said:**
> Any myth* package

If i search for mythweb, it only gives me one hit: "2:0.23.1+fixes25902-0ubuntu2".

---

### Post by tgm4883 on 2010-11-14
> **Nikas said:**
> If i search for mythweb, it only gives me one hit: "2:0.23.1+fixes25902-0ubuntu2".

Select mythweb, then hit ctrl+e. That should let you select the version

---

### Post by Nikas on 2010-11-14
> **tgm4883 said:**
> Select mythweb, then hit ctrl+e. That should let you select the version

Ah. I see. And i need to do this for **all** the myth packages?

---

### Post by tgm4883 on 2010-11-14
Yep, or you could purge all of myth* then reinstall, although I would backup the database if you did that first.

---

### Post by Nikas on 2010-11-14
> **tgm4883 said:**
> Yep, or you could purge all of myth* then reinstall, although I would backup the database if you did that first.

Sure. Do i have to backup anything else? I have like 1TB of recordings. Big family. ;)

Edit: My recordedseek table: 241MB. 5 300 000 rows. \o/

---

### Post by tgm4883 on 2010-11-14
> **Nikas said:**
> Sure. Do i have to backup anything else? I have like 1TB of recordings. Big family. ;)

Edit: My recordedseek table: 241MB. 5 300 000 rows. \o/

I'd just backup the database, recordings shouldn't be touched by removing the packages

---

### Post by Nikas on 2010-11-14
> **tgm4883 said:**
> I'd just backup the database, recordings shouldn't be touched by removing the packages

So, apt-get purge mythtv* (or myth*?)
And then the same whith install?

I have one frontend-only machine too. No backend-packages needed for that machine..

---

### Post by tgm4883 on 2010-11-14
> **Nikas said:**
> So, apt-get purge mythtv* (or myth*?)
And then the same whith install?

I have one frontend-only machine too. No backend-packages needed for that machine..

mythtv* should work, as mythplugins stuff would get removed as well

---

### Post by Nikas on 2010-11-15
Purge and then install worked great.

Thanks!

Edit: My frontend seems to be doing a db backup with every start. How can i disable it?

Edit2: After restarting my frontend-machine mythfrontend won't start.
Log:
2010-11-15 09:43:59.544 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'

ERROR: DBBackupDirectory is not a directory or is not writable. Please specify
       a directory in your database information file using DBBackupDirectory.
       If not using a database information file, please specify the
        --directory command-line option.

Invalid backup directory, stopped at /usr/share/mythtv/mythconverg_backup.pl line 870.
2010-11-15 09:43:59.785 DBUtil Error: Error backing up database: /usr/share/mythtv/mythconverg_backup.pl /tmp/mythtv_db_backup_conf_duHFif (255)
2010-11-15 09:43:59.785 Script-based database backup failed. Retrying with internal backup.
2010-11-15 09:43:59.790 Backing up database to file: '/mnt/disk1t_3/mythtv/db_backups/mythconverg-1264-20101115094359.sql'
2010-11-15 09:44:43.524 Compressing database backup file.
2010-11-15 09:45:08.444 Database Backup filename: '/mnt/disk1t_3/mythtv/db_backups/mythconverg-1264-20101115094359.sql.gz'
2010-11-15 09:45:08.444 Database Backup complete.
ICE default IO error handler doing an exit(), pid = 2627, errno = 32

I have removed the .ICEauthority file...

Edit again:
I changed "DisableAutomaticBackup" to 1 and everything works now. Strange. I am doing a backup every night using cron so no worries there. ;)

---

### Post by winewood on 2010-11-15
I do not undertand why a DB backup is necessary.
 
Isn't this just a summary of the files that you have recorded with the EPG info, ratings, watched yes/no?  I thought if you just rebuild it, and update the db with the files from your locaitons, wouldn't it be ok?
(I understand some people put music in their DB's as well, but i don't use that function)
 
Just a n00b question, any help would be appreciated.

---

### Post by tgm4883 on 2010-11-15
> **winewood said:**
> I do not undertand why a DB backup is necessary.
 
Isn't this just a summary of the files that you have recorded with the EPG info, ratings, watched yes/no?  I thought if you just rebuild it, and update the db with the files from your locaitons, wouldn't it be ok?
(I understand some people put music in their DB's as well, but i don't use that function)
 
Just a n00b question, any help would be appreciated.

With production systems, you will learn that you ALWAYS do a backup before altering something. 

For instance, if you did a complete reinstall without keeping your database, you now have a bunch of recordings named like this "4767_20101028162900.mpg" and absolutely no way to easily get them back into MythTV with any sort of metadata

---

### Post by cedyathome on 2010-11-16
> **Nikas said:**
> Purge and then install worked great.

Thanks!

Edit: My frontend seems to be doing a db backup with every start. How can i disable it?

Edit2: After restarting my frontend-machine mythfrontend won't start.
Log:
2010-11-15 09:43:59.544 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'

ERROR: DBBackupDirectory is not a directory or is not writable. Please specify
       a directory in your database information file using DBBackupDirectory.
       If not using a database information file, please specify the
        --directory command-line option.

Invalid backup directory, stopped at /usr/share/mythtv/mythconverg_backup.pl line 870.
2010-11-15 09:43:59.785 DBUtil Error: Error backing up database: /usr/share/mythtv/mythconverg_backup.pl /tmp/mythtv_db_backup_conf_duHFif (255)
2010-11-15 09:43:59.785 Script-based database backup failed. Retrying with internal backup.
2010-11-15 09:43:59.790 Backing up database to file: '/mnt/disk1t_3/mythtv/db_backups/mythconverg-1264-20101115094359.sql'
2010-11-15 09:44:43.524 Compressing database backup file.
2010-11-15 09:45:08.444 Database Backup filename: '/mnt/disk1t_3/mythtv/db_backups/mythconverg-1264-20101115094359.sql.gz'
2010-11-15 09:45:08.444 Database Backup complete.
ICE default IO error handler doing an exit(), pid = 2627, errno = 32

I have removed the .ICEauthority file...

Edit again:
I changed "DisableAutomaticBackup" to 1 and everything works now. Strange. I am doing a backup every night using cron so no worries there. ;)

See this [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
under the Quick start. I remember having to do that before backing up the DB for the first time using the scripts.

---

### Post by iitywygms on 2010-11-19
Latest update break opengl for anyone?  I have to run using qt or I get no menu on the main start page of mythtv.

---

### Post by Nikas on 2010-11-19
> **iitywygms said:**
> Latest update break opengl for anyone?  I have to run using qt or I get no menu on the main start page of mythtv.

Yep but it was not something that came from the autobuilds-repo. Some update to xserver i think. I just had to reinstall my nvidia driver.

---

### Post by iitywygms on 2010-11-19
So reinstalling nvidia driver fixes it?

---

### Post by iitywygms on 2010-11-19
One other thing that just popped up.
I now notice on standard def tv, a thin area of white lines going down each side of the video.  Right next to the black bars on each side. (Vertical)  Like the lines you sometimes see going across the top of the video image.  The line that looks like crawling ants. (I know it is the extra data broadcast with the video)
Not a big deal, but kind of annoying.
I think I may have jumped to .24 a bit to soon.  Seems a little more buggy that what I am use to.

---

### Post by Nikas on 2010-11-19
> **iitywygms said:**
> So reinstalling nvidia driver fixes it?

For me, it did.

---

### Post by novellahub on 2010-11-19
> **iitywygms said:**
> One other thing that just popped up.
I now notice on standard def tv, a thin area of white lines going down each side of the video.  Right next to the black bars on each side. (Vertical)  Like the lines you sometimes see going across the top of the video image.  The line that looks like crawling ants. (I know it is the extra data broadcast with the video)
Not a big deal, but kind of annoying.
I think I may have jumped to .24 a bit to soon.  Seems a little more buggy that what I am use to.

If you want to get rid of the extra band across the top of the videos, just adjust the overscan settings in nvidia-settings.

---

### Post by iitywygms on 2010-11-19
> **novellahub said:**
> If you want to get rid of the extra band across the top of the videos, just adjust the overscan settings in nvidia-settings.
Thanks, I have done that.  Actually I overscan the tv itself.  But anyway. The ones going down the sides are new.

---

### Post by iitywygms on 2010-11-19
so I noticed that mythmusic no longer has sound.  Anyone else experience this?
Fixed by setting up audio in mythmusic setting to default.

---

### Post by mellery on 2010-12-29
Is there a way to tell if the mythtv updates repo is getting updated?  I haven't gotten any new packages in about a week and want to see if its a problem on my end.

---

### Post by tgm4883 on 2010-12-29
> **mellery said:**
> Is there a way to tell if the mythtv updates repo is getting updated?  I haven't gotten any new packages in about a week and want to see if its a problem on my end.

Packages are only built if there are upstream changes, and there actually haven't been any upstream changes since Dec 20th (this isn't entirely true, there were some in the last 12 hours, but it was after yesterdays build).

You can view upstream 0.24 changes at 

[https://github.com/MythTV/mythtv/commits/fixes/0.24/](https://github.com/MythTV/mythtv/commits/fixes/0.24/)

You can view the packages being built at 

[https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages](https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages)

---

### Post by mellery on 2010-12-29
> **tgm4883 said:**
> Packages are only built if there are upstream changes, and there actually haven't been any upstream changes since Dec 20th (this isn't entirely true, there were some in the last 12 hours, but it was after yesterdays build).

You can view upstream 0.24 changes at 

[https://github.com/MythTV/mythtv/commits/fixes/0.24/](https://github.com/MythTV/mythtv/commits/fixes/0.24/)

You can view the packages being built at 

[https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages](https://edge.launchpad.net/~mythbuntu/+archive/0.24/+packages)

Thanks!  Thats good information.  Upgrading to maverick gave me all kinds of problems with mythtv/apache, and I think I've got them all just about ironed out now.

---

### Post by yonkiman on 2011-02-16
I'm trying to figure out how to get from 0.23.1 to 0.24.  In Mythbuntu Control Centre/Repositories, I have:

<CHECKED> Activate Mythbuntu Autobuilds Repo

0.23.1  US

<CHECKED> Activate Mythbuntu-testing PPA

I used to get daily/frequent updates, but haven't had anything for months and months.  I just checked today and 0.24 is released!  I totally missed that.  But the Control Centre pulldown doesn't have 0.24 - 0.23.1 is as high as it goes?

What's the safest way for me to upgrade?  

Cheers.

---

### Post by yonkiman on 2011-02-16
Nevermind - I just saw (earlier in this thread) that I need a newer version of ubuntu (I'm running 9.04).

---

### Post by koma77 on 2011-03-11
I have a problem with my mythbuntu 10.10 install.

I cannot update it anymore.

When I run sudo apt-get update i get:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 13551B881504888C Launchpad PPA for Mythbuntu Developers

W: Failed to fetch http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas on how to fix this?

---

### Post by tgm4883 on 2011-03-11
> **koma77 said:**
> I have a problem with my mythbuntu 10.10 install.

I cannot update it anymore.

When I run sudo apt-get update i get:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 13551B881504888C Launchpad PPA for Mythbuntu Developers

W: Failed to fetch http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas on how to fix this?

I just checked and that command completes fine here using the same repos. Are you sure it wasn't just a network flub?

---

### Post by Chewiesw on 2011-03-25
I am not sure if this expected behaviour but I am requested/offered to download the same 59MB of updated almost every 2nd day.
 The **LP. PPA - Mythbuntu 0.24 **updates include items like a music addon and a personal video recorder and others. 

Is there something wrong with my install or do I just ignore these updates once i have downloaded them

---

### Post by tgm4883 on 2011-03-25
> **Chewiesw said:**
> I am not sure if this expected behaviour but I am requested/offered to download the same 59MB of updated almost every 2nd day.
 The **LP. PPA - Mythbuntu 0.24 **updates include items like a music addon and a personal video recorder and others. 

Is there something wrong with my install or do I just ignore these updates once i have downloaded them

Are you sure they are the same? There is a new build almost every day

---

### Post by superm1 on 2011-03-25
> **tgm4883 said:**
> Are you sure they are the same? There is a new build almost every day

And if you want to know what's going into each build that changed - look at:

[https://github.com/MythTV/mythtv/commits/fixes%2F0.24](https://github.com/MythTV/mythtv/commits/fixes%2F0.24)

---

### Post by Chewiesw on 2011-03-31
> **superm1 said:**
> And if you want to know what's going into each build that changed - look at:

[https://github.com/MythTV/mythtv/commits/fixes%2F0.24](https://github.com/MythTV/mythtv/commits/fixes%2F0.24)

I am sure, took screenshots this time. The same modules the same size everything

---

### Post by tgm4883 on 2011-03-31
> **Chewiesw said:**
> I am sure, took screenshots this time. The same modules the same size everything

Can you attach the screenshots?

---

### Post by Chewiesw on 2011-03-31
Here we go

 downloaded and installed myhtv upgardes.png then three days later updates.png

---

### Post by tgm4883 on 2011-03-31
> **Chewiesw said:**
> Here we go

 downloaded and installed myhtv upgardes.png then three days later updates.png

Ok, that doesn't give us the full version number. A few questions.

1) What repo did you activate (US, UK, DE, PPA, etc)?
2) Did you actually install the updates?
3) If you select a package and click "description of update" it should show the full version number of the updated package. Please show us screenshots of this information.

---

### Post by letchcj on 2011-04-07
Same problem here, I have had no new builds for a week plus.

---

### Post by tgm4883 on 2011-04-07
> **letchcj said:**
> Same problem here, I have had no new builds for a week plus.

Please explain in detail. Do you mean

A) You are getting the same version as an update every day for the last week? If so, which location did you select and what version?

or

B) You haven't received any updates to MythTV in the last week. If this is the case, what MythTV version did you select? Note that there haven't been any updates to 0.24 since 3-28 and not a new build since 3-30

---

### Post by ktmom on 2011-06-13
Can someone help me understand the process that patches to mythtv go through to get to mythtv fixes?  Specifically I am wondering at what point this [mythtranscode]("https://github.com/MythTV/mythtv/commit/cbf2efa6") patch works it's way down the pipe to those of us aren't willing to compile their own copy of mythtv.

I'm running 10.04 mythbuntu with the .24 fixes PPA

---

### Post by superm1 on 2011-06-13
> **ktmom said:**
> Can someone help me understand the process that patches to mythtv go through to get to mythtv fixes?  Specifically I am wondering at what point this [mythtranscode]("https://github.com/MythTV/mythtv/commit/cbf2efa6") patch works it's way down the pipe to those of us aren't willing to compile their own copy of mythtv.

I'm running 10.04 mythbuntu with the .24 fixes PPA

If there isn't a ticket opened for it already or a lot of people complaining about it, it probably won't go into -fixes generally.

So you can either bug the developers in any of these ways to ask:
1) mythtv-dev mailing list
2) File a ticket at code.mythtv.org requesting it to be backported.

---

### Post by Nikas on 2011-07-10
No builds for .25 for a while?

---

### Post by superm1 on 2011-07-10
> **Nikas said:**
> No builds for .25 for a while?

Ah just checked and it looked like one of the patches needed to be refreshed for changes upstream.  I've refreshed it and tonight's build should kick off again.

Thanks for pointing it out.

---

### Post by Nikas on 2011-07-10
> **superm1 said:**
> Ah just checked and it looked like one of the patches needed to be refreshed for changes upstream.  I've refreshed it and tonight's build should kick off again.

Thanks for pointing it out.

Great! Thanks. :)

---

### Post by tgm4883 on 2011-07-10
> **Nikas said:**
> No builds for .25 for a while?

Looks like the patches are failing to apply. Looking into it.

---

### Post by Nikas on 2011-07-11
> **tgm4883 said:**
> Looks like the patches are failing to apply. Looking into it.

Seems to be working now.
Thanks!

---

### Post by extasy on 2012-02-16
Seem to be some problems with the latest fixes for 0.25. My frontend does not find the ip for the backend even when the frontend and backend is the same mashine. It also seems like Mythtv-common was not updated today (version 2:0.25.0~master.20120215.) that means that mythweb wont install due to decencies.


dpkg -l | grep myth
rc  libmyth-0.24-0                     2:0.25.0~master.20120212.5942398-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.25-0                     2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                     2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A python library to access some MythTV features
ii  libmythtv-perl                     2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A PERL library to access some MythTV features
ii  mythbuntu-bare-client              2.0                                                 Mythbuntu Bare Client
ii  mythbuntu-common                   0.63                                                Mythbuntu application support functions
ii  mythbuntu-control-centre           0.63-0ubuntu2                                       Mythbuntu Configuration Application
ii  mythbuntu-default-settings         1.02                                                default settings for Mythbuntu
ii  mythbuntu-desktop                  0.72                                                The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme            0.9                                                 Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator           0.26-0ubuntu1                                       Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber              0.9-0ubuntu2                                        Mythbuntu diagnostic utility
ii  mythbuntu-repos                    9.3-0ubuntu0+mythbuntu~auto20110703002132           Mythbuntu repository installer
ii  mythtv                             2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
ii  mythtv-backend                     2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (server)
ii  mythtv-backend-master              2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                      2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (common data)
ii  mythtv-database                    2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A personal video recorder application (database)
ii  mythtv-frontend                    2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (client)
ii  mythtv-theme-mythbuntu             2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 The mythbuntu MythTV Theme
ii  mythtv-transcode-utils             2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Utilities used for transcoding MythTV tasks
rc  mythvideo                          2:0.24.0+fixes.20110908.1de0431-0ubuntu1            A generic video player frontend module for MythTV
ii  mythweather                        2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Weather add-on module for MythTV
ii  mythweb                            2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Web interface add-on module for MythTV
ii  php-mythtv                         2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 PHP Bindings for MythTV

---

### Post by extasy on 2012-02-16
I would presume it's this problem:
[http://www.mythtv.org/pipermail/mythtv-users/2012-February/327830.html](http://www.mythtv.org/pipermail/mythtv-users/2012-February/327830.html)

But todays build have not fixed the issue.

---

### Post by superm1 on 2012-02-16
> **extasy said:**
> I would presume it's this problem:
[http://www.mythtv.org/pipermail/mythtv-users/2012-February/327830.html](http://www.mythtv.org/pipermail/mythtv-users/2012-February/327830.html)

But todays build have not fixed the issue.

couple of problems happened.  here's the order:

1) abi change (0.24->0.25).  some libraries are in both packages and threw things off for the first night's autobuild.  you could manually work around this
2) live tv broke (upstream change).  also in that same autobuild
3) mythweb broke due to a patch added for proper paths for some people.  it's not clear why this broke.  for someone having this scenario we need to understand why they are using /var/www/html not /var/www/mythweb (the default)
4) mythweb broke due to broken symlink
5) now last night amd64 failed to build.  this was to fix the symlink problem in mythweb.  live tv was fixed in this build.  abi change was fixed in this build.

so if you're on i386, last night's build should have all the problems fixed.  amd64 should be fixed with tonight's build.

---

### Post by extasy on 2012-02-16
Thanks for clearing it up!

I'm on x64 so that's why I haven't got it working I would presume!

Is it possible for you to just push a x64 build now?? ;) My kids would love being able to watch tv again :)

---

### Post by Nikas on 2012-02-16
> **superm1 said:**
> couple of problems happened.  here's the order:

1) abi change (0.24->0.25).  some libraries are in both packages and threw things off for the first night's autobuild.  you could manually work around this
2) live tv broke (upstream change).  also in that same autobuild
3) mythweb broke due to a patch added for proper paths for some people.  it's not clear why this broke.  for someone having this scenario we need to understand why they are using /var/www/html not /var/www/mythweb (the default)
4) mythweb broke due to broken symlink
5) now last night amd64 failed to build.  this was to fix the symlink problem in mythweb.  live tv was fixed in this build.  abi change was fixed in this build.

so if you're on i386, last night's build should have all the problems fixed.  amd64 should be fixed with tonight's build.

I have looked at the fix and it relies on the "BackendServerIP6" = NULL or "" for livetv. In my and my friends servers the "BackendServerIP6" is set to "::1". The frontend then tries to connect to ::1:6543 and fails so, i had to manually set the BackendServerIP6 to NULL in the database to make the connection work again in i386. My server is amd64 so im waiting for new packages. :-)

Edit: I spoke too soon. Same problem with i386:
"RemoteFile: penSocket(control socket): Could not connect to server :6543
FileRingBuf(myth://:6543/1007_20120217042644.mpg): RingBuffer::RingBuffer(): Failed to open remote file (myth://:6543/1007_20120217042644.mpg)"
Missing IP. Same problem for two of my friends now.

Waiting to try new packages. :)

---

### Post by tgm4883 on 2012-02-16
I just kicked off a new build. If all goes well it should be available within the hour

---

### Post by Nikas on 2012-02-16
> **tgm4883 said:**
> I just kicked off a new build. If all goes well it should be available within the hour

Thanks. LiveTV works again. :)

---

### Post by extasy on 2012-02-17
Thanks! worked as described!

---

### Post by pyrodex on 2012-02-17
In the last few builds of 0.25 debs for libmythtv-perl you are not loading any of the Perl Modules... they come up blank. Can you look into this?

---

### Post by extasy on 2012-03-06
Sorry to say that the problem is back! I can not connect to backend again. Problem was solved but has somehow found its way in. But now it seems like nothing can connect to backend, not even watch recorded shows like last time.

Problem solved!
A friend of mine found the problem, setting ipv6 address to "::1" did the trick!

---

### Post by bergqvistjl on 2012-03-07
The parser for automatically filling in Show titles/season numbers based on the file heirarchy on disc has changed for the worse. I'll use an example. I have my programs stored like this

[TV Series Title] (as a folder) --> Season 01 (folder) --> S01E01.mp4

for example. 

Now, in .24, the video screen would automatically use that to fill in the show title, and season no correctly, meaning I could then scan for metadata and it would fill in the rest (through tvdb)

Unfortunatly, since 0.25, the video screen seems to ignore the overall series title when scanning for videos, so while the heirarchy is preserved, in the info for each video, instead of the title being Frasier for example, the show title for all episodes in season 1, is: Season 1, which means it scans for a TV show called "Season 1" not "Frasier". Just letting you know of this, of course it would probably change for the release.

I hope you understand what I mean :$ I'll post screenshots when I get home over the weekend :)

---

### Post by dheianevans on 2012-04-16
If I choose the mythbuntu repos for .25, am I getting .25-fixes or is there a separate repos for that?

Thanks.

---

### Post by nickrout on 2012-04-16
> **dheianevans said:**
> If I choose the mythbuntu repos for .25, am I getting .25-fixes or is there a separate repos for that?

Thanks.

0.25-fixes.

---

### Post by Paulgirardin on 2012-04-16
> **extasy said:**
> Seem to be some problems with the latest fixes for 0.25. My frontend does not find the ip for the backend even when the frontend and backend is the same mashine. It also seems like Mythtv-common was not updated today (version 2:0.25.0~master.20120215.) that means that mythweb wont install due to decencies.


dpkg -l | grep myth
rc  libmyth-0.24-0                     2:0.25.0~master.20120212.5942398-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.25-0                     2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                     2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A python library to access some MythTV features
ii  libmythtv-perl                     2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A PERL library to access some MythTV features
ii  mythbuntu-bare-client              2.0                                                 Mythbuntu Bare Client
ii  mythbuntu-common                   0.63                                                Mythbuntu application support functions
ii  mythbuntu-control-centre           0.63-0ubuntu2                                       Mythbuntu Configuration Application
ii  mythbuntu-default-settings         1.02                                                default settings for Mythbuntu
ii  mythbuntu-desktop                  0.72                                                The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme            0.9                                                 Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator           0.26-0ubuntu1                                       Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber              0.9-0ubuntu2                                        Mythbuntu diagnostic utility
ii  mythbuntu-repos                    9.3-0ubuntu0+mythbuntu~auto20110703002132           Mythbuntu repository installer
ii  mythtv                             2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
ii  mythtv-backend                     2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (server)
ii  mythtv-backend-master              2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                      2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (common data)
ii  mythtv-database                    2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 A personal video recorder application (database)
ii  mythtv-frontend                    2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 A personal video recorder application (client)
ii  mythtv-theme-mythbuntu             2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 The mythbuntu MythTV Theme
ii  mythtv-transcode-utils             2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Utilities used for transcoding MythTV tasks
rc  mythvideo                          2:0.24.0+fixes.20110908.1de0431-0ubuntu1            A generic video player frontend module for MythTV
ii  mythweather                        2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Weather add-on module for MythTV
ii  mythweb                            2:0.25.0~master.20120215.567278c-0ubuntu0mythbuntu3 Web interface add-on module for MythTV
ii  php-mythtv                         2:0.25.0~master.20120216.2a74313-0ubuntu0mythbuntu3 PHP Bindings for MythTV

I'm seeing the same problem after upgrading on the 15th.

> **extasy said:**
> Sorry to say that the problem is back! I can not connect to backend again. Problem was solved but has somehow found its way in. But now it seems like nothing can connect to backend, not even watch recorded shows like last time.

Problem solved!
A friend of mine found the problem, setting ipv6 address to "::1" did the trick!

This didn't help as it was already set to ::1

If I manually start the BE it works ok.This is on a BE/FE machine.

---

### Post by tgm4883 on 2012-04-16
> **Paulgirardin said:**
> I'm seeing the same problem after upgrading on the 15th.



This didn't help as it was already set to ::1

If I manually start the BE it works ok.This is on a BE/FE machine.

This should really be in a different thread. This thread is for questions and issues regarding mythbuntu-repos (eg. builds not happening, mythbuntu-repos package broken, etc). It sounds like your backend isn't starting at boot.

---

### Post by dheianevans on 2012-04-16
> **nickrout said:**
> 0.25-fixes.

Thanks Nick!

---

### Post by ian dobson on 2012-06-06
Hi,

Are there actually any updates in the 0.25 fixes branch? My backend (ubuntu 12.04 with the mythbuntu repos enabled) doesn't seem to be getting any updates

```
dpkg -l | grep myth
ii  libmyth-0.25-0                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A python library to access some MythTV features
ii  libmythtv-perl                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A PERL library to access some MythTV features
ii  mythbuntu-repos                      9.6-0ubuntu0+mythbuntu                   Mythbuntu repository installer
ii  mythtv-backend                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (server)
ii  mythtv-common                        2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (common data)
ii  mythtv-database                      2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (database)
ii  mythtv-transcode-utils               2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Utilities used for transcoding MythTV tasks
ii  mythweb                              2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Web interface add-on module for MythTV
ii  php-mythtv                           2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 PHP Bindings for MythTV
```

Regards
Ian Dobson

---

### Post by tgm4883 on 2012-06-06
> **ian dobson said:**
> Hi,

Are there actually any updates in the 0.25 fixes branch? My backend (ubuntu 12.04 with the mythbuntu repos enabled) doesn't seem to be getting any updates

```
dpkg -l | grep myth
ii  libmyth-0.25-0                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A python library to access some MythTV features
ii  libmythtv-perl                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A PERL library to access some MythTV features
ii  mythbuntu-repos                      9.6-0ubuntu0+mythbuntu                   Mythbuntu repository installer
ii  mythtv-backend                       2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (server)
ii  mythtv-common                        2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (common data)
ii  mythtv-database                      2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 A personal video recorder application (database)
ii  mythtv-transcode-utils               2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Utilities used for transcoding MythTV tasks
ii  mythweb                              2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 Web interface add-on module for MythTV
ii  php-mythtv                           2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 PHP Bindings for MythTV
```

Regards
Ian Dobson

Yes there are, the latest version in our repos for 12.04 is 

2:0.25.0+fixes.20120605.c2c276d-0ubuntu0mythbuntu4

Is this an upgrade or fresh install of 12.04? Are you sure the repos are activated? Can you check in the mythbuntu file (should be mythbuntu-0_25-precise.list) in /etc/apt/sources.list.d/

---

### Post by ian dobson on 2012-06-06
Hi,

The backend is an upgrade. I started running ubuntu on it at about 8.04 snd upgraded it on every new version.

That looks like the problem:- 

```

cd /etc/apt/sources.list.d/
root@alpha2:/etc/apt/sources.list.d# ls
mythbuntu-repos.list  mythbuntu-repos.list.distUpgrade
root@alpha2:/etc/apt/sources.list.d# cat mythbuntu-repos.list
deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu precise main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main
root@alpha2:/etc/apt/sources.list.d# cat mythbuntu-repos.list.distUpgrade
# deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu precise main # disabled on upgrade to precise
# deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main # disabled on upgrade to precise

```

So how can I change this without using the control center? As the backend doesn't run X.

Regards
Ian Dobson

---

### Post by nickrout on 2012-06-07
amend the file to change 0.24 to 0.25

or ssh -Y backend from a machine running X and then run mythbuntu-control-centre

---

### Post by ian dobson on 2012-06-07
Hi,

Ok edited/created mythbuntu-0_25-precise.list

cat mythbuntu-0_25-precise.list
deb [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu) precise main

and now I get a  "NO_PUBKEY 13551B881504888C" error for  [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: when I do an apt-get update as root.

Regards
Ian Dobson

---

### Post by tgm4883 on 2012-06-07
> **ian dobson said:**
> Hi,

Ok edited/created mythbuntu-0_25-precise.list

cat mythbuntu-0_25-precise.list
deb [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu) precise main

and now I get a  "NO_PUBKEY 13551B881504888C" error for  [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: when I do an apt-get update as root.

Regards
Ian Dobson

remove that, and do

```
apt-add-repository ppa:mythbuntu/0.25
```

---

### Post by ian dobson on 2012-06-07
Hi,

I Just manually added the gpg key and it appears to be working now:-
gpg --keyserver pgpkeys.mit.edu --recv-key  13551B881504888C
gpg -a --export  13551B881504888C | sudo apt-key add -

Regards
Ian Dobson

---

### Post by Threk on 2012-09-30
Where do we need to go to request that MythTV 0.24 be added back to the repositories?

I made the mistake of upgrading my backend to 12.04, and now recordings are failing due to [this bug]("http://code.mythtv.org/trac/ticket/10732#")
which doesn't even look like it's being worked on. It's labeled as minor priority and medium severity --- How can failing to record can be anything less than critical severity!?

Everyone who reported the bug rolled back to 0.24 to fix it, so I rolled back to the previous Ubuntu LTS(10.04) for now but that's not supposed to be supported for much longer.

---

### Post by tgm4883 on 2012-09-30
> **Threk said:**
> Where do we need to go to request that MythTV 0.24 be added back to the repositories?

I made the mistake of upgrading my backend to 12.04, and now recordings are failing due to [this bug]("http://code.mythtv.org/trac/ticket/10732#")
which doesn't even look like it's being worked on. It's labeled as minor priority and medium severity --- How can failing to record can be anything less than critical severity!?

Everyone who reported the bug rolled back to 0.24 to fix it, so I rolled back to the previous Ubuntu LTS(10.04) for now but that's not supposed to be supported for much longer.

We're not going to add 0.24 builds for 12.04, as it shipped with 0.25. Further, there aren't any commits to the 0.24 branch anymore, so you're asking for something that would

A) only amount to a single build
B) require users do a healthy set of work to even get it installed
C) not be used by many users

I skimmed that bug report, did anyone happen to try the 0.26 version?

If you really want 0.24 on 12.04, you could attempt activating the Lucid repo on it (although it would be completely unsupported). Still I would prefer someone at least test it with 0.26.

---

### Post by Threk on 2012-09-30
> **tgm4883 said:**
> We're not going to add 0.24 builds for 12.04, as it shipped with 0.25. Further, there aren't any commits to the 0.24 branch anymore, so you're asking for something that would

A) only amount to a single build
B) require users do a healthy set of work to even get it installed
C) not be used by many users

I skimmed that bug report, did anyone happen to try the 0.26 version?

If you really want 0.24 on 12.04, you could attempt activating the Lucid repo on it (although it would be completely unsupported). Still I would prefer someone at least test it with 0.26.

None of the posts in the bug report even mention 0.26. Although it seems likely to me that the bug will probably have carried forward into 0.26, you're right that it should be tested. 

Since I JUST got my backend running and stable again I'm not going to mess with it right now, but when I get some free time (maybe next weekend) I'll swap some hard drives do a clean 12.04 install and run some tests.

I hadn't even considered the Lucid repo... in the likely case that the bug is still in 0.26 I might give that a try too. (Thanks for the suggestion)

Overall it still sounds to me like sometime within the next year I'm going to need to replace some perfectly good(though admittedly quite old) hardware simply because the software doesn't support it anymore, which is very frustrating.

---

### Post by nickrout on 2012-10-01
I for one am not sure why pvr cards are creating this problem but the fact is that analogue is pretty well dead as a transmission technology. Can still be useful for capturing the output of a stb though. But with the move to hd an hd-pvr is a better solution.

---

### Post by kingmoffa on 2012-10-09
Hi, 

I've been having trouble upgrading from .25 to .26 (sorry didnt use the offical way Myth Control Centre). 

After some messing about I thought I would purge all myth packages and use a mysql backup. 

sudo add-apt-repository ppa:mythbuntu/0.26 
sudo aptitude update
sudo aptitude install mythtv

................

 > Setting up mythtv-backend (2:0.26.0+fixes.20121009.2d2932a-0ubuntu0mythbuntu2) ...
mythtv-backend start/running, process 9636
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mythtv-database (2:0.26.0+fixes.20121009.2d2932a-0ubuntu0mythbuntu2) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv


Note I had removed mythconverg database from mysql so it should be a fresh install.  ( I have a backup)








*** Edit

I found this thread from the mailling list:

[http://www.gossamer-threads.com/lists/mythtv/users/529396](http://www.gossamer-threads.com/lists/mythtv/users/529396)

Editing the file: /var/lib/dpkg/info/mythtv-database.postinst  seemed to help it install.

---

### Post by tgm4883 on 2012-10-09
> **kingmoffa said:**
> Hi, 

I've been having trouble upgrading from .25 to .26 (sorry didnt use the offical way Myth Control Centre). 

After some messing about I thought I would purge all myth packages and use a mysql backup. 

sudo add-apt-repository ppa:mythbuntu/0.26 
sudo aptitude update
sudo aptitude install mythtv

................

 

Note I had removed mythconverg database from mysql so it should be a fresh install.  ( I have a backup)








*** Edit

I found this thread from the mailling list:

[http://www.gossamer-threads.com/lists/mythtv/users/529396](http://www.gossamer-threads.com/lists/mythtv/users/529396)

Editing the file: /var/lib/dpkg/info/mythtv-database.postinst  seemed to help it install.

Few questions.

1) How long have you been trying to upgrade?

2) Does the info in /etc/mythtv/config.xml and ~/.mythtv/config.xml match?

---

### Post by Henk Poley on 2012-12-12
It's probably somewhere in this thread.. but.. 

How do you do repo version selection on mythbuntu 12.04 from the command line over SSH ? As was previously done with mythbuntu-repo. I've just added it by hand in /etc/apt now, but apt and friends keeps complaining about signatures.

Edit: Answer'ish

```
sudo add-apt-repository ppa:mythbuntu/0.26
```

---

### Post by tgm4883 on 2012-12-12
> **Henk Poley said:**
> It's probably somewhere in this thread.. but.. 

How do you do repo version selection on mythbuntu 12.04 from the command line over SSH ? As was previously done with mythbuntu-repo. I've just added it by hand in /etc/apt now, but apt and friends keeps complaining about signatures.

Edit: Answer'ish

```
sudo add-apt-repository ppa:mythbuntu/0.26
```

add-apt-repository is the correct way.

---

### Post by davehill1 on 2012-12-20
Hello,  I'm running Mythbuntu 12.04 running with the 0.25-fixes repos and would like to test 0.26 with a quick & safe way back to 0.25 if I encounter some issues.  I'm a recent Mythdora convert, so please forgive the newbish question -- How does one revert a mythtv upgrade with Mythbuntu?

I'm NOT asking about database backup/restore -- I can handle that.  I'm interested in how to cleanly re-install the 0.25 packages.

I tried this on a frontend that I'm not actively using, after bringing it up to 0.26, I went back to Mythbuntu Control Center and changed my repos back to 0.25, removed the /etc/apt/sources.list.d/mythbuntu-0_26-precise.list*, but when I try to 'apt-get install' the myth packages, it still says they are the newest.  Do I have to first 'apt-get remove' them?

Thank you,
Dave Hill

---

### Post by nickrout on 2012-12-20
Yes remove then reinstall

---

### Post by prasivec on 2013-01-01
hello pleas who date download ne Mythbuntu 12.10 ? thank you :KS

---

### Post by marc.aronson on 2013-01-15
Hi, I am looking for advise on updating. I am new to Mythbuntu but a long-time LINHES / Knoppmyth user. I have successfully done a clean install of mythbuntu 12.04 on a test system and it is working. I have not yet applied any of the pending upgrades -- looks like there are over 200 available, and I haven't even added the mythbuntu repos yet.

Question -- Do people recommend that I apply all those updates, or is the base system, as released, the most stable? Any general thoughts, experiences or philosophies that people apply to the "should I update" question would be appreciated! 

Thanks!

Marc

---

### Post by dannyboy79 on 2013-01-15
> **marc.aronson said:**
> Hi, I am looking for advise on updating. I am new to Mythbuntu but a long-time LINHES / Knoppmyth user. I have successfully done a clean install of mythbuntu 12.04 on a test system and it is working. I have not yet applied any of the pending upgrades -- looks like there are over 200 available, and I haven't even added the mythbuntu repos yet.

Question -- Do people recommend that I apply all those updates, or is the base system, as released, the most stable? Any general thoughts, experiences or philosophies that people apply to the "should I update" question would be appreciated! 

Thanks!

Marc
Yes, I would apply all the updates as it will not only include improvements but most importantly there will be security updates.

---

### Post by jzig on 2013-09-05
I'm running Mythbuntu 12.04 with 0.25 fixes.  I'm planning on upgrading to 0.27 by changing to the 0.27 repos in MCC.  Then running 'apt-get dist-upgrade' from the terminal.

What user should I run 'apt-get dist-upgrade' as?  
Do I need to change things in the "update manager" before running 'apt-get dist-upgrade'?  
Do I need to uncheck the 0.25 repos?
Do I stop the backend first?
Any other advice for the novice?
I'll be doing this on a Clonzilla'd drive so I have a fall back to the original system.
Thanks.

---

### Post by tgm4883 on 2013-09-05
> **jzig said:**
> I'm running Mythbuntu 12.04 with 0.25 fixes.  I'm planning on upgrading to 0.27 by changing to the 0.27 repos in MCC.  Then running 'apt-get dist-upgrade' from the terminal.

What user should I run 'apt-get dist-upgrade' as?  
Do I need to change things in the "update manager" before running 'apt-get dist-upgrade'?  
Do I need to uncheck the 0.25 repos?
Do I stop the backend first?
Any other advice for the novice?
I'll be doing this on a Clonzilla'd drive so I have a fall back to the original system.
Thanks.

Just switch to 0.27 in MCC, do an apt-get update then an apt-get dist-upgrade

---

### Post by jzig on 2013-09-05
OK, Thanks tgm.

So no need to stop the backend first and no need to run as root, just run as what ever user comes up with the terminal window (doing this from the console).
Thanks again.

---

### Post by nickrout on 2013-09-05
> **jzig said:**
> I'm running Mythbuntu 12.04 with 0.25 fixes.  I'm planning on upgrading to 0.27 by changing to the 0.27 repos in MCC.  Then running 'apt-get dist-upgrade' from the terminal.

What user should I run 'apt-get dist-upgrade' as?   root via sudo> 
Do I need to change things in the "update manager" before running 'apt-get dist-upgrade'?no>   
Do I need to uncheck the 0.25 repos?Do you mean in MCC? I believe you can  only tick one at a time, but if you want 0.27 you should certainly untick 0.25> 
Do I stop the backend first?definitely> 
Any other advice for the novice? back up your database using [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore). 0.27 is not relaesed so this is beta code that may break (although many report it working well [http://www.gossamer-threads.com/lists/mythtv/users/551460](http://www.gossamer-threads.com/lists/mythtv/users/551460))> 
I'll be doing this on a Clonzilla'd drive so I have a fall back to the original system.
Thanks.Still backup the database as I said above.

---

### Post by jzig on 2013-09-06
Nickrout: Thanks for the specifics!
I backed up the database and stopped the backend and ran apt-get update and apt-get dist-upgrade.

The upgrade appeared to go fine until near the end.  It finally failed with a "No database selected" error.
I have included the terminal window output from just before the first error.

I don't know how a database should be selected?

I can reclone from the original hard drive, so I don't have to recover gracefully from this error,
but I don't know how change things for the next attempt.
Should I go from 0.25 to 0.26 and then to 0.27 instead of a single jump?
Thanks.

```
ziggy@mythbuntu:~$ sudo apt-get dist-upgrade
[sudo] password for ziggy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libmyth-0.25-0
The following NEW packages will be installed:
  fonts-tlwg-purisa libbit-vector-perl libc6-dbg libdate-calc-perl
  libdate-calc-xs-perl libmyth-0.27-0 mythtv-dbg
The following packages will be upgraded:
  libmyth-python libmythtv-perl mytharchive mythgallery mythmusic mythtv
  mythtv-backend mythtv-backend-master mythtv-common mythtv-database
  mythtv-frontend mythtv-theme-mythbuntu mythtv-transcode-utils mythweather
  mythweb php-mythtv
16 upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 154 MB of archives.
After this operation, 259 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main fonts-tlwg-purisa all 1:0.4.17-1ubuntu1 [374 kB]
Get:2 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-common amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [15.0 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main libbit-vector-perl amd64 7.1-1build2 [164 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/universe libdate-calc-perl all 6.3-1 [209 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main libc6-dbg amd64 2.15-0ubuntu10 [2,876 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/universe libdate-calc-xs-perl amd64 6.2-1build1 [59.1 kB]
Get:7 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-backend amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [1,658 kB]
Get:8 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythmusic amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [1,571 kB]
Get:9 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-transcode-utils amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [265 kB]
Get:10 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythweather amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [968 kB]
Get:11 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-frontend amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [4,957 kB]
Get:12 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythgallery amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [335 kB]
Get:13 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mytharchive amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [14.8 MB]
Get:14 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main libmyth-0.27-0 amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [13.7 MB]
Get:15 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main libmyth-python all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [427 kB]
Get:16 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main libmythtv-perl all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [97.8 kB]
Get:17 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-database all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [115 kB]
Get:18 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [77.4 kB]
Get:19 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-backend-master all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [75.5 kB]
Get:20 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-theme-mythbuntu all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [11.5 MB]
Get:21 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main php-mythtv all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [87.0 kB]
Get:22 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythweb all 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [1,743 kB]
Get:23 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main mythtv-dbg amd64 2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2 [82.7 MB]
Fetched 154 MB in 5min 20s (479 kB/s)                                          
Preconfiguring packages ...
Selecting previously unselected package fonts-tlwg-purisa.
(Reading database ... 146479 files and directories currently installed.)
Unpacking fonts-tlwg-purisa (from .../fonts-tlwg-purisa_1%3a0.4.17-1ubuntu1_all.deb) ...
Preparing to replace mythtv-common 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-common_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythtv-common ...
Preparing to replace mythtv-backend 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-backend_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythtv-backend ...
Preparing to replace mythmusic 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythmusic_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythmusic ...
Preparing to replace mythtv-transcode-utils 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-transcode-utils_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythtv-transcode-utils ...
Preparing to replace mythweather 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythweather_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythweather ...
Preparing to replace mythtv-frontend 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-frontend_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythtv-frontend ...
Preparing to replace mythgallery 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythgallery_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mythgallery ...
Preparing to replace mytharchive 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mytharchive_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Unpacking replacement mytharchive ...
Processing triggers for fontconfig ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
(Reading database ... 146553 files and directories currently installed.)
Removing libmyth-0.25-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package libmyth-0.27-0.
(Reading database ... 146503 files and directories currently installed.)
Unpacking libmyth-0.27-0 (from .../libmyth-0.27-0_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Preparing to replace libmyth-python 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../libmyth-python_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement libmyth-python ...
Selecting previously unselected package libbit-vector-perl.
Unpacking libbit-vector-perl (from .../libbit-vector-perl_7.1-1build2_amd64.deb) ...
Selecting previously unselected package libdate-calc-perl.
Unpacking libdate-calc-perl (from .../libdate-calc-perl_6.3-1_all.deb) ...
Selecting previously unselected package libc6-dbg.
Unpacking libc6-dbg (from .../libc6-dbg_2.15-0ubuntu10_amd64.deb) ...
Selecting previously unselected package libdate-calc-xs-perl.
Unpacking libdate-calc-xs-perl (from .../libdate-calc-xs-perl_6.2-1build1_amd64.deb) ...
Preparing to replace libmythtv-perl 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../libmythtv-perl_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement libmythtv-perl ...
Preparing to replace mythtv-database 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-database_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement mythtv-database ...
Preparing to replace mythtv 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement mythtv ...
Preparing to replace mythtv-backend-master 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-backend-master_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement mythtv-backend-master ...
Preparing to replace mythtv-theme-mythbuntu 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythtv-theme-mythbuntu_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement mythtv-theme-mythbuntu ...
Preparing to replace php-mythtv 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../php-mythtv_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement php-mythtv ...
Preparing to replace mythweb 2:0.25.2+fixes.20120911.cf06841-0ubuntu0mythbuntu4 (using .../mythweb_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_all.deb) ...
Unpacking replacement mythweb ...
Selecting previously unselected package mythtv-dbg.
Unpacking mythtv-dbg (from .../mythtv-dbg_2%3a0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up fonts-tlwg-purisa (1:0.4.17-1ubuntu1) ...
Setting up libmyth-0.27-0 (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythtv-common (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Installing new version of config file /etc/rsyslog.d/40-mythtv.conf ...
Setting up mythtv-transcode-utils (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythtv-backend (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Installing new version of config file /etc/init/mythtv-backend.conf ...
mythtv-backend start/running, process 4999
Setting up libmyth-python (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythtv-frontend (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythmusic (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up libbit-vector-perl (7.1-1build2) ...
Setting up libdate-calc-perl (6.3-1) ...
Setting up mythweather (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythgallery (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mytharchive (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up libc6-dbg (2.15-0ubuntu10) ...
Setting up libdate-calc-xs-perl (6.2-1build1) ...
Setting up libmythtv-perl (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythtv-database (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up mythtv-theme-mythbuntu (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up php-mythtv (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Setting up mythweb (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Setting up mythtv-dbg (2:0.27.0+fixes.20130906.e8093db-0ubuntu0mythbuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mythtv-database
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)
ziggy@mythbuntu:~$ 

```
It asked if I wanted to submit an automated crash report so I did.  There might be more info under Bug #1221735
[https://bugs.launchpad.net/mythbuntu/+bug/1221735](https://bugs.launchpad.net/mythbuntu/+bug/1221735)

---

### Post by tgm4883 on 2013-09-06
I've commented on the bug. Basically, you need to fix /etc/mythtv/config.xml

---

### Post by jzig on 2013-09-06
tgm, you are right, thanks.  It looks like my config.xml is not  populated at all!  I will populate it with what I find in mysql.txt and  see what happens.

---

### Post by jzig on 2013-09-06
Thanks TGM for getting me pointed in the right direction...
OK, there were 2 files named config.xml on the system.
/etc/mythtv/config.xml  and
/home/ziggy/.mythtv/config.xml

/etc/mythtv/config.xml was mostly unpopulated.

/home/ziggy/.mythtv/config.xml looked like it had all the data in it, although there are different sub-sections.

I just copied /home/ziggy/.mythtv/config.xml into /etc/mythtv/ and reran 'apt-get dist-upgrade'.  It completed without errors and the system seems to be running fine now.

Seems like some processes of Myth use one location and other processes use the other?
This was originally a clean install of 12.04.1 and 0.25 with no updates a year or two ago. And then upgraded directly to 0.27.

As you can see, the formats and contents of the 2 files were quite different.  Is there any way to know what all the proper contents should be? And are both locations important?  And should both locations be identical or do they serve different purposes?  Just curious now.

/etc/mythtv/config.xml
```
<Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host></Host>
    <UserName></UserName>
    <Password>5nlGPENB</Password>
    <DatabaseName></DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```


/home/ziggy/.mythtv/config.xml
```
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>U740CP5r</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
    <UDN>
      <MediaRenderer>{c0fecaf3-6fd3-4d65-9fa7-c13d5aae576</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>

```

---

### Post by jzig on 2013-09-06
Well I thought everything was working after the 0.27 upgrade... Mythweb doesn't respond, so I'm looking into that.  Webmin works however.

---

### Post by jzig on 2013-09-08
Mythweb didn't work because it picked up bad database info (name and password) from the incorrect /etc/mythtv/config.xml.  to correct that manually, edit /etc/apache2/sites-available/mythweb.conf and add the database name and password.

Looking back at the original drive before trying to upgrade, it turns out that the file /etc/mythtv/config.xml existed but was a file of zero length, causing the upgrade to produce a non-working /etc/mythtv/config.xml.  Then when the upgrade gets to installing the 0.27 mythtvbackend package it fails with a "no database selected" error and halts the upgrade at that point leaving things in a non working state.

I have no idea why /etc/mythtv/config.xml was zero length.  There is a valid config.xml at /home/ziggy/.mythtv/config.xml.  Copying this file to /etc/mythtv/config.xml before trying to upgrade to 0.27 allows an upgrade to go to completion.

I have tried clean installs from the same media used originally and they produce /etc/mythtv/config.xml with proper settings.  Some upgrade or configuration over the past year must have caused that file to be recreated with no contents.?.

Perhaps doing a sanity check on /etc/mythtv/config.xml before starting a 0.27 upgrade would be a good idea to prevent an upgrade failure.

---

### Post by williammanda on 2013-09-23
Is it possible to get mythtv 0.27 fixes from MythTV-Updates repository if Mythtv was not installed via mythbuntu? I have Ubuntu 13.10 with Mythtv 0.27 and would like to get the updates. Please advise.
Thanks

---

### Post by tgm4883 on 2013-09-23
> **williammanda said:**
> Is it possible to get mythtv 0.27 fixes from MythTV-Updates repository if Mythtv was not installed via mythbuntu? I have Ubuntu 13.10 with Mythtv 0.27 and would like to get the updates. Please advise.
Thanks

yes, you can do this the same way as any other supported Ubuntu release. See the graphic here [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by williammanda on 2013-09-23
I'm alittle confused....
I went to the site:

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) 

and the only option I could see to use was the "Install the Mythbuntu-repos package" by downloading this .deb file:

mythbuntu-repos.deb

at this url:

[https://sites.google.com/a/mythbuntu.org/website/repos/mythbuntu-repos.deb?attredirects=0](https://sites.google.com/a/mythbuntu.org/website/repos/mythbuntu-repos.deb?attredirects=0)

since I don't have Mythbuntu control centre installed because it doesn't work beyond 12.10. The install failed via the software center. Can I just get the ppa's that I can install into the repositories? or what else do I need to do?
Thanks

---

### Post by tgm4883 on 2013-09-24
> **williammanda said:**
> I'm alittle confused....
I went to the site:

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) 

and the only option I could see to use was the "Install the Mythbuntu-repos package" by downloading this .deb file:

mythbuntu-repos.deb

at this url:

[https://sites.google.com/a/mythbuntu.org/website/repos/mythbuntu-repos.deb?attredirects=0](https://sites.google.com/a/mythbuntu.org/website/repos/mythbuntu-repos.deb?attredirects=0)

since I don't have Mythbuntu control centre installed because it doesn't work beyond 12.10. The install failed via the software center. Can I just get the ppa's that I can install into the repositories? or what else do I need to do?
Thanks

You can enable it from the command line via 

```
sudo apt-add-repository ppa:mythbuntu/0.27
```

---

### Post by williammanda on 2013-09-24
How would I get the gpg key?

---

### Post by tgm4883 on 2013-09-24
> **williammanda said:**
> How would I get the gpg key?

It should be downloaded with that command.

---

### Post by griggs2 on 2013-10-06
I'm on MythBuntu 12.04.3 LTS, using MythTV 0.26.

When I change the Repos setting in MCC to 0.27 I get the warning that 0.27 is still in development, yet the MythTV website lists 0.27 as having been released as of Sept 18, 2013.

So two questions -
     1) Am I OK to go ahead and update to 0.27, or should I wait a bit longer?
     2) Is the MythBuntu MCC going to be changed/updated so that it doesn't give that warning any more?

Thanks!

---

### Post by novellahub on 2013-10-07
> **griggs2 said:**
> I'm on MythBuntu 12.04.3 LTS, using MythTV 0.26.

When I change the Repos setting in MCC to 0.27 I get the warning that 0.27 is still in development, yet the MythTV website lists 0.27 as having been released as of Sept 18, 2013.

So two questions -
     1) Am I OK to go ahead and update to 0.27, or should I wait a bit longer?
     2) Is the MythBuntu MCC going to be changed/updated so that it doesn't give that warning any more?

Thanks!

There is a refresh button in the MCC near where you select the Mythtv release you want. I had to refresh first and then select 0.27.

---

### Post by griggs2 on 2013-10-07
> **novellahub said:**
> There is a refresh button in the MCC near where you select the Mythtv release you want. I had to refresh first and then select 0.27.

Oh, I can change to the 0.27 Repo, that's not the problem - I just get the warning that it's still in Dev state (when in fact it's been recently changed to a "Released" state.)

./iz

---

### Post by tgm4883 on 2013-10-08
> **griggs2 said:**
> Oh, I can change to the 0.27 Repo, that's not the problem - I just get the warning that it's still in Dev state (when in fact it's been recently changed to a "Released" state.)

./iz

If you hit the 'refresh' button, it downloads a new release file and then it doesn't say it's in Dev state anymore.

---

### Post by griggs2 on 2013-10-09
> **tgm4883 said:**
> If you hit the 'refresh' button, it downloads a new release file and then it doesn't say it's in Dev state anymore.

<face palm mode on> Stupid! Stupid! Stupid! <face palm mode off>

Well now don't I feel like an idiot!?

Thanks for the "secret" button push! 

I'll crawl back under the sheets now and hide myself in shame.

Thanks!

---

### Post by l-sdt on 2015-04-27
Is 12.04 still supported, or has it now reached end-of-life?

I notice that [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/precise/main/binary-i386/Packages) is still at 2:0.27.4+fixes.20150418.7860e91, while [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/trusty/main/binary-i386/Packages) has been updated to 2:0.27.4+fixes.20150426.bcdaa88.

The reason I ask is that the current precise package has a rather major mythwelcome bug ([https://code.mythtv.org/trac/ticket/12441](https://code.mythtv.org/trac/ticket/12441)) which has apparently been fixed in the 20150426 build.

---

### Post by l-sdt on 2015-04-28
I didn't realise how old this thread was :)

Reports of the death of 12.04 have been greatly exaggerated - a new set of packages got built yesterday. Thanks all!

---

### Post by melben on 2016-03-10
How often is the 0.28 repo built for trusty?

I've installed 0.28 and have a few issues I might submit bug reports for, but it would be nice if there were regular builds to see if the issues have already been fixed, or to confirm quickly once a fix has been put in place.

Thanks
Ben

---

### Post by tgm4883 on 2016-03-10
> **melben said:**
> How often is the 0.28 repo built for trusty?

I've installed 0.28 and have a few issues I might submit bug reports for, but it would be nice if there were regular builds to see if the issues have already been fixed, or to confirm quickly once a fix has been put in place.

Thanks
Ben

It's built daily, as long as there is an upstream change.

---

### Post by melben on 2016-03-10
> **tgm4883 said:**
> It's built daily, as long as there is an upstream change.

I don't really know which branch I should be looking at but when I look at the MythTV Commits list:
[http://www.gossamer-threads.com/lists/mythtv/commits/](http://www.gossamer-threads.com/lists/mythtv/commits/)

and the recent closed tickets:
[https://code.mythtv.org/trac/report/14](https://code.mythtv.org/trac/report/14)

there seems to be commits after the 7th, but that's the last time it was built.

The commits are for "fixes/0.28" and "master".

Is this just a timing thing, or am I not understanding how this works.

I'm not in a hurry for any of these particular fixes, just want to understand how things happen.

Thanks
Ben

---

### Post by tgm4883 on 2016-03-13
> **melben said:**
> I don't really know which branch I should be looking at but when I look at the MythTV Commits list:
[http://www.gossamer-threads.com/lists/mythtv/commits/](http://www.gossamer-threads.com/lists/mythtv/commits/)

and the recent closed tickets:
[https://code.mythtv.org/trac/report/14](https://code.mythtv.org/trac/report/14)

there seems to be commits after the 7th, but that's the last time it was built.

The commits are for "fixes/0.28" and "master".

Is this just a timing thing, or am I not understanding how this works.

I'm not in a hurry for any of these particular fixes, just want to understand how things happen.

Thanks
Ben

Just had a minute to look at this and it looks like it broke when we added ARM64 builds. (The builds were still working, but weren't getting moved to the right location) I've just commited a fix for this and hope to see the new builds there in a few minutes

---

### Post by melben on 2016-03-13
yes, that's looking better. Thanks.

---

### Post by MBEeng on 2016-06-19
I am running Mythbuntu 0.27 on Ubuntu 12.04 LTS.  If I upgrade to 0.28 via the update repo, will it automatically upgrade to Ubuntu 14.04 LTS, or is it a two-step process?  Are there any problems with the 0.28 upgrade?

---

### Post by gottabefoss on 2016-06-21
> **MBEeng said:**
> I am running Mythbuntu 0.27 on Ubuntu 12.04 LTS.  If I upgrade to 0.28 via the update repo, will it automatically upgrade to Ubuntu 14.04 LTS, or is it a two-step process?  Are there any problems with the 0.28 upgrade?

I'm not 100% sure if .28 works on 12.04 LTS. But regardless, updating to .28 mythtv doesn't upgrade mythbuntu. That's a completely separate process.

FWIW, I upgraded to .28 on 14.04 LTS and it was pretty smooth. But be sure to backup your database before installing just in case.

---

