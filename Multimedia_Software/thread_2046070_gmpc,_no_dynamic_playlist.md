---
title: "gmpc, no dynamic playlist"
date: 2012-08-22
forum: Multimedia Software
---

### Post by SlugSlug on 2012-08-22
Using GMPC  version 11.8.90

The dynamic playlist had stopped working. I get this error when launching from terminal. I've tried both the version is ubuntu repos and the gmpc repo 

```

(gmpc:12444): Plugin-CRITICAL **: plugin_load: module failed to load: awnplugin.so:/usr/lib/gmpc/plugins/awnplugin.so: undefined symbol: gmpc_meta_watcher_match_data


(gmpc:12444): Plugin-CRITICAL **: Failed to load plugin: awnplugin.so: Failed to load plugin awnplugin.so: '/usr/lib/gmpc/plugins/awnplugin.so: undefined symbol: gmpc_meta_watcher_match_data'


(gmpc:12444): Plugin-CRITICAL **: pluging has with name: Last FM metadata fetcher is blacklisted: 'Plugin is intergrated into GMPC'

(gmpc:12444): Plugin-CRITICAL **: Last FM metadata fetcher: Not loading plugin.

(gmpc:12444): Plugin-CRITICAL **: plugin_load: module failed to load: dynlistplugin.so:/usr/lib/gmpc/plugins/dynlistplugin.so: undefined symbol: gmpc_meta_watcher_get_meta_path_callback


(gmpc:12444): Plugin-CRITICAL **: Failed to load plugin: dynlistplugin.so: Failed to load plugin dynlistplugin.so: '/usr/lib/gmpc/plugins/dynlistplugin.so: undefined symbol: gmpc_meta_watcher_get_meta_path_callback'

```

---

### Post by SlugSlug on 2012-08-24
bump

---

### Post by SlugSlug on 2012-08-25
ok for anyone else with this prob..

remove any ppa for gmpc you have

purge gmpc &  reinstall gmpc 

add gmpc ppa

install gmpc-dynamicplayist

remove ppa

Do not update gmpc with the ppa!


guess this will get fixed soon

---

