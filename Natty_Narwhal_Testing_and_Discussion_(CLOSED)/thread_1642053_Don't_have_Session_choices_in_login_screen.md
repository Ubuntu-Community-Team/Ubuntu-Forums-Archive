---
title: "Don't have Session choices in login screen"
date: 2010-12-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by quixote on 2010-12-09
I changed to a custom login screen in Maverick, then I upgraded to Natty a few days ago.  It's retained my custom login (which I only was using to try).  That's not showing any Session choices at the bottom.  So I can only go to Unity desktop.  On my system Unity has no System functions at all.  No synaptic, no update manager, nothing.  No Preferences or Login prefs under that.

I don't know if that's normal for now.  But I'd like to revert to the regular (Classic) desktop for now so that I can play with the system a bit.

 Is there a command line way to set the session to Ubuntu Classic for the next boot?

Is there some way to show System menus in the Unity desktop?

---

### Post by quixote on 2010-12-09
Well, the answer to the menu question was in one of the Natty Stickies in this forum:

Start a terminal using ctrl-alt-t, and type ```
gnome-panel &
```Keep the terminal open, or the panel disappears.  Once I had the panel, I could change my login setup, so that dealt with it.

I'm still curious, though, if anyone happens to know, how would I for instance in a recovery console boot into a specific desktop manager (gdm, whatever) and desktop shell (unity, ordinary, etc.)

---

### Post by dino99 on 2010-12-10
sudo service gdm stop

---

### Post by seeker5528 on 2010-12-10
Don't know where the default session is set, but.....

If you want to add synaptic to the dock in Unity, run synaptic then right click it's icon on the dock and choose 'Pin to Launcher'.

If you want to get to the control panel stuff open a terminal window and type```
gnome-control-center
```

If you want to run compiz without Unity run ccsm and disable the Unity plugin. Then you probably have to run gnome-panel from a terminal window so you can get to the control center stuff and add gnome-panel to the applications to autostart.

An alternative way to add gnome-panel to the start up applications, you can create a .desktop file in '~/.config/autostart' named 'gnome-panel.desktop' with some contents like ```
[Desktop Entry]
Type=Application
Exec=/usr/bin/gnome-panel
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=gnome-panel
Name=gnome-panel
Comment[en_US]=
Comment=
```

Not sure how that plays with Unity if you later enable it again, but you can always (either from the menus on gnome-panel or from gnome-control-center) run the applet for choosing what to autostart to enable/disable the start up items by checking/unchecking them in the list.

You can set which window manager to use by creating a file named .xprofile in your home directory with a line like:

```
export WINDOW_MANAGER="/usr/bin/metacity"
```

Normally I would expect that to be enough, but there was some issue between gnome-panel and unity and gnome-panel was disabled in the default ubuntu session so you might have to add gnome-panel to your start up stuff for that case as well since it would still technically be the default 'Ubuntu Desktop' session.

Later, Seeker

---

### Post by scradock on 2010-12-10
> **dino99 said:**
> sudo service gdm stop
or even "sudo service gdm start"

just worked for me, when straight autologin was bringing up desktop, autostarted app but no desktop icons or unity bars.....

---

### Post by quixote on 2010-12-11
Thanks to all for the replies.  Seeker5528: they ought to put that info on a sticky on the new desktop! :D  I'm going off to try all that out right now.

---

