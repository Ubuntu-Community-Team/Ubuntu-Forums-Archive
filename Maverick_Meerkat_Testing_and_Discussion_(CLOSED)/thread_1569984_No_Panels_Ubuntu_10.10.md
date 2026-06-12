---
title: "No Panels Ubuntu 10.10"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by The Bushman on 2010-09-07
I have ubuntu 10.10 muti desktop - gnome,KDE, xfce running. I just upgraded to the beta version. Everything in kde, xfce is okay but for some reason in gnome. I have no panels at all. Bottom and top panels disappeared and also update manager in gnome is messed up as well. This is the log from update manager - am just an adventurous newby please KISS - Keep It Simple $ Stupid. Been using ubuntu for 10 months. 

:) am finally loving my laptop

Log Here->
```

dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
Setting up apturl-kde (0.4.1ubuntu7) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        dpkg: dependency problems prevent configuration of at-spi:
 at-spi depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing at-spi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.31); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.32); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of atomix:
 atomix depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 atomix depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 atomix depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing atomix (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of avant-window-navigator:
 avant-window-navigator depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing avant-window-navigator (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of awn-applets-c-core:
 awn-applets-c-core depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 awn-applets-c-core depends on avant-window-navigator; however:
  Package avant-window-navigator is not configured yet.
dpkg: error processing awn-applets-c-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of banshee:
 banshee depends on gstreamer0.10-plugins-good (>= 0.10.8-4); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing banshee (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of baobab:
 baobab depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing baobab (--configure):No apport report written because MaxReports has already been reached
                                No apport report written because MaxReports has already been reached
                    No apport report written because MaxReports has already been reached
        No apport report written because MaxReports has already been reached

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins:
 compiz-plugins depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity-common:
 metacity-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing metacity-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmetacity-private0:
 libmetacity-private0 depends on metacity-common (>= 1:2.30); however:
  Package metacity-common is nNo apport report written because MaxReports has already been reached
                  No apport report written because MaxReports has already been reached
      ot configured yet.
 libmetacity-private0 depends on metacity-common (<< 1:2.31); however:
  Package metacity-common is not configured yet.
dpkg: error processing libmetacity-private0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libmetacity-private0 (>= 1:2.26.0); however:
  Package libmetacity-private0 is not configured yet.
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 compiz-gnome depends on compiz-plugins (= 1:0.8.6-0ubuntu5); however:
  Package compiz-plugins is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-plugins (>= 1:0.8.6-0ubuntu5); however:
  Package compiz-plugins is not configured yet.
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.31); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.32); however:
  Package nautilus-data is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-common:
 libgnomekbd-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomekbd-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgnomekbd-common (>= 2.31.5-0ubuntu2); however:
  Package libgnomekbd-common is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libgnomekbd4 (>= 2.31.5); however:
  Package libgnomekbd4 is not configured yet.
 gnome-settings-daemon depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-settings-daemon depends on libgnome2-common; however:
  Package libgnome2-common is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libmetacity-private0 (>= 1:2.26.0); however:
  Package libmetacity-private0 is not configured yet.
 metacity depends on metacity-common (>= 1:2.30); however:
  Package metacity-common is not configured yet.
 metacity depends on metacity-common (<< 1:2.31); however:
  Package metacity-common is not configured yet.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutter-common:
 mutter-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing mutter-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmutter-private0:
 libmutter-private0 depends on mutter-common (>= 2.31); however:
  Package mutter-common is not configured yet.
 libmutter-private0 depends on mutter-common (<< 2.32); however:
  Package mNo apport report written because MaxReports has already been reached
                                                                               No apport report written because MaxReports has already been reached
                                                                   No apport report written because MaxReports has already been reached
                                                       No apport report written because MaxReports has already been reached
                                           No apport report written because MaxReports has already been reached
                               No apport report written because MaxReports has already been reached
                   No apport report written because MaxReports has already been reached
       No apport report written because MaxReports has already been reached
                                                                           No apport report written because MaxReports has already been reached
                                                               No apport report written because MaxReports has already been reached
                                                   No apport report written because MaxReports has already been reached
                                       No apport report written because MaxReports has already been reached
                           No apport report written because MaxReports has already been reached
               utter-common is not configured yet.
dpkg: error processing libmutter-private0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutter:
 mutter depends on libmutter-private0; however:
  Package libmutter-private0 is not configured yet.
 mutter depends on mutter-common (>= 2.31); however:
  Package mutter-common is not configured yet.
 mutter depends on mutter-common (<< 2.32); however:
  Package mutter-common is not configured yet.
dpkg: error processing mutter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-settings-daemon (>= 2.26); however:
  Package gnome-settings-daemon is not configured yet.
 gnome-session depends on metacity | mutter | compiz-gnome | sawfish; however:
  Package metacity is not configured yet.
  Package mutter is not configured yet.
  Package compiz-gnome is not configured yet.
  Package sawfish is notNo apport report written because MaxReports has already been reached
            No apport report written because MaxReports has already been reached
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        No apport report written because MaxReports has already been reached
                                            No apport report written because MaxReports has already been reached
                                No apport report written because MaxReports has already been reached
                    No apport report written because MaxReports has already been reached
        No apport report written because MaxReports has already been reached
                                                                             installed.
 gnome-session depends on nautilus (>= 2.26); however:
  Package nautilus is not configured yet.
 gnome-session depends on gnome-session-bin (>= 2.31.6-0ubuntu1); however:
  Package gnome-session-bin is not configured yet.
 gnome-session depends on gnome-session-bin (<< 2.32); however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
No apport report written because MaxReports has already been reached
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
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of edubuntu-artwork:
 edubuntu-artwork depends on gdm; however:
  Package gdm is not configured yet.
 edubuntu-artwork depends on light-themes; however:
  Package light-themes is not configured yet.
dpkg: error processing edubuntu-artwork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgstfarsight0.10-0:
 libgstfarsight0.10-0 depends on gstreamer0.10-plugins-good (>= 0.10.17-1ubuntu1); however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing libgstfarsight0.10-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtelepathy-farsight0:
 libtelepathy-farsight0 depends on libgstfarsight0.10-0 (>= 0.0.3); however:
  Package libgstfarsight0.10-0 is not configured yet.
dpkg: error processing libtelepathy-farsight0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on libgstfarsight0.10-0 (>= 0.0.1); however:
  Package libgstfarsight0.10-0 is not configured yet.
 empathy depends on libtelepathy-farsight0 (>= 0.0.6); however:
  Package libtelepathy-farsight0 is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather-common:
 libgweather-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgweather-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgweather-common (>= 2.24.0); however:
  Package libgweather-common is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libgweather1 (>= 2.30.0); however:
  Package libgweather1 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libgweather1 (>= 2.30.0); however:
  Package libgweather1 is not configured yet.
 evolution depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 evolution depends on evolution-data-server (>= 2.30.3); however:
  Package evolution-data-server is not configured yet.
 evolution depends on evolution-data-server (<< 2.31); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 evolution-exchange depends on evolution (>= 2.30.0); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.31.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firestarter:
 firestarter depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 firestarter depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 firestarter depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 firestarter depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing firestarter (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for python-central ...
Errors were encountered while processing:
 gconf2
 gnome-applets-data
 aisleriot
 at-spi
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 atomix
 avant-window-navigator
 awn-applets-c-core
 gstreamer0.10-plugins-good
 banshee
 baobab
 capplets-data
 compiz-plugins
 metacity-common
 libmetacity-private0
 compiz-gnome
 compiz
 nautilus-data
 nautilus
 libgnomekbd-common
 libgnomekbd4
 gnome-settings-daemon
 gnome-session-bin
 libpanel-applet2-0
 metacity
 mutter-common
 libmutter-private0
 mutter
 gnome-session
 gnome-power-manager
 gdm
 light-themes
 edubuntu-artwork
 libgstfarsight0.10-0
 libtelepathy-farsight0
 empathy
 eog
 evince
 libgweather-common
 libgweather1
 evolution-data-server
 evolution
 evolution-exchange
 evolution-webcal
 f-spot
 file-roller
 firestarter
Processing was halted because there were too many errors.
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Elfy on 2010-09-07
Moved to maverick forum - please also use code tags.

---

