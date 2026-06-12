---
title: "audacious global hotkey plugin"
date: 2009-07-10
forum: Multimedia Software
---

### Post by ayu on 2009-07-10
Hi,

I have the Global Hotkey plugin set and working well in Audacious. However, when I restart the system, the hotkeys don't work until I click the preferences button for the Global Hotkey plugin (and exit without changing anything). Is this a bug in Audacious 1.5.1? Is there any way to make the plugin work everytime without having to enter the preferences dialog for the plugin?

Thanks,
Ayu

---

### Post by spunionring on 2010-06-25
I have this same problem.

---

### Post by ayu on 2010-09-03
Hi spunionring and anybody else who may have this problem,

I think this may be fixed if you check Compiz and Gnome keyboard settings; make sure they are not set to anything there or they will override Audacious's settings.

---

### Post by The__Doctor on 2012-12-12
Although this is already marked as solved and is old, I have an alternative solution. I also had a similar problem with global hotkey plugin but also the status icon plugin. If one edits /home/{user}/.config/audacious/plugin-registry, there is a list of plugins and also whether they are enabled or not. 

```

general /usr/lib/x86_64-linux-gnu/audacious/General/hotkey.so
stamp 1340971748
name Global Hotkey
priority 0
about 1
config 1
enabled 0

```If you change the last line from enabled 0 to enabled 1, the plugin will be enabled. This works for any other plugin.

NOTE: I'm using lubuntu 12.10. The plugins-registry file might change on a different system, I'm not sure.

---

