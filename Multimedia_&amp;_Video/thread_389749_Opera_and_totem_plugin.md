---
title: "Opera and totem plugin"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Kray on 2007-03-21
Few days ago I've seen few Apple ads ([http://www.apple.com/getamac/ads/)](http://www.apple.com/getamac/ads/)). No, I'm not going to buy Mac, but some ads are really briliant and funny ('Security' is plainly genious ;-)). That said, I have serious problems with making this ads play in Opera.

They are all in QuickTime format, and I can watch them in Totem and Firefox (using totem-plugins). Opera is compatible with mozilla plugins, but with default configuration when launched via

```
opera --debugplugin
```

there are many messages describing problems with totem plugins:

```
operapluginwrapper: [plugin probing] /usr/lib/opera/plugins/libnpp.so
opera: plugin detection successful: /usr/lib/opera/plugins/libnpp.so
operapluginwrapper: [plugin failed ] /usr/lib/mozilla/plugins/libtotem-complex-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
operapluginwrapper: [plugin failed ] /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
opera: plugin detection successful: /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
operapluginwrapper: [plugin failed ] /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libjavaplugin.so
operapluginwrapper: [plugin failure] (No 'mimedescription') /usr/lib/mozilla/plugins/libjavaplugin.so
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libflashplayer.so
opera: plugin detection successful: /usr/lib/mozilla/plugins/libflashplayer.so
operapluginwrapper: [plugin failed ] /usr/lib/mozilla/plugins/libtotem-basic-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin failed ] /usr/lib/firefox/plugins/libtotem-complex-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin failed ] /usr/lib/firefox/plugins/libtotem-gmp-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin probing] /usr/lib/firefox/plugins/libtotem-mully-plugin.so
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
opera: plugin detection successful: /usr/lib/firefox/plugins/libtotem-mully-plugin.so
operapluginwrapper: [plugin failed ] /usr/lib/firefox/plugins/libtotem-narrowspace-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
operapluginwrapper: [plugin probing] /usr/lib/firefox/plugins/libjavaplugin.so
operapluginwrapper: [plugin failure] (No 'mimedescription') /usr/lib/firefox/plugins/libjavaplugin.so
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin probing] /usr/lib/firefox/plugins/libflashplayer.so
opera: plugin detection successful: /usr/lib/firefox/plugins/libflashplayer.so
operapluginwrapper: [plugin probing] /usr/lib/firefox/plugins/libunixprintplugin.so
operapluginwrapper: [plugin failure] (No 'mimedescription') /usr/lib/firefox/plugins/libunixprintplugin.so
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin failed ] /usr/lib/firefox/plugins/libtotem-basic-plugin.so, libxpcom.so: cannot open shared object file: No such file or directory
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection

```

I can create symlinks in /usr/lib to various needed by totem plugins libraries (libxpcom.so and similar) but after that when trying to play embedded quicktime movies I got message that totem plugins crashes and gray rect instead movie is displayed.

Anyone got a solution to this problem?

Edgy, Opera 9.1

---

### Post by jiminycricket on 2007-04-13
What symlinks have you made?  I can try it out on Feisty with Opera 9.2 and see if it works..

---

### Post by jazzgossen on 2008-01-10
I have similar problems, using Ubuntu 7.10 and Opera 9.24.

opera --debugplugin says
```
operapluginwrapper: [plugin probing] /usr/lib/opera/plugins/libnpp.so
opera: plugin detection successful: /usr/lib/opera/plugins/libnpp.so
operapluginwrapper: [plugin probing] /usr/lib/opera/plugins/libflashplayer.so
opera: plugin detection successful: /usr/lib/opera/plugins/libflashplayer.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
opera: plugin detection successful: /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/nppdf.so
opera: plugin detection successful: /usr/lib/mozilla/plugins/nppdf.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
opera: plugin detection successful: /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
opera: plugin detection successful: /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/nphelix.so
opera: plugin detection successful: /usr/lib/mozilla/plugins/nphelix.so
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libjavaplugin_oji.so
operapluginwrapper: [plugin failure] (No 'mimedescription') /usr/lib/mozilla/plugins/libjavaplugin_oji.so
opera: pluginwrapper exited cleanly with exit code 1 during plug-in detection
operapluginwrapper: [plugin probing] /usr/lib/mozilla/plugins/libtotem-basic-plugin.so
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
opera: plugin detection successful: /usr/lib/mozilla/plugins/libtotem-basic-plugin.so


```

In Firefox, the plugin works great.

I have the following symlinks in /usr/lib/mozilla
```
~> ls -l /usr/lib/mozilla/plugins/
totalt 1108
lrwxrwxrwx 1 root root      38 2007-10-20 09:28 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 root root      36 2007-10-20 09:34 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2007-10-20 09:34 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-10-20 09:34 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2007-10-20 09:34 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2007-10-20 09:34 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2007-10-20 09:34 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2007-10-20 09:34 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2007-10-20 09:34 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-12-06 18:59 nphelix.so -> /opt/RealPlayer/mozilla/nphelix.so*
lrwxrwxrwx 1 root root      35 2007-12-06 18:59 nphelix.xpt -> /opt/RealPlayer/mozilla/nphelix.xpt*
-rwxr-xr-x 1 root root 1127564 2007-11-06 19:35 nppdf.so*


```

Any ideas what to do?

---

