---
title: "totem plugin in firefox 3.5"
date: 2009-09-05
forum: Multimedia Software
---

### Post by robertbub on 2009-09-05
For some reason, my totem-mozilla package doesn't work any more.  I'm running Shiretoko Firefox 3.5.2 .  When I open a audio/wav file, it suggests Movie Player, but no longer offers the totem plug-in.

I see in /usr/lib/xulrunner-addons/plugins/:```
$ ls /usr/lib/xulrunner-addons/plugins/
flashplugin-alternative.so@            libtotem-mully-plugin.so@
libjavaplugin.so@                      libtotem-narrowspace-plugin.so@
libmoonloader.so@                      libunixprintplugin.so
libnullplugin.so                       libvlcplugin.so@
librhythmbox-itms-detection-plugin.so  mozplugger.so@
libtotem-cone-plugin.so@               nppdf.so@
libtotem-gmp-plugin.so@

```So, it's definitely there.  But firefox doesn't load it.

Is there any way around this?

---

### Post by robertbub on 2009-09-05
I fixed this.

It turns out, through the Tools->Addons->Plugins menu, you need to disable all the "mplayerplugin"-based plugins and enable all the "totem"-based plugins, and restart Firefox.

I haven't tried it, but, looking at the Preferences->Applications tab, everything looks copacetic.

---

