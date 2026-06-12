---
title: "Skype won't launch?"
date: 2016-02-20
forum: Multimedia Software
---

### Post by Excuse_Me on 2016-02-20
I have installed Skype and the icons shows up in dash but when I click on it or click on it nothing happens.. How could this be?

---

### Post by ajgreeny on 2016-02-20
Where did the skype package you installed come from; how did you install it?

The easiest way is to enable the partner repos and install just like any other software with software-center or synaptic or whatever you use.

What error message, if any, do you get if you firstly stop skype with ```
killall skype
``` then start it again in terminal with command ```
skype
```

---

### Post by Excuse_Me on 2016-02-20
> **ajgreeny said:**
> Where did the skype package you installed come from; how did you install it?

The easiest way is to enable the partner repos and install just like any other software with software-center or synaptic or whatever you use.

What error message, if any, do you get if you firstly stop skype with ```
killall skype
``` then start it again in terminal with command ```
skype
```

First time I searched for skype in software center for some reason there were no hits so I installed it in command line and it showed up under applications but every time I click the icon nothing happens. Since I have found it in software center and uninstalled and reinstalled it there.

```
laptop@laptop:~$ killall skype
skype: no process found
laptop@laptop:~$ skype
bash: /usr/bin/skype: cannot execute binary file: Exec format error
laptop@laptop:~$ killall skype 
skype: no process found
laptop@laptop:~$ skype
bash: /usr/bin/skype: cannot execute binary file: Exec format error
```

This is what I get wheter I've tried starting it up or not.. What could I do to access skype?

---

### Post by ajgreeny on 2016-02-20
It sounds as if you might have the wrong architecture version of skype installed; are you running a 32 bit system but trying to install a 64 bit version of skype.

If I simulate an installation of skype on my Xubuntu 14.04 64 bit system this is the output I get
```
sudo apt-get -s install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  skype-bin:i386
The following NEW packages will be installed
  skype skype-bin:i386
0 to upgrade, 2 to newly install.
Inst skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Inst skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
Conf skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Conf skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
```
What do you see if you remove all skype packages currently installed and start again installing skype with the command I show above?

---

### Post by Excuse_Me on 2016-02-20
> **ajgreeny said:**
> It sounds as if you might have the wrong architecture version of skype installed; are you running a 32 bit system but trying to install a 64 bit version of skype.

If I simulate an installation of skype on my Xubuntu 14.04 64 bit system this is the output I get
```
sudo apt-get -s install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  skype-bin:i386
The following NEW packages will be installed
  skype skype-bin:i386
0 to upgrade, 2 to newly install.
Inst skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Inst skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
Conf skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Conf skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
```
What do you see if you remove all skype packages currently installed and start again installing skype with the command I show above?

I am running the 64 version of Ubuntu.
I followed your advise and unstilade skype with ubuntu software center (does this "remove all skype packages"?

After I followed your terminal actions and also what I was prompted to do there, it looked like this:

```
[CODE]laptop@laptop:~$ sudo apt-get -s install skype
[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-sv linux-headers-4.2.0-16
  linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
  linux-image-extra-4.2.0-16-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  skype
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Inst skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [amd64])
Conf skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [amd64])
laptop@laptop:~$ ^C
laptop@laptop:~$ ^C
laptop@laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
laptop@laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```
The following packages will be REMOVED:
  gstreamer1.0-plugins-base:i386 kde-l10n-engb kde-l10n-sv libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libaudio2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libbsd0:i386 libcdparanoia0:i386 libcups2:i386 libdbus-1-3:i386
  libdbusmenu-qt2:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386
  libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386
  libgnutls-deb0-28:i386 libgssapi-krb5-2:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhogweed4:i386
  libice6:i386 libicu55:i386 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libllvm3.6v5:i386 libmng2:i386 libmysqlclient18:i386 libnettle6:i386
  libogg0:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpciaccess0:i386
  libpng12-0:i386 libpulse0:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386 libqtwebkit4:i386
  libsamplerate0:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtheora0:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libvisual-0.4-0:i386
  libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxi6:i386 libxml2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386
  libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386 linux-headers-4.2.0-16
  linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
  linux-image-extra-4.2.0-16-generic mysql-common skype-bin:i386 sni-qt:i386
0 upgraded, 0 newly installed, 118 to remove and 0 not upgraded.
After this operation, 665 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 274360 files and directories currently installed.)
Removing gstreamer1.0-plugins-base:i386 (1.6.0-1ubuntu1) ...
Removing kde-l10n-engb (4:15.08.2-0ubuntu1) ...
Removing kde-l10n-sv (4:15.08.2-0ubuntu1) ...
Removing libvisual-0.4-plugins:i386 (0.4.0.dfsg.1-7build1) ...
Removing libasound2-plugins:i386 (1.0.29-1ubuntu1) ...
Removing libasound2:i386 (1.0.29-0ubuntu1) ...
Removing libpulse0:i386 (1:6.0-0ubuntu13) ...
Removing libasyncns0:i386 (0.8-5build1) ...
Removing skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1) ...
Removing sni-qt:i386 (0.2.7+15.10.20150729-0ubuntu1) ...
Removing libcups2:i386 (2.1.0-4ubuntu3) ...
Removing libavahi-client3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common-data:i386 (0.6.31-4ubuntu4) ...
Removing libqtwebkit4:i386 (2.3.2-0ubuntu10) ...
Removing libqt4-opengl:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libglu1-mesa:i386 (9.0.0-2) ...
Removing libgl1-mesa-glx:i386 (11.0.2-1ubuntu4) ...
Removing libgl1-mesa-dri:i386 (11.0.2-1ubuntu4) ...
Removing libllvm3.6v5:i386 (1:3.6.2-1) ...
Removing libedit2:i386 (3.1-20150325-1ubuntu1) ...
Removing libbsd0:i386 (0.7.0-2) ...
Removing libcdparanoia0:i386 (3.10.2+debian-11) ...
Removing libdbusmenu-qt2:i386 (0.9.3+15.10.20150604-0ubuntu1) ...
Removing libdrm-amdgpu1:i386 (2.4.64-1) ...
Removing libdrm-intel1:i386 (2.4.64-1) ...
Removing libdrm-nouveau2:i386 (2.4.64-1) ...
Removing libdrm-radeon1:i386 (2.4.64-1) ...
Removing libdrm2:i386 (2.4.64-1) ...
Removing libelf1:i386 (0.163-4ubuntu1) ...
Removing libgnutls-deb0-28:i386 (3.3.15-5ubuntu2) ...
Removing libp11-kit0:i386 (0.23.1-3) ...
Removing libsndfile1:i386 (1.0.25-9.1ubuntu0.15.10.1) ...
Removing libflac8:i386 (1.3.1-4) ...
Removing libglapi-mesa:i386 (11.0.2-1ubuntu4) ...
Removing libhogweed4:i386 (3.1.1-4ubuntu0.1) ...
Removing libgmp10:i386 (2:6.0.0+dfsg-7) ...
Removing libgssapi-krb5-2:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libgstreamer-plugins-base1.0-0:i386 (1.6.0-1ubuntu1) ...
Removing libgstreamer1.0-0:i386 (1.6.0-1) ...
Removing libxslt1.1:i386 (1.1.28-2build2) ...
Removing libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3) ...
Removing libicu55:i386 (55.1-4ubuntu1) ...
Removing libjack-jackd2-0:i386 (1.9.10+20140719git3eb0ae6a~dfsg-3ubuntu1) ...
Removing libjson-c2:i386 (0.11-4ubuntu2) ...
Removing libkrb5-3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libk5crypto3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libkeyutils1:i386 (1.5.9-5ubuntu1) ...
Removing libkrb5support0:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libqt4-sql-mysql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libmysqlclient18:i386 (5.6.28-0ubuntu0.15.10.1) ...
Removing libnettle6:i386 (3.1.1-4ubuntu0.1) ...
Removing libvorbisenc2:i386 (1.3.4-2) ...
Removing libvorbis0a:i386 (1.3.4-2) ...
Removing libtheora0:i386 (1.1.1+dfsg.1-7) ...
Removing libogg0:i386 (1.3.2-1) ...
Removing liborc-0.4-0:i386 (1:0.4.24-1) ...
Removing libpciaccess0:i386 (0.13.4-1) ...
Removing libqt4-dbus:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libsamplerate0:i386 (0.1.8-8) ...
Removing libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1) ...
Removing libsqlite3-0:i386 (3.8.11.1-1) ...
Removing libssl1.0.0:i386 (1.0.2d-0ubuntu1.3) ...
Removing libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Removing libtasn1-6:i386 (4.5-2) ...
Removing libvisual-0.4-0:i386 (0.4.0-6) ...
Removing libwrap0:i386 (7.6.q-25) ...
Removing libxxf86vm1:i386 (1:1.1.4-1) ...
Removing libxv1:i386 (2:1.0.10-1) ...
Removing libx11-xcb1:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb-sync1:i386 (1.11-0ubuntu1) ...
Removing libxcb-present0:i386 (1.11-0ubuntu1) ...
Removing libxcb-dri2-0:i386 (1.11-0ubuntu1) ...
Removing libxcb-dri3-0:i386 (1.11-0ubuntu1) ...
Removing libxcb-glx0:i386 (1.11-0ubuntu1) ...
Removing libxdamage1:i386 (1:1.1.4-2) ...
Removing libxss1:i386 (1:1.2.2-1) ...
Removing libxfixes3:i386 (1:5.0.1-2) ...
Removing libxshmfence1:i386 (1.2-1) ...
Removing linux-headers-4.2.0-16-generic (4.2.0-16.19) ...
Removing linux-headers-4.2.0-16 (4.2.0-16.19) ...
Removing linux-image-extra-4.2.0-16-generic (4.2.0-16.19) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-rc8-touchpad
Found initrd image: /boot/initrd.img-4.4.0-rc8-touchpad
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-4.2.0-16-generic (4.2.0-16.19) ...
Examining /etc/kernel/prerm.d.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-rc8-touchpad
Found initrd image: /boot/initrd.img-4.4.0-rc8-touchpad
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Adding boot menu entry for EFI firmware configuration
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Removing mysql-common (5.6.28-0ubuntu0.15.10.1) ...
Removing libqt4-declarative:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqt4-script:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqt4-xmlpatterns:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqt4-network:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqtdbus4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libdbus-1-3:i386 (1.10.0-1ubuntu1) ...
Removing libqt4-xml:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqt4-sql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libqtgui4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libaudio2:i386 (1.9.4-3) ...
Removing libfontconfig1:i386 (2.11.1-0ubuntu6) ...
Removing libexpat1:i386 (2.1.0-7) ...
Removing libqtcore4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8) ...
Removing libglib2.0-0:i386 (2.46.1-1) ...
Removing libffi6:i386 (3.2.1-3) ...
Removing libfreetype6:i386 (2.5.2-4ubuntu2) ...
Removing libxt6:i386 (1:1.1.5-0ubuntu1) ...
Removing libsm6:i386 (2:1.2.2-1) ...
Removing libice6:i386 (2:1.0.9-1) ...
Removing libtiff5:i386 (4.0.3-12.3ubuntu2) ...
Removing libjbig0:i386 (2.1-3.1) ...
Removing libmng2:i386 (2.0.2-0ubuntu3) ...
Removing libjpeg8:i386 (8c-2ubuntu8) ...
Removing libjpeg-turbo8:i386 (1.3.0-0ubuntu2) ...
Removing liblcms2-2:i386 (2.6-3ubuntu2) ...
Removing libpng12-0:i386 (1.2.51-0ubuntu3.15.10.2) ...
Removing libstdc++6:i386 (5.2.1-22ubuntu2) ...
Removing libxi6:i386 (2:1.7.4-1) ...
Removing libxrender1:i386 (1:0.9.9-0ubuntu1) ...
Removing libxext6:i386 (2:1.3.3-1) ...
Removing libx11-6:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb1:i386 (1.11-0ubuntu1) ...
Removing libxau6:i386 (1:1.0.8-1) ...
Removing libxdmcp6:i386 (1:1.1.2-1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
laptop@laptop:~$ ^C
laptop@laptop:~$ ^C
laptop@laptop:~$ sudo apt-get -s install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gstreamer1.0-plugins-base:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libbsd0:i386
  libcdparanoia0:i386 libcups2:i386 libdbus-1-3:i386 libdbusmenu-qt2:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386 libgnutls-deb0-28:i386
  libgssapi-krb5-2:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libhogweed4:i386 libice6:i386 libicu55:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libllvm3.6v5:i386 libmng2:i386
  libmysqlclient18:i386 libnettle6:i386 libogg0:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpng12-0:i386 libpulse0:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386
  libqtgui4:i386 libqtwebkit4:i386 libsamplerate0:i386 libsm6:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386
  libstdc++6:i386 libtasn1-6:i386 libtheora0:i386 libtiff5:i386
  libtxc-dxtn-s2tc0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxml2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386
  libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common
  skype-bin:i386 sni-qt:i386
Suggested packages:
  gvfs:i386 nas:i386 gnutls-bin:i386 krb5-doc:i386 krb5-user:i386
  gstreamer1.0-tools:i386 jackd2:i386 libqt4-declarative-folderlistmodel:i386
  libqt4-declarative-gestures:i386 libqt4-declarative-particles:i386
  libqt4-declarative-shaders:i386 qt4-qmlviewer:i386 libqt4-dev:i386
  libicu52:i386 libthai0:i386 qt4-qtconfig:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  gstreamer1.0-plugins-base:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libbsd0:i386
  libcdparanoia0:i386 libcups2:i386 libdbus-1-3:i386 libdbusmenu-qt2:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386 libgnutls-deb0-28:i386
  libgssapi-krb5-2:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libhogweed4:i386 libice6:i386 libicu55:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libllvm3.6v5:i386 libmng2:i386
  libmysqlclient18:i386 libnettle6:i386 libogg0:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpng12-0:i386 libpulse0:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386
  libqtgui4:i386 libqtwebkit4:i386 libsamplerate0:i386 libsm6:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386
  libstdc++6:i386 libtasn1-6:i386 libtheora0:i386 libtiff5:i386
  libtxc-dxtn-s2tc0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxml2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386
  libxss1:i386 libxt6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common skype
  skype-bin:i386 sni-qt:i386
0 upgraded, 113 newly installed, 0 to remove and 0 not upgraded.
Inst libbsd0:i386 (0.7.0-2 Ubuntu:15.10/wily [i386])
Inst libffi6:i386 (3.2.1-3 Ubuntu:15.10/wily [i386])
Inst libjson-c2:i386 (0.11-4ubuntu2 Ubuntu:15.10/wily [i386])
Inst libkeyutils1:i386 (1.5.9-5ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxau6:i386 (1:1.0.8-1 Ubuntu:15.10/wily [i386])
Inst libxdmcp6:i386 (1:1.1.2-1 Ubuntu:15.10/wily [i386])
Inst libxcb1:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libx11-6:i386 (2:1.6.3-1ubuntu2 Ubuntu:15.10/wily [i386])
Inst libxext6:i386 (2:1.3.3-1 Ubuntu:15.10/wily [i386])
Inst libasyncns0:i386 (0.8-5build1 Ubuntu:15.10/wily [i386])
Inst libice6:i386 (2:1.0.9-1 Ubuntu:15.10/wily [i386])
Inst libsm6:i386 (2:1.2.2-1 Ubuntu:15.10/wily [i386])
Inst libxt6:i386 (1:1.1.5-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libaudio2:i386 (1.9.4-3 Ubuntu:15.10/wily [i386])
Inst libavahi-common-data:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Inst libavahi-common3:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Inst libdbus-1-3:i386 (1.10.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libavahi-client3:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Inst libcdparanoia0:i386 (3.10.2+debian-11 Ubuntu:15.10/wily [i386])
Inst libexpat1:i386 (2.1.0-7 Ubuntu:15.10/wily [i386])
Inst libpng12-0:i386 (1.2.51-0ubuntu3.15.10.2 Ubuntu:15.10/wily-updates [i386])
Inst libfreetype6:i386 (2.5.2-4ubuntu2 Ubuntu:15.10/wily [i386])
Inst libfontconfig1:i386 (2.11.1-0ubuntu6 Ubuntu:15.10/wily [i386])
Inst libjpeg-turbo8:i386 (1.3.0-0ubuntu2 Ubuntu:15.10/wily [i386])
Inst liblcms2-2:i386 (2.6-3ubuntu2 Ubuntu:15.10/wily [i386])
Inst libjpeg8:i386 (8c-2ubuntu8 Ubuntu:15.10/wily [i386])
Inst libmng2:i386 (2.0.2-0ubuntu3 Ubuntu:15.10/wily [i386])
Inst mysql-common (5.6.28-0ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [all])
Inst libstdc++6:i386 (5.2.1-22ubuntu2 Ubuntu:15.10/wily [i386])
Inst libmysqlclient18:i386 (5.6.28-0ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [i386])
Inst libogg0:i386 (1.3.2-1 Ubuntu:15.10/wily [i386])
Inst libsamplerate0:i386 (0.1.8-8 Ubuntu:15.10/wily [i386])
Inst libjbig0:i386 (2.1-3.1 Ubuntu:15.10/wily [i386])
Inst libtiff5:i386 (4.0.3-12.3ubuntu2 Ubuntu:15.10/wily [i386])
Inst libvisual-0.4-0:i386 (0.4.0-6 Ubuntu:15.10/wily [i386])
Inst libvorbis0a:i386 (1.3.4-2 Ubuntu:15.10/wily [i386])
Inst libvorbisenc2:i386 (1.3.4-2 Ubuntu:15.10/wily [i386])
Inst libwrap0:i386 (7.6.q-25 Ubuntu:15.10/wily [i386])
Inst libxdamage1:i386 (1:1.1.4-2 Ubuntu:15.10/wily [i386])
Inst libxfixes3:i386 (1:5.0.1-2 Ubuntu:15.10/wily [i386])
Inst libxi6:i386 (2:1.7.4-1 Ubuntu:15.10/wily [i386])
Inst libxshmfence1:i386 (1.2-1 Ubuntu:15.10/wily [i386])
Inst libicu55:i386 (55.1-4ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3 Ubuntu:15.10/wily-updates [i386])
Inst libxslt1.1:i386 (1.1.28-2build2 Ubuntu:15.10/wily [i386])
Inst libxss1:i386 (1:1.2.2-1 Ubuntu:15.10/wily [i386])
Inst libxv1:i386 (2:1.0.10-1 Ubuntu:15.10/wily [i386])
Inst libxxf86vm1:i386 (1:1.1.4-1 Ubuntu:15.10/wily [i386])
Inst libdrm2:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Inst libglapi-mesa:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Inst libx11-xcb1:i386 (2:1.6.3-1ubuntu2 Ubuntu:15.10/wily [i386])
Inst libxcb-dri2-0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxcb-dri3-0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxcb-glx0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxcb-present0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libxcb-sync1:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libdrm-amdgpu1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Inst libpciaccess0:i386 (0.13.4-1 Ubuntu:15.10/wily [i386])
Inst libdrm-intel1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Inst libdrm-nouveau2:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Inst libdrm-radeon1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Inst libelf1:i386 (0.163-4ubuntu1 Ubuntu:15.10/wily [i386])
Inst libedit2:i386 (3.1-20150325-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libllvm3.6v5:i386 (1:3.6.2-1 Ubuntu:15.10/wily [i386])
Inst libgl1-mesa-dri:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Inst libgl1-mesa-glx:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Inst libglu1-mesa:i386 (9.0.0-2 Ubuntu:15.10/wily [i386])
Inst libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1 Ubuntu:15.10/wily [i386])
Inst libgmp10:i386 (2:6.0.0+dfsg-7 Ubuntu:15.10/wily [i386])
Inst libnettle6:i386 (3.1.1-4ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libhogweed4:i386 (3.1.1-4ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libp11-kit0:i386 (0.23.1-3 Ubuntu:15.10/wily [i386])
Inst libtasn1-6:i386 (4.5-2 Ubuntu:15.10/wily [i386])
Inst libgnutls-deb0-28:i386 (3.3.15-5ubuntu2 Ubuntu:15.10/wily [i386])
Inst libsqlite3-0:i386 (3.8.11.1-1 Ubuntu:15.10/wily [i386])
Inst libssl1.0.0:i386 (1.0.2d-0ubuntu1.3 Ubuntu:15.10/wily-updates [i386])
Inst libglib2.0-0:i386 (2.46.1-1 Ubuntu:15.10/wily [i386])
Inst libkrb5support0:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libk5crypto3:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libkrb5-3:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libgssapi-krb5-2:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Inst libgstreamer1.0-0:i386 (1.6.0-1 Ubuntu:15.10/wily [i386])
Inst liborc-0.4-0:i386 (1:0.4.24-1 Ubuntu:15.10/wily [i386])
Inst libgstreamer-plugins-base1.0-0:i386 (1.6.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libtheora0:i386 (1.1.1+dfsg.1-7 Ubuntu:15.10/wily [i386])
Inst gstreamer1.0-plugins-base:i386 (1.6.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libasound2:i386 (1.0.29-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libjack-jackd2-0:i386 (1.9.10+20140719git3eb0ae6a~dfsg-3ubuntu1 Ubuntu:15.10/wily [i386])
Inst libflac8:i386 (1.3.1-4 Ubuntu:15.10/wily [i386])
Inst libsndfile1:i386 (1.0.25-9.1ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [i386])
Inst libpulse0:i386 (1:6.0-0ubuntu13 Ubuntu:15.10/wily [i386])
Inst libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libasound2-plugins:i386 (1.0.29-1ubuntu1 Ubuntu:15.10/wily [i386])
Inst libcups2:i386 (2.1.0-4ubuntu3 Ubuntu:15.10/wily [i386])
Inst libqtcore4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-xml:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqtdbus4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-dbus:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-network:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-script:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-sql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-xmlpatterns:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-declarative:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386]) []
Inst libxrender1:i386 (1:0.9.9-0ubuntu1 Ubuntu:15.10/wily [i386]) []
Inst libqtgui4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libdbusmenu-qt2:i386 (0.9.3+15.10.20150604-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst libqt4-opengl:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqt4-sql-mysql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Inst libqtwebkit4:i386 (2.3.2-0ubuntu10 Ubuntu:15.10/wily [i386])
Inst libvisual-0.4-plugins:i386 (0.4.0.dfsg.1-7build1 Ubuntu:15.10/wily [i386])
Inst sni-qt:i386 (0.2.7+15.10.20150729-0ubuntu1 Ubuntu:15.10/wily [i386])
Inst skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [i386])
Inst skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [amd64])
Conf libbsd0:i386 (0.7.0-2 Ubuntu:15.10/wily [i386])
Conf libffi6:i386 (3.2.1-3 Ubuntu:15.10/wily [i386])
Conf libjson-c2:i386 (0.11-4ubuntu2 Ubuntu:15.10/wily [i386])
Conf libkeyutils1:i386 (1.5.9-5ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxau6:i386 (1:1.0.8-1 Ubuntu:15.10/wily [i386])
Conf libxdmcp6:i386 (1:1.1.2-1 Ubuntu:15.10/wily [i386])
Conf libxcb1:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libx11-6:i386 (2:1.6.3-1ubuntu2 Ubuntu:15.10/wily [i386])
Conf libxext6:i386 (2:1.3.3-1 Ubuntu:15.10/wily [i386])
Conf libasyncns0:i386 (0.8-5build1 Ubuntu:15.10/wily [i386])
Conf libice6:i386 (2:1.0.9-1 Ubuntu:15.10/wily [i386])
Conf libsm6:i386 (2:1.2.2-1 Ubuntu:15.10/wily [i386])
Conf libxt6:i386 (1:1.1.5-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libaudio2:i386 (1.9.4-3 Ubuntu:15.10/wily [i386])
Conf libavahi-common-data:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Conf libavahi-common3:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Conf libdbus-1-3:i386 (1.10.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libavahi-client3:i386 (0.6.31-4ubuntu4 Ubuntu:15.10/wily [i386])
Conf libcdparanoia0:i386 (3.10.2+debian-11 Ubuntu:15.10/wily [i386])
Conf libexpat1:i386 (2.1.0-7 Ubuntu:15.10/wily [i386])
Conf libpng12-0:i386 (1.2.51-0ubuntu3.15.10.2 Ubuntu:15.10/wily-updates [i386])
Conf libfreetype6:i386 (2.5.2-4ubuntu2 Ubuntu:15.10/wily [i386])
Conf libfontconfig1:i386 (2.11.1-0ubuntu6 Ubuntu:15.10/wily [i386])
Conf libjpeg-turbo8:i386 (1.3.0-0ubuntu2 Ubuntu:15.10/wily [i386])
Conf liblcms2-2:i386 (2.6-3ubuntu2 Ubuntu:15.10/wily [i386])
Conf libjpeg8:i386 (8c-2ubuntu8 Ubuntu:15.10/wily [i386])
Conf libmng2:i386 (2.0.2-0ubuntu3 Ubuntu:15.10/wily [i386])
Conf mysql-common (5.6.28-0ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [all])
Conf libstdc++6:i386 (5.2.1-22ubuntu2 Ubuntu:15.10/wily [i386])
Conf libmysqlclient18:i386 (5.6.28-0ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [i386])
Conf libogg0:i386 (1.3.2-1 Ubuntu:15.10/wily [i386])
Conf libsamplerate0:i386 (0.1.8-8 Ubuntu:15.10/wily [i386])
Conf libjbig0:i386 (2.1-3.1 Ubuntu:15.10/wily [i386])
Conf libtiff5:i386 (4.0.3-12.3ubuntu2 Ubuntu:15.10/wily [i386])
Conf libvisual-0.4-0:i386 (0.4.0-6 Ubuntu:15.10/wily [i386])
Conf libvorbis0a:i386 (1.3.4-2 Ubuntu:15.10/wily [i386])
Conf libvorbisenc2:i386 (1.3.4-2 Ubuntu:15.10/wily [i386])
Conf libwrap0:i386 (7.6.q-25 Ubuntu:15.10/wily [i386])
Conf libxdamage1:i386 (1:1.1.4-2 Ubuntu:15.10/wily [i386])
Conf libxfixes3:i386 (1:5.0.1-2 Ubuntu:15.10/wily [i386])
Conf libxi6:i386 (2:1.7.4-1 Ubuntu:15.10/wily [i386])
Conf libxshmfence1:i386 (1.2-1 Ubuntu:15.10/wily [i386])
Conf libicu55:i386 (55.1-4ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3 Ubuntu:15.10/wily-updates [i386])
Conf libxslt1.1:i386 (1.1.28-2build2 Ubuntu:15.10/wily [i386])
Conf libxss1:i386 (1:1.2.2-1 Ubuntu:15.10/wily [i386])
Conf libxv1:i386 (2:1.0.10-1 Ubuntu:15.10/wily [i386])
Conf libxxf86vm1:i386 (1:1.1.4-1 Ubuntu:15.10/wily [i386])
Conf libdrm2:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Conf libglapi-mesa:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Conf libx11-xcb1:i386 (2:1.6.3-1ubuntu2 Ubuntu:15.10/wily [i386])
Conf libxcb-dri2-0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxcb-dri3-0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxcb-glx0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxcb-present0:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libxcb-sync1:i386 (1.11-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libdrm-amdgpu1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Conf libpciaccess0:i386 (0.13.4-1 Ubuntu:15.10/wily [i386])
Conf libdrm-intel1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Conf libdrm-nouveau2:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Conf libdrm-radeon1:i386 (2.4.64-1 Ubuntu:15.10/wily [i386])
Conf libelf1:i386 (0.163-4ubuntu1 Ubuntu:15.10/wily [i386])
Conf libedit2:i386 (3.1-20150325-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libllvm3.6v5:i386 (1:3.6.2-1 Ubuntu:15.10/wily [i386])
Conf libgl1-mesa-dri:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Conf libgl1-mesa-glx:i386 (11.0.2-1ubuntu4 Ubuntu:15.10/wily [i386])
Conf libglu1-mesa:i386 (9.0.0-2 Ubuntu:15.10/wily [i386])
Conf libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1 Ubuntu:15.10/wily [i386])
Conf libgmp10:i386 (2:6.0.0+dfsg-7 Ubuntu:15.10/wily [i386])
Conf libnettle6:i386 (3.1.1-4ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libhogweed4:i386 (3.1.1-4ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libp11-kit0:i386 (0.23.1-3 Ubuntu:15.10/wily [i386])
Conf libtasn1-6:i386 (4.5-2 Ubuntu:15.10/wily [i386])
Conf libgnutls-deb0-28:i386 (3.3.15-5ubuntu2 Ubuntu:15.10/wily [i386])
Conf libsqlite3-0:i386 (3.8.11.1-1 Ubuntu:15.10/wily [i386])
Conf libssl1.0.0:i386 (1.0.2d-0ubuntu1.3 Ubuntu:15.10/wily-updates [i386])
Conf libglib2.0-0:i386 (2.46.1-1 Ubuntu:15.10/wily [i386])
Conf libkrb5support0:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libk5crypto3:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libkrb5-3:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libgssapi-krb5-2:i386 (1.13.2+dfsg-2ubuntu0.1 Ubuntu:15.10/wily-updates [i386])
Conf libgstreamer1.0-0:i386 (1.6.0-1 Ubuntu:15.10/wily [i386])
Conf liborc-0.4-0:i386 (1:0.4.24-1 Ubuntu:15.10/wily [i386])
Conf libgstreamer-plugins-base1.0-0:i386 (1.6.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libtheora0:i386 (1.1.1+dfsg.1-7 Ubuntu:15.10/wily [i386])
Conf gstreamer1.0-plugins-base:i386 (1.6.0-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libasound2:i386 (1.0.29-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libjack-jackd2-0:i386 (1.9.10+20140719git3eb0ae6a~dfsg-3ubuntu1 Ubuntu:15.10/wily [i386])
Conf libflac8:i386 (1.3.1-4 Ubuntu:15.10/wily [i386])
Conf libsndfile1:i386 (1.0.25-9.1ubuntu0.15.10.1 Ubuntu:15.10/wily-updates [i386])
Conf libpulse0:i386 (1:6.0-0ubuntu13 Ubuntu:15.10/wily [i386])
Conf libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libasound2-plugins:i386 (1.0.29-1ubuntu1 Ubuntu:15.10/wily [i386])
Conf libcups2:i386 (2.1.0-4ubuntu3 Ubuntu:15.10/wily [i386])
Conf libqtcore4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-xml:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqtdbus4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-dbus:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-network:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-script:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-sql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-xmlpatterns:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libxrender1:i386 (1:0.9.9-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libqt4-declarative:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqtgui4:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libdbusmenu-qt2:i386 (0.9.3+15.10.20150604-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf libqt4-opengl:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqt4-sql-mysql:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8 Ubuntu:15.10/wily [i386])
Conf libqtwebkit4:i386 (2.3.2-0ubuntu10 Ubuntu:15.10/wily [i386])
Conf libvisual-0.4-plugins:i386 (0.4.0.dfsg.1-7build1 Ubuntu:15.10/wily [i386])
Conf sni-qt:i386 (0.2.7+15.10.20150729-0ubuntu1 Ubuntu:15.10/wily [i386])
Conf skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [i386])
Conf skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:15.10/wily [amd64])[/CODE]

After doing this there was no icon for skype in the dash

Thankful for further suggestions..

---

### Post by Excuse_Me on 2016-02-20
latest step I tried was installing through ubuntu after install, that didnt work either though, icon shows up in dash but nothing happens when I click it

---

### Post by Excuse_Me on 2016-02-20
I also tried this command
sudo apt-get autoremove --purge skype and reinstalling and I still have the same prolem. Skype icon is there but doesn't launch when I click it

---

### Post by ajgreeny on 2016-02-20
Well, I am beaten by this, I'm afraid.  Once again try starting it with command **skype** in terminal to see if any errors are shown.

Just to test this out I have just installed skype on a Lubuntu 14.04 64bit system using synaptic and that is working perfectly, and I have also installed it in Xubuntu 16.04 64bit with complete success.

There must be something strange going on that neither you or I am aware of if we can not get skype running properly when installed from the repos.
As a final try it may be worth purging skype, running autoremove again to get rid of dependencies for skype, then reinstalling skype. That will make sure any configuration except for the hidden ~/.skype folder in your /home is also removed.

---

### Post by Excuse_Me on 2016-02-21
> **ajgreeny said:**
> It sounds as if you might have the wrong architecture version of skype installed; are you running a 32 bit system but trying to install a 64 bit version of skype.

If I simulate an installation of skype on my Xubuntu 14.04 64 bit system this is the output I get
```
sudo apt-get -s install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  skype-bin:i386
The following NEW packages will be installed
  skype skype-bin:i386
0 to upgrade, 2 to newly install.
Inst skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Inst skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
Conf skype-bin:i386 (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [i386])
Conf skype (4.3.0.37-0ubuntu0.12.04.1 Partner archive:14.04/trusty [amd64])
```
What do you see if you remove all skype packages currently installed and start again installing skype with the command I show above?

Wow! Tnx for your effort!! There is one thing I forgot to mention, before I could find skype on software center I did follow a guide to install it via an app called "synaptic package manager" which resultet in it not being (visibly) installed at all. I did however install a number of packages when prompted to do so which I have later uninstalled to my best knowledge. I do not know if this might have anything to do with the problem.

Anyway if you or anyone else has any further tips on how I could get skype running on 15.10 it would obviously be much appreciated
Thanks a lot have a nice sunday!

---

### Post by ajgreeny on 2016-02-21
It doesn't matter whether you use command "apt-get install", software-center, or synaptic, or even command "dpkg -i package"; they all do the same job and you should end up with the same applications installed.

I generally use synaptic myself as it is, in my opinion, the best package manager available for Ubuntu, and as it happens, I have never, ever, used the software-center so have actually removed it from my Xubuntu installation.

---

### Post by Excuse_Me on 2016-02-21
> **ajgreeny said:**
> It doesn't matter whether you use command "apt-get install", software-center, or synaptic, or even command "dpkg -i package"; they all do the same job and you should end up with the same applications installed.

I generally use synaptic myself as it is, in my opinion, the best package manager available for Ubuntu, and as it happens, I have never, ever, used the software-center so have actually removed it from my Xubuntu installation.

Guess that's why it didnt work even when i did a fresh install of ubuntu and installed it with ubuntu after install.. Still the skype icon in dash but it wont launch no matter how many time I press it..

---

### Post by shane_faulkinbury2 on 2016-02-22
All I did was installed Skype from the Ubuntu Software Center, went into Files/Computer and clicked on the magnifying glass and typed in Skype.  A couple of them showed up so I just copied and pasted one onto the dash/desktop and everything works fine!  :D

---

### Post by gordintoronto on 2016-02-22
Skype is a 32-bit application. To run it on 64-bit Ubuntu you need to install multiarch.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

