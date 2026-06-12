---
title: "Current Unity state"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vikktor91 on 2011-02-17
Hello, i have almost fully upgraded natty desktop(i've downgraded xorg to 1.9, to get nvidia working).Yesterday Unity 3D was working just fine, but after today's upgrade i can's start it.When i select "Ubuntu Desktop Edition" it starts unity 2d.Is this bug in natty or in my system?Here's list of the packages that were upgraded

```
Commit Log for Thu Feb 17 09:55:50 2011


Removed the following packages:
computer-janitor-gtk

Upgraded the following packages:
apport (1.17.2-0ubuntu2) to 1.18-0ubuntu1
binutils (2.21-5ubuntu1) to 2.21.0.20110216-1ubuntu1
bsdutils (1:2.17.2-9.1ubuntu1) to 1:2.17.2-9.1ubuntu2
capplets-data (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
computer-janitor (2.0.5-0ubuntu1) to 2.1.0-0ubuntu1
cpp-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
empathy (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
empathy-common (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
g++-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
gcc-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
gcc-4.5-base (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
geoclue (0.12.0-1ubuntu6) to 0.12.0-1ubuntu7
gir1.2-gtk-2.0 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
gnome-control-center (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
gnome-screensaver (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
gtk2-engines-pixbuf (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
imagemagick (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libblkid1 (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
libdc1394-22 (2.1.2-3ubuntu2) to 2.1.2-3ubuntu3
libegl1-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libegl1-mesa-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libegl1-mesa-drivers (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgail-common (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgail18 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgcc1 (1:4.5.2-2ubuntu3) to 1:4.5.2-3ubuntu1
libgeoclue0 (0.12.0-1ubuntu6) to 0.12.0-1ubuntu7
libgl1-mesa-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-dri (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-dri-experimental (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-glx (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libglapi-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libglu1-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgnome-window-settings1 (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
libgomp1 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libgssapi-krb5-2 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libgstfarsight0.10-0 (0.0.24-1ubuntu1) to 0.0.25-0ubuntu1
libgtk2.0-0 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-bin (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-common (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-dev (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libk5crypto3 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libkrb5-3 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libkrb5support0 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libltdl-dev (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libltdl7 (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libmagickcore3 (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libmagickcore3-extra (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libmagickwand3 (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libstdc++6 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libstdc++6-4.5-dev (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libtiff4 (3.9.4-5) to 3.9.4-5ubuntu1
libtool (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libubuntuone-1.0-1 (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
libubuntuone1.0-cil (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
libunity-2d-private-dev (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
libunity-2d-private0 (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
libuuid1 (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
libwebkitgtk-1.0-0 (1.3.10-1ubuntu1) to 1.3.10-1ubuntu2
libwebkitgtk-1.0-common (1.3.10-1ubuntu1) to 1.3.10-1ubuntu2
mesa-common-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
mount (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
nautilus-sendto-empathy (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
python-apport (1.17.2-0ubuntu2) to 1.18-0ubuntu1
python-cupshelpers (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
python-farsight (0.0.24-1ubuntu1) to 0.0.25-0ubuntu1
python-problem-report (1.17.2-0ubuntu2) to 1.18-0ubuntu1
python-ubuntuone (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
system-config-printer-common (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
system-config-printer-gnome (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
system-config-printer-udev (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
telepathy-gabble (0.11.6-1ubuntu1) to 0.11.6-1ubuntu2
totem (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-common (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-mozilla (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-plugins (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
unity-2d (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-default-settings (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-launcher (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-panel (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-places (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-spread (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
update-manager (1:0.145.13) to 1:0.146
update-manager-core (1:0.145.13) to 1:0.146
update-notifier (0.110.3ubuntu3) to 0.110.4ubuntu1
update-notifier-common (0.110.3ubuntu3) to 0.110.4ubuntu1
util-linux (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
uuid-runtime (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
```

Thanks in advance

---

### Post by farooq23 on 2011-02-17
> **vikktor91 said:**
> Hello, i have almost fully upgraded natty desktop(i've downgraded xorg to 1.9, to get nvidia working).Yesterday Unity 3D was working just fine, but after today's upgrade i can's start it.When i select "Ubuntu Desktop Edition" it starts unity 2d.Is this bug in natty or in my system?Here's list of the packages that were upgraded

```
Commit Log for Thu Feb 17 09:55:50 2011


Removed the following packages:
computer-janitor-gtk

Upgraded the following packages:
apport (1.17.2-0ubuntu2) to 1.18-0ubuntu1
binutils (2.21-5ubuntu1) to 2.21.0.20110216-1ubuntu1
bsdutils (1:2.17.2-9.1ubuntu1) to 1:2.17.2-9.1ubuntu2
capplets-data (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
computer-janitor (2.0.5-0ubuntu1) to 2.1.0-0ubuntu1
cpp-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
empathy (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
empathy-common (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
g++-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
gcc-4.5 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
gcc-4.5-base (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
geoclue (0.12.0-1ubuntu6) to 0.12.0-1ubuntu7
gir1.2-gtk-2.0 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
gnome-control-center (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
gnome-screensaver (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
gtk2-engines-pixbuf (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
imagemagick (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libblkid1 (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
libdc1394-22 (2.1.2-3ubuntu2) to 2.1.2-3ubuntu3
libegl1-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libegl1-mesa-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libegl1-mesa-drivers (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgail-common (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgail18 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgcc1 (1:4.5.2-2ubuntu3) to 1:4.5.2-3ubuntu1
libgeoclue0 (0.12.0-1ubuntu6) to 0.12.0-1ubuntu7
libgl1-mesa-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-dri (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-dri-experimental (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgl1-mesa-glx (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libglapi-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libglu1-mesa (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
libgnome-window-settings1 (1:2.32.1-0ubuntu4) to 1:2.32.1-0ubuntu5
libgomp1 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libgssapi-krb5-2 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libgstfarsight0.10-0 (0.0.24-1ubuntu1) to 0.0.25-0ubuntu1
libgtk2.0-0 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-bin (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-common (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libgtk2.0-dev (2.24.0-0ubuntu2) to 2.24.0-0ubuntu3
libk5crypto3 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libkrb5-3 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libkrb5support0 (1.8.3+dfsg-4) to 1.8.3+dfsg-4ubuntu1
libltdl-dev (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libltdl7 (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libmagickcore3 (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libmagickcore3-extra (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libmagickwand3 (7:6.6.2.6-1ubuntu2) to 7:6.6.2.6-1ubuntu3
libstdc++6 (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libstdc++6-4.5-dev (4.5.2-2ubuntu3) to 4.5.2-3ubuntu1
libtiff4 (3.9.4-5) to 3.9.4-5ubuntu1
libtool (2.2.6b-2ubuntu1) to 2.2.6b-2ubuntu2
libubuntuone-1.0-1 (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
libubuntuone1.0-cil (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
libunity-2d-private-dev (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
libunity-2d-private0 (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
libuuid1 (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
libwebkitgtk-1.0-0 (1.3.10-1ubuntu1) to 1.3.10-1ubuntu2
libwebkitgtk-1.0-common (1.3.10-1ubuntu1) to 1.3.10-1ubuntu2
mesa-common-dev (7.11.0+git20110214.07eb660f-0ubuntu0sarvatt) to 7.11.0+git20110216.4d6994e4-0ubuntu0ricotz
mount (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
nautilus-sendto-empathy (2.33.1-0ubuntu3) to 2.33.1-0ubuntu4
python-apport (1.17.2-0ubuntu2) to 1.18-0ubuntu1
python-cupshelpers (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
python-farsight (0.0.24-1ubuntu1) to 0.0.25-0ubuntu1
python-problem-report (1.17.2-0ubuntu2) to 1.18-0ubuntu1
python-ubuntuone (0.3.10-0ubuntu1) to 0.3.11-0ubuntu1
system-config-printer-common (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
system-config-printer-gnome (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
system-config-printer-udev (1.2.6+20110208-0ubuntu1) to 1.2.7+20110216-0ubuntu1
telepathy-gabble (0.11.6-1ubuntu1) to 0.11.6-1ubuntu2
totem (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-common (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-mozilla (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
totem-plugins (2.32.0-0ubuntu8) to 2.32.0-0ubuntu9
unity-2d (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-default-settings (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-launcher (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-panel (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-places (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
unity-2d-spread (3.2.2-0ubuntu2~bzr388) to 3.2.2-0ubuntu2~bzr392
update-manager (1:0.145.13) to 1:0.146
update-manager-core (1:0.145.13) to 1:0.146
update-notifier (0.110.3ubuntu3) to 0.110.4ubuntu1
update-notifier-common (0.110.3ubuntu3) to 0.110.4ubuntu1
util-linux (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
uuid-runtime (2.17.2-9.1ubuntu1) to 2.17.2-9.1ubuntu2
```Thanks in advance

check weather your xserver is still 1.9 or 1.10. if it is 1.10 after update, you might have to downgrade it again.

---

### Post by Harry33 on 2011-02-17
> **farooq23 said:**
> check weather your xserver is still 1.9 or 1.10. if it is 1.10 after update, you might have to downgrade it again.

The list above does not contain xserver updates, although xserver 1.10 was updated today:
[https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.901+git20110131.be3be758-0ubuntu5](https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.901+git20110131.be3be758-0ubuntu5)

---

### Post by vikktor91 on 2011-02-18
FIXED
Somehow the nvidia-current drivers were installed :-k So i'he to remove them and install drivers from nvidia site.Thanks for the comments ;]

---

