---
title: "Run nvidia-settings X startup"
date: 2007-11-09
forum: Mythbuntu
---

### Post by ali1234 on 2007-11-09
I need to run nvidia-settings to get a correct overscan on TV out. Under Gnome I just added it to the session manager, but xfce doesn't have anywhere to automatically start programs. So how do I do it?

---

### Post by superm1 on 2007-11-15
> **ali1234 said:**
> I need to run nvidia-settings to get a correct overscan on TV out. Under Gnome I just added it to the session manager, but xfce doesn't have anywhere to automatically start programs. So how do I do it?
Actually it should be started via the automatic login scripts.

Just save your settings, and try to log in again.

---

### Post by Rosewood_Arts on 2008-02-01
"it should be started via the automatic login scripts"

I have this same annoyance...exactly how do I start nvidia-settings via the automatic login scripts?

Would be nice to be able to add this (or any chosen program) to the "Services" list for automatic startup.  Have not found how to programs to that list.

Next question:  Once started, how do I keep the settings running?  Seems that when the screen goes off, so do the nvidia-settings, and I have to restart them manually.

Thanks for any / all suggestions.

---

### Post by superm1 on 2008-02-01
When you run nvidia-settings and save its settings, it should make a ~/.nvidiasettings-rc or similar file.  Make sure this is in your home directory.

If it somehow ended up in /root, that might be why its not starting up on its own. (in which case, please file a bug so we can fix this in hardy)

---

### Post by ppww on 2008-04-19
~/.nvidia-settings-rc is being created, but it is not reloaded during session start.  Something needs to cause the "nvidia-settings --load-config-only" command to run.

I've found that I can make this happen by creating a file named ~/.config/autostart/nvidia-settings.desktop with the following contents:

```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Load NVIDIA X Server Settings
Comment=Load NVIDIA X Server Settings
Exec=/usr/bin/nvidia-settings --load-config-only
Icon=/usr/share/pixmaps/nvidia-settings.png
Categories=System;Settings;
```

If there's a way of doing it that's less of a hack, I'd appreciate knowing how.

---

### Post by p1977p on 2008-04-22
> **ppww said:**
> ~/.nvidia-settings-rc is being created, but it is not reloaded during session start.  Something needs to cause the "nvidia-settings --load-config-only" command to run.

I've found that I can make this happen by creating a file named ~/.config/autostart/nvidia-settings.desktop with the following contents:

```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Load NVIDIA X Server Settings
Comment=Load NVIDIA X Server Settings
Exec=/usr/bin/nvidia-settings --load-config-only
Icon=/usr/share/pixmaps/nvidia-settings.png
Categories=System;Settings;
```If there's a way of doing it that's less of a hack, I'd appreciate knowing how.

Go to  [COLOR=Sienna]***Settings > Autostarted  Applications > Add new***[/COLOR]
Give a custom name for the new application , say "Bright"
Give the command as "_**nvidia-settings -l**_"
Save & exit. That's it. The command is run everytime you log in!!

---

### Post by ppww on 2008-04-22
> **p1977p said:**
> Go to  [COLOR=Sienna]***Settings > Autostarted  Applications > Add new***[/COLOR]
Give a custom name for the new application , say "Bright"
Give the command as "_**nvidia-settings -l**_"

Mythbuntu 8.04rc seems to lack the "Autostarted Applications" menu item, or else I've inadvertently done something to make it disappear.  But I'm guessing your solution and mine lead to creation of a similar file, so they work equally well.

---

### Post by laga on 2008-04-22
You need to install one additional package to get support for autostarted applications back. I don't remember the name of the package, but if you search the forums you'll find it.

(Once you've found it, let me know and I'll try to get it added to mythbuntu again ;)).

---

### Post by ppww on 2008-04-22
The application itself is already installed; I can run "xfce4-autostart-editor" from a shell.  The package you may be referring to is [_xfce4-mcs-plugins-extra_]("http://packages.ubuntu.com/hardy/x11/xfce4-mcs-plugins-extra"), which adds Autostarted Apps as a widget in the Xfce Settings Manager (but not as a popup menu item).

---

