---
title: "[SOLVED] Partial lock on all channels after update"
date: 2008-05-28
forum: Mythbuntu
---

### Post by twostar on 2008-05-28
I ran a system update last night because i've been having stability issues with the front end in 8.04. Now I can't get any channels to lock. 98% signal strength and I'm only getting a (L----) on every channel. This is all OTA and worked fine before updating (well they locked fine). I thought the updates were all minor and didn't see any specifically for myth. 

Any ideas?

edit: using a Kworld 115 and only ATSC channels.

---

### Post by twostar on 2008-05-28
This is the log of the updates performed. Also note that it worked fine until I rebooted the box.

```
Upgraded the following packages:
apache2 (2.2.8-1) to 2.2.8-1ubuntu0.1
apache2-mpm-prefork (2.2.8-1) to 2.2.8-1ubuntu0.1
apache2-utils (2.2.8-1) to 2.2.8-1ubuntu0.1
apache2.2-common (2.2.8-1) to 2.2.8-1ubuntu0.1
apparmor (2.1+1075-0ubuntu9) to 2.1+1075-0ubuntu9.1
apparmor-utils (2.1+1075-0ubuntu9) to 2.1+1075-0ubuntu9.1
apport (0.108) to 0.108.2
apport-gtk (0.108) to 0.108.2
bash (3.2-0ubuntu16) to 3.2-0ubuntu18
bsdutils (1:2.13.1-5ubuntu1) to 1:2.13.1-5ubuntu2
dbus (1.1.20-1ubuntu1) to 1.1.20-1ubuntu2
dbus-x11 (1.1.20-1ubuntu1) to 1.1.20-1ubuntu2
gcc-3.3-base (1:3.3.6-15ubuntu4) to 1:3.3.6-15ubuntu6
gdm (2.20.5-0ubuntu3) to 2.20.6-0ubuntu2
gksu (2.0.0-5ubuntu2) to 2.0.0-5ubuntu3
gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
hal (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8.1
jockey-common (0.3.3-0ubuntu7) to 0.3.3-0ubuntu8
jockey-gtk (0.3.3-0ubuntu7) to 0.3.3-0ubuntu8
kdelibs-data (4:3.5.9-0ubuntu7) to 4:3.5.9-0ubuntu7.1
kdelibs4c2a (4:3.5.9-0ubuntu7) to 4:3.5.9-0ubuntu7.1
libapache2-mod-php5 (5.2.4-2ubuntu5) to 5.2.4-2ubuntu5.1
libdbus-1-3 (1.1.20-1ubuntu1) to 1.1.20-1ubuntu2
libglib2.0-0 (2.16.3-1) to 2.16.3-1ubuntu2
libgnome-keyring0 (2.22.1-1) to 2.22.1-1ubuntu1
libgnutls13 (2.0.4-1ubuntu2) to 2.0.4-1ubuntu2.1
libgtk2.0-0 (2.12.9-3ubuntu2) to 2.12.9-3ubuntu4
libgtk2.0-common (2.12.9-3ubuntu2) to 2.12.9-3ubuntu4
libhal-storage1 (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8.1
libhal1 (0.5.11~rc2-1ubuntu7) to 0.5.11~rc2-1ubuntu8.1
libldap-2.4-2 (2.4.7-6ubuntu3) to 2.4.7-6ubuntu4.1
libpam-modules (0.99.7.1-5ubuntu6) to 0.99.7.1-5ubuntu6.1
libpam-runtime (0.99.7.1-5ubuntu6) to 0.99.7.1-5ubuntu6.1
libpam0g (0.99.7.1-5ubuntu6) to 0.99.7.1-5ubuntu6.1
libqt4-core (4.3.4-0ubuntu3) to 4.4.0-1ubuntu5~hardy1
libqt4-gui (4.3.4-0ubuntu3) to 4.4.0-1ubuntu5~hardy1
libspeex1 (1.1.12-3) to 1.1.12-3ubuntu0.8.04.1
libssl0.9.8 (0.9.8g-4ubuntu3) to 0.9.8g-4ubuntu3.1
libstdc++5 (1:3.3.6-15ubuntu4) to 1:3.3.6-15ubuntu6
linux-image-generic (2.6.24.16.18) to 2.6.24.17.19
linux-restricted-modules-common (2.6.24.12-16.34) to 2.6.24.12-17.36
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.17.19
lshw (02.12.01-2ubuntu1) to 02.12.01-2ubuntu1.1
mount (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
nvidia-glx-new (169.12+2.6.24.12-16.34) to 169.12+2.6.24.12-17.36
openssh-client (1:4.7p1-8ubuntu1) to 1:4.7p1-8ubuntu1.2
openssh-server (1:4.7p1-8ubuntu1) to 1:4.7p1-8ubuntu1.2
php5 (5.2.4-2ubuntu5) to 5.2.4-2ubuntu5.1
php5-common (5.2.4-2ubuntu5) to 5.2.4-2ubuntu5.1
php5-mysql (5.2.4-2ubuntu5) to 5.2.4-2ubuntu5.1
python-apport (0.108) to 0.108.2
python-problem-report (0.108) to 0.108.2
sudo (1.6.9p10-1ubuntu3) to 1.6.9p10-1ubuntu3.2
update-manager (1:0.87.24) to 1:0.87.27
update-manager-core (1:0.87.24) to 1:0.87.27
util-linux (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
util-linux-locales (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
xserver-xorg-video-intel (2:2.2.1-1ubuntu12) to 2:2.2.1-1ubuntu13
xulrunner-1.9 (1.9~b5+nobinonly-0ubuntu3) to 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1

Installed the following packages:
libqt4-assistant (4.4.0-1ubuntu5~hardy1)
libqt4-dbus (4.4.0-1ubuntu5~hardy1)
libqt4-designer (4.4.0-1ubuntu5~hardy1)
libqt4-network (4.4.0-1ubuntu5~hardy1)
libqt4-opengl (4.4.0-1ubuntu5~hardy1)
libqt4-script (4.4.0-1ubuntu5~hardy1)
libqt4-svg (4.4.0-1ubuntu5~hardy1)
libqt4-test (4.4.0-1ubuntu5~hardy1)
libqt4-xml (4.4.0-1ubuntu5~hardy1)
libqtcore4 (4.4.0-1ubuntu5~hardy1)
libqtgui4 (4.4.0-1ubuntu5~hardy1)
linux-image-2.6.24-17-generic (2.6.24-17.31)
linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.36)
linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25)
openssh-blacklist (0.1-1ubuntu0.8.04.1)
```

---

### Post by modorf on 2008-05-28
which input on the card are you using?
I would try the other input.

---

### Post by twostar on 2008-05-28
I tried that with one channel and while it showed some signal it was considerably lower then normal. 

I'm wondering if it has to do with my database. Is there an easy way to check the db for errors? I may also delete and set up the card again in myth. I haven't had more then a few minutes to work on it yet.

---

### Post by twostar on 2008-06-07
Ended up reinstalling the entire OS. removing and reinstalling the card in Myth didn't work. Something somewhere got changed and broke it but now it's working fine from clean install.

---

### Post by rune.evjen on 2008-06-15
I found that when upgrading the kernel from 2.6.24-16-generic to 2.6.24-18-generic I could not get a lock on any encrypted channel.

Booting the -16 kernel solved this issue. I have not had time to investigate why. 

I have not tried the -17 kernel that you are using, but for me -16 works and -18 does not.

I am using a Technotrend DVB-C 2300 card with a CI interface and a CAM module for decryption.

Rune

---

