---
title: "Can't install flash plugin"
date: 2018-05-05
forum: Multimedia Software
---

### Post by jord19812 on 2018-05-05
I am unable to stream some videos online due to a lack of a flash plugin.  When I try to install it, I get this error message:

```
Preparing to unpack .../adobe-flashplugin_1%3a20180410.1-0ubuntu1_amd64.deb ...
Unpacking adobe-flashplugin (1:20180410.1-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/adobe-flashplugin_1%3a20180410.1-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/16x16/apps/flash-player-properties.png', which is also in package flash-plugin 29.0.0.140-1
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20180410.1-0ubuntu1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20180410.1-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/adobe-flash-properties-gtk_1%3a20180410.1-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/flash-player-properties', which is also in package flash-plugin 29.0.0.140-1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_1%3a20180410.1-0ubuntu1_amd64.deb
 /var/cache/apt/archives/adobe-flash-properties-gtk_1%3a20180410.1-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hoping to fix this in the next few hours so I can stream the Kentucky Derby!

---

### Post by &amp;KyT$0P# on 2018-05-05
Does this get it working? -
```
sudo apt-get purge flash-plugin
```

---

### Post by jord19812 on 2018-05-06
Thank you.

---

