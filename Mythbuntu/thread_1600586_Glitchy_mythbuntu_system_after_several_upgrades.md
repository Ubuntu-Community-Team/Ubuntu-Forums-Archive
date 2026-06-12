---
title: "Glitchy mythbuntu system after several upgrades"
date: 2010-10-19
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-10-19
hi, so i have been using mythbuntu for a while and as such have upgraded along the way to 10.10 (from 9.04 on the current install).  Over time i have been "carrying" a few glitches after each upgrade and am now faced with the chalenge of fixing them or starting 10.10 from scratch!

First big one is that at some point part of my gnome power management has become broken, although i dont use power management really it does cause update errors every time i install a new update as well as package operation errors.

The warning is that gnome power defaults have not been set contact your administrator.  (Pretty vague i know).

Any ideas on how i can fix this?

I also get an error every time i update, the log is attached to see if someone can help me get to the bottom of what is causing the problems;

```
installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace libc6-i386 2.12.1-0ubuntu6 (using .../libc6-i386_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Preparing to replace libc-dev-bin 2.12.1-0ubuntu6 (using .../libc-dev-bin_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.12.1-0ubuntu6 (using .../libc6-dev_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.12.1-0ubuntu7) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.12.1-0ubuntu7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace gconf2-common 2.31.91-0ubuntu3 (using .../gconf2-common_2.31.91-0ubuntu3.1_all.deb) ...
Unpacking replacement gconf2-common ...
Preparing to replace libgconf2-4 2.31.91-0ubuntu3 (using .../libgconf2-4_2.31.91-0ubuntu3.1_amd64.deb) ...
Unpacking replacement libgconf2-4 ...
Preparing to replace gconf2 2.31.91-0ubuntu3 (using .../gconf2_2.31.91-0ubuntu3.1_amd64.deb) ...
Unpacking replacement gconf2 ...
Preparing to replace udev 162-2 (using .../udev_162-2.1_amd64.deb) ...
Adding 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace libudev0 162-2 (using .../libudev0_162-2.1_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libgudev-1.0-0 1:162-2 (using .../libgudev-1.0-0_1%3a162-2.1_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace jockey-gtk 0.5.10-0ubuntu5 (using .../jockey-gtk_0.5.10-0ubuntu5.1_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.5.10-0ubuntu5 (using .../jockey-common_0.5.10-0ubuntu5.1_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace dkms 2.1.1.2-3ubuntu1 (using .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace libutouch-grail1 1.0.14-0ubuntu1 (using .../libutouch-grail1_1.0.15-0ubuntu1_amd64.deb) ...
Unpacking replacement libutouch-grail1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up libc6-i386 (2.12.1-0ubuntu7) ...
Setting up libc-dev-bin (2.12.1-0ubuntu7) ...
Setting up libc6-dev (2.12.1-0ubuntu7) ...
Setting up gconf2-common (2.31.91-0ubuntu3.1) ...
Setting up libgconf2-4 (2.31.91-0ubuntu3.1) ...
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults/%gconf-tree.xml'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu2-0 (>= 2.0.8); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 apturl depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
 aptuNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
rl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not confNo apport report written because MaxReports is reached already
igured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
Setting up udev (162-2.1) ...
udev start/running, process 5296
Removing 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gdm depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gdm depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-common:
 libgnomekbd-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomekbd-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgnomekbd-common (>= 2.32.0-0ubuntu1); however:
  Package libgnomekbd-common is not configured yet.
dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuratNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ion of gnome-screensaver:
 gnome-screensaver depends on libgnomekbd4 (>= 2.29.5); however:
  Package libgnomekbd4 is not configured yet.
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
Setting up libudev0 (162-2.1) ...
Setting up libgudev-1.0-0 (1:162-2.1) ...
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
- leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on gstreamer0.10-plugins-good (>= 0.10.0); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-common:
 mythbuntu-common depends on software-properties-gtk; however:
  PackagNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
e software-properties-gtk is not configured yet.
dpkg: error processing mythbuntu-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-default-settings:
 mythbuntu-default-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing mythbuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
Setting up jockey-common (0.5.10-0ubuntu5.1) ...
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-manager depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mythbuntu-desktop:
 mythbuntu-desktop depends on gdebi; however:
  Package gdebi is not configured yet.
 mythbuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 mythbuntu-desktop depends on mythbuntu-default-settings; however:
  Package mythbuntu-default-settings is not configured yet.
 mythbuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing mythbuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgame:
 mythgame depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yetNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
.
dpkg: error processing mythgame (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmovies:
 mythmovies depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmovies (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnetvision:
 mythnetvision depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
 mythnetvision depends on mythbrowser (>= 0.22); however:
  Package mythbrowser is not configured yet.
dpkg: error processing mythnetvision (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
pkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 network-manager-gnome depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on apturl (>= 0.1.2ubuntu1) | apturl-kde; however:
  Package apturl is not configured yet.
  Package apturl-kde is not installed.
dpkg: error processing xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on xul-ext-ubufox; however:
  Package xul-ext-ubufox is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
 update-notifier depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
Setting up dkms (2.1.1.2-3ubuntu1.1) ...
Setting up libutouch-grail1 (1.0.15-0ubuntu1) ...
Processing triggers for python-central ...
Setting up jockey-gtk (0.5.10-0ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Errors were encountered while processing:
 gconf2
 libgksu2-0
 gksu
 software-properties-gtk
 apturl
 evince
 libgnomevfs2-common
 libgnomevfs2-0
 firefox-gnome-support
 gdebi
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libpanel-applet2-0
 gnome-session-bin
 gdm
 gedit
 gnome-power-manager
 libgnomekbd-common
 libgnomekbd4
 gnome-screensaver
 gnome-user-share
 gstreamer0.10-plugins-good
 libgnomeui-0
 libgnomevfs2-extra
 miro
 mythtv-frontend
 mythbrowser
 mythbuntu-common
 mythbuntu-default-settings
 update-manager
 mythbuntu-desktop
 mythgallery
 mythgame
 mythmovies
 mythnetvision
 mythnews
 mythtv-backend
 mythtv
 mythtv-backend-master
 mythvideo
 mythweather
 network-manager-gnome
 python-gnome2
 xul-ext-ubufox
 ubufox
 update-notifier
 mythmusic
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults/%gconf-tree.xml'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythbuntu-default-settings:
 mythbuntu-default-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing mythbuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-desktop:
 mythbuntu-desktop depends on mythbuntu-default-settings; however:
  Package mythbuntu-default-settings is not configured yet.
 mythbuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing mythbuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on gstreamer0.10-plugins-good (>= 0.10.0); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-common:
 libgnomekbd-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomekbd-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu2-0 (>= 2.0.8); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on apturl (>= 0.1.2ubuntu1) | apturl-kde; however:
  Package apturl is not configured yet.
  Package apturl-kde is not installed.
dpkg: error processing xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgnomekbd-common (>= 2.32.0-0ubuntu1); however:
  Package libgnomekbd-common is not configured yet.
dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on xul-ext-ubufox; however:
  Package xul-ext-ubufox is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-common:
 mythbuntu-common depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing mythbuntu-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgame:
 mythgame depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgame (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmovies:
 mythmovies depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmovies (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnetvision:
 mythnetvision depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
 mythnetvision depends on mythbrowser (>= 0.22); however:
  Package mythbrowser is not configured yet.
dpkg: error processing mythnetvision (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured

```

Thanks;

Andy

---

### Post by geekyhawkes on 2010-10-19
I have also started having problems with mplayer since the upgrade to 10.10.  I can select any video and mplayer launchs but doesnt play the file (when loaded via myth front end, if i start mplayer from the command line then the file plays fine so its not codec driven).  

I can skip forward in mplyaer but cannot get it to play, wierd?

---

### Post by superm1 on 2010-10-19
> **geekyhawkes said:**
> hi, so i have been using mythbuntu for a while and as such have upgraded along the way to 10.10 (from 9.04 on the current install).  Over time i have been "carrying" a few glitches after each upgrade and am now faced with the chalenge of fixing them or starting 10.10 from scratch!

First big one is that at some point part of my gnome power management has become broken, although i dont use power management really it does cause update errors every time i install a new update as well as package operation errors.

The warning is that gnome power defaults have not been set contact your administrator.  (Pretty vague i know).

Any ideas on how i can fix this?

I also get an error every time i update, the log is attached to see if someone can help me get to the bottom of what is causing the problems;

```
installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace libc6-i386 2.12.1-0ubuntu6 (using .../libc6-i386_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Preparing to replace libc-dev-bin 2.12.1-0ubuntu6 (using .../libc-dev-bin_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.12.1-0ubuntu6 (using .../libc6-dev_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.12.1-0ubuntu7) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.12.1-0ubuntu7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208477 files and directories currently installed.)
Preparing to replace gconf2-common 2.31.91-0ubuntu3 (using .../gconf2-common_2.31.91-0ubuntu3.1_all.deb) ...
Unpacking replacement gconf2-common ...
Preparing to replace libgconf2-4 2.31.91-0ubuntu3 (using .../libgconf2-4_2.31.91-0ubuntu3.1_amd64.deb) ...
Unpacking replacement libgconf2-4 ...
Preparing to replace gconf2 2.31.91-0ubuntu3 (using .../gconf2_2.31.91-0ubuntu3.1_amd64.deb) ...
Unpacking replacement gconf2 ...
Preparing to replace udev 162-2 (using .../udev_162-2.1_amd64.deb) ...
Adding 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace libudev0 162-2 (using .../libudev0_162-2.1_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libgudev-1.0-0 1:162-2 (using .../libgudev-1.0-0_1%3a162-2.1_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace jockey-gtk 0.5.10-0ubuntu5 (using .../jockey-gtk_0.5.10-0ubuntu5.1_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.5.10-0ubuntu5 (using .../jockey-common_0.5.10-0ubuntu5.1_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace dkms 2.1.1.2-3ubuntu1 (using .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace libutouch-grail1 1.0.14-0ubuntu1 (using .../libutouch-grail1_1.0.15-0ubuntu1_amd64.deb) ...
Unpacking replacement libutouch-grail1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up libc6-i386 (2.12.1-0ubuntu7) ...
Setting up libc-dev-bin (2.12.1-0ubuntu7) ...
Setting up libc6-dev (2.12.1-0ubuntu7) ...
Setting up gconf2-common (2.31.91-0ubuntu3.1) ...
Setting up libgconf2-4 (2.31.91-0ubuntu3.1) ...
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults/%gconf-tree.xml'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu2-0 (>= 2.0.8); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 apturl depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
 aptuNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
rl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not confNo apport report written because MaxReports is reached already
igured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
Setting up udev (162-2.1) ...
udev start/running, process 5296
Removing 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gdm depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gdm depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-common:
 libgnomekbd-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomekbd-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgnomekbd-common (>= 2.32.0-0ubuntu1); however:
  Package libgnomekbd-common is not configured yet.
dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuratNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ion of gnome-screensaver:
 gnome-screensaver depends on libgnomekbd4 (>= 2.29.5); however:
  Package libgnomekbd4 is not configured yet.
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
Setting up libudev0 (162-2.1) ...
Setting up libgudev-1.0-0 (1:162-2.1) ...
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
- leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on gstreamer0.10-plugins-good (>= 0.10.0); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-common:
 mythbuntu-common depends on software-properties-gtk; however:
  PackagNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
e software-properties-gtk is not configured yet.
dpkg: error processing mythbuntu-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-default-settings:
 mythbuntu-default-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing mythbuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
Setting up jockey-common (0.5.10-0ubuntu5.1) ...
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-manager depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mythbuntu-desktop:
 mythbuntu-desktop depends on gdebi; however:
  Package gdebi is not configured yet.
 mythbuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 mythbuntu-desktop depends on mythbuntu-default-settings; however:
  Package mythbuntu-default-settings is not configured yet.
 mythbuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing mythbuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgame:
 mythgame depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yetNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
.
dpkg: error processing mythgame (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmovies:
 mythmovies depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmovies (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnetvision:
 mythnetvision depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
 mythnetvision depends on mythbrowser (>= 0.22); however:
  Package mythbrowser is not configured yet.
dpkg: error processing mythnetvision (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
pkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 network-manager-gnome depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on apturl (>= 0.1.2ubuntu1) | apturl-kde; however:
  Package apturl is not configured yet.
  Package apturl-kde is not installed.
dpkg: error processing xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on xul-ext-ubufox; however:
  Package xul-ext-ubufox is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
 update-notifier depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
Setting up dkms (2.1.1.2-3ubuntu1.1) ...
Setting up libutouch-grail1 (1.0.15-0ubuntu1) ...
Processing triggers for python-central ...
Setting up jockey-gtk (0.5.10-0ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Errors were encountered while processing:
 gconf2
 libgksu2-0
 gksu
 software-properties-gtk
 apturl
 evince
 libgnomevfs2-common
 libgnomevfs2-0
 firefox-gnome-support
 gdebi
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libpanel-applet2-0
 gnome-session-bin
 gdm
 gedit
 gnome-power-manager
 libgnomekbd-common
 libgnomekbd4
 gnome-screensaver
 gnome-user-share
 gstreamer0.10-plugins-good
 libgnomeui-0
 libgnomevfs2-extra
 miro
 mythtv-frontend
 mythbrowser
 mythbuntu-common
 mythbuntu-default-settings
 update-manager
 mythbuntu-desktop
 mythgallery
 mythgame
 mythmovies
 mythnetvision
 mythnews
 mythtv-backend
 mythtv
 mythtv-backend-master
 mythvideo
 mythweather
 network-manager-gnome
 python-gnome2
 xul-ext-ubufox
 ubufox
 update-notifier
 mythmusic
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 98, in <module>
    os.remove(os.path.join(defaults_dest,f))
OSError: [Errno 2] No such file or directory: '/var/lib/gconf/defaults/%gconf-tree.xml'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythbuntu-default-settings:
 mythbuntu-default-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing mythbuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-desktop:
 mythbuntu-desktop depends on mythbuntu-default-settings; however:
  Package mythbuntu-default-settings is not configured yet.
 mythbuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing mythbuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of miro:
 miro depends on gstreamer0.10-plugins-good (>= 0.10.0); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing miro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-common:
 libgnomekbd-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomekbd-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu2-0 (>= 2.0.8); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on apturl (>= 0.1.2ubuntu1) | apturl-kde; however:
  Package apturl is not configured yet.
  Package apturl-kde is not installed.
dpkg: error processing xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on gksu; however:
  Package gksu is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgnomekbd-common (>= 2.32.0-0ubuntu1); however:
  Package libgnomekbd-common is not configured yet.
dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on xul-ext-ubufox; however:
  Package xul-ext-ubufox is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on gksu | kdebase-bin; however:
  Package gksu is not configured yet.
  Package kdebase-bin is not installed.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbuntu-common:
 mythbuntu-common depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing mythbuntu-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgame:
 mythgame depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgame (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmovies:
 mythmovies depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmovies (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnetvision:
 mythnetvision depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
 mythnetvision depends on mythbrowser (>= 0.22); however:
  Package mythbrowser is not configured yet.
dpkg: error processing mythnetvision (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured

```

Thanks;

Andy
Try:
```
sudo dpkg-reconfigure gconf2
```

---

### Post by geekyhawkes on 2010-10-19
Thanks, sadly i get the following back;

/usr/sbin/dpkg-reconfigure: gconf2 is broken or not fully installed 

Thoughts?  Any idea why mplayer might be playing up?

---

### Post by superm1 on 2010-10-19
> **geekyhawkes said:**
> Thanks, sadly i get the following back;

/usr/sbin/dpkg-reconfigure: gconf2 is broken or not fully installed 

Thoughts?  Any idea why mplayer might be playing up?
Get the gconf2 thing fixed, and then worry about mplayer.

try this:

```
sudo apt-get install --reinstall gconf2
```

---

### Post by geekyhawkes on 2010-10-20
Sounds good to me, sadly i get a load of errors when i try and run the reinstall as detailed above.  The errors are pretty much as i detailed above regarding dependances not met etc.  

Thanks for your help so far, any other thoughts?

---

### Post by LowSky on 2010-10-20
can we see a copy of /etc/apt/sources.list

maybe a line or two are messed up

---

### Post by geekyhawkes on 2010-10-21
Of course, i hadnt even thought about the sources being messed up (still learning linux, every day).

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://debian.slimdevices.com stable main # disabled on upgrade to maverick
```

Not that its saying much, but nothing obviously wrong that i can see.

---

### Post by geekyhawkes on 2010-10-23
Actually i gave a slight duff steer earlier, when i run files from terminal in mplayer then i get the same issue of the file not playing but being able to scan forward.  I can play the films in VLC so it isnt codec driven, but not sure how to get myplayer back up and running!?

---

### Post by geekyhawkes on 2010-10-30
Anyone got any more ideas how to fix these errors?

---

### Post by geekyhawkes on 2010-11-01
This is really starting to frustrate me, i could just reinstall my entire mediacenter but I was kind of hoping to not have to do that over something that seems like it should be simple.

---

### Post by geekyhawkes on 2010-11-14
So time has marched on and i am still having the above problems!  I dont want ot have to reinstall my entire system (isnt that a windows thing after all! and not linux), but I am running out of patience.  I have a media center that i cannot watch any dvd / rips on and get errors each time any update comes out!

---

### Post by winewood on 2010-11-14
geekyhawkes,
 
I too noticed that when I ran ALL updates too all the software on my box, it would mess up some items that were working. As a result, I resorted to only updating the security patches, and leaving the software patches alone. This way my box had the most important updates, and I could rest assure that my wife could still watch TV as a simple update does not leave me looking at a black screen. 
 
Is there any reason to update to the latest software each week, if you are running fine?
 
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
 
Once you have a backup you can untar the files to revert back to a working config, in case an update breaks you.

---

### Post by machogeek on 2011-03-08
This worked for me:

sudo dpkg --purge --force-all <package_name>

in this case... 
sudo dpkg --purge --force-all gconf2

Then I followed the instructions on this page. 

[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

Reinstall gconf2 and other dependencies that were removed.

---

### Post by geekyhawkes on 2011-03-10
too late for me, i ended up reinstalling.  but thanks for the replies, its all good advice for the serach function if anyone else suffers my fate!

---

