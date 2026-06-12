---
title: "gconf-editor does not have .schemas files for several compiz plugins"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cprofitt on 2010-10-03
There is no 'expo' node or other settings available in gconf-editor.

Meerkat
[IMG]http://launchpadlibrarian.net/57033471/Screenshot-Configuration%20Editor.png[/IMG]

Lucid

---

### Post by cprofitt on 2010-10-03
There is no compiz-expo.schemas in \usr\share\gconf\schemas

This would appear to be the issue... going to test now.

---

### Post by cprofitt on 2010-10-03
After copying a compiz-gconf.schemas file over and reinstalling compiz components in Synaptic I now have the appropriate gconf-editor nodes for expo.

---

### Post by cprofitt on 2010-10-03
Here is the bug report if others want to confirm they have the same issue  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/654063](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/654063)

---

### Post by cprofitt on 2010-10-03
It looks like the following are also missing:

animation
colorfilter
ezoom
i,gjpeg
kdecompat
mag
mousepoll
neg
put
resizeinfo
ring
rotate
scaleaddon
thumbnail
titleinfo
vpswitch
wall
winrules
workarounds

Not sure if these are important, but I find it odd that such a large groups of .schemas were left out.

---

### Post by cprofitt on 2010-10-04
I did an upgrade and the .schemas are not present either. The 'keys' that I modified are in the 'nodes' but the rest of the schema is missing.

---

### Post by cprofitt on 2010-10-05
Does anyone know how to, after adding these schema files, force gconf-editor to use them?

Also, is there a reason that these are missing?

---

### Post by ktp on 2010-10-05
wonder if you have compiz-fusion-plugins-extra package installed.  Also wonder if you have compizconfig-settings-manager package installed and what happens if you save the setting and choosing gconf as the backend (compizconfig-backend-gconf package).

---

### Post by cprofitt on 2010-10-05
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compizconfig-backend-gconf

are the installed packages -- in 10.04 the nodes were in gconf-editor with that in 10.10 they are not.

---

