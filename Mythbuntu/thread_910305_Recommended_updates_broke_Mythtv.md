---
title: "Recommended updates broke Mythtv"
date: 2008-09-04
forum: Mythbuntu
---

### Post by se99paj on 2008-09-04
Last night I decided to download a list of updates, as I run mythtv all the time I hardly ever go to the desktop and see the updates so thought I'd do it last night.

After a quick reboot the updates have crippled Mythtv, the front end cannot connect to the backend and when I try and run mythsetup it tells me that the backend is still running even after stopping it using the command line.

Also as the PC kept freezing I had to do a few reboots, somehow this caused my single user job to become 7 jobs all doing the same thing, and I can't cancel any of them.

I'm going to try and let the jobs finish this evening, then I can take a better look at the backend logs. I'll post the logs on here later tonight.

---

### Post by superm1 on 2008-09-04
If you can identify which update(s) are causing this, it would be most beneficial so we could either yank them or figure out what happened.

---

### Post by se99paj on 2008-09-04
These are the updates that I installed:

Commit Log for Wed Sep  3 20:38:34 2008
Upgraded the following packages:
eject (2.1.5-6) to 2.1.5-6ubuntu1
libgksu2-0 (2.0.5-1ubuntu5.1) to 2.0.5-1ubuntu5.2
libglib2.0-0 (2.16.4-0ubuntu2) to 2.16.4-0ubuntu3
libmyth-0.21-0 (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
libmyth-perl (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
libmyth-python (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
libsoup2.4-1 (2.4.1-1) to 2.4.1-1ubuntu1
libtheora-dev (1.0~beta2-2) to 1.0~beta3-1~hardy1
libtheora0 (1.0~beta2-2) to 1.0~beta3-1~hardy1
libtiff4 (3.8.2-7ubuntu3) to 3.8.2-7ubuntu3.1
libtiff4-dev (3.8.2-7ubuntu3) to 3.8.2-7ubuntu3.1
libtiffxx0c2 (3.8.2-7ubuntu3) to 3.8.2-7ubuntu3.1
mytharchive (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mytharchive-data (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythbrowser (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythcontrols (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythflix (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythgallery (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythgame (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythmovies (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythmusic (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythnews (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythphone (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-backend (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-backend-master (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-common (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-database (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-frontend (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythtv-transcode-utils (0.21.0+fixes16838-0ubuntu3.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythvideo (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythweather (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1
mythweb (0.21.0+fixes16838-0ubuntu2.1) to 0.21.0+fixes18207-0ubuntu4~hardy1


Commit Log for Sun Aug 31 14:53:49 2008
Upgraded the following packages:
initramfs-tools (0.85eubuntu39.1) to 0.85eubuntu39.2
kdelibs-data (4:3.5.9-0ubuntu7.1) to 4:3.5.10-0ubuntu1~hardy1
kdelibs4c2a (4:3.5.9-0ubuntu7.1) to 4:3.5.10-0ubuntu1~hardy1
libarts1c2a (1.5.9-0ubuntu2) to 1.5.10-0ubuntu1~hardy1
libartsc0 (1.5.9-0ubuntu2) to 1.5.10-0ubuntu1~hardy1
libcamel1.2-11 (2.22.3-0ubuntu1) to 2.22.3-0ubuntu2
libebook1.2-9 (2.22.3-0ubuntu1) to 2.22.3-0ubuntu2
libedataserver1.2-9 (2.22.3-0ubuntu1) to 2.22.3-0ubuntu2
libnspr4-0d (4.7.1+1.9-0ubuntu0.8.04.1) to 4.7.1+1.9-0ubuntu0.8.04.5
libnss3-1d (3.12.0.2+1.9-0ubuntu0.8.04.1) to 3.12.0.3-0ubuntu0.8.04.4
libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
libxine1 (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-bin (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-console (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-ffmpeg (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-misc-plugins (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-plugins (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-x (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-libc-dev (2.6.24-19.36) to 2.6.24-19.41
linux-source-2.6.24 (2.6.24-19.36) to 2.6.24-19.41
mozilla-plugin-vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
pciutils (1:2.2.4-1.1ubuntu4) to 1:2.2.4-1.1ubuntu5
tzdata (2008c-1ubuntu0.8.04) to 2008e-1ubuntu0.8.04
update-manager (1:0.87.27) to 1:0.87.30
update-manager-core (1:0.87.27) to 1:0.87.30
update-notifier (0.70.7) to 0.70.9
update-notifier-common (0.70.7) to 0.70.9
vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
vlc-nox (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
vlc-plugin-esd (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
vlc-plugin-pulse (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
xserver-xorg-video-intel (2:2.2.1-1ubuntu13.4) to 2:2.2.1-1ubuntu13.6

Also this thread seems to have exactly the same issues:
[http://ubuntuforums.org/showthread.php?t=910342](http://ubuntuforums.org/showthread.php?t=910342)

---

### Post by superm1 on 2008-09-04
Well you've got hardy-backports on.  It's possible the mythtv backport is what killed it then.  You shouldn't need to be cautious of things cmoing from hardy-updates or hardy-security, but take stuff in -backports with a grain of salt.

---

### Post by Boppy3125 on 2008-09-04
I had a problem after updating last night.  I just installed a couple of weeks ago and last updated a couple of days later.  Last night I was putzing with my remote and decided up do updates, then I rebooted.  I coudl watch TV before the updates, I could not watch TV after (it just sat at a black screen for a short while then went back to the menu.)  This morning I checked and it was working.  Very odd.

---

### Post by se99paj on 2008-09-04
It looks like a complete shutdown and then reboot as solved most of the problems. I've still got an issue with the cards as I uninstalled them and now I'm having some problems adding them but I'm going to reinstall the drivers to see if that gets around the problem.

---

### Post by mosabua on 2008-09-07
Taking the updates from backports with a grain of salt is fair enough. But also too late for me. I have the same problem with the frontend not taking to the backend. The backend log is full of QSqlQuery::exec: database not open
although I can run mythfilldatabase just fine.

So what now? Downgrade to the previous version? Or some other fix?

---

### Post by mosabua on 2008-09-07
I found out now that it seem the mythtv-database seems to be hooped in the latest version from hardy backports. I got

sudo dpkg-reconfigure mythtv-database
/usr/sbin/dpkg-reconfigure: mythtv-database is broken or not fully installed

so I tried
sudo apt-get install mythtv-database

which resulted in

Setting up mythtv-database (0.21.0+fixes18207-0ubuntu4~hardy1) ...
 * Starting MySQL database server mysqld                                                                                                            [ OK ]
Failed to execute SQL: GRANT ALL PRIVILEGES ON .* TO @localhost IDENTIFIED BY 'O13I7MQIFXX'\nYou have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '* TO @localhost IDENTIFIED BY 'O13I7MQIFXX'' at line 1 at -e line 8, <> line 1.
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.21.0+fixes18207-0ubuntu4~hardy1); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

(password string was modified before posting here..). Look like a problem with a query generation in the installer..

---

