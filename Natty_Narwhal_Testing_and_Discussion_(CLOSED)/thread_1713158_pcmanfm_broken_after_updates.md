---
title: "pcmanfm broken after updates?"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-03-23
upgrades 2:00pm Pacific Standard time: 
mirror.anl.gov United States:
64-bit Natty:
Seems to have given no access to pcmanfm
Any other users find same?
```
rick@rick-HP:~$ aptitude show pcmanfm
Package: pcmanfm                         
New: yes
State: installed
Automatically installed: no
Version: 0.9.8+git-6240436419-0ubuntu1
Priority: optional
Section: universe/utils
Maintainer: Julien Lavergne <gilir@ubuntu.com>


  
```Start-Date: 2011-03-23  13:54:17
Upgrade: libpcsclite1:amd64 (1.7.0-2ubuntu1, 1.7.0-2ubuntu2), libgtk2.0-common:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), unity:amd64 (3.6.6-0ubuntu2, 3.6.6-0ubuntu3), libc-bin:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), libxcomposite1:amd64 (0.4.3-1, 0.4.3-1ubuntu1), libgail18:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), libcompizconfig0:amd64 (0.9.4-0ubuntu1, 0.9.4-0ubuntu2), gwibber-service-identica:amd64 (2.91.91.1-0ubuntu1, 2.91.92-0ubuntu1), libgudev-1.0-0:amd64 (166-0ubuntu5, 166-0ubuntu6), libevdocument3:amd64 (2.32.0-0ubuntu11, 2.32.0-0ubuntu12), linux-headers-2.6.38-7:amd64 (2.6.38-7.37, 2.6.38-7.3, python-piston-mini-client:amd64 (0.1+bzr29-0ubuntu1, 0.3~bzr31-0ubuntu1), unity-common:amd64 (3.6.6-0ubuntu2, 3.6.6-0ubuntu3), libdee-1.0-1:amd64 (0.5.16-0ubuntu1, 0.5.16-0ubuntu3), libgexiv2-0:amd64 (0.3.0-0ubuntu1, 0.3.1-0ubuntu1), libapparmor-perl:amd64 (2.6.0-0ubuntu3, 2.6.0-0ubuntu4), libgnomevfs2-common:amd64 (2.24.4-0ubuntu2, 2.24.4-0ubuntu3), libevview3:amd64 (2.32.0-0ubuntu11, 2.32.0-0ubuntu12), libgnomevfs2-extra:amd64 (2.24.4-0ubuntu2, 2.24.4-0ubuntu3), transmission-gtk:amd64 (2.13-0ubuntu6, 2.13-0ubuntu7), gwibber-service-twitter:amd64 (2.91.91.1-0ubuntu1, 2.91.92-0ubuntu1), gwibber-service-facebook:amd64 (2.91.91.1-0ubuntu1, 2.91.92-0ubuntu1), gir1.2-gtk-2.0:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), gstreamer0.10-plugins-good:amd64 (0.10.28-0ubuntu3, 0.10.28-0ubuntu4), libc6-i386:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), transmission-common:amd64 (2.13-0ubuntu6, 2.13-0ubuntu7), compiz-plugins-main:amd64 (0.9.4-0ubuntu4, 0.9.4git20110322-0ubuntu1), udev:amd64 (166-0ubuntu5, 166-0ubuntu6), apparmor-utils:amd64 (2.6.0-0ubuntu3, 2.6.0-0ubuntu4), multiarch-support:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), libenchant1c2a:amd64 (1.6.0-1, 1.6.0-2), libgnomevfs2-0:amd64 (2.24.4-0ubuntu2, 2.24.4-0ubuntu3), libtelepathy-glib0:amd64 (0.13.17-1ubuntu1, 0.14.1-1ubuntu1), alsa-utils:amd64 (1.0.24.2-0ubuntu2, 1.0.24.2-0ubuntu3), evince-common:amd64 (2.32.0-0ubuntu11, 2.32.0-0ubuntu12), compiz-gnome:amd64 (0.9.4-0ubuntu7, 0.9.4git20110322-0ubuntu2), libgcrypt11:amd64 (1.4.6-4ubuntu1, 1.4.6-4ubuntu2), evince:amd64 (2.32.0-0ubuntu11, 2.32.0-0ubuntu12), libgail-common:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), gstreamer0.10-pulseaudio:amd64 (0.10.28-0ubuntu3, 0.10.28-0ubuntu4), gwibber-service:amd64 (2.91.91.1-0ubuntu1, 2.91.92-0ubuntu1), ufw:amd64 (0.30.0-3ubuntu1, 0.30.1-1ubuntu1), compiz-plugins:amd64 (0.9.4-0ubuntu7, 0.9.4git20110322-0ubuntu2), libapparmor1:amd64 (2.6.0-0ubuntu3, 2.6.0-0ubuntu4), libdecoration0:amd64 (0.9.4-0ubuntu7, 0.9.4git20110322-0ubuntu2), libudev0:amd64 (166-0ubuntu5, 166-0ubuntu6), gtk2-engines-pixbuf:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), libc6-dev:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), apparmor:amd64 (2.6.0-0ubuntu3, 2.6.0-0ubuntu4), compiz:amd64 (0.9.4-0ubuntu7, 0.9.4git20110322-0ubuntu2), compiz-fusion-plugins-main:amd64 (0.9.4-0ubuntu4, 0.9.4git20110322-0ubuntu1), gwibber:amd64 (2.91.91.1-0ubuntu1, 2.91.92-0ubuntu1), libgtk2.0-bin:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3), libxi6:amd64 (1.4.1-1ubuntu1, 1.4.1-1ubuntu2), libc-dev-bin:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), compiz-core:amd64 (0.9.4-0ubuntu7, 0.9.4git20110322-0ubuntu2), libc6:amd64 (2.13-0ubuntu8, 2.13-0ubuntu9), binutils:amd64 (2.21.0.20110302-2ubuntu3, 2.21.0.20110322-1ubuntu1), libgtk2.0-0:amd64 (2.24.3-0ubuntu2, 2.24.3-0ubuntu3)
Remove: libpoppler12:amd64 (0.16.2-0ubuntu1)
End-Date: 2011-03-23  13:57:43

---

### Post by garvinrick4 on 2011-03-23
One install pcmanfm is stable and one install is not I have to assume it is my machine
and or user and not upgrades now.

---

