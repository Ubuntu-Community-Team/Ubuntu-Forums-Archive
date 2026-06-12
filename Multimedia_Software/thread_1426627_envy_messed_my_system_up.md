---
title: "envy messed my system up"
date: 2010-03-10
forum: Multimedia Software
---

### Post by nkbatsi on 2010-03-10
hi to all,
 i had the usual problems with
 flash slowing my computer down.
i tried envy packages and now i' ve 
lost my display drivers and my synaptic is 
not functioning properly.

the message i get every time i try to install or
uninstall packages is:

E: libqt4-svg: subprocess installed post-installation script returned error exit status 2
E: libclucene0ldbl: subprocess installed post-installation script returned error exit status 2
E: libsoprano4: dependency problems - leaving unconfigured
E: soprano-daemon: dependency problems - leaving unconfigured
E: libexiv2-5: subprocess installed post-installation script returned error exit status 2
E: libstreams0: subprocess installed post-installation script returned error exit status 2
E: libstreamanalyzer0: dependency problems - leaving unconfigured
E: kdelibs5-data: subprocess installed post-installation script returned error exit status 2
E: kdelibs5: dependency problems - leaving unconfigured
E: kdelibs-bin: dependency problems - leaving unconfigured
E: exiv2: dependency problems - leaving unconfigured
E: libknotificationitem1: dependency problems - leaving unconfigured
E: libqt4-opengl: subprocess installed post-installation script returned error exit status 2
E: libqt4-webkit: subprocess installed post-installation script returned error exit status 2
E: libplasma3: dependency problems - leaving unconfigured
E: libxine1-bin: subprocess installed post-installation script returned error exit status 2
E: libxine1-misc-plugins: dependency problems - leaving unconfigured
E: libxcb-shape0: subprocess installed post-installation script returned error exit status 2
E: libxcb-shm0: subprocess installed post-installation script returned error exit status 2
E: libxcb-xv0: subprocess installed post-installation script returned error exit status 2
E: libxine1-x: dependency problems - leaving unconfigured
E: libxine1-console: dependency problems - leaving unconfigured
E: libxine1: dependency problems - leaving unconfigured
E: phonon-backend-xine: dependency problems - leaving unconfigured
E: kdebase-runtime: dependency problems - leaving unconfigured
E: kdebase-runtime-bin-kde4: dependency problems - leaving unconfigured

can anybody help?

thanks

---

### Post by doas777 on 2010-03-10
try running:
```

sudo apt-get update && sudo apt-get upgrade

```
it should rerun any install scripts that failed.

---

### Post by nkbatsi on 2010-03-10
thank you doas777,

i opened a terminal and did update.
when i tried to upgrade this came up:

177 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
26 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

any more suggestions?

---

### Post by doas777 on 2010-03-10
> **nkbatsi said:**
> thank you doas777,

i opened a terminal and did update.
when i tried to upgrade this came up:

177 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
26 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

any more suggestions?

usually that means that you have synaptic or software center open. close them and try the command again. if you don;t have them open, then reboot and try again.
only one apt using application can be open at a time.

---

### Post by nkbatsi on 2010-03-10
> **doas777 said:**
> usually that means that you have synaptic or software center open. close them and try the command again. if you don;t have them open, then reboot and try again.
only one apt using application can be open at a time.

[SIZE="3"]this is the whole drill of upgrade:[/SIZE]
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50 linux-generic linux-headers-generic linux-image-generic
  sreadahead
The following packages will be upgraded:
  adduser app-install-data-partner apparmor apparmor-utils apport apport-gtk
  avahi-autoipd avahi-daemon brasero checkbox checkbox-gtk cups cups-bsd
  cups-client cups-common devicekit-disks devicekit-power dhcp3-client
  dhcp3-common empathy empathy-doc evince evolution evolution-common
  evolution-documentation-el evolution-documentation-en evolution-indicator
  evolution-plugins f-spot foomatic-filters gcalctool gdm gimp gimp-data
  gnome-about gnome-desktop-data gnome-power-manager gnome-screensaver
  gnome-settings-daemon grub-common grub-pc gstreamer0.10-alsa
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x
  gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gzip ibus ibus-gtk
  jockey-common jockey-gtk kerneloops-daemon libapparmor-perl libapparmor1
  libavahi-core6 libavahi-glib1 libavahi-gobject0 libavahi-ui0
  libbrasero-media0 libcairo2 libclutter-gtk-0.10-0 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libdevkit-power-gobject1 libempathy-common libempathy-gtk-common
  libempathy-gtk28 libempathy30 libevdocument1 libevview1 libgail-common
  libgail18 libgd2-xpm libgd2-xpm-dev libgimp2.0 libglib2.0-data
  libgnome-desktop-2-11 libgstreamer-plugins-base0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libhtml-parser-perl libibus1
  libindicate-gtk1 libindicate3 libmetacity0 libmysqlclient16
  libnautilus-extension1 libpoppler-glib4 libpoppler5 libpq5 libpurple-bin
  libpurple0 libsmbclient libthai-data libthai0 libvorbis0a libvorbisenc2
  libvorbisfile3 libwbclient0 lintian linux-firmware metacity metacity-common
  mysql-common nautilus nautilus-data ntpdate nvidia-common
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-human openoffice.org-writer openssl
  poppler-utils python python-apport python-avahi python-ibus python-libxml2
  python-minimal python-problem-report python-ubuntuone-client
  python-ubuntuone-storageprotocol python-uno rhythmbox rsyslog samba-common
  samba-common-bin smbclient software-center sudo system-tools-backends
  telepathy-gabble totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk ttf-opensymbol ubuntu-xsplash-artwork
  ubuntuone-client ubuntuone-client-gnome udev uno-libs3 update-manager
  update-manager-core upstart ure x11-common xorg xsane xsane-common
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-intel xsplash xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support
177 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
26 not fully installed or removed.
Need to get 28.0MB/160MB of archives.
After this operation, 4,661kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main openoffice.org-core 1:3.1.1-5ubuntu1.1 [28.0MB]
Fetched 28.0MB in 1min 18s (357kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 137439 files and directories currently installed.)
Preparing to replace libwbclient0 2:3.4.0-3ubuntu5 (using .../libwbclient0_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Unpacking replacement libwbclient0 ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.
nkbatsi@kavourdistiri:~$ 

[SIZE="3"]i think that i'm not running two apts at the same time so the segmentation fault seems to be my problem, except if there is an apt running in the background without me knowing [/SIZE]

---

### Post by doas777 on 2010-03-10
yeah, the seg fault is somthing more serious. the previous message you had 
```

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

is the one indicating that you have multiple apps that use apt/dpkg running. 

at this point, you may want to do a clean/autoremove;
```

sudo apt-get update && sudo apt-get clean && sudo apt-get autoremove

```

---

### Post by nkbatsi on 2010-03-10
> **doas777 said:**
> yeah, the seg fault is somthing more serious. the previous message you had 
```

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

is the one indicating that you have multiple apps that use apt/dpkg running. 

at this point, you may want to do a clean/autoremove;
```

sudo apt-get update && sudo apt-get clean && sudo apt-get autoremove

```

[SIZE="3"]ok did all the above this is what i get in the last step[/SIZE]

nkbatsi@kavourdistiri:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 165 not upgraded.
29 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cups (1.4.1-5ubuntu2.4) ...
 * Starting Common Unix Printing System: cupsd                           [ OK ] 


Setting up foomatic-filters (4.0.3-0ubuntu2.2) ...

Setting up libqt4-svg (4.5.3really4.5.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-svg (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libclucene0ldbl (0.9.20-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libclucene0ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
dpkg: error processing libsoprano4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of soprano-daemon:
 soprano-daemon depends on libsoprano4 (>= 2.3.0); however:
  Package libsoprano4 is not configured yet.
dpkg: error processing soprano-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up libexiv2-5 (0.18.2-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libexiv2-5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libstreams0 (0.7.0-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libstreams0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libstreamanalyzer0:
 libstreamanalyzer0 depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
 libstreamanalyzer0 depends on libexiv2-5; however:
  Package libexiv2-5 is not configured yet.
 libstreamanalyzer0 depends on libstreams0 (= 0.7.0-1); however:
  Package libstreams0 is not configured yet.
dpkg: error processing libstreamanalyzer0 (--configure):
 dependency problems - leaving unconfigured
Setting up kdelibs5-data (4:4.3.5-0ubuntu1~karmic1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdelibs5-data (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdelibs5:
 kdelibs5 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 kdelibs5 depends on libsoprano4 (>= 2.2.69); however:
  Package libsoprano4 is not configured yet.
 kdelibs5 depends on libstreamanalyzer0 (>= 0.7.0); however:
  Package libstreamanalyzer0 is not configured yet.
 kdelibs5 depends on kdelibs5-data (>= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5-data is not configured yet.
dpkg: error processing kdelibs5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on kdelibs5 (= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5 is not configured yet.
 kdelibs-bin depends on liNo apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    bsoprano4 (>= 2.1.67); however:
  Package libsoprano4 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-emailmerge (1:3.1.1-5ubuntu1.1) ...
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
Copying: mailmerge.py
Enabling: mailmerge.py
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml

unopkg done.

dpkg: dependency problems prevent configuration of exiv2:
 exiv2 depends on libexiv2-5; however:
  Package libexiv2-5 is not configured yet.
dpkg: error processing exiv2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotificationitem1:
 libknotificationitem1 depends on kdelibs5 (>= 4:4.3.4); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libknotificationitem1 (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-opengl (4.5.3really4.5.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-opengl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-webkit (4.5.3really4.5.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-webkit (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 libplasma3 depends on libqt4-opengl (>= 4.5.1); however:
  Package libqt4-opengl is not configured yet.
 libplasma3 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 libplasma3 depends on libqt4-webkit (>= 4.5.1); however:
  Package libqt4-webkit is not configured yet.
 libplasma3 depends on kdelibs5-data (= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5-data is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
Setting up libxine1-bin (1.1.16.3-0ubuntu4) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxine1-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1-misc-plugins:
 libxine1-misc-plugins depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-misc-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up libxcb-shape0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-shape0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxcb-shm0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxcb-xv0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-xv0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1-x:
 libxine1-x depends on libxcb-shape0; however:
  Package libxcb-shape0 is not configured yet.
 libxine1-x depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
 libxine1-x depends on libxcb-xv0; however:
  Package libxcb-xv0 is not configured yet.
 libxine1-x depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-x (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1-console:
 libxine1-console depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-console (--configure):
 depNo apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      endency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxine1-misc-plugins (= 1.1.16.3-0ubuntu4) | libxine1-plugins (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-misc-plugins is not configured yet.
  Package libxine1-plugins is not installed.
 libxine1 depends on libxine1-x (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-x is not configured yet.
 libxine1 depends on libxine1-console (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-console is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phonon-backend-xine:
 phonon-backend-xine depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
dpkg: error processing phonon-backend-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 kdebase-runtime depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
 kdebase-runtime depends on libknotificationitem1; however:
  Package libknotificationitem1 is not configured yet.
 kdebase-runtime depends on libplasma3 (>= 4:4.3.5); however:
  Package libplasma3 is not configured yet.
 kdebase-runtime depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 kdebase-runtime depends on libsoprano4 (>= 2.3.0); however:
  Package libsoprano4 is not configured yet.
 kdebase-runtime depends on libstreamanalyzer0 (>= 0.7.0); however:
  Package libstreamanalyzer0 is not configured yet.
 kdebase-runtime depends on libstreams0 (>= 0.7.0); however:
  Package libstreams0 is not configured yet.
 kdebase-runtime depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
 kdebase-runtime depends on phonon-backend-xine | phonon-backend; however:
  Package phonon-backend-xine is not configured yet.
  Package phonon-backend is not installed.
  Package phonon-backend-xine which provides phonon-backend is not configured yet.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime-bin-kde4:
 kdebase-runtime-bin-kde4 depends on kdebase-runtime (>= 4:4.3.5); however:
  Package kdebase-runtime is not configured yet.
 kdebase-runtime-bin-kde4 depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 kdebase-runtime-bin-kde4 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
dpkg: error processing kdebase-runtime-bin-kde4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-svg
 libclucene0ldbl
 libsoprano4
 soprano-daemon
 libexiv2-5
 libstreams0
 libstreamanalyzer0
 kdelibs5-data
 kdelibs5
 kdelibs-bin
 exiv2
 libknotificationitem1
 libqt4-opengl
 libqt4-webkit
 libplasma3
 libxine1-bin
 libxine1-misc-plugins
 libxcb-shape0
 libxcb-shm0
 libxcb-xv0
 libxine1-x
 libxine1-console
 libxine1
 phonon-backend-xine
 kdebase-runtime
 kdebase-runtime-bin-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
nkbatsi@kavourdistiri:~$ 

[SIZE="3"]can you help me on

---

### Post by doas777 on 2010-03-10
well all the files that you can't install, are the QT backend required by envy, so lets try removing it directly:
```

sudo apt-get remove envyng

```

---

### Post by nkbatsi on 2010-03-10
> **doas777 said:**
> well all the files that you can't install, are the QT backend required by envy, so lets try removing it directly:
```

sudo apt-get remove envyng

```

[SIZE="3"]ok did it...[/SIZE]

nkbatsi@kavourdistiri:~$ sudo apt-get remove envyng
[sudo] password for nkbatsi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
nkbatsi@kavourdistiri:~$ 

[SIZE="3"]seems there's no such package installed[/SIZE]

---

### Post by nkbatsi on 2010-03-10
oh and something that might be important: my pc is very old, but still operating fine for my needs. this thread contains all the info about my system and problems i had in the recent past when i first installed ubuntu on it:
 [Bug 519561] BUG: Bad page map in process gnome-panel pte:00000001 pmd:1c4a6067

of course i got over these problems and the pc was working fine for some time, but my messing around with it brought me to this point.

---

### Post by doas777 on 2010-03-10
well, envyNG is the correct envy package for any version of ubuntu since gutsy. what did you do when you tried to install it?

here is a link to the envy faq, that has some instructions for uninstalling it, but they may or may not be right for your situation,
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by nkbatsi on 2010-03-10
> **doas777 said:**
> well, envyNG is the correct envy package for any version of ubuntu since gutsy. what did you do when you tried to install it?

here is a link to the envy faq, that has some instructions for uninstalling it, but they may or may not be right for your situation,
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

i believe i did it in the proper way, through synaptic manager, but it gave me an error message ,which i don't remember, in the first place.
 i installed envyng-core just by itself through synaptic. after that i realized that core needed either gtk or qt to run. i uninstalled envyng-core through terminal and then reinstalled core and gtk. 
then i ran envyng -t, which removed my old driver and then it could not create a new driver for me so i ended up with a vesa driver. i had a backup so i already replaced the vesa driver with the previous, so my graphics are ok now. 

the problem is that synaptic remains non-operating!

---

### Post by doas777 on 2010-03-10
well, now that you have your packages lined up, can you run the "clean and autoremove" line i posted on the last page?

---

### Post by nkbatsi on 2010-03-10
> **doas777 said:**
> well, now that you have your packages lined up, can you run the "clean and autoremove" line i posted on the last page?

did the following: 

sudo apt-get update && sudo apt-get clean && sudo apt-get autoremove

all worked fine except the last one,
this is the last lines i get from autoremove:


dpkg: error processing kdebase-runtime-bin-kde4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-svg
 libclucene0ldbl
 libsoprano4
 soprano-daemon
 libexiv2-5
 libstreams0
 libstreamanalyzer0
 kdelibs5-data
 kdelibs5
 kdelibs-bin
 exiv2
 libknotificationitem1
 libqt4-opengl
 libqt4-webkit
 libplasma3
 libxine1-bin
 libxine1-misc-plugins
 libxcb-shape0
 libxcb-shm0
 libxcb-xv0
 libxine1-x
 libxine1-console
 libxine1
 phonon-backend-xine
 kdebase-runtime
 kdebase-runtime-bin-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nkbatsi on 2010-03-10
got to go now. i'll deal with the problem tomorrow.
many many thanks doas777. i'll seek for your help tomorrow too!

---

