---
title: "How do I add my script to the Unity  launcher bar?"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-03-05
I created a launcher on the desktop to run a script that I use frequently.

Is there a way to move it to the launcher bar?

If not, will there be in the final release?

If not I would see this as a major problem.

---

### Post by mc4man on 2011-03-05
The launcher is broken into sections, the top section that you can add to uses .desktops
You can (or should be able to) add any .desktop that is in an applications folder, ie, /usr/share/applications, /usr/local/share/applications, ~/.local/share/applications

This can include any custom made .desktops and that .desktop can call a script
Also any .desktop should be available in the dash

So if your script can be set up that way you may be able to add to the launcher

.............................
There are some oddities here -  if your created .desktop uses a binary that has a 'default .desktop it seems quite possible that things can go south and you can't add a custom version to the launcher. The reason behind this is unknown to me atm.

Ex. (in this case I don't really want to have in launcher, just as example
I create a desktop for vlc that uses a script as the Exec= named vlc-cd.desktop with a display name of VLC Cd Player

On a fresh install I just made I can easily add to the launcher, it shows up separately from a 'normal' vlc launcher (vlc.desktop) screens show (also added 2 add. custom vlc launchers, the icons could be changed, no need as ex.

Now on a slightly older install, while "VLC Cd Player" will show in dash, when adding to the launcher it always comes up as the default - "VLC media player", no additional vlcXXX.desktops can be added

So overall, atm, you can add custom.desktops to the launcher and these .desktops can call scripts. Overall though the whole deal here is a bit sketchy and less than ideal.

---

### Post by JRV on 2011-03-05
> This can include any custom made .desktops and that .desktop can call a script
Also any .desktop should be available in the dash

How do I create a .desktop?
Do I currently have any on my system to look at for a sample?

A search for .desktop turned up nothing?

What is the dash?

> So overall, atm, you can add custom.desktops to the launcher and these .desktops can call scripts. Overall though the whole deal here is a bit sketchy and less than ideal.

What is atm?

---

### Post by kyleabaker on 2011-03-05
> **JRV said:**
> How do I create a .desktop?
Do I currently have any on my system to look at for a sample?

A search for .desktop turned up nothing?

What is the dash?



What is atm?

You can find examples at:
/usr/share/applications

Just open one of those in a text editor of your choice. An example .desktop file looks like this:

```
[Desktop Entry]
Name=Calculator
Comment=Perform arithmetic, scientific or financial calculations
Exec=gcalctool
Icon=accessories-calculator
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Calculator
X-GNOME-DocPath=gcalctool/gcalctool.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gcalctool
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-OtherBinaries=gnome-calculator
X-Ubuntu-Gettext-Domain=gcalctool
```

---

### Post by JRV on 2011-03-05
Solved, thank you Kyleabaker and Mc4man.

---

