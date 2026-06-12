---
title: "Fail to install digikam on Ubuntu 13.04"
date: 2013-04-29
forum: Multimedia Software
---

### Post by lallalla on 2013-04-29
I recently upgraded Ubuntu 12.10 to 13.04 and this messed up my digikam installation.

I had installed digikam 3.1 on Ubuntu 12.10 following this recipe, which worked out of the box.
[http://dia-scan.blogspot.co.uk/2013/03/how-to-compile-digikam-31-on-ubuntu-1204.html](http://dia-scan.blogspot.co.uk/2013/03/how-to-compile-digikam-31-on-ubuntu-1204.html)

After upgrading to 13.04 the software centre tells me that digikam is not installed. Trying to install digikam via the software centre produces this error: Package operation failed

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 253499 files and directories currently installed.) 
Unpacking libkface-data (from .../libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb (--unpack): 
 trying to overwrite '/usr/share/kde4/apps/libkface/haarcascades/haarcascade_frontalface_alt2.xml', which is also in package digikam3.1 20130330-1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking libkface1 (from .../libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libkface.so.1.0.0', which is also in package digikam3.1 20130330-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
No apport report written because MaxReports is reached already
Unpacking libkgeomap-data (from .../libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb (--unpack): 
 trying to overwrite '/usr/share/locale/sk/LC_MESSAGES/libkgeomap.mo', which is also in package digikam3.1 20130330-1 
No apport report written because MaxReports is reached already
Unpacking libkgeomap1 (from .../libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libkgeomap.so.1.0.0', which is also in package digikam3.1 20130330-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
No apport report written because MaxReports is reached already
Unpacking digikam-data (from .../digikam-data_4%3a3.1.0-0ubuntu1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/digikam-data_4%3a3.1.0-0ubuntu1_all.deb (--unpack): 
 trying to overwrite '/usr/share/locale/sk/LC_MESSAGES/digikam.mo', which is also in package digikam3.1 20130330-1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking digikam (from .../digikam_4%3a3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/digikam_4%3a3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/digikam', which is also in package digikam3.1 20130330-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
No apport report written because MaxReports is reached already
Unpacking libkvkontakte1 (from .../libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libkvkontakte.so.1.0.0', which is also in package digikam3.1 20130330-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
No apport report written because MaxReports is reached already
Unpacking libmediawiki1 (from .../libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libmediawiki.so.1.0.0', which is also in package digikam3.1 20130330-1 
No apport report written because MaxReports is reached already
Unpacking kipi-plugins-common (from .../kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb (--unpack): 
 trying to overwrite '/usr/share/applications/kde4/kipiplugins.desktop', which is also in package digikam3.1 20130330-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
No apport report written because MaxReports is reached already
Unpacking kipi-plugins (from .../kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/bin/scangui', which is also in package digikam3.1 20130330-1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb 
 /var/cache/apt/archives/libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb 
 /var/cache/apt/archives/libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/digikam-data_4%3a3.1.0-0ubuntu1_all.deb 
 /var/cache/apt/archives/digikam_4%3a3.1.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb 
 /var/cache/apt/archives/kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb 
Error in function: 


Trying to install via the terminal results in this error

sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  digikam-data kipi-plugins kipi-plugins-common libkface-data libkface1
  libkgeomap-data libkgeomap1 libkvkontakte1 libmediawiki1
Suggested packages:
  digikam-doc gallery kmail vorbis-tools
The following NEW packages will be installed
  digikam digikam-data kipi-plugins kipi-plugins-common libkface-data
  libkface1 libkgeomap-data libkgeomap1 libkvkontakte1 libmediawiki1
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.4 MB of archives.
After this operation, 92.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 253499 files and directories currently installed.)
Unpacking libkface-data (from .../libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/libkface/haarcascades/haarcascade_frontalface_alt2.xml', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libkface1 (from .../libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libkface.so.1.0.0', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    Unpacking libkgeomap-data (from .../libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/sk/LC_MESSAGES/libkgeomap.mo', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    Unpacking libkgeomap1 (from .../libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libkgeomap.so.1.0.0', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking digikam-data (from .../digikam-data_4%3a3.1.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/digikam-data_4%3a3.1.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/sk/LC_MESSAGES/digikam.mo', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package digikam.
Unpacking digikam (from .../digikam_4%3a3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/digikam_4%3a3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/digikam', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libkvkontakte1 (from .../libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libkvkontakte.so.1.0.0', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libmediawiki1 (from .../libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libmediawiki.so.1.0.0', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    Unpacking kipi-plugins-common (from .../kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/applications/kde4/kipiplugins.desktop', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking kipi-plugins (from .../kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/scangui', which is also in package digikam3.1 20130330-1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/libkface-data_1.0~digikam3.1.0-0ubuntu1_all.deb
 /var/cache/apt/archives/libkface1_1.0~digikam3.1.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libkgeomap-data_1.0~digikam3.1.0-0ubuntu1_all.deb
 /var/cache/apt/archives/libkgeomap1_1.0~digikam3.1.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/digikam-data_4%3a3.1.0-0ubuntu1_all.deb
 /var/cache/apt/archives/digikam_4%3a3.1.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libkvkontakte1_1.0~digikam3.1.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libmediawiki1_1.0~digikam3.1.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/kipi-plugins-common_4%3a3.1.0-0ubuntu1_all.deb
 /var/cache/apt/archives/kipi-plugins_4%3a3.1.0-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help in sorting this problem will be greatly appreciated. Thanks!

---

### Post by lallalla on 2013-05-01
any takers? Thanks!

---

### Post by monkeybrain2012 on 2013-05-01
Well I never do any "upgrade", I always do fresh install and one of the reasons is that you need to have a fairly "pristine" system to upgrade successfully. So if you have installed things from PPAs or other ways outside the official repo (sounds like your case), or proprietary driver your upgrade may be messed up. They used to advise people to disable all ppas (and restore the applications to the repo version?) and uninstall the proprietary drivers before you do the upgrade, I don't know if this is still the case.

---

### Post by sudodus on 2013-05-01
I use digikam in 12.04. I have beta tested Lubuntu 13.04, but I have not migrated my main system. Usually several bugs will appear during the first month of a new version. The original testing (alpha, beta, release candidate) is focusing on the default packages, installation and upgrading. To use packages between flavours should work, but the debugging comes later on.

First try to update your system

```
sudo apt-get update && sudo apt-get upgrade
```

then try again to install ```
sudo apt-get install digikam
```

If you still have problems, it would be nice if you report a bug about it. If no automatic bug reporting tool shows up, you can run

```
 sudo apport-bug digikam
```

and try to add a description manually.

---

### Post by monkeybrain2012 on 2013-05-01
I think you have to clean up all your digikam 3.1 files manually first. Or, perhaps less painfully, to try installing digikam again using the link so that perhaps the new files will overwrite the broken old ones if the directory structure of 13.04 is the same. I don't know if this will work, just taking a stab, but it doesn't seem to involve any risk.If it doesn't work you should get an error when you do "sudo  checkinstall" in the last step and you can just remove the build folder which should be in your $Home (But I can be wrong, so do it at your own risk. :))

---

### Post by lallalla on 2013-05-01
Thanks for your reply! I tried installing via terminal before and received the same error message. Submitted bug report.

---

### Post by lallalla on 2013-05-01
Tried installing using the mentioned link but that failed as well. I will remove files manually as you suggested and see what happens. Cross fingers this does not end up requiring a full OS reinstallation....... Thanks!

---

### Post by monkeybrain2012 on 2013-05-01
> **lallalla said:**
> Thanks for your reply! I tried installing via terminal before and received the same error message. Submitted bug report.

It is not really a bug for digitkam, but you have messed up your packaging system with the upgrade apparently.

---

