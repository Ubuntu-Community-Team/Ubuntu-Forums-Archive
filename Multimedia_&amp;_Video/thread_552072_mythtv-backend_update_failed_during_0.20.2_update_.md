---
title: "mythtv-backend update failed during 0.20.2 update for Schedules Direct"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by mb12345 on 2007-09-16
I am running a clean Feisty Fawn installation of Kubuntu, and have had MythTV running perfectly since Edgy.  I signed up for Schedules Direct and went to update my MythTV setup today to handle that.  The Adept Notifier noticed the new MythTV packages, and so I chose to upgrade them to the latest version.  During the update, I received an error on the installation of mythtv-backend.  So I attempted the update via the command line and received the following error:

====================================
The following packages will be upgraded:
  mythtv-backend mythtv-common mythtv-database mythtv-frontend
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
Need to get 0B/7693kB of archives.
After unpacking 28.7kB disk space will be freed.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 170662 files and directories currently installed.)
Preparing to replace mythtv-frontend 0.20-svn20070122-0.0ubuntu6 (using .../mythtv-frontend_0.20.2-0ubuntu0.7.04.1_i386.deb) ...
Unpacking replacement mythtv-frontend ...
Preparing to replace mythtv-database 0.20-svn20070122-0.0ubuntu6 (using .../mythtv-database_0.20.2-0ubuntu0.7.04.1_all.deb) ...
Unpacking replacement mythtv-database ...
Preparing to replace mythtv-backend 0.20-svn20070122-0.0ubuntu6 (using .../mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb) ...
Stopping MythTV server: mythbackend invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping MythTV server: mythbackend invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting MythTV server: mythbackendmythbackend: error while loading shared libraries: libmythtv-0.20.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace mythtv-common 0.20-svn20070122-0.0ubuntu6 (using .../mythtv-common_0.20.2-0ubuntu0.7.04.1_all.deb) ...
Unpacking replacement mythtv-common ...
Errors were encountered while processing:
 /var/cache/apt/archives/mythtv-backend_0.20.2-0ubuntu0.7.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
====================================

I have tried everything I can think of, including reinstalling the previous svn versions and installing one package at a time.  I've tried reinstalling the svn version of libmyth I had running and then reinstalling as above, to the same error.  I've tried updating libmyth first, and then running the above update, and get the same error.  (BTW, libmyth and all the plugins were already at the latest 7.04 version from so many attempts at fixing this issue, hence why they did not appear in my screenshot above as requiring an update).   

Here is where all my packages currently stand:

====================================
# dpkg --list "*myth*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
iU  libmyth-0.20                      0.20.2-0ubuntu0.7.04.1            Common library code for MythTV and add-on modules (runtime)
ii  mytharchive                       0.20.2-0ubuntu0.7.04              create and burn DVD's from MythTV - binary file
ii  mytharchive-data                  0.20.2-0ubuntu0.7.04              create and burn DVD's from MythTV - data files
ii  mythbrowser                       0.20.2-0ubuntu0.7.04              A small web browser module for MythTV
ii  mythcontrols                      0.20.2-0ubuntu0.7.04              External controls for MythTV
ii  mythdvd                           0.20.2-0ubuntu0.7.04              DVD add-on module for MythTV
ii  mythflix                          0.20.2-0ubuntu0.7.04              netflix module for MythTV
ii  mythgallery                       0.20.2-0ubuntu0.7.04              Image gallery/slideshow add-on module for MythTV
ii  mythgame                          0.20.2-0ubuntu0.7.04              Emulator & PC Game frontend module for MythTV
ii  mythmusic                         0.20.2-0ubuntu0.7.04              Music add-on module for MythTV
ii  mythnews                          0.20.2-0ubuntu0.7.04              An RSS feed news reader module for MythTV
ii  mythphone                         0.20.2-0ubuntu0.7.04              a phone and videophone module for MythTV
ii  mythplugins                       0.20.2-0ubuntu0.7.04              Wrapper package for MythTV plugins
un  mythtv                            <none>                            (no description available)
iFR mythtv-backend                    0.20-svn20070122-0.0ubuntu6       A personal video recorder application (server)
iU  mythtv-common                     0.20.2-0ubuntu0.7.04.1            A personal video recorder application (common data)
iU  mythtv-database                   0.20.2-0ubuntu0.7.04.1            A personal video recorder application (database)
un  mythtv-doc                        <none>                            (no description available)
iU  mythtv-frontend                   0.20.2-0ubuntu0.7.04.1            A personal video recorder application (client)
ii  mythtv-themes                     0.20-0.1                          Additional themes for MythTV
ii  mythvideo                         0.20.2-0ubuntu0.7.04              A generic video player frontend module for MythTV
ii  mythweather                       0.20.2-0ubuntu0.7.04              Weather add-on module for MythTV
ii  mythweb                           0.20.2-0ubuntu0.7.04              Web interface add-on module for MythTV
====================================

Does anyone have any suggestions for how to fix this?  All of the mythtv 0.20.2 packages seem to upgrade fine, except mythtv-backend.  I've tried everything I can think of, using all the combinations of older svn and newest 0.20.2 packages, and I can't seem to find anything that works.  I'm not sure why the upgrade can't seem to stop the mythtv-backend service, as the error indicates, nor why it cannot restart it.  Any and all suggestions would be greatly appreciated, as now I don't have a working pvr, and obviously old zap2it data is just about gone.

Thanks!

Mike

---

### Post by mb12345 on 2007-09-16
I solved the problem.  The issue was that, for whatever reason, the preinstall script located in /var/lib/dpkg/info/mythtv-backend.prerm simply didn't work.  So I commented out the entire file (it was basically just checked to see if the backed was running, and stopped it if it was), and the upgrade ran cleanly.  All is well again!

---

