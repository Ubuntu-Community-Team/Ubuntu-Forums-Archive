---
title: "FGLRX ATI/AMD Catalyst 12.3 Won't Boot on Ubuntu 11.10"
date: 2012-04-14
forum: Multimedia Software
---

### Post by fortitude on 2012-04-14
Hi folks, I had a situation yesterday and am hoping for a solution. Here's what happened....

1) I let Ubuntu Update Manager install a bunch of updates yesterday. Prior to that, I had a perfectly working system running Ubuntu 11.10 and Catalyst 11.12.

2) I noticed that XBMC would not work. It asked for a valid OpenGL driver.

3) I tried to open Catalyst Control Center..... no response.

4) I tried running the installer for 12.3. It said I had a FGLRX driver installed already. I closed the installer.

5) I ran the uninstall script for my old driver. It would not uninstall. It said there were changed files. I ran it again with the --force option. That worked, but worried it may have hosed the system.

6) Installed 12.3 successfully from f1 terminal after stopping lightdm. Rebooted -- system hung at black screen with flashing cursor.

7) Booted to recovery mode, mounted, and then ran the uninstall script for 12.3.

8) Rebooted and ran the 12.3 installer from within the shell this time without stopping lightdm. Rebooted. Same thing. Repeated step 7.

9) Installed the 11.8 driver that comes with Ubuntu 11.10. Rebooted. It worked, but I get artifacts in games under wine and the video tears a bit when watching a DVD... newer drivers seemed to improve those issues. So, I'm still looking for a new driver.

Any tips to troubleshoot why a 12.3 Catalyst install fails to boot on Ubuntu 11.10? Did I break something in step 5 with the --force switch?

---

### Post by fortitude on 2012-04-14
I did a little bit more research.... here is the dpkg.log from yesterday.... I see some FGLRX lines in there.

```

2012-04-13 12:21:36 startup archives unpack
2012-04-13 12:21:37 upgrade google-chrome-stable 18.0.1025.151-r130497 18.0.1025.162-r131933
2012-04-13 12:21:37 status half-configured google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:37 status unpacked google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:37 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status triggers-pending man-db 2.6.0.2-2
2012-04-13 12:21:40 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status triggers-pending bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 12:21:40 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status triggers-pending desktop-file-utils 0.18-0ubuntu9
2012-04-13 12:21:40 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status triggers-pending gnome-menus 3.2.0-0ubuntu2
2012-04-13 12:21:40 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status half-installed google-chrome-stable 18.0.1025.151-r130497
2012-04-13 12:21:40 status unpacked google-chrome-stable 18.0.1025.162-r131933
2012-04-13 12:21:40 status unpacked google-chrome-stable 18.0.1025.162-r131933
2012-04-13 12:21:40 upgrade libgl1-mesa-dri 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:40 status half-configured libgl1-mesa-dri 7.11-0ubuntu3
2012-04-13 12:21:40 status unpacked libgl1-mesa-dri 7.11-0ubuntu3
2012-04-13 12:21:40 status half-configured libgl1-mesa-dri:i386 7.11-0ubuntu3
2012-04-13 12:21:40 status half-installed libgl1-mesa-dri 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-dri 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-dri 7.11-0ubuntu3.2
2012-04-13 12:21:41 status unpacked libgl1-mesa-dri 7.11-0ubuntu3.2
2012-04-13 12:21:41 upgrade libgl1-mesa-dri:i386 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:41 status half-configured libgl1-mesa-dri:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-dri:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-dri:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-dri:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-dri:i386 7.11-0ubuntu3.2
2012-04-13 12:21:41 status unpacked libgl1-mesa-dri:i386 7.11-0ubuntu3.2
2012-04-13 12:21:41 upgrade libgl1-mesa-glx 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:41 status half-configured libgl1-mesa-glx 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx 7.11-0ubuntu3
2012-04-13 12:21:41 status half-configured libgl1-mesa-glx:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-glx 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-glx 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx 7.11-0ubuntu3.2
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx 7.11-0ubuntu3.2
2012-04-13 12:21:41 upgrade libgl1-mesa-glx:i386 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:41 status half-configured libgl1-mesa-glx:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-glx:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status half-installed libgl1-mesa-glx:i386 7.11-0ubuntu3
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx:i386 7.11-0ubuntu3.2
2012-04-13 12:21:41 status unpacked libgl1-mesa-glx:i386 7.11-0ubuntu3.2
2012-04-13 12:21:42 upgrade libglapi-mesa:i386 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:42 status half-configured libglapi-mesa:i386 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglapi-mesa:i386 7.11-0ubuntu3
2012-04-13 12:21:42 status half-configured libglapi-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglapi-mesa:i386 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglapi-mesa:i386 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglapi-mesa:i386 7.11-0ubuntu3.2
2012-04-13 12:21:42 status unpacked libglapi-mesa:i386 7.11-0ubuntu3.2
2012-04-13 12:21:42 upgrade libglapi-mesa 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:42 status half-configured libglapi-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglapi-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglapi-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglapi-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglapi-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:42 status unpacked libglapi-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:42 upgrade libglu1-mesa 7.11-0ubuntu3 7.11-0ubuntu3.2
2012-04-13 12:21:42 status half-configured libglu1-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglu1-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglu1-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status half-installed libglu1-mesa 7.11-0ubuntu3
2012-04-13 12:21:42 status unpacked libglu1-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:42 status unpacked libglu1-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:42 upgrade winbind 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:42 status half-configured winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:42 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:42 status half-installed winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:42 status half-installed winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status triggers-pending ureadahead 0.100.0-11
2012-04-13 12:21:43 status half-installed winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status half-installed winbind 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:43 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:43 upgrade samba 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:43 status half-configured samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status half-installed samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status half-installed samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status half-installed samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status triggers-pending ufw 0.30.1-2ubuntu1
2012-04-13 12:21:43 status half-installed samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:43 status triggers-pending ureadahead 0.100.0-11
2012-04-13 12:21:43 status half-installed samba 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 upgrade libwbclient0 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 status half-configured libwbclient0 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status unpacked libwbclient0 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status half-installed libwbclient0 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status half-installed libwbclient0 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status unpacked libwbclient0 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 status unpacked libwbclient0 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 upgrade smbclient 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:44 status half-configured smbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status unpacked smbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:44 status half-installed smbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed smbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed smbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status unpacked smbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 status unpacked smbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 upgrade libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 status half-configured libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status unpacked libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status unpacked libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 status unpacked libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 upgrade samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 status half-configured samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status unpacked samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status half-installed samba-common-bin 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:45 status unpacked samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:45 status unpacked samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 upgrade samba-common 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 status half-configured samba-common 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status half-installed samba-common 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status half-installed samba-common 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 upgrade libsmbclient 2:3.5.11~dfsg-1ubuntu2.1 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 status half-configured libsmbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status unpacked libsmbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status half-installed libsmbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status half-installed libsmbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status half-installed libsmbclient 2:3.5.11~dfsg-1ubuntu2.1
2012-04-13 12:21:46 status unpacked libsmbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 status unpacked libsmbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:46 trigproc man-db 2.6.0.2-2 2.6.0.2-2
2012-04-13 12:21:46 status half-configured man-db 2.6.0.2-2
2012-04-13 12:21:47 status installed man-db 2.6.0.2-2
2012-04-13 12:21:47 trigproc bamfdaemon 0.2.104-0ubuntu1.1 0.2.104-0ubuntu1.1
2012-04-13 12:21:47 status half-configured bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 12:21:48 status installed bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 12:21:48 trigproc desktop-file-utils 0.18-0ubuntu9 0.18-0ubuntu9
2012-04-13 12:21:48 status half-configured desktop-file-utils 0.18-0ubuntu9
2012-04-13 12:21:48 status installed desktop-file-utils 0.18-0ubuntu9
2012-04-13 12:21:48 trigproc gnome-menus 3.2.0-0ubuntu2 3.2.0-0ubuntu2
2012-04-13 12:21:48 status half-configured gnome-menus 3.2.0-0ubuntu2
2012-04-13 12:21:48 status installed gnome-menus 3.2.0-0ubuntu2
2012-04-13 12:21:48 trigproc ureadahead 0.100.0-11 0.100.0-11
2012-04-13 12:21:48 status half-configured ureadahead 0.100.0-11
2012-04-13 12:21:48 status installed ureadahead 0.100.0-11
2012-04-13 12:21:48 trigproc ufw 0.30.1-2ubuntu1 0.30.1-2ubuntu1
2012-04-13 12:21:48 status half-configured ufw 0.30.1-2ubuntu1
2012-04-13 12:21:48 status installed ufw 0.30.1-2ubuntu1
2012-04-13 12:21:48 startup packages configure
2012-04-13 12:21:48 configure google-chrome-stable 18.0.1025.162-r131933 <none>
2012-04-13 12:21:48 status unpacked google-chrome-stable 18.0.1025.162-r131933
2012-04-13 12:21:48 status half-configured google-chrome-stable 18.0.1025.162-r131933
2012-04-13 12:21:53 status installed google-chrome-stable 18.0.1025.162-r131933
2012-04-13 12:21:53 configure libgl1-mesa-dri 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:53 status unpacked libgl1-mesa-dri 7.11-0ubuntu3.2
2012-04-13 12:21:53 status half-configured libgl1-mesa-dri 7.11-0ubuntu3.2
2012-04-13 12:21:53 status installed libgl1-mesa-dri 7.11-0ubuntu3.2
2012-04-13 12:21:53 configure libgl1-mesa-dri:i386 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:53 status unpacked libgl1-mesa-dri:i386 7.11-0ubuntu3.2
2012-04-13 12:21:53 status half-configured libgl1-mesa-dri:i386 7.11-0ubuntu3.2
2012-04-13 12:21:53 status installed libgl1-mesa-dri:i386 7.11-0ubuntu3.2
2012-04-13 12:21:53 configure libglapi-mesa 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:53 status unpacked libglapi-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:53 status half-configured libglapi-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:53 status installed libglapi-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:53 status triggers-pending libc-bin 2.13-20ubuntu5.1
2012-04-13 12:21:53 configure libgl1-mesa-glx 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:53 status unpacked libgl1-mesa-glx 7.11-0ubuntu3.2
2012-04-13 12:21:53 status half-configured libgl1-mesa-glx 7.11-0ubuntu3.2
2012-04-13 12:21:54 status installed libgl1-mesa-glx 7.11-0ubuntu3.2
2012-04-13 12:21:54 configure libglapi-mesa:i386 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:54 status unpacked libglapi-mesa:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 status half-configured libglapi-mesa:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 status installed libglapi-mesa:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 configure libgl1-mesa-glx:i386 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:54 status unpacked libgl1-mesa-glx:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 status half-configured libgl1-mesa-glx:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 status installed libgl1-mesa-glx:i386 7.11-0ubuntu3.2
2012-04-13 12:21:54 configure libglu1-mesa 7.11-0ubuntu3.2 <none>
2012-04-13 12:21:54 status unpacked libglu1-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:54 status half-configured libglu1-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:54 status installed libglu1-mesa 7.11-0ubuntu3.2
2012-04-13 12:21:54 configure libwbclient0 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:21:54 status unpacked libwbclient0 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status half-configured libwbclient0 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status installed libwbclient0 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 configure samba-common 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:21:54 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status unpacked samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:21:54 status half-configured samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:50 status installed samba-common 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:50 configure winbind 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:50 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:50 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status half-configured winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status installed winbind 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 configure samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:51 status unpacked samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status half-configured samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status installed samba-common-bin 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 configure samba 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status unpacked samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:51 status half-configured samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 status installed samba 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 configure smbclient 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:52 status unpacked smbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 status half-configured smbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 status installed smbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 configure libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:52 status unpacked libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 status unpacked libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:52 status half-configured libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:53 status installed libpam-smbpass 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:53 configure libsmbclient 2:3.5.11~dfsg-1ubuntu2.2 <none>
2012-04-13 12:22:53 status unpacked libsmbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:53 status half-configured libsmbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:53 status installed libsmbclient 2:3.5.11~dfsg-1ubuntu2.2
2012-04-13 12:22:53 trigproc libc-bin 2.13-20ubuntu5.1 <none>
2012-04-13 12:22:53 status half-configured libc-bin 2.13-20ubuntu5.1
2012-04-13 12:22:53 status installed libc-bin 2.13-20ubuntu5.1
2012-04-13 13:48:30 startup packages configure
2012-04-13 20:53:30 startup archives unpack
2012-04-13 20:53:31 install fglrx 2:8.881-0ubuntu4.1 2:8.881-0ubuntu4.1
2012-04-13 20:53:31 status half-installed fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:32 status triggers-pending ureadahead 0.100.0-11
2012-04-13 20:53:32 status half-installed fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 install fglrx-amdcccle <none> 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status half-installed fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 trigproc ureadahead 0.100.0-11 0.100.0-11
2012-04-13 20:53:33 status half-configured ureadahead 0.100.0-11
2012-04-13 20:53:33 status installed ureadahead 0.100.0-11
2012-04-13 20:53:33 startup packages configure
2012-04-13 20:53:33 configure fglrx 2:8.881-0ubuntu4.1 <none>
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status unpacked fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:33 status half-configured fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status installed fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status triggers-pending gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:53:53 status triggers-awaited fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status triggers-pending bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:53:53 status triggers-awaited fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status triggers-pending initramfs-tools 0.99ubuntu8
2012-04-13 20:53:53 status triggers-pending libc-bin 2.13-20ubuntu5.1
2012-04-13 20:53:53 trigproc gnome-menus 3.2.0-0ubuntu2 <none>
2012-04-13 20:53:53 status half-configured gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:53:53 status installed gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:53:53 trigproc bamfdaemon 0.2.104-0ubuntu1.1 <none>
2012-04-13 20:53:53 status half-configured bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:53:53 status installed fglrx 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status installed bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:53:53 configure fglrx-amdcccle 2:8.881-0ubuntu4.1 <none>
2012-04-13 20:53:53 status unpacked fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status half-configured fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 status installed fglrx-amdcccle 2:8.881-0ubuntu4.1
2012-04-13 20:53:53 trigproc initramfs-tools 0.99ubuntu8 <none>
2012-04-13 20:53:53 status half-configured initramfs-tools 0.99ubuntu8
2012-04-13 20:54:01 status installed initramfs-tools 0.99ubuntu8
2012-04-13 20:54:01 trigproc libc-bin 2.13-20ubuntu5.1 <none>
2012-04-13 20:54:01 status half-configured libc-bin 2.13-20ubuntu5.1
2012-04-13 20:54:01 status installed libc-bin 2.13-20ubuntu5.1
2012-04-13 20:54:02 status triggers-pending gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:54:02 status not-installed fakepackage <none>
2012-04-13 20:54:03 status triggers-pending bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 status not-installed fakepackage <none>
2012-04-13 20:54:03 startup packages configure
2012-04-13 20:54:03 trigproc bamfdaemon 0.2.104-0ubuntu1.1 <none>
2012-04-13 20:54:03 status half-configured bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 status installed bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 trigproc gnome-menus 3.2.0-0ubuntu2 <none>
2012-04-13 20:54:03 status half-configured gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:54:03 status installed gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:54:03 status triggers-pending gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:54:03 status not-installed fakepackage <none>
2012-04-13 20:54:03 status triggers-pending bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 status not-installed fakepackage <none>
2012-04-13 20:54:03 startup packages configure
2012-04-13 20:54:03 trigproc bamfdaemon 0.2.104-0ubuntu1.1 <none>
2012-04-13 20:54:03 status half-configured bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 status installed bamfdaemon 0.2.104-0ubuntu1.1
2012-04-13 20:54:03 trigproc gnome-menus 3.2.0-0ubuntu2 <none>
2012-04-13 20:54:03 status half-configured gnome-menus 3.2.0-0ubuntu2
2012-04-13 20:54:03 status installed gnome-menus 3.2.0-0ubuntu2

```

---

### Post by fortitude on 2012-04-15
I solved this myself, so I'm marking this thread as solved.

The main problem was that I had modified /etc/lightdm/lightdm.conf for a multi-seat config. Changing it back to the default allowed the driver to be installed and boot. However, I found that installing from compiled debs (as recommended in certain guides) failed as well (it installed, but the test (fglrxinfo) failed), I had to just sh the run file, which worked just fine.

Here is more or less what I did:

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

and, just in case, 

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/atithen

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic

[COLOR=#000000][FONT=sans-serif]*If you are using the x86_64 architecture (64 bit)*: 1. Install "ia32-libs" before proceeding![/FONT][/COLOR]
sudo apt-get install ia32-libs

[COLOR=#000000][FONT=sans-serif]2. Create a symlink from /usr/lib64 to /usr/lib :[/FONT][/COLOR]

cd /usr ; sudo ln -svT lib /usr/lib64

***Download the latest Catalyst package.***

[COLOR=#000000][FONT=sans-serif]This package contains both the 32-bit and 64-bit driver.[/FONT][/COLOR]
cd ~/; mkdir catalyst[12.3]("http://wiki.cchtml.com/index.php/12.3"); cd catalyst[12.3]("http://wiki.cchtml.com/index.php/12.3")/
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-](http://www2.ati.com/drivers/linux/amd-driver-installer-)[12-3]("http://wiki.cchtml.com/index.php/12-3")-x86.x86_64.run
chmod +x amd-driver-installer-[12-3]("http://wiki.cchtml.com/index.php/12-3")-x86.x86_64.run

control + alt + F1

log in, etc...

sudo /etc/init.d/lightdm stop
cd catalyst[12.3]("http://wiki.cchtml.com/index.php/12.3")/
sudo sh amd-driver-installer-[12-3]("http://wiki.cchtml.com/index.php/12-3")-x86.x86_64.run
sudo aticonfig --initial
sudo /etc/init.d/lightdm start

---

