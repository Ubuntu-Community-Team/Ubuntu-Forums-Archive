---
title: "Synaptic update has really messed up my sound"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Dr.Suave on 2008-12-16
Hiya - I'm trying to set up a new installation of Ubuntu on a Phillips Freevents laptop, and on clean install, the sound works. 

However, after a software update (which includes: 
alsa-utils (1.0.17-0ubuntu2) to 1.0.17-0ubuntu3
pulseaudio (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-esound-compat (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-gconf (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-hal (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-x11 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-utils (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1) sound becomes completely ruined, with system noises very faint and drowned out by a large crackling, and applications like Skype not working sound wise at all.

Is there any way to fix this? Has anyone else had any kind of experience like this?

Any help at all is really. really appreciated.

Here's the full list of updates (which I found in Synaptic's history):

Commit Log for Tue Dec 16 23:15:35 2008


Upgraded the following packages:
alsa-utils (1.0.17-0ubuntu2) to 1.0.17-0ubuntu3
apparmor (2.3+1289-0ubuntu4) to 2.3+1289-0ubuntu4.1
apparmor-utils (2.3+1289-0ubuntu4) to 2.3+1289-0ubuntu4.1
base-files (4.0.4ubuntu2) to 4.0.4ubuntu2.2
bind9-host (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
ca-certificates (20080514-0ubuntu1) to 20080514-0ubuntu1.1
capplets-data (1:2.24.0.1-0ubuntu7) to 1:2.24.0.1-0ubuntu7.1
command-not-found (0.2.26ubuntu1) to 0.2.26ubuntu1.1
command-not-found-data (0.2.26ubuntu1) to 0.2.26ubuntu1.1
compiz (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
compiz-core (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
compiz-fusion-plugins-main (0.7.8-0ubuntu2) to 0.7.8-0ubuntu2.2
compiz-gnome (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
compiz-plugins (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
compiz-wrapper (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
console-setup (1.25ubuntu3) to 1.25ubuntu4
cups (1.3.9-2) to 1.3.9-2ubuntu3
cups-bsd (1.3.9-2) to 1.3.9-2ubuntu3
cups-client (1.3.9-2) to 1.3.9-2ubuntu3
cups-common (1.3.9-2) to 1.3.9-2ubuntu3
dnsutils (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
evolution (2.24.1-0ubuntu2) to 2.24.2-0ubuntu1
evolution-common (2.24.1-0ubuntu2) to 2.24.2-0ubuntu1
evolution-data-server (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
evolution-data-server-common (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
evolution-exchange (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
evolution-plugins (2.24.1-0ubuntu2) to 2.24.2-0ubuntu1
f-spot (0.5.0.3-0ubuntu2) to 0.5.0.3-0ubuntu4
firefox (3.0.3+nobinonly-0ubuntu2) to 3.0.4+nobinonly-0ubuntu0.8.10.1
firefox-3.0 (3.0.3+nobinonly-0ubuntu2) to 3.0.4+nobinonly-0ubuntu0.8.10.1
firefox-3.0-branding (3.0.3+nobinonly-0ubuntu2) to 3.0.4+nobinonly-0ubuntu0.8.10.1
firefox-3.0-gnome-support (3.0.3+nobinonly-0ubuntu2) to 3.0.4+nobinonly-0ubuntu0.8.10.1
firefox-gnome-support (3.0.3+nobinonly-0ubuntu2) to 3.0.4+nobinonly-0ubuntu0.8.10.1
gdm-guest-session (0.6) to 0.6.1
gedit (2.24.0-0ubuntu1) to 2.24.2-0ubuntu1
gedit-common (2.24.0-0ubuntu1) to 2.24.2-0ubuntu1
gnome-cards-data (1:2.24.1-0ubuntu2) to 1:2.24.1.1-0ubuntu1
gnome-control-center (1:2.24.0.1-0ubuntu7) to 1:2.24.0.1-0ubuntu7.1
gnome-games (1:2.24.1-0ubuntu2) to 1:2.24.1.1-0ubuntu1
gnome-games-data (1:2.24.1-0ubuntu2) to 1:2.24.1.1-0ubuntu1
gnome-panel (1:2.24.1-0ubuntu2) to 1:2.24.1-0ubuntu2.1
gnome-panel-data (1:2.24.1-0ubuntu2) to 1:2.24.1-0ubuntu2.1
gnome-pilot (2.0.15-2ubuntu3) to 2.0.15-2ubuntu4
gnome-power-manager (2.24.0-0ubuntu8) to 2.24.0-0ubuntu8.1
gnome-settings-daemon (2.24.0-0ubuntu3) to 2.24.0-0ubuntu3.3
gnome-terminal (2.24.1-0ubuntu1) to 2.24.1.1-0ubuntu1
gnome-terminal-data (2.24.1-0ubuntu1) to 2.24.1.1-0ubuntu1
hal-info (20081013-0ubuntu3) to 20081124-0ubuntu1~intrepid
human-theme (0.28.5) to 0.28.6
initramfs-tools (0.92bubuntu15) to 0.92bubuntu16
jockey-common (0.5~beta3-0ubuntu5) to 0.5~beta3-0ubuntu6.1
jockey-gtk (0.5~beta3-0ubuntu5) to 0.5~beta3-0ubuntu6.1
language-pack-en (1:8.10+20081025) to 1:8.10+20081107
language-pack-en-base (1:8.10+20081025) to 1:8.10+20081107
language-pack-gnome-en (1:8.10+20081025) to 1:8.10+20081107
language-pack-gnome-en-base (1:8.10+20081025) to 1:8.10+20081107
libapparmor-perl (2.3+1289-0ubuntu4) to 2.3+1289-0ubuntu4.1
libapparmor1 (2.3+1289-0ubuntu4) to 2.3+1289-0ubuntu4.1
libasound2-plugins (1.0.17-0ubuntu4) to 1.0.17-0ubuntu5
libbind9-40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libcamel1.2-14 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libcups2 (1.3.9-2) to 1.3.9-2ubuntu3
libcupsimage2 (1.3.9-2) to 1.3.9-2ubuntu3
libdecoration0 (1:0.7.8-0ubuntu4) to 1:0.7.8-0ubuntu4.1
libdeskbar-tracker (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
libdns43 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libebackend1.2-0 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libebook1.2-9 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libecal1.2-7 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libedata-book1.2-2 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libedata-cal1.2-6 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libedataserver1.2-11 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libedataserverui1.2-8 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libegroupwise1.2-13 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libexchange-storage1.2-3 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libgdata-google1.2-1 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libgdata1.2-1 (2.24.1-0ubuntu1) to 2.24.2-0ubuntu1
libglib2.0-0 (2.18.2-0ubuntu1) to 2.18.2-0ubuntu2
libglib2.0-data (2.18.2-0ubuntu1) to 2.18.2-0ubuntu2
libgnome-pilot2 (2.0.15-2ubuntu3) to 2.0.15-2ubuntu4
libgnome-window-settings1 (1:2.24.0.1-0ubuntu7) to 1:2.24.0.1-0ubuntu7.1
libgnomecanvas2-0 (2.20.1.1-1ubuntu2) to 2.20.1.1-1ubuntu3
libgnomecanvas2-common (2.20.1.1-1ubuntu2) to 2.20.1.1-1ubuntu3
libgnutls26 (2.4.1-1build1) to 2.4.1-1ubuntu0.2
libgphoto2-2 (2.4.2-0ubuntu2) to 2.4.2-0ubuntu3
libgphoto2-port0 (2.4.2-0ubuntu2) to 2.4.2-0ubuntu3
libgtkhtml-editor-common (1:3.24.1-0ubuntu1) to 1:3.24.1.1-0ubuntu1
libgtkhtml-editor0 (1:3.24.1-0ubuntu1) to 1:3.24.1.1-0ubuntu1
libgtkhtml3.14-19 (1:3.24.1-0ubuntu1) to 1:3.24.1.1-0ubuntu1
libgtksourceview2.0-0 (2.4.0-0ubuntu1) to 2.4.1-0ubuntu1
libgtksourceview2.0-common (2.4.0-0ubuntu1) to 2.4.1-0ubuntu1
libisc44 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libisccc40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libisccfg40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
liblwres40 (1:9.5.0.dfsg.P2-1ubuntu2) to 1:9.5.0.dfsg.P2-1ubuntu3
libnm-glib0 (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
libnm-util0 (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
libpam-modules (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.3
libpam-runtime (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.3
libpam0g (1.0.1-4ubuntu5) to 1.0.1-4ubuntu5.3
libpanel-applet2-0 (1:2.24.1-0ubuntu2) to 1:2.24.1-0ubuntu2.1
libpango1.0-0 (1.22.1-0ubuntu1) to 1.22.2-0ubuntu1
libpango1.0-common (1.22.1-0ubuntu1) to 1.22.2-0ubuntu1
libpulse-browse0 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libpulse0 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libpulsecore5 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
libshout3 (2.2.2-4) to 2.2.2-4ubuntu1
libsmbclient (2:3.2.3-1ubuntu3) to 2:3.2.3-1ubuntu3.3
libsnmp-base (5.4.1~dfsg-7.1ubuntu6) to 5.4.1~dfsg-7.1ubuntu6.1
libsnmp15 (5.4.1~dfsg-7.1ubuntu6) to 5.4.1~dfsg-7.1ubuntu6.1
libtotem-plparser12 (2.24.1-0ubuntu2) to 2.24.2-0ubuntu1
libtracker-gtk0 (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
libtrackerclient0 (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
libv4l-0 (0.5.0-3~intrepid1) to 0.5.6-1~intrepid1
libvolume-id0 (124-8) to 124-9
libwbclient0 (2:3.2.3-1ubuntu3) to 2:3.2.3-1ubuntu3.3
libx11-6 (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
libx11-data (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
libx11-xcb1 (2:1.1.5-2ubuntu1) to 2:1.1.5-2ubuntu1.1
libxml2 (2.6.32.dfsg-4ubuntu1) to 2.6.32.dfsg-4ubuntu1.1
libxml2-utils (2.6.32.dfsg-4ubuntu1) to 2.6.32.dfsg-4ubuntu1.1
linux-generic (2.6.27.7.11) to 2.6.27.9.13
linux-headers-2.6.27-7 (2.6.27-7.14) to 2.6.27-7.16
linux-headers-2.6.27-7-generic (2.6.27-7.14) to 2.6.27-7.16
linux-headers-generic (2.6.27.7.11) to 2.6.27.9.13
linux-image-2.6.27-7-generic (2.6.27-7.14) to 2.6.27-7.16
linux-image-generic (2.6.27.7.11) to 2.6.27.9.13
linux-libc-dev (2.6.27-7.14) to 2.6.27-9.19
linux-restricted-modules-common (2.6.27-7.12) to 2.6.27-9.13
linux-restricted-modules-generic (2.6.27.7.11) to 2.6.27.9.13
login (1:4.1.1-1ubuntu1) to 1:4.1.1-1ubuntu1.1
network-manager (0.7~~svn20081018t105859-0ubuntu1) to 0.7~~svn20081018t105859-0ubuntu1.8.10.1
network-manager-gnome (0.7~~svn20081020t000444-0ubuntu1) to 0.7~~svn20081020t000444-0ubuntu1.8.10.1
nvidia-96-modaliases (96.43.05-0ubuntu10) to 96.43.09-0ubuntu1
openoffice.org-base-core (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-calc (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-common (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-core (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-draw (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-emailmerge (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-gnome (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-gtk (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-impress (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-math (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-style-human (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
openoffice.org-writer (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
passwd (1:4.1.1-1ubuntu1) to 1:4.1.1-1ubuntu1.1
pm-utils (1.1.2.4-1ubuntu7) to 1.1.2.4-1ubuntu8
ppp (2.4.4rel-10ubuntu2) to 2.4.4rel-10ubuntu2.8.10.1
procps (1:3.2.7-9ubuntu2) to 1:3.2.7-9ubuntu2.1
pulseaudio (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-esound-compat (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-gconf (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-hal (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-module-x11 (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
pulseaudio-utils (0.9.10-2ubuntu9) to 0.9.10-2ubuntu9.1
python-libxml2 (2.6.32.dfsg-4ubuntu1) to 2.6.32.dfsg-4ubuntu1.1
python-software-properties (0.68) to 0.68.1
python-uno (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
rhythmbox (0.11.6svn20081008-0ubuntu4) to 0.11.6svn20081008-0ubuntu4.2
samba-common (2:3.2.3-1ubuntu3) to 2:3.2.3-1ubuntu3.3
smbclient (2:3.2.3-1ubuntu3) to 2:3.2.3-1ubuntu3.3
software-properties-gtk (0.68) to 0.68.1
splix (2.0.0~rc2-0ubuntu2) to 2.0.0~rc2-0ubuntu2.3
system-tools-backends (2.6.0-1ubuntu1) to 2.6.0-1ubuntu1.1
totem (2.24.2-0ubuntu4) to 2.24.3-0ubuntu1
totem-common (2.24.2-0ubuntu4) to 2.24.3-0ubuntu1
totem-gstreamer (2.24.2-0ubuntu4) to 2.24.3-0ubuntu1
totem-mozilla (2.24.2-0ubuntu4) to 2.24.3-0ubuntu1
totem-plugins (2.24.2-0ubuntu4) to 2.24.3-0ubuntu1
tracker (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
tracker-search-tool (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
tracker-utils (0.6.6-1ubuntu5) to 0.6.6-1ubuntu5.1
transmission-common (1.34-0ubuntu2) to 1.34-0ubuntu2.1
transmission-gtk (1.34-0ubuntu2) to 1.34-0ubuntu2.1
ttf-opensymbol (1:2.4.1-11ubuntu2) to 1:2.4.1-11ubuntu2.1
ubufox (0.6-0ubuntu1) to 0.6-0ubuntu1.8.10.1
udev (124-8) to 124-9
update-manager (1:0.93.32) to 1:0.93.34
update-manager-core (1:0.93.32) to 1:0.93.34
vinagre (2.24.1-0ubuntu1) to 2.24.1-0ubuntu1.1
xkb-data (1.3-2ubuntu4) to 1.3-2ubuntu4.4
xserver-xorg-input-evdev (1:2.0.99+git20080912-0ubuntu5) to 1:2.0.99+git20080912-0ubuntu6
xserver-xorg-input-vmmouse (1:12.5.1-1ubuntu5) to 1:12.5.1-1ubuntu5.1
xulrunner-1.9 (1.9.0.3+nobinonly-0ubuntu1) to 1.9.0.4+nobinonly-0ubuntu0.8.10.1
xulrunner-1.9-gnome-support (1.9.0.3+nobinonly-0ubuntu1) to 1.9.0.4+nobinonly-0ubuntu0.8.10.1

Installed the following packages:
linux-headers-2.6.27-9 (2.6.27-9.19)
linux-headers-2.6.27-9-generic (2.6.27-9.19)
linux-image-2.6.27-9-generic (2.6.27-9.19)
linux-restricted-modules-2.6.27-9-generic (2.6.27-9.13)

Thanks a lot

Wilf

---

### Post by alex.rayu on 2008-12-16
Thats an epedemy here - PulseAudio crashes after updates. No easy way to fix. Most advise removing it. The problem is specific to Gnome.

---

### Post by Dr.Suave on 2008-12-17
Tried removing pulseaudio, but sounds were still crackly.

Have reinstalled, removed pulseaudio, and unchecked the offending updates so they don't install.

However, this is my girlfriend's laptop, and I'd rather be able to give her a fully working system to use - anyone know how to make it so Pulseaudio NEVER updates? (Even though I've removed it, I just want to be sure it will never cause ANY problems! :) )

---

