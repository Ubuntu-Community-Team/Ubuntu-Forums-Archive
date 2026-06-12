---
title: "Error trying to install today's Maverick updates"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-08-10
A few minutes ago, I ran "sudo aptitude update", then "sudo aptitude safe-upgrade". The upgrade step gave the following error and, I believe, none of the many updates were installed:

```

Errors were encountered while processing:
/var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu2_i386.deb
E: Sub-process /usr/lib/dpkg returned an error code (1)

```

I believe it had something to do with unmet dependencies.

Do I need to try to fix something, or just wait and try again tomorrow?

Thanks,
Tim

---

### Post by MacUntu on 2010-08-10
> **ratcheer said:**
> or just wait and try again tomorrow
^^^ ;)

---

### Post by ratcheer on 2010-08-10
Ok, thanks.

Tim

---

### Post by ptn107 on 2010-08-10
I just did a quick workaround:

1) Download [_libgirepository1.0-1_0.9.3-0ubuntu2 32-bit_]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/libgirepository1.0-1_0.9.3-0ubuntu2_i386.deb") or [_libgirepository1.0-1_0.9.3-0ubuntu2 64-bit_]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/libgirepository1.0-1_0.9.3-0ubuntu2_amd64.deb")

2) Install the package manually (mine was 64-bit, yours might not be)
```
cd Downloads/
sudo dpkg -i libgirepository1.0-1_0.9.3-0ubuntu2_amd64.deb
```

3) Remove the older conflicting package
```
sudo dpkg -P libgirepository1.0-0
```

---

### Post by cheesypoof on 2010-08-11
For some reason I had to do the commands in the reverse order. Nevertheless it worked so thanks for the fix ptn107.

---

### Post by jppr on 2010-08-11
I  just finished fresh installation daily alternate and there is not  any problems, the new packages have been updated without any problems.[IMG]http://www.google.fi/images/cleardot.gif[/IMG]

---

### Post by ratcheer on 2010-08-11
Well, it is good news and bad news.

Today, all the Maverick updates installed successfully, including libgirepository 0.9.3. It gave me a red "Restart required" icon at the top right of the screen. I restarted and ...

However, I can no longer start a gui desktop. It boots to a text login screen. I tried starting gdm and it said it was already running. I tried restarting gdm, which succeeded, but still left me at a text desktop.

What next? Time to reinstall Maverick from scratch?

Tim

---

### Post by W00ster on 2010-08-11
> **ratcheer said:**
> Well, it is good news and bad news.

Today, all the Maverick updates installed successfully, including libgirepository 0.9.3. It gave me a red "Restart required" icon at the top right of the screen. I restarted and ...

However, I can no longer start a gui desktop. It boots to a text login screen. I tried starting gdm and it said it was already running. I tried restarting gdm, which succeeded, but still left me at a text desktop.

What next? Time to reinstall Maverick from scratch?

Tim

I had the same problem yesterday.
Turned out that xorg had been deinstalled.

apt-get install xorg 
took care of it for me.

---

### Post by mick222 on 2010-08-11
Same problem here tried downloading the file but it wouldn't install because of the broken packages.Then ran "sudo apt_get install -f and got the following error.

> dpkg: error processing /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libgirepository-everything-1.0.so.1.0.0', which is also in package libgirepository1.0-0 0.6.14-1ubuntu2
configured to not write apport reports

---

### Post by kansasnoob on 2010-08-11
It "self-resolved" for me using Synaptic:

> Commit Log for Wed Aug 11 06:30:41 2010


[B][COLOR="Red"]Removed the following packages:
libgirepository1.0-0[/COLOR][/B]

Upgraded the following packages:
adobe-flashplugin (10.1.53.64-1lucid1) to 10.1.82.76-1maverick1
apparmor (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
apparmor-utils (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
bash (4.1-2ubuntu3) to 4.1-2ubuntu4
debhelper (7.4.20ubuntu6) to 8.0.0ubuntu1
foomatic-db (20100806-0ubuntu2) to 20100806-0ubuntu5
foomatic-db-engine (4.0.4-0ubuntu1) to 4.0.5-0ubuntu4
foomatic-filters (4.0.4-0ubuntu2) to 4.0.5-0ubuntu2
gconf-defaults-service (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2-common (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gir1.0-freedesktop (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2
gir1.0-glib-2.0 (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2
gnome-menus (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
gstreamer0.10-plugins-bad (0.10.19-1ubuntu2) to 0.10.19-1ubuntu3
gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3) to 0.90.3+git20100810-0ubuntu1
gtk2-engines-pixbuf (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
gwibber (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
gwibber-service (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
hpijs (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-cups (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-data (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-gui (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
indicator-application (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libapparmor-perl (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libapparmor1 (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libappindicator0 (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libappindicator0.1-cil (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libclutter-1.0-0 (1.2.12-0ubuntu3) to 1.2.12-0ubuntu4
libclutter-gtk-0.10-0 (0.10.4-1ubuntu1) to 0.10.4-1ubuntu2
libdbusmenu-glib1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libdbusmenu-gtk1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libgail-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgail18 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgconf2-4 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
libgdk-pixbuf2.0-0 (2.21.6-2ubuntu3) to 2.21.6-2ubuntu5
libgnome-menu2 (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
libgtk2.0-0 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-bin (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libhpmud0 (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libindicate-gtk2 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libindicate4 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libjson-glib-1.0-0 (0.10.2-2ubuntu1) to 0.10.2-2ubuntu2
libqt4-dbus (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-designer (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-help (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-network (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-script (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-scripttools (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql-mysql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-svg (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-test (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-webkit (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xml (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xmlpatterns (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtcore4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtgui4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
librsvg2-2 (2.26.3-2) to 2.26.3-2ubuntu1
librsvg2-common (2.26.3-2) to 2.26.3-2ubuntu1
libsane-hpaio (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libsoup-gnome2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libsoup2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libtotem-plparser17 (2.30.2-1) to 2.30.2-1build1
libunique-1.0-0 (1.1.6-1ubuntu2) to 1.1.6-1ubuntu3
libwebkit-1.0-2 (1.2.3-1) to 1.2.3-1ubuntu1
libwebkit-1.0-common (1.2.3-1) to 1.2.3-1ubuntu1
libwnck-common (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
libwnck22 (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
openprinting-ppds (20100806-0ubuntu2) to 20100806-0ubuntu5
python-appindicator (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
python-gmenu (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
python-gobject (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-gobject-cairo (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-indicate (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
telepathy-butterfly (0.5.12-1) to 0.5.12-1ubuntu1
time (1.7-23build1) to 1.7-23ubuntu1
update-manager (1:0.142.5) to 1:0.142.7
update-manager-core (1:0.142.5) to 1:0.142.7
xterm (261-1ubuntu1) to 261-1ubuntu2

[B][COLOR="Red"]Installed the following packages:
libgirepository1.0-1 (0.9.3-0ubuntu2)[/COLOR][/B]


---

### Post by ratcheer on 2010-08-11
> **W00ster said:**
> I had the same problem yesterday.
Turned out that xorg had been deinstalled.

apt-get install xorg 
took care of it for me.

Thanks for the tip, but that did not work for me.

I tracked down the problem in Xorg.0.log. My existing video driver (nVidia 256.44) does not support the new X server 8.0 ABI. It tellos me to either get a newer video driver from nVidia or downgrade the X server.

Is there a newer nVidia driver that supports the new X server?

Tim

---

### Post by ratcheer on 2010-08-11
I just searched the nVidial download site and they still say that 256.44 is the latest, even when I expand the search to include Beta drivers.

Tim

---

### Post by ratcheer on 2010-08-11
Another possible workaround I have found is to edit xorg.conf and add a new section:

```

Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection

```

But, how would I know when the problem was solved?

Tim

---

### Post by plun on 2010-08-11
> **ratcheer said:**
> 
I tracked down the problem in Xorg.0.log. My existing video driver (nVidia 256.44) does not support the new X server 8.0 ABI. It tellos me to either get a newer video driver from nVidia or downgrade the X server.

Is there a newer nVidia driver that supports the new X server?

Tim

You must add -ignoreABI to xorg.conf


```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```

After that ver 256.44 works....

---

### Post by ratcheer on 2010-08-11
> **plun said:**
> You must add -ignoreABI to xorg.conf


```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```After that ver 256.44 works....

Yes, I already found that, but it seems to be a kludge, to me. I don't like doing things like that, because they usually come back and bite you, later.

Tim

---

### Post by taavikko on 2010-08-11
> **ratcheer said:**
> Yes, I already found that, but it seems to be a kludge, to me. I don't like doing things like that, because they usually come back and bite you, later.

Tim

Then use nouveau until nvidia-current is up-to-date.
Check the changelogs when the binary-blob supports the newer X

---

### Post by plun on 2010-08-11
> **ratcheer said:**
> Yes, I already found that, but it seems to be a kludge, to me. I don't like doing things like that, because they usually come back and bite you, later.

Tim

Well, there is no other way to solve this for the moment.

---

### Post by jppr on 2010-08-11
> **kansasnoob said:**
> It "self-resolved" for me using Synaptic:

Quote:
                                                 Commit Log for Wed Aug 11 06:30:41 2010


[B][COLOR=Red]Removed the following packages:
libgirepository1.0-0[/COLOR][/B]

Upgraded the following packages:
adobe-flashplugin (10.1.53.64-1lucid1) to 10.1.82.76-1maverick1
apparmor (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
apparmor-utils (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
bash (4.1-2ubuntu3) to 4.1-2ubuntu4
debhelper (7.4.20ubuntu6) to 8.0.0ubuntu1
foomatic-db (20100806-0ubuntu2) to 20100806-0ubuntu5
foomatic-db-engine (4.0.4-0ubuntu1) to 4.0.5-0ubuntu4
foomatic-filters (4.0.4-0ubuntu2) to 4.0.5-0ubuntu2
gconf-defaults-service (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2-common (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gir1.0-freedesktop (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2
gir1.0-glib-2.0 (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2
gnome-menus (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
gstreamer0.10-plugins-bad (0.10.19-1ubuntu2) to 0.10.19-1ubuntu3
gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3) to 0.90.3+git20100810-0ubuntu1
gtk2-engines-pixbuf (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
gwibber (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
gwibber-service (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
hpijs (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-cups (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-data (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-gui (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
indicator-application (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libapparmor-perl (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libapparmor1 (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libappindicator0 (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libappindicator0.1-cil (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libclutter-1.0-0 (1.2.12-0ubuntu3) to 1.2.12-0ubuntu4
libclutter-gtk-0.10-0 (0.10.4-1ubuntu1) to 0.10.4-1ubuntu2
libdbusmenu-glib1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libdbusmenu-gtk1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libgail-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgail18 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgconf2-4 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
libgdk-pixbuf2.0-0 (2.21.6-2ubuntu3) to 2.21.6-2ubuntu5
libgnome-menu2 (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
libgtk2.0-0 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-bin (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libhpmud0 (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libindicate-gtk2 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libindicate4 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libjson-glib-1.0-0 (0.10.2-2ubuntu1) to 0.10.2-2ubuntu2
libqt4-dbus (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-designer (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-help (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-network (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-script (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-scripttools (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql-mysql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-svg (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-test (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-webkit (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xml (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xmlpatterns (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtcore4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtgui4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
librsvg2-2 (2.26.3-2) to 2.26.3-2ubuntu1
librsvg2-common (2.26.3-2) to 2.26.3-2ubuntu1
libsane-hpaio (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libsoup-gnome2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libsoup2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libtotem-plparser17 (2.30.2-1) to 2.30.2-1build1
libunique-1.0-0 (1.1.6-1ubuntu2) to 1.1.6-1ubuntu3
libwebkit-1.0-2 (1.2.3-1) to 1.2.3-1ubuntu1
libwebkit-1.0-common (1.2.3-1) to 1.2.3-1ubuntu1
libwnck-common (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
libwnck22 (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
openprinting-ppds (20100806-0ubuntu2) to 20100806-0ubuntu5
python-appindicator (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
python-gmenu (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
python-gobject (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-gobject-cairo (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-indicate (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
telepathy-butterfly (0.5.12-1) to 0.5.12-1ubuntu1
time (1.7-23build1) to 1.7-23ubuntu1
update-manager (1:0.142.5) to 1:0.142.7
update-manager-core (1:0.142.5) to 1:0.142.7
xterm (261-1ubuntu1) to 261-1ubuntu2

[B][COLOR=Red]Installed the following packages:
libgirepository1.0-1 (0.9.3-0ubuntu2)[/COLOR][/B]

I have upgraded all those packages without any problems, there is now also new network-manager :popcorn:

---

### Post by yotux on 2010-08-11
I did some updates today and the system will not allow me to enable network manager

I have added an entry to my /etc/network/interfaces for a temp work around.  Will check back for updates tommorrow.

---

### Post by ratcheer on 2010-08-12
Ok, thanks everyone. I installed the IgnoreABI workaround to get back up. I just need to remember to check whether I can remove it the next time an nVidia driver is released.

Tim

---

### Post by Mills00013 on 2010-08-12
In regards to the actual libgirepository package, am I correct in assuming that having only one version (between libgirepository1.0-0 and libgirepository1.0-1) is all that I need? After forcing the manual installation of the 1.0-1 file, it kept them both on the system simultaneously. Update manager is now stalling because it wants to remove all my new packages to update the old one to the newest version.

tldr - I should only need one version of this, right? Should be safe to remove the old one completely, as long as it doesnt bring anything else with it?

---

### Post by ratcheer on 2010-08-12
> **Mills00013 said:**
> In regards to the actual libgirepository package, am I correct in assuming that having only one version (between libgirepository1.0-0 and libgirepository1.0-1) is all that I need? After forcing the manual installation of the 1.0-1 file, it kept them both on the system simultaneously. Update manager is now stalling because it wants to remove all my new packages to update the old one to the newest version.

tldr - I should only need one version of this, right? Should be safe to remove the old one completely, as long as it doesnt bring anything else with it?

I am not sure about what you need to do, but I am fairly cretain that on my system, it uninstalled the old one as part of the process of installing the new one. So, it sounds reasonable that you could uninstall the old one, then reinstall the new one. But don't take that as gospel.

Tim

---

### Post by Harry33 on 2010-08-14
> **Mills00013 said:**
> In regards to the actual libgirepository package, am I correct in assuming that having only one version (between libgirepository1.0-0 and libgirepository1.0-1) is all that I need?

In maverick, you cannot have both them if you installed all the necessary packages of the gobject-introspection:
It consists of three packages:
1. gir1.0-freedesktop_0.93-0ubuntu4
2. gir1.0-glib-2.0_0.93-0ubuntu4
3. libgirepository1.0-1_0.93-0ubuntu4

The second one depends on the third one (libgirepository1.0-1) and replaces libgirepository1.0-0.

If synaptic does not resolve the dependencies, uninstall
libgirepository1.0-0 first (with dependant packages) and then install the new ones.
Remember, also packages
python-gobject_2.21.5-0ubuntu3 and
python-gobject-cairo_2.21.5-0ubuntu3
depend on the libgirepository1.0-1.
You may need to remove the old ones too if upgrading does not succeed.

---

### Post by Yumi on 2010-08-14
Thanks for this workaround. Saved my day as I decided to join the testers at a bad time! But now and so far everything is working smoothly.

Please could you notify this thread when things are solved and the modification of xorg.conf can be removed.

Thanks
Michael

---

### Post by cariboo on 2010-08-15
I would suggest you keep an eye on [this]("http://ubuntuforums.org/showthread.php?t=1549195") sticky.

---

### Post by jerrylamos on 2010-08-15
> **Harry33 said:**
> In maverick, you cannot have both them if you installed all the necessary packages of the gobject-introspection:
It consists of three packages:
1. gir1.0-freedesktop_0.93-0ubuntu4
2. gir1.0-glib-2.0_0.93-0ubuntu4
3. libgirepository1.0-1_0.93-0ubuntu4

The second one depends on the third one (libgirepository1.0-1) and replaces libgirepository1.0-0.

If synaptic does not resolve the dependencies, uninstall
libgirepository1.0-0 first (with dependant packages) and then install the new ones.
Uninstall did me in.  It would not install libgirepository1.0-1.

Thrashed around a while then installed Alpha 3 from CD.  The Alpha 2 updated to Alpha 3 choked on the libgirepository problem.

Only mess I had is with the two hard drives, the IDE and the SATA.  For Alpha 3 I had to change the boot order in the bios ?! otherwise Alpha 3 Grub thought the boot was hd(1,0) while Maverick thought it was /dev/sda.  Backwards.

Jerry

---

### Post by MarkieB on 2010-08-18
no longer participating in ubuntuforums.org

---

