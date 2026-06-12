---
title: "Sound Juicer missing menu bar (15.04 with Gnome)"
date: 2015-08-06
forum: Multimedia Software
---

### Post by ButcherBaker on 2015-08-06
Kind Ubuntu fans,
Please see attached screenshot.
I installed Sound Juicer using synaptic on Ubuntu 15.04.
I'm using Gnome desktop.
The menu bar is missing!    
It appears correctly in 14.04 (with Gnome).

Under System Settings > Appearance > Behavior I have 
"Show menus for a window: In the window's title bar"

Is there some other configuration that is needed?
Thanks,
BB

---

### Post by mc4man on 2015-08-06
Would depend on which gnome session
gnome-shell - it's in the appmenu in top panel
unity - it's accessed by clicking on sound juicer in unity panel or in window deco with the setting you mentioned
gnome-session flashback - by default not available - run this ( don't use in an ubuntu session, eg. unity or you'll get 2 menus
```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```
note the above will add the menu to sj window in gnome-shell also


If still an issue run & post - 
```
echo $XDG_CURRENT_DESKTOP
```

Edit - scr. of in gnome-session-flashback after gsettings command

---

### Post by ButcherBaker on 2015-08-06
Thank you.  Yes, I'm using gnome-session flashback, and the gsettings command you provided did the trick.  I now have a menu bar!  
Out of curiosity, is there a way to configure that setting with a graphical tool like gnome tweak tool, dconf editor, or something?

---

### Post by mc4man on 2015-08-06
> **ButcherBaker said:**
> Thank you.  Yes, I'm using gnome-session flashback, and the gsettings command you provided did the trick.  I now have a menu bar!  
Out of curiosity, is there a way to configure that setting with a graphical tool like gnome tweak tool, dconf editor, or something?

I guess you could with care manually enter it in dconf-editor between the braces

---

