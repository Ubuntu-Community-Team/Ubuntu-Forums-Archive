---
title: "stream video in firefox"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by carverj on 2007-01-31
Hi all,
        Have removed totem & mplayer plugins from usr/lib/mozilla-firefox/plugins to install RealPlayer 10 plugin.

Following error:

```
Copying RealPlayer files...sh: cannot create /usr/lib/mozilla-firefox/plugins/install.log: Permission denied
sh: cannot create /usr/lib/mozilla-firefox/plugins/install.log: Permission denied
sh: cannot create install.log: Permission denied
sh: cannot create /usr/lib/mozilla-firefox/plugins/install.log: Permission denied
sh: ./postinst/postinst.sh: not found

RealPlayer installation is complete.
Cleaning up installation files...
Done.

```

Just wondering what I have done wrong here?
Thanks very much

---

### Post by HenrikAn on 2007-01-31
It looks like you were expected to run the install as root?
Try again with
```
sudo ...
```

---

### Post by carverj on 2007-01-31
Thanks mate, getting there now... although

```
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ..y.
enter the prefix for symbolic links [/usr]: ....../us...................
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
configuring pixmaps...
configuring locale...
configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

```

Does this look OK?

---

### Post by Clouseau on 2007-01-31
Does Totem play wmv files, because when I try to play streaming video, all I get is the audio and visualizations. Also, I need to know if M-Player is as good as I hear. Anyones opinion will be very helpful. Please explain why you like it.
Thanks

:guitar:

---

### Post by carverj on 2007-01-31
Could someone please take a look at the contents of my /usr/lib/mozilla-firefox/plugins directory below and let me know what needs to be deleted or amended in order to use a streaming plugin.

```
jeremy@jeremy-desktop:/usr/lib/mozilla-firefox/plugins$ ls -l
total 664
drwxr-sr-x 2 root root   4096 2007-02-01 01:41 Bin
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 codecs
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 common
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 doc
-rw-r--r-- 1 root root  25290 2007-02-01 01:41 install.log
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 lib
lrwxrwxrwx 1 root root     39 2007-01-31 19:31 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root     36 2007-02-01 05:32 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root     37 2007-02-01 05:32 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root     38 2007-02-01 05:32 libtotem-complex-plugin.so -> ../../totem/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root     39 2007-02-01 05:32 libtotem-complex-plugin.xpt -> ../../totem/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root     34 2007-02-01 05:32 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root     35 2007-02-01 05:32 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root     36 2007-02-01 05:32 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root     37 2007-02-01 05:32 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root     42 2007-02-01 05:32 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root     43 2007-02-01 05:32 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root   9044 2007-01-03 05:29 libunixprintplugin.so
-rwxr-xr-x 1 root root  11286 2006-07-19 14:17 LICENSE
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 mozilla
lrwxrwxrwx 1 root root     51 2007-02-01 01:37 nphelix.so -> /usr/lib/mozilla-firefox/plugins/mozilla/nphelix.so
lrwxrwxrwx 1 root root     52 2007-02-01 01:37 nphelix.xpt -> /usr/lib/mozilla-firefox/plugins/mozilla/nphelix.xpt
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 plugins
drwxr-sr-x 2 root root   4096 2006-07-19 14:17 postinst
-rw-r--r-- 1 root root   3047 2006-07-19 14:17 README
-rwxr-xr-x 1 root root   2492 2007-02-01 01:41 realplay
-rwxr-xr-x 1 root root   2486 2007-02-01 01:41 realplay.bak
-rwxr-xr-x 1 root root 570344 2006-07-19 14:17 realplay.bin
drwxr-sr-x 7 root root   4096 2006-07-19 14:17 share

```

Also, I'm sure I deleted the libtotem plugins, but they have reinstalled themselves.

---

