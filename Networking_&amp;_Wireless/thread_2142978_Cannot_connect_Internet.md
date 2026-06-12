---
title: "Cannot connect Internet"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by Abbeyww on 2013-05-07
Hi. 
A while back I updated all of thethings that the Update manager suggested. Since there were so manythings that needed upgrading, it took a very long time. After Irestated my laptop and my internet connection wasn't connecting. Itried to undo some updates thinking it would solve the problem, butnothing happened. I left it alone for about 6 months and come back toit as I need it to do some work. At the top where the connection signis, there is an exclamation mark right on it. I also tried typing inifconfig in the terminal and this came up: 


lo                 link encap:Local Loopback
inet addr:127.0.01Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACKRUNNING MTU:16436 Metric:1
RX packets:12errors:0 dropped:0 overruns:0 frame:0
TX packets:12errors:0 dropped:0 overruns:0 carrier:0
collisions:0txqeuelen:0
RX bytes:720(720.0 B) TX bytes:720 (720.0 B)


Also, in my network connection under'wired' it has 'Wired connection 1'
I don't know much about computers so Ireally don't know what to do. I would appreciate any help I can get.

---

### Post by Hadaka on 2013-05-07
Hi,what version of ubuntu? 12.04? and do you
recall what you attempted to "undo" ? From your
ifconfig output we see there is no wireless or wired
listed. please open a terminal ctrl/alt/t and then COPY
and paste this command.
```
lspci -nn | egrep '0200|0280'
```
thanks.

---

### Post by Abbeyww on 2013-05-25
I'm sorry for the late reply!

The laptop I am using is Ubuntu 10.04 LTS 32 bit. 
I'm not 100% sure of what I did. I was told to upgrade everything that the Upgrade Manager suggested and so I did. After that the Internet connection went missing. Looking at the history of installed, upgraded and removed software packages, I tried to remove what I thought was the cause of it but re-installed it incase I did something worse to it. After that I haven't touched anything since.

The history says:
```

10/26/2012 (09:45) - Installed: 
[SIZE=1]network-manager (0.8-ubuntu3.3)
network-manager-gnome (0.8-ubuntu3.3)
[/SIZE]
10/26/2012 (09:40) - Removed:
[SIZE=1]network-manager
network-manager-gnome[/SIZE]

10/25/2012 (10:52) - Upgraded:
[FONT=verdana][SIZE=1][COLOR=#000000]acpid (1.0.10-5ubuntu2.1) to1.0.10-5ubuntu2.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]adobe-flash-properties-gtk(11.1.102.62-0lucid1) to 11.2.202.243-0lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]adobe-flashplugin (11.1.102.62-0lucid1) to11.2.202.243-0lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]app-install-data-partner (12.10.04.3) to12.10.04.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apparmor (2.5-0ubuntu3) to2.5.1-0ubuntu0.10.04.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apparmor-utils (2.5-0ubuntu3) to2.5.1-0ubuntu0.10.04.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apport (1.13.3-0ubuntu2) to1.13.3-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apport-gtk (1.13.3-0ubuntu2) to1.13.3-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apt (0.7.25.3ubuntu9.1) to 0.7.25.3ubuntu9.14[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apt-transport-https (0.7.25.3ubuntu9.1) to0.7.25.3ubuntu9.14[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apt-utils (0.7.25.3ubuntu9.1) to0.7.25.3ubuntu9.14[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]aptitude (0.4.11.11-1ubuntu10) to0.4.11.11-1ubuntu10lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apturl (0.4.1ubuntu4) to 0.4.1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]apturl-common (0.4.1ubuntu4) to0.4.1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]at (3.1.11-1ubuntu5) to 3.1.11-1ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]avahi-autoipd (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]avahi-daemon (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]avahi-utils (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]base-files (5.0.0ubuntu20.10.04.2) to5.0.0ubuntu20.10.04.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]bind9-host (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]binutils (2.20.1-3ubuntu7) to2.20.1-3ubuntu7.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]brasero (2.30.2-0ubuntu1) to2.30.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]brasero-common (2.30.2-0ubuntu1) to2.30.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]bsdutils (1:2.17.2-0ubuntu1) to1:2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]byobu (2.68-0ubuntu1.1) to 2.68-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]bzip2 (1.0.5-4) to 1.0.5-4ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ca-certificates (20090814) to20090814ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ca-certificates-java (20100406ubuntu1) to20100406ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]capplets-data (1:2.30.1-0ubuntu1) to1:2.30.1-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]checkbox (0.9.1) to 0.9.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]checkbox-gtk (0.9.1) to 0.9.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]compiz (1:0.8.4-0ubuntu15) to1:0.8.4-0ubuntu15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]compiz-core (1:0.8.4-0ubuntu15) to1:0.8.4-0ubuntu15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]compiz-gnome (1:0.8.4-0ubuntu15) to1:0.8.4-0ubuntu15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]compiz-plugins (1:0.8.4-0ubuntu15) to1:0.8.4-0ubuntu15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]compizconfig-backend-gconf (0.8.4-0ubuntu2)to 0.8.4-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]consolekit (0.4.1-3ubuntu1) to0.4.1-3ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]coreutils (7.4-2ubuntu2) to 7.4-2ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cpp-4.4 (4.4.3-4ubuntu5) to 4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cron (3.0pl1-106ubuntu5) to3.0pl1-106ubuntu7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cups (1.4.3-1ubuntu1.2) to 1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cups-bsd (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cups-client (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cups-common (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cups-driver-gutenprint (5.2.5-0ubuntu1) to5.2.5-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]curl (7.19.7-1ubuntu1) to 7.19.7-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]cvs (1:1.12.13-12ubuntu1) to1:1.12.13-12ubuntu1.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dbus (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dbus-x11 (1.2.16-2ubuntu4) to1.2.16-2ubuntu4.7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]desktopcouch (0.6.4-0ubuntu3) to0.6.4-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dhcp3-client (3.1.3-2ubuntu3) to3.1.3-2ubuntu3.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dhcp3-common (3.1.3-2ubuntu3) to3.1.3-2ubuntu3.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dmsetup (2:1.02.39-1ubuntu4) to2:1.02.39-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dnsmasq-base (2.52-1) to 2.52-1ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dnsutils (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dpkg (1.15.5.6ubuntu4.1) to1.15.5.6ubuntu4.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]dpkg-dev (1.15.5.6ubuntu4.4) to1.15.5.6ubuntu4.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]e2fslibs (1.41.11-1ubuntu2) to1.41.11-1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]e2fsprogs (1.41.11-1ubuntu2) to1.41.11-1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]empathy (2.30.2-0ubuntu1) to2.30.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]empathy-common (2.30.2-0ubuntu1) to2.30.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-base (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-crypto (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-inets (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-mnesia (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-public-key (1:13.b.3-dfsg-2ubuntu2)to 1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-runtime-tools(1:13.b.3-dfsg-2ubuntu2) to 1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-ssl (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-syntax-tools (1:13.b.3-dfsg-2ubuntu2)to 1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]erlang-xmerl (1:13.b.3-dfsg-2ubuntu2) to1:13.b.3-dfsg-2ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evince (2.30.3-0ubuntu1.1) to2.30.3-0ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evolution (2.28.3-0ubuntu10) to2.28.3-0ubuntu10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evolution-common (2.28.3-0ubuntu10) to2.28.3-0ubuntu10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evolution-data-server (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evolution-data-server-common(2.28.3.1-0ubuntu5) to 2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]evolution-plugins (2.28.3-0ubuntu10) to2.28.3-0ubuntu10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ffmpeg (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]fglrx-modaliases (2:8.723.1-0ubuntu4) to2:8.723.1-0ubuntu6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]firefox(3.6.9+build1+nobinonly-0ubuntu0.10.04.1) to 16.0.1+build1-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]firefox-branding(3.6.9+build1+nobinonly-0ubuntu0.10.04.1) to 16.0.1+build1-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]firefox-gnome-support(3.6.9+build1+nobinonly-0ubuntu0.10.04.1) to 16.0.1+build1-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]foomatic-filters (4.0.4-0ubuntu1) to4.0.4-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]fuse-utils (2.8.1-1.1ubuntu2) to2.8.1-1.1ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]g++-4.4 (4.4.3-4ubuntu5) to 4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gcalctool (5.30.0.is.5.28.2-0ubuntu2) to5.30.0.is.5.28.2-0ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gcc-4.4 (4.4.3-4ubuntu5) to 4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gcc-4.4-base (4.4.3-4ubuntu5) to4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gdm (2.30.2.is.2.30.0-0ubuntu3) to2.30.2.is.2.30.0-0ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gdm-guest-session (0.15) to 0.15ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ghostscript (8.71.dfsg.1-0ubuntu5.3) to8.71.dfsg.1-0ubuntu5.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ghostscript-cups (8.71.dfsg.1-0ubuntu5.3) to8.71.dfsg.1-0ubuntu5.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ghostscript-x (8.71.dfsg.1-0ubuntu5.3) to8.71.dfsg.1-0ubuntu5.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gimp (2.6.8-2ubuntu1.1) to 2.6.8-2ubuntu1.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gimp-data (2.6.8-2ubuntu1.1) to2.6.8-2ubuntu1.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-control-center (1:2.30.1-0ubuntu1) to1:2.30.1-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-power-manager (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-screensaver (2.30.0-0ubuntu2) to2.30.0-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-settings-daemon (2.30.1-0ubuntu1) to2.30.1-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-system-tools (2.30.0-0ubuntu2) to2.30.0-0ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-terminal (2.29.6-0ubuntu5) to2.30.2-0ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-terminal-data (2.29.6-0ubuntu5) to2.30.2-0ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-user-guide (2.30.0+git20100403ubuntu2)to 2.30.0+git20100403ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-user-guide-en(2.30.0+git20100403ubuntu2) to 2.30.0+git20100403ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnome-utils (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnupg (1.4.10-2ubuntu1) to 1.4.10-2ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gnupg-curl (1.4.10-2ubuntu1) to1.4.10-2ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gpgv (1.4.10-2ubuntu1) to 1.4.10-2ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]grub-common (1.98-1ubuntu7) to1.98-1ubuntu13[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]grub-pc (1.98-1ubuntu7) to 1.98-1ubuntu13[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gtk2-engines-pixbuf (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gwibber (2.30.2-0ubuntu1) to 2.30.3-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gwibber-service (2.30.2-0ubuntu1) to2.30.3-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]gzip (1.3.12-9ubuntu1) to 1.3.12-9ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]hpijs (3.10.2-2ubuntu2) to 3.10.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]hplip (3.10.2-2ubuntu2) to 3.10.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]hplip-data (3.10.2-2ubuntu2) to3.10.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]icedtea-6-jre-cacao (6b18-1.8.1-0ubuntu1) to6b24-1.11.4-1ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]icedtea6-plugin (6b18-1.8.1-0ubuntu1) to6b21.2-2ubuntu0.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ifupdown (0.6.8ubuntu29.1) to0.6.8ubuntu29.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]imagemagick (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]indicator-sound (0.2.3-0ubuntu1) to0.2.6-0ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]initscripts (2.87dsf-4ubuntu17) to2.87dsf-4ubuntu17.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]insserv (1.12.0-14) to 1.12.0-14ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdebase-runtime (4:4.4.2-0ubuntu4.1) to4:4.4.5-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdebase-runtime-data (4:4.4.2-0ubuntu4.1) to4:4.4.5-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdelibs-bin (4:4.4.2-0ubuntu4) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdelibs5 (4:4.4.2-0ubuntu4) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdelibs5-data (4:4.4.2-0ubuntu4) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdepimlibs-data (4:4.4.2-0ubuntu2.1) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdepimlibs5 (4:4.4.2-0ubuntu2.1) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]kdesudo (3.4.2.3-0ubuntu1) to3.4.2.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]language-pack-en (1:10.04+20100714) to1:10.04+20110931[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]language-pack-en-base (1:10.04+20100714) to1:10.04+20110931[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]language-pack-gnome-en (1:10.04+20100714) to1:10.04+20110931[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]language-pack-gnome-en-base(1:10.04+20100714) to 1:10.04+20110931[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libapparmor-perl (2.5-0ubuntu3) to2.5.1-0ubuntu0.10.04.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libapparmor1 (2.5-0ubuntu3) to2.5.1-0ubuntu0.10.04.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libarchive1 (2.8.0-2) to 2.8.0-2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-client3 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-common-data (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-common3 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-core6 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-glib1 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-gobject0 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavahi-ui0 (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavcodec-extra-52 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavdevice52 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavfilter0 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavformat52 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libavutil-extra-49 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libbind9-60 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libblkid1 (2.17.2-0ubuntu1) to2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libbrasero-media0 (2.30.2-0ubuntu1) to2.30.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libbz2-1.0 (1.0.5-4) to 1.0.5-4ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libc-bin (2.11.1-0ubuntu7.2) to2.11.1-0ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libc-dev-bin (2.11.1-0ubuntu7.2) to2.11.1-0ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libc6 (2.11.1-0ubuntu7.2) to2.11.1-0ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libc6-dev (2.11.1-0ubuntu7.2) to2.11.1-0ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libc6-i686 (2.11.1-0ubuntu7.2) to2.11.1-0ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcamel1.2-14 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libck-connector0 (0.4.1-3ubuntu1) to0.4.1-3ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcomerr2 (1.41.11-1ubuntu2) to1.41.11-1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcouchdb-glib-1.0-2 (0.6.3-0ubuntu1) to 0.6.3-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcups2 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcupscgi1 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcupsdriver1 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcupsimage2 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcupsmime1 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcupsppdc1 (1.4.3-1ubuntu1.2) to1.4.3-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcurl3 (7.19.7-1ubuntu1) to7.19.7-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libcurl3-gnutls (7.19.7-1ubuntu1) to7.19.7-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdbus-1-3 (1.2.16-2ubuntu4) to1.2.16-2ubuntu4.7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdbus-glib-1-2 (0.84-1) to 0.84-1ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdecoration0 (1:0.8.4-0ubuntu15) to1:0.8.4-0ubuntu15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdesktopcouch-glib-1.0-2 (0.6.3-0ubuntu1)to 0.6.3-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdevkit-power-gobject1 (1:0.9.1-1) to1:0.9.1-1ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdevmapper1.02.1 (2:1.02.39-1ubuntu4) to2:1.02.39-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libdns64 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libebackend1.2-0 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libebook1.2-9 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libecal1.2-7 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libedata-book1.2-2 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libedata-cal1.2-6 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libedataserver1.2-11 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libedataserverui1.2-8 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libegroupwise1.2-13 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libevdocument2 (2.30.3-0ubuntu1.1) to2.30.3-0ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libevview2 (2.30.3-0ubuntu1.1) to2.30.3-0ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libexchange-storage1.2-3 (2.28.3.1-0ubuntu5)to 2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libexif12 (0.6.19-1) to 0.6.19-1ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libexpat1 (2.0.1-7ubuntu1) to2.0.1-7ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libfreetype6 (2.3.11-1ubuntu2.2) to2.3.11-1ubuntu2.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libfuse2 (2.8.1-1.1ubuntu2) to2.8.1-1.1ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgail-common (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgail18 (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgc1c2 (1:6.8-1.2ubuntu1) to1:6.8-1.2ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgcc1 (1:4.4.3-4ubuntu5) to1:4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgcrypt11 (1.4.4-5ubuntu2) to1.4.4-5ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdata-common (0.5.2-0ubuntu1) to0.5.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdata-google1.2-1 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdata1.2-1 (2.28.3.1-0ubuntu5) to2.28.3.1-0ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdata6 (0.5.2-0ubuntu1) to0.5.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdict-1.0-6 (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgdiplus (2.4.2-1build1) to2.4.2-1ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgimp2.0 (2.6.8-2ubuntu1.1) to2.6.8-2ubuntu1.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgksu2-0 (2.0.13~pre1-1ubuntu4) to2.0.13~pre1-1ubuntu4.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgl1-mesa-dri (7.7.1-1ubuntu3) to7.7.1-1ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgl1-mesa-glx (7.7.1-1ubuntu3) to7.7.1-1ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libglu1-mesa (7.7.1-1ubuntu3) to7.7.1-1ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgnome-window-settings1(1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgnutls26 (2.8.5-2) to 2.8.5-2ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgomp1 (4.4.3-4ubuntu5) to4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgs8 (8.71.dfsg.1-0ubuntu5.3) to8.71.dfsg.1-0ubuntu5.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.2) to1.8.1+dfsg-2ubuntu0.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgtk-vnc-1.0-0 (0.3.10-2ubuntu2) to0.3.10-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgtk2.0-0 (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgtk2.0-bin (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgtk2.0-common (2.20.1-0ubuntu2) to2.20.1-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgudev-1.0-0 (1:151-12.1) to 1:151-12.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgutenprint2 (5.2.5-0ubuntu1) to5.2.5-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgweather-common (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libgweather1 (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libhpmud0 (3.10.2-2ubuntu2) to3.10.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libicu42 (4.2.1-3) to 4.2.1-3ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libimobiledevice0 (0.9.7-1ubuntu1) to0.9.7-1ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libisc60 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libisccc60 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libisccfg60 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libjasper1 (1.900.1-7) to1.900.1-7ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libk5crypto3 (1.8.1+dfsg-2ubuntu0.2) to1.8.1+dfsg-2ubuntu0.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libkrb5-3 (1.8.1+dfsg-2ubuntu0.2) to1.8.1+dfsg-2ubuntu0.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libkrb5support0 (1.8.1+dfsg-2ubuntu0.2) to1.8.1+dfsg-2ubuntu0.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]liblcms1 (1.18.dfsg-1ubuntu2) to1.18.dfsg-1ubuntu2.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libldap-2.4-2 (2.4.21-0ubuntu5.3) to2.4.21-0ubuntu5.7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]liblircclient0 (0.8.6-0ubuntu4.1) to0.8.6-0ubuntu4.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]liblwres60 (1:9.7.0.dfsg.P1-1) to1:9.7.0.dfsg.P1-1ubuntu0.8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmagickcore2 (7:6.5.7.8-1ubuntu1) to7:6.5.7.8-1ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmagickcore2-extra (7:6.5.7.8-1ubuntu1) to7:6.5.7.8-1ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmagickwand2 (7:6.5.7.8-1ubuntu1) to7:6.5.7.8-1ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmetacity-private0 (1:2.30.1-0ubuntu1) to1:2.30.1-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmodplug0c2 (1:0.8.7-1build1) to1:0.8.7-1ubuntu0.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-cairo2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-corlib2.0-cil (2.4.4~svn151842-1ubuntu4)to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-data-tds2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-i18n-west2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-posix2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-security2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-sharpzip2.84-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-sqlite2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-system-data2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-system-runtime2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-system-web2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono-system2.0-cil(2.4.4~svn151842-1ubuntu4) to 2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libmono2.0-cil (2.4.4~svn151842-1ubuntu4) to2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libnautilus-extension1 (1:2.30.1-0ubuntu1.1)to 1:2.30.1-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libnm-glib2 (0.8-0ubuntu3) to 0.8-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libnm-util1 (0.8-0ubuntu3) to 0.8-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libnspr4-0d (4.8.4-0ubuntu1) to4.8.6-0ubuntu0.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libnss3-1d (3.12.6-0ubuntu3) to3.12.9+ckbi-1.82-0ubuntu0.10.04.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpam-ck-connector (0.4.1-3ubuntu1) to0.4.1-3ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpam-modules (1.1.1-2ubuntu5) to1.1.1-2ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpam-runtime (1.1.1-2ubuntu5) to1.1.1-2ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpam0g (1.1.1-2ubuntu5) to1.1.1-2ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpango1.0-0 (1.28.0-0ubuntu2) to1.28.0-0ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpango1.0-common (1.28.0-0ubuntu2) to1.28.0-0ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libparted0debian1 (2.2-5ubuntu5.1) to2.2-5ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpcsclite1 (1.5.3-1ubuntu4.1) to 1.5.3-1ubuntu4.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libperl5.10 (5.10.1-8ubuntu2) to5.10.1-8ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libphonon4 (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libplasma3 (4:4.4.2-0ubuntu4) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libplymouth2 (0.8.2-2ubuntu2) to0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpng12-0 (1.2.42-1ubuntu2.1) to1.2.42-1ubuntu2.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpolkit-agent-1-0 (0.96-2) to0.96-2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpolkit-backend-1-0 (0.96-2) to0.96-2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpolkit-gobject-1-0 (0.96-2) to0.96-2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpoppler-glib4 (0.12.4-0ubuntu5) to0.12.4-0ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpoppler5 (0.12.4-0ubuntu5) to0.12.4-0ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpostproc51 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpurple-bin (1:2.6.6-1ubuntu4) to1:2.6.6-1ubuntu4.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpurple0 (1:2.6.6-1ubuntu4) to1:2.6.6-1ubuntu4.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libpython2.6 (2.6.5-1ubuntu6) to2.6.5-1ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-assistant (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-dbus (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-designer (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-gui (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-help (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-network (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-opengl (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-qt3support (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-script (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-scripttools (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-sql (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-sql-sqlite (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-svg (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-test (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-webkit (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-xml (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqt4-xmlpatterns (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqtcore4 (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libqtgui4 (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libraptor1 (1.4.21-1ubuntu1) to1.4.21-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]librsvg2-2 (2.26.3-0ubuntu1) to2.26.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]librsvg2-common (2.26.3-0ubuntu1) to2.26.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libslp1 (1.2.1-7.6) to 1.2.1-7.6ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsmbclient (2:3.4.7~dfsg-1ubuntu3.1) to2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsndfile1 (1.0.21-2) to1.0.21-2ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsnmp-base(5.4.2.1~dfsg0ubuntu1-0ubuntu2.1) to 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1)to 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsoup-gnome2.4-1 (2.30.2-0ubuntu0.1) to2.30.2-0ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libsoup2.4-1 (2.30.2-0ubuntu0.1) to2.30.2-0ubuntu0.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libss2 (1.41.11-1ubuntu2) to1.41.11-1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libssl0.9.8 (0.9.8k-7ubuntu8) to0.9.8k-7ubuntu8.13[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libstdc++6 (4.4.3-4ubuntu5) to 4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libstdc++6-4.4-dev (4.4.3-4ubuntu5) to4.4.3-4ubuntu5.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libswscale0 (4:0.5.1-1ubuntu1) to4:0.5.9-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libtasn1-3 (2.4-1) to 2.4-1ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libtiff4 (3.9.2-2ubuntu0.3) to3.9.2-2ubuntu0.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libudev0 (151-12.1) to 151-12.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libupower-glib1 (0.9.1-1) to 0.9.1-1ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libuuid1 (2.17.2-0ubuntu1) to2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libvorbis0a (1.2.3-3ubuntu1) to1.2.3-3ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libvorbisenc2 (1.2.3-3ubuntu1) to1.2.3-3ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libvorbisfile3 (1.2.3-3ubuntu1) to1.2.3-3ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libwbclient0 (2:3.4.7~dfsg-1ubuntu3.9) to2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libwebkit-1.0-2 (1.2.0-1) to1.2.7-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libwebkit-1.0-common (1.2.0-1) to1.2.7-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libxfont1 (1:1.4.1-1) to 1:1.4.1-1ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libxml2 (2.7.6.dfsg-1ubuntu1) to 2.7.6.dfsg-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libxml2-utils (2.7.6.dfsg-1ubuntu1) to2.7.6.dfsg-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]libxslt1.1 (1.1.26-1ubuntu1) to1.1.26-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-firmware (1.34.1) to 1.34.14[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-generic (2.6.32.24.25) to 2.6.32.44.51[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-headers-2.6.32-24 (2.6.32-24.42) to 2.6.32-24.43[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-headers-2.6.32-24-generic(2.6.32-24.42) to 2.6.32-24.43[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-headers-generic (2.6.32.24.25) to2.6.32.44.51[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-image-2.6.32-24-generic (2.6.32-24.42)to 2.6.32-24.43[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-image-generic (2.6.32.24.25) to2.6.32.44.51[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]linux-libc-dev (2.6.32-24.42) to2.6.32-44.98[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]login (1:4.1.4.2-1ubuntu2) to1:4.1.4.2-1ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]logrotate (3.7.8-4ubuntu2) to3.7.8-4ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-base (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-core (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-cxx (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-desktop (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-graphics (4.0-0ubuntu8) to4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-invalid-mta (4.0-0ubuntu8) to4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-printing (4.0-0ubuntu8) to4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]lsb-release (4.0-0ubuntu8) to 4.0-0ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]man-db (2.5.7-2) to 2.5.7-2ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]media-player-info (6-1) to 16-1~lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]metacity (1:2.30.1-0ubuntu1) to1:2.30.1-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]metacity-common (1:2.30.1-0ubuntu1) to1:2.30.1-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mobile-broadband-provider-info (20100407-1)to 20111113-1ubuntu0.10.04[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]modemmanager (0.3-0ubuntu2) to0.3-0ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mono-2.0-gac (2.4.4~svn151842-1ubuntu4) to2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mono-gac (2.4.4~svn151842-1ubuntu4) to2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mono-runtime (2.4.4~svn151842-1ubuntu4) to2.4.4~svn151842-1ubuntu4.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mount (2.17.2-0ubuntu1) to2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]mountall (2.15.2) to 2.15.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nautilus (1:2.30.1-0ubuntu1.1) to1:2.30.1-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nautilus-data (1:2.30.1-0ubuntu1.1) to1:2.30.1-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nautilus-sendto-empathy (2.30.2-0ubuntu1) to2.30.3-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]network-manager (0.8-0ubuntu3) to0.8-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]network-manager-gnome (0.8-0ubuntu3) to0.8-0ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ntpdate (1:4.2.4p8+dfsg-1ubuntu2) to1:4.2.4p8+dfsg-1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nvidia-173-modaliases (173.14.22-0ubuntu11)to 173.14.22-0ubuntu11.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nvidia-96-modaliases (96.43.17-0ubuntu1) to96.43.17-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]nvidia-current-modaliases(195.36.24-0ubuntu1~10.04) to 195.36.24-0ubuntu1~10.04.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openjdk-6-jre (6b18-1.8.1-0ubuntu1) to6b24-1.11.4-1ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1)to 6b24-1.11.4-1ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openjdk-6-jre-lib (6b18-1.8.1-0ubuntu1) to6b24-1.11.4-1ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-base-core(1:3.2.0-7ubuntu4.1) to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-calc (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-common (1:3.2.0-7ubuntu4.1)to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-core (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-draw (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-emailmerge(1:3.2.0-7ubuntu4.1) to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-gnome (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-gtk (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-impress (1:3.2.0-7ubuntu4.1)to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-math (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-style-human(1:3.2.0-7ubuntu4.1) to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openoffice.org-writer (1:3.2.0-7ubuntu4.1)to 1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openssh-client (1:5.3p1-3ubuntu4) to1:5.3p1-3ubuntu7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]openssl (0.9.8k-7ubuntu8) to0.9.8k-7ubuntu8.13[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]oxygen-icon-theme (4:4.4.2-0ubuntu2) to4:4.4.5-0ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]parted (2.2-5ubuntu5.1) to 2.2-5ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]passwd (1:4.1.4.2-1ubuntu2) to1:4.1.4.2-1ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]perl (5.10.1-8ubuntu2) to 5.10.1-8ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]perl-base (5.10.1-8ubuntu2) to5.10.1-8ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]perl-modules (5.10.1-8ubuntu2) to5.10.1-8ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]phonon (4:4.6.2-0ubuntu5.1) to4:4.6.2-0ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plasma-scriptengine-javascript(4:4.4.2-0ubuntu4.1) to 4:4.4.5-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plymouth (0.8.2-2ubuntu2) to0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plymouth-label (0.8.2-2ubuntu2) to0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2)to 0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plymouth-theme-ubuntu-text (0.8.2-2ubuntu2)to 0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]plymouth-x11 (0.8.2-2ubuntu2) to0.8.2-2ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]pm-utils (1.3.0-1ubuntu2) to 1.3.0-1ubuntu3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]policykit-1 (0.96-2) to 0.96-2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]poppler-utils (0.12.4-0ubuntu5) to0.12.4-0ubuntu5.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]procps (1:3.2.8-1ubuntu4) to1:3.2.8-1ubuntu4.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-apport (1.13.3-0ubuntu2) to1.13.3-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-apt (0.7.94.2ubuntu6.2) to0.7.94.2ubuntu6.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-avahi (0.6.25-1ubuntu6) to0.6.25-1ubuntu6.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-crypto (2.0.1+dfsg1-4ubuntu2) to2.0.1+dfsg1-4ubuntu2.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-desktopcouch (0.6.4-0ubuntu3) to0.6.4-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-desktopcouch-records (0.6.4-0ubuntu3)to 0.6.4-0ubuntu3.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-gnomeapplet (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-gnomekeyring (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-httplib2 (0.6.0-1) to0.7.2-1ubuntu2~0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-imaging (1.1.7-1) to 1.1.7-1ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-kde4 (4:4.4.2-0ubuntu2) to4:4.4.5-0ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-lazr.restfulclient(0.9.11-1ubuntu1.1) to 0.9.11-1ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-libxml2 (2.7.6.dfsg-1ubuntu1) to2.7.6.dfsg-1ubuntu1.6[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-mako (0.2.5-2ubuntu1) to0.2.5-2ubuntu1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-pam (0.4.2-12.1ubuntu1) to0.4.2-12.1ubuntu1.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-papyon (0.4.8-0ubuntu1) to0.4.8-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-problem-report (1.13.3-0ubuntu2) to1.13.3-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-qt4 (4.7.2-0ubuntu1) to4.7.2-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-software-properties (0.75.10) to0.75.10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-ubuntuone-client (1.2.2-0ubuntu2) to1.2.2-0ubuntu2.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-ubuntuone-storageprotocol(1.2.0-0ubuntu1) to 1.2.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-uno (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-wadllib (1.1.4-1ubuntu1) to1.1.4-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python-wnck (2.30.0-0ubuntu1) to2.30.0-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python2.6 (2.6.5-1ubuntu6) to2.6.5-1ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]python2.6-minimal (2.6.5-1ubuntu6) to2.6.5-1ubuntu6.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]rdesktop (1.6.0-2ubuntu3) to1.6.0-2ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]rsync (3.0.7-1ubuntu1) to 3.0.7-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]rsyslog (4.2.0-2ubuntu8) to 4.2.0-2ubuntu8.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]samba-common (2:3.4.7~dfsg-1ubuntu3.9) to2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]samba-common-bin (2:3.4.7~dfsg-1ubuntu3.1)to 2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]screen (4.0.3-14ubuntu1) to4.0.3-14ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]skype (2.2.0.35-0lucid1) to 4.0.0.8-0lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]smbclient (2:3.4.7~dfsg-1ubuntu3.9) to2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]software-properties-gtk (0.75.10) to0.75.10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]software-properties-kde (0.75.10.1) to0.75.10.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ssh-askpass-gnome (1:5.3p1-3ubuntu4) to1:5.3p1-3ubuntu7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]sudo (1.7.2p1-1ubuntu5.2) to1.7.2p1-1ubuntu5.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]system-tools-backends (2.9.4-0ubuntu1) to2.9.4-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]sysv-rc (2.87dsf-4ubuntu17) to2.87dsf-4ubuntu17.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]sysvinit-utils (2.87dsf-4ubuntu17) to2.87dsf-4ubuntu17.5[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]tar (1.22-2) to 1.22-2ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]telepathy-gabble (0.8.12-0ubuntu1) to0.8.12-0ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]tomboy (1.2.1-0ubuntu1) to 1.2.2-0ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ttf-mscorefonts-installer (3.2) to3.2ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ttf-opensymbol (1:3.2.0-7ubuntu4.1) to1:3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ttf-thai-tlwg (1:0.4.13-4) to1:0.4.13-4ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]tzdata (2010l-0ubuntu0.10.04) to2012e-0ubuntu0.10.04[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]tzdata-java (2010l-0ubuntu0.10.04) to2012e-0ubuntu0.10.04[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ubufox (0.9~rc2-0ubuntu2.1) to2.1.1-0ubuntu0.10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ubuntuone-client (1.2.2-0ubuntu2) to1.2.2-0ubuntu2.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ubuntuone-client-gnome (1.2.2-0ubuntu2) to1.2.2-0ubuntu2.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]udev (151-12.1) to 151-12.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]unattended-upgrades (0.55ubuntu4) to0.55ubuntu7[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4.1) to1.6.0+OOo3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-inetd (4.35) to 4.35ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-manager (1:0.134.10) to 1:0.134.12.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-manager-core (1:0.134.10) to1:0.134.12.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-manager-kde (1:0.134.11) to1:0.134.12.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-notifier (0.99.3) to 0.99.3ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]update-notifier-common (0.99.3) to0.99.3ubuntu0.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]upower (0.9.1-1) to 0.9.1-1ubuntu1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]upstart (0.6.5-7) to 0.6.5-8[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ure (1.6.0+OOo3.2.0-7ubuntu4.1) to1.6.0+OOo3.2.0-7ubuntu4.4[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]ureadahead (0.100.0-4.1.2) to 0.100.0-4.1.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]usb-creator-common (0.2.22.1) to 0.2.22.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]usb-creator-gtk (0.2.22.1) to 0.2.22.3[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]util-linux (2.17.2-0ubuntu1) to2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]uuid-runtime (2.17.2-0ubuntu1) to2.17.2-0ubuntu1.10.04.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]vino (2.28.2-0ubuntu2) to 2.28.2-0ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]w3m (0.5.2-2.1ubuntu1.1) to0.5.2-2.1ubuntu1.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]winbind (2:3.4.7~dfsg-1ubuntu3.9) to2:3.4.7~dfsg-1ubuntu3.10[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]wpasupplicant (0.6.9-3ubuntu3) to0.6.9-3ubuntu3.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]x11-common (1:7.5+5ubuntu1) to1:7.5+5ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]x11-xserver-utils (7.5+1ubuntu2) to7.5+1ubuntu2.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xdg-utils (1.0.2-6.1ubuntu3) to1.0.2-6.1ubuntu3.2[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xkb-data (1.8-1ubuntu8) to1.8-1ubuntu8.1~10.04.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xorg (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-common (2:1.7.6-2ubuntu7.3) to2:1.7.6-2ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-xorg (1:7.5+5ubuntu1) to1:7.5+5ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-xorg-core (2:1.7.6-2ubuntu7.3) to2:1.7.6-2ubuntu7.11[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-xorg-input-all (1:7.5+5ubuntu1) to1:7.5+5ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-xorg-video-all (1:7.5+5ubuntu1) to1:7.5+5ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xserver-xorg-video-geode (2.11.8-4) to2.11.11-1~lucid1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xsltproc (1.1.26-1ubuntu1) to1.1.26-1ubuntu1.1[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]xulrunner-1.9.2(1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1) to1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1[/COLOR][/SIZE]
[/FONT]
Installed:
[SIZE=1][FONT=verdana][COLOR=#000000]firefox-locale-en (16.0.1+build1-0ubuntu0.10.04.1)[/COLOR][/FONT][/SIZE][SIZE=1][FONT=verdana][COLOR=#000000]icedtea-6-plugin (1.2-2ubuntu0.10.04.2)[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=verdana][COLOR=#000000]icedtea-netx (1.2-2ubuntu0.10.04.2)[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=verdana][COLOR=#000000]linux-headers-2.6.32-44 (2.6.32-44.98)[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=verdana][COLOR=#000000]linux-headers-2.6.32-44-generic(2.6.32-44.98)[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=verdana][COLOR=#000000]linux-image-2.6.32-44-generic (2.6.32-44.98)[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=verdana][COLOR=#000000]xul-ext-ubufox (2.1.1-0ubuntu0.10.04.1)[/COLOR][/FONT][/SIZE]
```

Also, I enter the code in the terminal and this is what came up:

04:00.0 Network controller [[COLOR=#ff0000]0280[/COLOR]]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
07:00.0 Ethernet controller [[COLOR=#ff0000]0200[/COLOR]]: Broadcom Corporation Netlink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

---

### Post by xenex79 on 2013-05-25
Try this, (ctrl+alt+t) open a terminal, then type.
```
sudo ifup -a
```
It will ask you to enter your password but nothing will be output on screen, then restart the computer, check your network manager to setup a connection to the internet.

---

### Post by Abbeyww on 2013-05-26
Thank you but I still cannot connect to the internet.

Also, I cannot find auto eth0. Does that have anything to do with it?

---

### Post by xenex79 on 2013-05-26
Yes it does, eth0 is the network card and wlan0 is for wireless.
usually you can check them and bring them up/down (enabled/disabled) using the command 
```
sudo ifconfig
```
which should list your devices
```
steve@server:~$ sudo ifconfig

br0      Link encap:Ethernet  HWaddr 00:0c:f6:0b:e5:73  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe0b:e573/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104109964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56402820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149775670098 (149.7 GB)  TX bytes:7149629359 (7.1 GB)


eth0    Link encap:Ethernet  HWaddr 00:0c:f6:0b:e5:73  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104146997 errors:20 dropped:0 overruns:0 frame:22
          TX packets:56473865 errors:3 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:926484180 (926.4 MB)  TX bytes:2902318618 (2.9 GB)


eth1    Link encap:Ethernet  HWaddr 00:50:ba:e9:23:67  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47776981 (47.7 MB)  TX bytes:13601223 (13.6 MB)


eth2    Link encap:Ethernet  HWaddr 00:0f:1f:5a:f4:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2400 (2.4 KB)  TX bytes:2400 (2.4 KB)
```


I'm not sure why your devices are not being recognised but you can find more help on the command here [http://linux.die.net/man/8/ifconfig](http://linux.die.net/man/8/ifconfig).
You could also check the contents of the file /etc/network/interfaces to see if you can find anything in there.

If i can come up with anything else for you I'll post back but I'm just a novice on the networking side of things, I had my own problem posted just the other day which thankfully has been resolved now.

---

