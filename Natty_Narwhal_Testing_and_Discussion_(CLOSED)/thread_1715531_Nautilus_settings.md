---
title: "Nautilus settings?"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-03-27
I am wondering how to set preferences in Nautilus. In Maverick and Lucid I can do Edit > Preference by opening any folder. Now those options are all missing.

---

### Post by coffeecat on 2011-03-27
I can still do that in a Natty Nautilus. Except that the edit menu is in the panel. Global menu is that? I'm still getting to learn all the terms for the Unity desktop.

**EDIT**: except the Nautilus global menu is calling itself "Applications" which is confusing.

---

### Post by beew on 2011-03-27
Yeah now I see it, but the global menu was missing before I rebooted. Thanks.

---

### Post by coffeecat on 2011-03-27
> **coffeecat said:**
> **EDIT**: except the Nautilus global menu is calling itself "Applications" which is confusing.

That's a weird one. I've found the explanation. I had a custom launcher in the dock opening a Nautilus window in /usr/share/applications which I had set up when the dash was still iffy. It must have been confusing things. I removed it, logged out and in and now the nautilus global menu says "Home Folder" even if I browse to somewhere in the filesystem.

---

### Post by cariboo on 2011-03-27
> **coffeecat said:**
> That's a weird one. I've found the explanation. I had a custom launcher in the dock opening a Nautilus window in /usr/share/applications which I had set up when the dash was still iffy. It must have been confusing things. I removed it, logged out and in and now the nautilus global menu says "Home Folder" even if I browse to somewhere in the filesystem.

It does here too, I didn't notice it until I saw your post, I'd suggest it may be a bug.

---

### Post by Atermoon on 2011-03-27
> **cariboo907 said:**
> It does here too, I didn't notice it until I saw your post, I'd suggest it may be a bug.

That's why I removed the home folder from the dock and dropped File Browser from /usr/share/applications instead. Now it says File Browser all the time. Not very informative but better than saying Home Folder when you're actually browsing something else.

---

### Post by mc4man on 2011-03-27
> **Atermoon said:**
> That's why I removed the home folder from the dock and dropped File Browser from /usr/share/applications instead. Now it says File Browser all the time. Not very informative but better than saying Home Folder when you're actually browsing something else.

Atm it only displays the name (display name), of the .desktop whose window is in focus. So by default all nautilus windows are from /usr/share/applications/nautilus-home.desktop (display name 'Home Folder'

You can make it say anything you wish when in nautilus windows, the current limitation being it only shows the .desktop's _display_ name, not location (dir,) name

What can confuse the launcher is if there are 2 or more launcher icons calling nautilus, better to only have one.

---

### Post by cariboo on 2011-03-27
I just edited  nautilus-home.desktop, and changed Home Folder to Nautilus:

```
[Desktop Entry]
Name=Nautilus
Comment=Open your personal folder
TryExec=nautilus
Exec=nautilus --no-desktop
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus
``` 

the launcher file is located in /usr/share/applications. Now it says Nautilus in the panel.

---

