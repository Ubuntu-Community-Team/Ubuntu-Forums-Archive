---
title: "Unable To Upgrade To MythTV 0.28 on 14.04"
date: 2016-04-22
forum: Mythbuntu
---

### Post by Windisch on 2016-04-22
I'm having an issue trying to upgrade to 0.28.  When I attempt an upgrade, I am given the following output:

Calculating upgrade... Done
The following packages have been kept back:
  mytharchive mythbrowser mythgallery mythgame mythmusic mythnetvision
  mythnews mythtv-backend mythtv-common mythtv-dbg mythtv-frontend
  mythtv-transcode-utils mythweather mythweb

The following packages will be upgraded:
  libmyth-python libmythtv-perl mythtv mythtv-backend-master mythtv-database
  mythtv-theme-mythbuntu php-mythtv

7 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

The current installed Myth packages appear to be 2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3.

Is there something I should look at to resolve the issue?  A package installed that I need to remove?

Thanks,
  Adam

---

### Post by tgm4883 on 2016-04-22
> **Windisch said:**
> I'm having an issue trying to upgrade to 0.28.  When I attempt an upgrade, I am given the following output:

Calculating upgrade... Done
The following packages have been kept back:
  mytharchive mythbrowser mythgallery mythgame mythmusic mythnetvision
  mythnews mythtv-backend mythtv-common mythtv-dbg mythtv-frontend
  mythtv-transcode-utils mythweather mythweb

The following packages will be upgraded:
  libmyth-python libmythtv-perl mythtv mythtv-backend-master mythtv-database
  mythtv-theme-mythbuntu php-mythtv

7 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

The current installed Myth packages appear to be 2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3.

Is there something I should look at to resolve the issue?  A package installed that I need to remove?

Thanks,
  Adam

When you upgrade major mythtv versions (eg. 0.27 to 0.28) you need to do

```
apt-get dist-upgrade
```

because it needs to install additional packages.

---

### Post by Windisch on 2016-04-22
Thanks for the reply.  I don't see the same errors when I run it, so I will give it a shot after it's done recording shows for the night.

---

### Post by Windisch on 2016-04-23
I ran into an issue when trying to do the dist-upgrade 

Preparing to unpack .../mythtv-frontend_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb ...Unpacking mythtv-frontend (2:0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5) over (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
Preparing to unpack .../mythtv-backend_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb ...
mythtv-backend stop/waiting
Unpacking mythtv-backend (2:0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5) over (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/mythtv-backend_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/share/mythtv/html/js/jquery.min.js', which is also in package mythtv-common 2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3
mythtv-backend start/running, process 5774
dpkg: considering deconfiguration of mythtv-backend, which would be broken by installation of mythtv-common ...
dpkg: yes, will deconfigure mythtv-backend (broken by mythtv-common)
Preparing to unpack .../mythtv-common_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb ...
De-configuring mythtv-backend (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
mythtv-backend stop/waiting
Unpacking mythtv-common (2:0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5) over (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
Preparing to unpack .../mythnews_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb ...
Unpacking mythnews (2:0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5) over (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
Preparing to unpack .../mythmusic_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb ...
Unpacking mythmusic (2:0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5) over (2:0.27.6+fixes.20160408.815cab6-0ubuntu0mythbuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-backend_2%3a0.28.0+fixes.20160422.eeac182-0ubuntu0mythbuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on this error?

---

### Post by clueo8 on 2016-04-28
I got this error too.  A few things to mention:

1.  Did you stop the backend before attempting the upgrade?  I would ensure its stopped before upgrading.
2.  Try running ```
sudo apt-get dist-upgrade
```again, I believe it will tell you to try and run something like ```
sudo apt-get install -f
```.

I'm not 100% sure if the install -f was the last thing I ran, but I ran another dist-upgrade again just to ensure that there was nothing left to install, and I was good to go!

---

### Post by Windisch on 2016-04-28
Looks like that may have done the trick.  I panicked when I saw all of the dependency errors and reverted to my snapshot last time.  Thanks for your help guys![**[COLOR=#DD4814][B][URL="http://ubuntuforums.org/member.php?u=41297"][B][COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=191664")[/B][/COLOR][/B][/URL]

---

### Post by simon130 on 2016-04-29
I am on ubuntu 14.04 as well, may I ask where you got the mythtv-frontend 0.28 from? Did you add some special PPA repository?
The package version on trusty seems to be 0.27:
[http://packages.ubuntu.com/search?keywords=mythtv-frontend&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=mythtv-frontend&searchon=names&suite=all&section=all)
I would like to upgrad to mythtv 0.28 as well.

---

### Post by clueo8 on 2016-04-29
[http://www.ubuntuupdates.org/ppa/mythtv_0.28]("http://www.ubuntuupdates.org/ppa/mythtv_0.28")

---

### Post by simon130 on 2016-04-29
thanks

---

