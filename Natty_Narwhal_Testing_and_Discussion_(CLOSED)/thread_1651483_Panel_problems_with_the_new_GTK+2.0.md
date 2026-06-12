---
title: "Panel problems with the new GTK+2.0"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2010-12-23
After todays upgrade of GTK+2.0_2.23.3-1ubuntu2 certain applets became invisible in the panel.
These applets are certainly affected:
- Clock (including Weather and Calendar functions)
- Wastebasket (Trash)
- Notification Area (including Network-Manager-Applet)

As a workaround, applets do reappear, when I downgrade to the previous version of GTK (2.23.2-0ubuntu4).
Installing the version 2.23.3-1ubuntu2 I get the following error message:

Unpacking replacement libgtk2.0-bin ...
Processing triggers for man-db ...
Gdk-CRITICAL **: IA__gdk_window_add_filter: assertion `window == NULL || GDK_IS_WINDOW (window)' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gdk-CRITICAL **: IA__gdk_window_add_filter: assertion `window == NULL || GDK_IS_WINDOW (window)' failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103

Does anyone else get this?
See bug #693758
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693758](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693758)

---

### Post by Harry33 on 2010-12-23
Oh, and I get these with Gnome-Classic.

---

### Post by pressureman on 2010-12-23
Me too...

Maybe this is some crafty plan to encourage people to switch to Unity ;-)

Classic desktop certainly does seem to be getting neglected at this stage of the development phase.

---

### Post by duanedesign on 2010-12-23
I had this exact bug when I update/upgraded today. Thanks for the tip on the workaround. You can downgrade the libgtk2.0-0 package with the following commands.

```
wget http://launchpadlibrarian.net/60749886/libgtk2.0-0_2.23.2-0ubuntu4_amd64.deb
```
Once downloaded.
```
sudo dpkg -i --force-all libgtk2.0-0_2.23.2-0ubuntu4_amd64.deb
```
Then Sign out and back in.

---

### Post by hugmenot on 2010-12-23
> **duanedesign said:**
> I had this exact bug when I update/upgraded today. Thanks for the tip on the workaround. You can downgrade the libgtk2.0-0 package with the following commands.

```
wget https://launchpad.net/ubuntu/natty/amd64/libgtk2.0-0/2.23.2-0ubuntu4
```
Once downloaded.
```
sudo dpkg -i --force-all libgtk2.0-0_2.23.2-0ubuntu4_amd64.deb
```
Then Sign out and back in.

Try that again.

---

### Post by miegiel on 2010-12-23
> **duanedesign said:**
> I had this exact bug when I update/upgraded today. Thanks for the tip on the workaround. You can downgrade the libgtk2.0-0 package with the following commands.

```
wget https://launchpad.net/ubuntu/natty/amd64/libgtk2.0-0/2.23.2-0ubuntu4
```
Once downloaded.
```
sudo dpkg -i --force-all libgtk2.0-0_2.23.2-0ubuntu4_amd64.deb
```
Then Sign out and back in.

Are you sure there are no typos in the wget line?

In any case I found a link to the i386 .deb in [https://launchpad.net/ubuntu/natty/i386/libgtk2.0-0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/natty/i386/libgtk2.0-0/2.23.2-0ubuntu4)

For me the mount and mixer panel applet also failed. And I can't copy/paste and select/middlebutton-paste from 1 app to another. (Running xubuntu!)

I'm hesitating to reboot, sign off/in. I've got unmet dependencies now (bah can't paste): *gtk2-engines-pixbuf, libgail18* and *libgtk2.0-bin*

---

### Post by Harry33 on 2010-12-23
Here is how you can downgrade the buggy GTK+2.0_2.23.3-1ubuntu2 packages:
Note, that you must downgrade all six (6) of them, otherwise there will be depency problems.

The safest way I know is to go and download the deb packages from Launchpad:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4)
Just choose the architecture first.
Packages:
gir1.2-gtk-2.0
gtk2-engines-pixbuf
libgail18
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common

Then (all apps closed) in terminal go to the folder you downloaded them,
To see the packages, run: dir
Then run (where x is the exact name of the package):
sudo dpkg -i x1.deb x2.deb ...

---

### Post by miegiel on 2010-12-23
> **Harry33 said:**
> Here is how you can downgrade the buggy GTK+2.0_2.23.3-1ubuntu2 packages:
Note, that you must downgrade all six (6) of them, otherwise there will be depency problems.

The safest way I know is to go and download the deb packages from Launchpad:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4)
Just choose the architecture first.
Packages:
gir1.2-gtk-2.0
gtk2-engines-pixbuf
libgail18
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common

Then (all apps closed) in terminal go to the folder you downloaded them,
To see the packages, run: dir
Then run (where x is the exact name of the package):
sudo dpkg -i x1.deb x2.deb ...

Thanks, that was exactly what I needed to know to solve this. Only *libgail-common* is missing in your list, but that's a minor detail.

---

### Post by Harry33 on 2010-12-23
> **miegiel said:**
> Thanks, that was exactly what I needed to know to solve this. Only *libgail-common* is missing in your list, but that's a minor detail.

Yes it is missing for a reason.
I do not have at-spi installed, so I do not have libgail-common installed either.

---

### Post by tghe-retford on 2010-12-23
The same bug will also cause Flash within GTK+2.0 applications to fail to show. Downgrading to version 2.23.2-0ubuntu4 fixes that problem.

---

### Post by afv on 2010-12-23
Panel problems solved at gtk+2.0 version 2.23.3-1ubuntu3:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.3-1ubuntu3](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.3-1ubuntu3)

---

### Post by Harry33 on 2010-12-23
> **afv said:**
> Panel problems solved at gtk+2.0 version 2.23.3-1ubuntu3:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.3-1ubuntu3](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.3-1ubuntu3)

Yes new version is building right now.
It should fix this.
Will test it once it gets built.

---

### Post by Harry33 on 2010-12-23
Right. This is fixed.
The version GTK+2.0_2.32.3-1ubuntu3 works OK.

---

### Post by Harry33 on 2010-12-23
No it is not OK. It was too early to claim this fixed.
Panels are OK now, but there is another problem around.
Firefox and Chromium both crash (segmentation fault) if you mark (paint) and copy text.

Yes and as before, downgrading to version GTK+2.0_2.23.2-0ubuntu4 works fine. No more segfaults.

---

### Post by Harry33 on 2010-12-24
Finally a working GTK+2.0.
The newest upload GTK+2-0_2.23.3.is2.23.2-0ubuntu1 is, as the package name suggests a rollback to the previous working build.
Anyway - panels do work and so does the copy function too.
This is solved for now.

---

