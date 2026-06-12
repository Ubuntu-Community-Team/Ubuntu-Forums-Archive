---
title: "XFCE menu item missing after 10.04-&gt;10.10 upgrade"
date: 2010-10-12
forum: Mythbuntu
---

### Post by davidstoll on 2010-10-12
My software sources menu item is missing after I upgraded from 10.04 to 10.10.

I'm running XFCE, and just can't figure out how to easily edit/add/remove items/shortcuts to the menu.

I would appreciate help.

---

### Post by superm1 on 2010-10-12
Try launching this app from cmd line:

```
# gksudo software-properties-gtk
```

Not sure why the menu item would have disappeared unless it got uninstalled somehow on upgrade.

---

### Post by davidstoll on 2010-10-12
Yes, it does work from command line...I forgot to mention that. :\


> **superm1 said:**
> Try launching this app from cmd line:

```
# gksudo software-properties-gtk
```

Not sure why the menu item would have disappeared unless it got uninstalled somehow on upgrade.

---

### Post by superm1 on 2010-10-12
> **davidstoll said:**
> Yes, it does work from command line...I forgot to mention that. :\
Peculiar then.

Is the .desktop file still installed?  Look for /usr/share/applications/software-properties-gtk.desktop

It should have Categories=System;Settings; which would make it show up in the menus.

---

### Post by davidstoll on 2010-10-12
> **superm1 said:**
> 
Is the .desktop file still installed?  Look for /usr/share/applications/software-properties-gtk.desktop

It should have Categories=System;Settings; which would make it show up in the menus.

Yes, the .desktop file is located there.
software-properties-gtk.desktop...

```

[Desktop Entry]
Name=Software Sources
GenericName=Software Sources
Comment=Configure the sources for installable software and updates
Exec=gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
Icon=software-properties
Terminal=false
NoDisplay=true
X-MultipleArgs=false
Type=Application
Categories=System;Settings;
MimeType=text/x-apt-sources-list;
X-KDE-SubstituteUID=true
X-Ubuntu-Gettext-Domain=software-properties

```

---

### Post by davidstoll on 2010-10-12
I installed the alacarte menu editor.  The item was listed in this editor but not checked....so I "checked" it and it's all better.

I know that this didn't exactly answer why, but it did fix it.

alacarte is kind of cool, just found out about it.

---

### Post by superm1 on 2010-10-12
> **davidstoll said:**
> I installed the alacarte menu editor.  The item was listed in this editor but not checked....so I "checked" it and it's all better.

I know that this didn't exactly answer why, but it did fix it.

alacarte is kind of cool, just found out about it.
Well as long as it's fixed :)

---

