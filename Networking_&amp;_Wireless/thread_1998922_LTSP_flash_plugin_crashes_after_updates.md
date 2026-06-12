---
title: "LTSP: flash plugin crashes after updates"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by v4169sgr on 2012-06-07
I am running an alternate install 64 bit Ubuntu 12.04 with ltsp-server-standalone.

I recently ran a few updates, including adding wine from the repos, adding Medibuntu, and adding google earth, all on the server, which runs as a user workstation.

Before the updates, the flash plugin ran fine in thin clients. However, it now crashes. No problem with running the flash plugin on the server / workstation.

I have since followed the LTSPManual pdf to copy over my sources list, add Medibuntu in the chroot, update and upgrade, and then update the image, but the flash plugin still crashes.

I'd like to get the flash plugin working again in my thin clients. How do I do this?
	
A couple of important points: these are 32 bit clients on a 64 bit server, and the users are logging in with Ubuntu 2D sessions

Suggestions appreciated!

Thanks!

---

### Post by v4169sgr on 2012-06-07
Here is my apt repo history for today:

```
Start-Date: 2012-06-07  07:30:19
Commandline: aptdaemon role='role-commit-packages' sender=':1.83'
Upgrade: libkrb5-3:amd64 (1.10+dfsg~beta1-2, 1.10+dfsg~beta1-2ubuntu0.1), libk5c
rypto3:amd64 (1.10+dfsg~beta1-2, 1.10+dfsg~beta1-2ubuntu0.1), unity:amd64 (5.12-
0ubuntu1, 5.12-0ubuntu1.1), update-notifier-common:amd64 (0.119ubuntu8.1, 0.119u
buntu8.4), libv4l-0:amd64 (0.8.6-1ubuntu1, 0.8.6-1ubuntu2), bind9-host:amd64 (9.
8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubuntu0.1), update-notifier:amd64 (0.119ubuntu8.1,
 0.119ubuntu8.4), python-ubuntuone-client:amd64 (3.0.0-0ubuntu1, 3.0.0-0ubuntu1.
1), ubuntuone-client:amd64 (3.0.0-0ubuntu1, 3.0.0-0ubuntu1.1), dnsutils:amd64 (9
.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubuntu0.1), bamfdaemon:amd64 (0.2.114-0ubuntu1, 0
.2.118-0ubuntu0.1), unity-common:amd64 (5.12-0ubuntu1, 5.12-0ubuntu1.1), firefox
-globalmenu:amd64 (12.0+build1-0ubuntu0.12.04.1, 13.0+build1-0ubuntu0.12.04.1), 
python-ubuntuone-storageprotocol:amd64 (3.0.0-0ubuntu1, 3.0.0-0ubuntu1.1), libdn
s81:amd64 (9.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubuntu0.1), libv4lconvert0:amd64 (0.8
.6-1ubuntu1, 0.8.6-1ubuntu2), libisccc80:amd64 (9.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4
ubuntu0.1), firefox:amd64 (12.0+build1-0ubuntu0.12.04.1, 13.0+build1-0ubuntu0.12
.04.1), liblwres80:amd64 (9.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubuntu0.1), libkrb5sup
port0:amd64 (1.10+dfsg~beta1-2, 1.10+dfsg~beta1-2ubuntu0.1), libsyncdaemon-1.0-1
:amd64 (3.0.0-0ubuntu1, 3.0.0-0ubuntu1.1), libunity-core-5.0-5:amd64 (5.12-0ubun
tu1, 5.12-0ubuntu1.1), remmina-common:amd64 (1.0.0-1ubuntu6, 1.0.0-1ubuntu6.1), 
libbind9-80:amd64 (9.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubuntu0.1), firefox-locale-en
:amd64 (12.0+build1-0ubuntu0.12.04.1, 13.0+build1-0ubuntu0.12.04.1), unity-servi
ces:amd64 (5.12-0ubuntu1, 5.12-0ubuntu1.1), remmina-plugin-rdp:amd64 (1.0.0-1ubu
ntu6, 1.0.0-1ubuntu6.1), libisccfg82:amd64 (9.8.1.dfsg.P1-4, 9.8.1.dfsg.P1-4ubun
tu0.1), krb5-locales:amd64 (1.10+dfsg~beta1-2, 1.10+dfsg~beta1-2ubuntu0.1), remm
ina-plugin-vnc:amd64 (1.0.0-1ubuntu6, 1.0.0-1ubuntu6.1), libgssapi-krb5-2:amd64 
(1.10+dfsg~beta1-2, 1.10+dfsg~beta1-2ubuntu0.1), libisc83:amd64 (9.8.1.dfsg.P1-4
, 9.8.1.dfsg.P1-4ubuntu0.1), libbamf3-0:amd64 (0.2.114-0ubuntu1, 0.2.118-0ubuntu
0.1), libbamf0:amd64 (0.2.114-0ubuntu1, 0.2.118-0ubuntu0.1), firefox-gnome-suppo
rt:amd64 (12.0+build1-0ubuntu0.12.04.1, 13.0+build1-0ubuntu0.12.04.1), remmina:a
md64 (1.0.0-1ubuntu6, 1.0.0-1ubuntu6.1)
End-Date: 2012-06-07  07:30:49

Start-Date: 2012-06-07  11:38:07
Commandline: apt-get --yes --quiet --allow-unauthenticated install medibuntu-key
ring
Install: medibuntu-keyring:amd64 (2008.04.20)
End-Date: 2012-06-07  11:38:09

Start-Date: 2012-06-07  11:38:30
Commandline: apt-get install app-install-data-medibuntu apport-hooks-medibuntu
Install: apport-hooks-medibuntu:amd64 (1medibuntu1), app-install-data-medibuntu:
amd64 (10.10.0)
End-Date: 2012-06-07  11:38:48

Start-Date: 2012-06-07  11:45:13
Commandline: apt-get install libdvdcss2
Install: libdvdcss2:amd64 (1.2.12-0.0medibuntu1)
End-Date: 2012-06-07  11:45:15

Start-Date: 2012-06-07  11:46:10
Commandline: apt-get install mplayer vlc
Install: libva-x11-1:amd64 (1.0.15-4, automatic), libbluray1:amd64 (0.2.1+git201
11208.63e308d-3, automatic), libsvga1:amd64 (1.4.3-31, automatic), libxcb-xv0:am
d64 (1.8.1-1, automatic), libtar0:amd64 (1.2.11-8, automatic), mplayer:amd64 (1.
0~rc4.dfsg1+svn34540-1+medibuntu1), libiso9660-8:amd64 (0.83-1, automatic), libc
ddb2:amd64 (1.3.2-3fakesync1, automatic), libdvbpsi7:amd64 (0.2.2-1, automatic),
 libvlc5:amd64 (2.0.1-4, automatic), libsdl-image1.2:amd64 (1.2.10-3, automatic)
, vlc-nox:amd64 (2.0.1-4, automatic), libesd0:amd64 (0.2.41-10build3, automatic)
, libresid-builder0c2a:amd64 (2.1.1-12, automatic), libupnp3:amd64 (1.6.6-5.1, a
utomatic), vlc-plugin-notify:amd64 (2.0.1-4, automatic), libaacs0:amd64 (0.3.0-4
, automatic), libmatroska5:amd64 (1.3.0-1, automatic), libxcb-keysyms1:amd64 (0.
3.8-1build1, automatic), esound-common:amd64 (0.2.41-10build3, automatic), libxc
b-composite0:amd64 (1.8.1-1, automatic), vlc:amd64 (2.0.1-4), libsidplay2:amd64 
(2.1.1-12, automatic), libvdpau1:amd64 (0.4.1-3ubuntu1, automatic), vlc-data:amd
64 (2.0.1-4, automatic), libvlccore5:amd64 (2.0.1-4, automatic), libvcdinfo0:amd
64 (0.7.23-4.1ubuntu1, automatic), libebml3:amd64 (1.2.2-2, automatic), libxcb-r
andr0:amd64 (1.8.1-1, automatic), vlc-plugin-pulse:amd64 (2.0.1-4, automatic), l
ibaudiofile1:amd64 (0.3.3-2, automatic)
End-Date: 2012-06-07  11:46:27

Start-Date: 2012-06-07  11:47:18
Commandline: apt-get install w64codecs
Install: w64codecs:amd64 (20071007-0medibuntu2)
End-Date: 2012-06-07  11:47:20

Start-Date: 2012-06-07  11:57:33
Commandline: /usr/sbin/synaptic
Install: libopenal1:i386 (1.13-4ubuntu3, automatic), libkrb5-3:i386 (1.10+dfsg~b
eta1-2ubuntu0.1, automatic), libk5crypto3:i386 (1.10+dfsg~beta1-2ubuntu0.1, auto
matic), libpam-winbind:amd64 (3.6.3-2ubuntu2.2, automatic), libstdc++6:i386 (4.6
.3-1ubuntu5, automatic), libxfixes3:i386 (5.0-4ubuntu4, automatic), ttf-umefont:
amd64 (434-1, automatic), libncurses5:i386 (5.9-4, automatic), libxcomposite1:i3
86 (0.4.3-2build1, automatic), libldap-2.4-2:i386 (2.4.28-1.1ubuntu4, automatic)
, fonts-horai-umefont:amd64 (434-1), libv4l-0:i386 (0.8.6-1ubuntu2, automatic), 
liblcms1:i386 (1.19.dfsg-1ubuntu3, automatic), gnome-exe-thumbnailer:amd64 (0.9-
0ubuntu1, automatic), libroken18-heimdal:i386 (1.6~git20120311.dfsg.1-2, automat
ic), libunistring0:amd64 (0.9.3-5, automatic), libunistring0:i386 (0.9.3-5, auto
matic), wine1.4-amd64:amd64 (1.4-0ubuntu4, automatic), libgphoto2-port0:i386 (2.
4.13-1ubuntu1, automatic), libcomerr2:i386 (1.42-1ubuntu2, automatic), libselinu
x1:i386 (2.1.0-4.1ubuntu1, automatic), libjpeg-turbo8:i386 (1.1.90+svn733-0ubunt
u4, automatic), libjpeg8:i386 (8c-2ubuntu7, automatic), libmagickcore4:amd64 (6.
6.9.7-5ubuntu3.1, automatic), libdrm-radeon1:i386 (2.4.32-1ubuntu1, automatic), 
wine1.4:amd64 (1.4-0ubuntu4, automatic), libdbus-1-3:i386 (1.4.18-1ubuntu1, auto
matic), libsane:i386 (1.0.22-7ubuntu1, automatic), odbcinst1debian2:amd64 (2.2.1
4p2-5ubuntu3, automatic), libtinfo5:i386 (5.9-4, automatic), libxxf86vm1:i386 (1
.1.1-2build1, automatic), libgl1-mesa-dri:i386 (8.0.2-0ubuntu3.1, automatic), li
bmagickwand4:amd64 (6.6.9.7-5ubuntu3.1, automatic), gcc-4.6-base:i386 (4.6.3-1ub
untu5, automatic), libxcb-glx0:i386 (1.8.1-1, automatic), libasn1-8-heimdal:i386
 (1.6~git20120311.dfsg.1-2, automatic), libgl1-mesa-glx:i386 (8.0.2-0ubuntu3.1, 
automatic), libcdt4:amd64 (2.26.3-10ubuntu1, automatic), libxslt1.1:i386 (1.1.26
-8ubuntu1, automatic), libmagickcore4-extra:amd64 (6.6.9.7-5ubuntu3.1, automatic
), libgomp1:i386 (4.6.3-1ubuntu5, automatic), libpcre3:i386 (8.12-4, automatic),
 libcapi20-3:amd64 (3.12.20071127-0ubuntu11, automatic), libcapi20-3:i386 (3.12.
20071127-0ubuntu11, automatic), libx11-xcb1:i386 (1.4.99.1-0ubuntu2, automatic),
 libgnutls26:i386 (2.12.14-5ubuntu3, automatic), libglapi-mesa:i386 (8.0.2-0ubun
tu3.1, automatic), odbcinst:amd64 (2.2.14p2-5ubuntu3, automatic), libgssapi3-hei
mdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libtasn1-3:i386 (2.10-1ubuntu1.
1, automatic), libfreetype6:i386 (2.4.8-1ubuntu2, automatic), libglib2.0-0:i386 
(2.32.1-0ubuntu2, automatic), libexpat1:i386 (2.0.1-7.2ubuntu1, automatic), libv
4lconvert0:i386 (0.8.6-1ubuntu2, automatic), liblqr-1-0:amd64 (0.4.1-1.1, automa
tic), unixodbc:amd64 (2.2.14p2-5ubuntu3, automatic), libavahi-common-data:i386 (
0.6.30-5ubuntu2, automatic), libffi6:i386 (3.0.11~rc1-5, automatic), libelf1:i38
6 (0.152-1ubuntu3, automatic), wine1.4-common:amd64 (1.4-0ubuntu4, automatic), l
ibgcc1:i386 (4.6.3-1ubuntu5, automatic), libxcb1:i386 (1.8.1-1, automatic), wine
-gecko1.4:amd64 (1.4.0-0ubuntu2, automatic), wine-gecko1.4:i386 (1.4.0-0ubuntu2,
 automatic), libp11-kit0:i386 (0.12-2ubuntu1, automatic), libdrm2:i386 (2.4.32-1
ubuntu1, automatic), libwind0-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic)
, libxau6:i386 (1.0.6-4, automatic), imagemagick-common:amd64 (6.6.9.7-5ubuntu3.
1, automatic), libcups2:i386 (1.5.3-0ubuntu1, automatic), winetricks:amd64 (0.0+
20120308, automatic), libxinerama1:i386 (1.1.1-3build1, automatic), libkrb5suppo
rt0:i386 (1.10+dfsg~beta1-2ubuntu0.1, automatic), libgif4:i386 (4.1.6-9ubuntu1, 
automatic), libpathplan4:amd64 (2.26.3-10ubuntu1, automatic), libcroco3:i386 (0.
6.5-1, automatic), libdrm-nouveau1a:i386 (2.4.32-1ubuntu1, automatic), icoutils:
amd64 (0.29.1-2, automatic), libice6:i386 (1.0.7-2build1, automatic), libxdmcp6:
i386 (1.1.0-4, automatic), libieee1284-3:i386 (0.2.11-10build1, automatic), libg
crypt11:i386 (1.5.0-3ubuntu0.1, automatic), libdrm-intel1:i386 (2.4.32-1ubuntu1,
 automatic), libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.1, automatic), libkeyutils1:i38
6 (1.5.2-2, automatic), libgpm2:i386 (1.20.4-4, automatic), libasound2:i386 (1.0
.25-1ubuntu10.1, automatic), libxpm4:i386 (3.5.9-4, automatic), libusb-0.1-4:i38
6 (0.1.12-20, automatic), netpbm:amd64 (10.0-15, automatic), wine:amd64 (1.4-0ub
untu4), libxrender1:i386 (0.9.6-2build1, automatic), libhcrypto4-heimdal:i386 (1
.6~git20120311.dfsg.1-2, automatic), liborc-0.4-0:i386 (0.4.16-1ubuntu2, automat
ic), libhx509-5-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libgvc5:amd6
4 (2.26.3-10ubuntu1, automatic), wine1.4-i386:i386 (1.4-0ubuntu4, automatic), zl
ib1g:i386 (1.2.3.4.dfsg-3ubuntu4, automatic), libgettextpo0:amd64 (0.18.1.1-5ubu
ntu3, automatic), libgettextpo0:i386 (0.18.1.1-5ubuntu3, automatic), libgd2-xpm:
i386 (2.0.36~rc1~dfsg-6ubuntu2, automatic), libheimbase1-heimdal:i386 (1.6~git20
120311.dfsg.1-2, automatic), libtiff4:i386 (3.9.5-2ubuntu1, automatic), libpng12
-0:i386 (1.2.46-3ubuntu4, automatic), libgstreamer-plugins-base0.10-0:i386 (0.10
.36-1, automatic), libpciaccess0:i386 (0.12.902-1, automatic), libuuid1:i386 (2.
20.1-1ubuntu3, automatic), libavahi-client3:i386 (0.6.30-5ubuntu2, automatic), t
tf-unfonts-core:amd64 (1.0.3.is.1.0.2-080608-5ubuntu1, automatic), libmpg123-0:a
md64 (1.12.1-3.2ubuntu1, automatic), libmpg123-0:i386 (1.12.1-3.2ubuntu1, automa
tic), libnetpbm10:amd64 (10.0-15, automatic), libx11-6:i386 (1.4.99.1-0ubuntu2, 
automatic), libsasl2-2:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), libdb5.1:i386 
(5.1.25-11build1, automatic), libfontconfig1:i386 (2.8.0-3ubuntu9, automatic), i
magemagick:amd64 (6.6.9.7-5ubuntu3.1, automatic), libsm6:i386 (1.2.0-2build1, au
tomatic), libgraph4:amd64 (2.26.3-10ubuntu1, automatic), libheimntlm0-heimdal:i3
86 (1.6~git20120311.dfsg.1-2, automatic), libxdamage1:i386 (1.1.3-2build1, autom
atic), winbind:amd64 (3.6.3-2ubuntu2.2, automatic), libodbc1:amd64 (2.2.14p2-5ub
untu3, automatic), libexif12:i386 (0.6.20-2, automatic), libglu1-mesa:i386 (8.0.
2-0ubuntu3.1, automatic), libgssapi-krb5-2:i386 (1.10+dfsg~beta1-2ubuntu0.1, aut
omatic), fonts-droid:amd64 (20101110+git-2, automatic), libxi6:i386 (1.6.0-0ubun
tu2, automatic), libc6:i386 (2.15-0ubuntu10, automatic), libgstreamer0.10-0:i386
 (0.10.36-1ubuntu1, automatic), libxcursor1:i386 (1.1.12-1, automatic), libxt6:i
386 (1.1.1-2build1, automatic), libxext6:i386 (1.3.0-3build1, automatic), libsas
l2-modules:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), fonts-unfonts-core:amd64 (
1.0.3.is.1.0.2-080608-5ubuntu1, automatic), libavahi-common3:i386 (0.6.30-5ubunt
u2, automatic), libxrandr2:i386 (1.3.2-2, automatic), libsqlite3-0:i386 (3.7.9-2
ubuntu1, automatic), libltdl7:i386 (2.4.2-1ubuntu1, automatic), ttf-droid:amd64 
(20101110+git-2, automatic), libkrb5-26-heimdal:i386 (1.6~git20120311.dfsg.1-2, 
automatic), libssl1.0.0:i386 (1.0.1-4ubuntu5.2, automatic), libgpg-error0:i386 (
1.10-2ubuntu1, automatic), libllvm3.0:i386 (3.0-4ubuntu1, automatic), libgphoto2
-2:i386 (2.4.13-1ubuntu1, automatic)
End-Date: 2012-06-07  11:58:49

Start-Date: 2012-06-07  12:02:31
Commandline: aptdaemon role='role-commit-packages' sender=':1.345'
Upgrade: libavutil-extra-51:amd64 (0.8.1ubuntu1, 0.8.1ubuntu1+medibuntu1), print
er-driver-ptouch:amd64 (1.3-3, 1.3-3ubuntu0.1), libavcodec-extra-53:amd64 (0.8.1
ubuntu1, 0.8.1ubuntu1+medibuntu1)
End-Date: 2012-06-07  12:02:36

Start-Date: 2012-06-07  12:04:08
Commandline: apt-get install lsb-core msttcorefonts
Install: rpm2cpio:amd64 (4.9.1.1-1build1, automatic), debhelper:amd64 (9.2012011
5ubuntu3, automatic), dh-apparmor:amd64 (2.7.102-0ubuntu3, automatic), m4:amd64 
(1.4.16-2ubuntu1, automatic), librpmio2:amd64 (4.9.1.1-1build1, automatic), libr
pm2:amd64 (4.9.1.1-1build1, automatic), rpm-common:amd64 (4.9.1.1-1build1, autom
atic), po-debconf:amd64 (1.0.16+nmu2ubuntu1, automatic), intltool-debian:amd64 (
0.35.0+20060710.1, automatic), libc6-i386:amd64 (2.15-0ubuntu10, automatic), get
text:amd64 (0.18.1.1-5ubuntu3, automatic), pax:amd64 (20120216-1, automatic), he
irloom-mailx:amd64 (12.5-1build1, automatic), rpm:amd64 (4.9.1.1-1build1, automa
tic), librpmbuild2:amd64 (4.9.1.1-1build1, automatic), lsb-invalid-mta:amd64 (4.
0-0ubuntu20, automatic), html2text:amd64 (1.3.2a-15, automatic), lib32z1:amd64 (
1.2.3.4.dfsg-3ubuntu4, automatic), librpmsign0:amd64 (4.9.1.1-1build1, automatic
), lsb-core:amd64 (4.0-0ubuntu20), libmail-sendmail-perl:amd64 (0.79.16-1, autom
atic), alien:amd64 (8.86, automatic), ncurses-term:amd64 (5.9-4, automatic), lib
sys-hostname-long-perl:amd64 (1.4-2, automatic)
End-Date: 2012-06-07  12:04:21

Start-Date: 2012-06-07  12:04:36
Commandline: apt-get autoremove
Remove: libunistring0:i386 (0.9.3-5), libgomp1:i386 (4.6.3-1ubuntu5), dcraw:amd6
4 (8.99-1build1), libcroco3:i386 (0.6.5-1), libgettextpo0:i386 (0.18.1.1-5ubuntu
3)
End-Date: 2012-06-07  12:04:39

Start-Date: 2012-06-07  12:13:43
Commandline: apt-get install -f
Install: bluez-alsa:i386 (4.98-2ubuntu7, automatic), libsdl-ttf2.0-0:i386 (2.0.9
-1.1ubuntu1, automatic), libgconf-2-4:i386 (3.2.5-0ubuntu2, automatic), libatk1.
0-0:i386 (2.4.0-0ubuntu1, automatic), libstdc++5:i386 (3.3.6-25ubuntu1, automati
c), ia32-libs-multiarch:i386 (20090808ubuntu36, automatic), libqt4-declarative:i
386 (4.8.1-0ubuntu4.1, automatic), libgail18:i386 (2.24.10-0ubuntu6, automatic),
 libao-common:amd64 (1.1.0-1ubuntu2, automatic), libqt4-qt3support:i386 (4.8.1-0
ubuntu4.1, automatic), libunistring0:i386 (0.9.3-5, automatic), libcupsimage2:i3
86 (1.5.3-0ubuntu1, automatic), libidn11:i386 (1.23-2, automatic), libnss3:i386 
(3.13.1.with.ckbi.1.88-1ubuntu6, automatic), libwrap0:i386 (7.6.q-21, automatic)
, libcaca0:i386 (0.99.beta17-2.1ubuntu2, automatic), gtk2-engines:i386 (2.20.2-1
ubuntu1, automatic), libgudev-1.0-0:i386 (175-0ubuntu9, automatic), libsamplerat
e0:i386 (0.1.8-4, automatic), libacl1:i386 (2.2.51-5ubuntu1, automatic), libcdpa
ranoia0:i386 (3.10.2+debian-10ubuntu1, automatic), libcairo-gobject2:i386 (1.10.
2-6.1ubuntu2, automatic), libavc1394-0:i386 (0.5.3-1ubuntu2, automatic), ia32-li
bs:amd64 (20090808ubuntu36, automatic), libbz2-1.0:i386 (1.0.6-1, automatic), li
baio1:i386 (0.3.109-2ubuntu1, automatic), odbcinst1debian2:i386 (2.2.14p2-5ubunt
u3, automatic), libqt4-test:i386 (4.8.1-0ubuntu4.1, automatic), libqt4-script:i3
86 (4.8.1-0ubuntu4.1, automatic), libqt4-designer:i386 (4.8.1-0ubuntu4.1, automa
tic), libsdl-mixer1.2:i386 (1.2.11-7, automatic), libqt4-network:i386 (4.8.1-0ub
untu4.1, automatic), libqt4-dbus:i386 (4.8.1-0ubuntu4.1, automatic), libcap2:i38
6 (2.22-1ubuntu3, automatic), libproxy1:i386 (0.4.7-0ubuntu4, automatic), ibus-g
tk:i386 (1.4.1-3ubuntu1, automatic), libdbus-glib-1-2:i386 (0.98-1ubuntu1, autom
atic), libtdb1:i386 (1.2.9-4, automatic), libspeex1:i386 (1.2~rc1-3ubuntu2, auto
matic), gvfs-libs:i386 (1.12.1-0ubuntu1, automatic), libjack-jackd2-0:i386 (1.9.
8~dfsg.1-1ubuntu1, automatic), libgomp1:i386 (4.6.3-1ubuntu5, automatic), libibu
s-1.0-0:i386 (1.4.1-3ubuntu1, automatic), libcairo2:i386 (1.10.2-6.1ubuntu2, aut
omatic), libvisual-0.4-0:i386 (0.4.0-4, automatic), libcanberra-gtk-module:i386 
(0.28-3ubuntu3, automatic), libcanberra0:i386 (0.28-3ubuntu3, automatic), gtk2-e
ngines-murrine:i386 (0.98.2-0ubuntu1, automatic), libwavpack1:i386 (4.60.1-2, au
tomatic), libqt4-opengl:i386 (4.8.1-0ubuntu4.1, automatic), libsoup-gnome2.4-1:i
386 (2.38.1-1, automatic), libmysqlclient18:i386 (5.5.22-0ubuntu1, automatic), g
streamer0.10-plugins-good:i386 (0.10.31-1ubuntu1, automatic), libqt4-xmlpatterns
:i386 (4.8.1-0ubuntu4.1, automatic), librsvg2-common:i386 (2.36.1-0ubuntu1, auto
matic), libdatrie1:i386 (0.2.5-3, automatic), libncursesw5:i386 (5.9-4, automati
c), libiec61883-0:i386 (1.2.0-0.1ubuntu1, automatic), libjson0:i386 (0.9-1ubuntu
1, automatic), libgdk-pixbuf2.0-0:i386 (2.26.1-1, automatic), libsdl-image1.2:i3
86 (1.2.10-3, automatic), libpixman-1-0:i386 (0.24.4-1, automatic), libsdl1.2deb
ian:i386 (1.2.14-6.4ubuntu3, automatic), libxaw7:i386 (1.0.9-3ubuntu1, automatic
), libgdbm3:i386 (1.8.3-10, automatic), libcurl3:i386 (7.22.0-3ubuntu4, automati
c), libqtcore4:i386 (4.8.1-0ubuntu4.1, automatic), libesd0:i386 (0.2.41-10build3
, automatic), libmikmod2:i386 (3.1.12-2, automatic), libxft2:i386 (2.2.0-3ubuntu
2, automatic), libcroco3:i386 (0.6.5-1, automatic), libpulse-mainloop-glib0:i386
 (1.1-0ubuntu15, automatic), libtheora0:i386 (1.1.1+dfsg.1-3ubuntu2, automatic),
 libaa1:i386 (1.4p5-39ubuntu1, automatic), libspeexdsp1:i386 (1.2~rc1-3ubuntu2, 
automatic), libthai0:i386 (0.1.16-3, automatic), libao4:i386 (1.1.0-1ubuntu2, au
tomatic), libxmu6:i386 (1.1.0-3, automatic), libcanberra-gtk0:i386 (0.28-3ubuntu
3, automatic), libvorbisfile3:i386 (1.3.2-1ubuntu3, automatic), libqt4-sql:i386 
(4.8.1-0ubuntu4.1, automatic), libflac8:i386 (1.2.1-6, automatic), libqt4-svg:i3
86 (4.8.1-0ubuntu4.1, automatic), libgail-common:i386 (2.24.10-0ubuntu6, automat
ic), libraw1394-11:i386 (2.0.7-1ubuntu1, automatic), libnspr4:i386 (4.8.9-1ubunt
u2, automatic), libshout3:i386 (2.2.2-7ubuntu1, automatic), libdv4:i386 (1.0.0-3
ubuntu1, automatic), libvorbisenc2:i386 (1.3.2-1ubuntu3, automatic), libqt4-xml:
i386 (4.8.1-0ubuntu4.1, automatic), libasyncns0:i386 (0.8-4, automatic), gstream
er0.10-x:i386 (0.10.36-1, automatic), libgettextpo0:i386 (0.18.1.1-5ubuntu3, aut
omatic), libxss1:i386 (1.2.1-2, automatic), libsdl-net1.2:i386 (1.2.7-5, automat
ic), libjasper1:i386 (1.900.1-13, automatic), libvisual-0.4-plugins:i386 (0.4.0.
dfsg.1-7, automatic), libudev0:i386 (175-0ubuntu9, automatic), libgnome-keyring0
:i386 (3.2.2-2, automatic), libxtst6:i386 (1.2.0-4, automatic), gtk2-engines-pix
buf:i386 (2.24.10-0ubuntu6, automatic), libqtgui4:i386 (4.8.1-0ubuntu4.1, automa
tic), libtag1c2a:i386 (1.7-1ubuntu5, automatic), librsvg2-2:i386 (2.36.1-0ubuntu
1, automatic), libssl0.9.8:i386 (0.9.8o-7ubuntu3.1, automatic), libmad0:i386 (0.
15.1b-7ubuntu1, automatic), gtk2-engines-oxygen:i386 (1.2.2-0ubuntu1.1, automati
c), xaw3dg:i386 (1.5+E-18.1ubuntu1, automatic), libpango1.0-0:i386 (1.30.0-0ubun
tu2, automatic), libpulse0:i386 (1.1-0ubuntu15, automatic), libpulsedsp:i386 (1.
1-0ubuntu15, automatic), gvfs:i386 (1.12.1-0ubuntu1, automatic), libqt4-sql-mysq
l:i386 (4.8.1-0ubuntu4.1, automatic), libxcb-render0:i386 (1.8.1-1, automatic), 
libodbc1:i386 (2.2.14p2-5ubuntu3, automatic), libqt4-scripttools:i386 (4.8.1-0ub
untu4.1, automatic), librtmp0:i386 (2.4~20110711.gitc28f1bab-1, automatic), libv
orbis0a:i386 (1.3.2-1ubuntu3, automatic), libqtwebkit4:i386 (2.2.1-1ubuntu4, aut
omatic), libattr1:i386 (2.4.46-5ubuntu1, automatic), libxp6:i386 (1.0.1-2, autom
atic), libaudio2:i386 (1.9.3-4, automatic), libxcb-shm0:i386 (1.8.1-1, automatic
), libxv1:i386 (1.0.6-2build1, automatic), libslang2:i386 (2.2.4-3ubuntu1, autom
atic), mysql-common:amd64 (5.5.22-0ubuntu1, automatic), gstreamer0.10-plugins-ba
se:i386 (0.10.36-1, automatic), libsndfile1:i386 (1.0.25-4, automatic), libmng1:
i386 (1.0.10-3, automatic), libgtk2.0-0:i386 (2.24.10-0ubuntu6, automatic), liba
sound2-plugins:i386 (1.0.25-1ubuntu1, automatic), glib-networking:i386 (2.32.1-1
ubuntu1, automatic), libsoup2.4-1:i386 (2.38.1-1, automatic), libogg0:i386 (1.2.
2~dfsg-1ubuntu1, automatic), libtag1-vanilla:i386 (1.7-1ubuntu5, automatic), lib
audiofile1:i386 (0.3.3-2, automatic)
End-Date: 2012-06-07  12:14:46

Start-Date: 2012-06-07  13:27:15
Commandline: aptdaemon role='role-commit-packages' sender=':1.84'
Upgrade: python-cupshelpers:amd64 (1.3.8+20120201-0ubuntu8, 1.3.8+20120201-0ubun
tu8.1), system-config-printer-gnome:amd64 (1.3.8+20120201-0ubuntu8, 1.3.8+201202
01-0ubuntu8.1), system-config-printer-udev:amd64 (1.3.8+20120201-0ubuntu8, 1.3.8
+20120201-0ubuntu8.1), system-config-printer-common:amd64 (1.3.8+20120201-0ubunt
u8, 1.3.8+20120201-0ubuntu8.1)
End-Date: 2012-06-07  13:27:20

Start-Date: 2012-06-07  13:59:31
Commandline: /usr/sbin/synaptic
Purge: flashplugin-installer:amd64 (11.2.202.235ubuntu0.12.04.1)
End-Date: 2012-06-07  13:59:33

Start-Date: 2012-06-07  13:59:48
Commandline: /usr/sbin/synaptic
Install: flashplugin-installer:amd64 (11.2.202.235ubuntu0.12.04.1)
End-Date: 2012-06-07  14:00:12
```

The two entries for flahplugin-installer were after I noticed something was wrong and tried correcting it.

This was known to work yesterday.

Suggestions appreciated.

---

### Post by v4169sgr on 2012-06-07
Google Earth forced the install of a whole bunch of i386 packages [more than 100]. I needed to use "apt-get install -f" to sort out the dependencies.

---

### Post by v4169sgr on 2012-06-07
Can someone help me out here? I just don't understand why flash worked yesterday in my thin clients and does not work today.

The flash plugin hash not changed since the 4th June.

On my machine though I notice that firefox was updated from v 12 [running on the 6th] to v 13 [running on the 7th with broken flash in the thin client].

Here is an except from the log:

```
Start-Date: 2012-06-04  16:36:51
firefox:amd64 (11.0+build1-0ubuntu4, 12.0+build1-0ubuntu0.12.04.1)

Start-Date: 2012-06-07  07:30:19
firefox:amd64 (12.0+build1-0ubuntu0.12.04.1, 13.0+build1-0ubuntu0.12.04.1)
```

I really do not undertand and am getting very frustrated. Last thing I want to do is fiddle with flash - lost enough time in previous distros with that!

Should I go back from firefox v 13 to firefox v 12? How would I go about doing that safely?

---

### Post by v4169sgr on 2012-06-07
'Force version' in Synaptic only gives me v 11 - I want v 12, which I know works. Grrrr ...

Suggestions welcome!

---

### Post by v4169sgr on 2012-06-07
OK, so reading around shows v 13 and flash aren't going to play nice. There's some good advice out there about downloading an older version of Flash from Adobe directly, extracting the plugin .so and applying that to the right folder. It'll probably work for you if that's what you want to do. For the time being I've decided to take the path of least resistance, have installed Chromium v 18 from the repos, which works in thin clients with flash, and will advise the users to use that for their videos. Brings back the memories of days with Galleon etc :)

---

