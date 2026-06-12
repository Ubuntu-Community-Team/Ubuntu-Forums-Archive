---
title: "MythTv display messed up in bands"
date: 2009-01-10
forum: Mythbuntu
---

### Post by BroadArrow on 2009-01-10
My MythTV frontend and backend setup displays messed up and displaying in stripey bands. 

The result is a completely illegible and unusable front or back end and all I can do is exit (luckily I remember the escape, down, enter, sequence).

The problem occured in both Ubuntu (with MythTV packages installed) and in a Mythbuntu installation on the same machine.

The Xubuntu and Ubuntu desktops displayed normally using the ATI video card, although I'm having fun getting the right VGA or HDMI modes for my TV.

Here is a copy of mythfrontend.log but I can't see any obvious problem:

```
Starting mythfrontend.real..
2009-01-11 17:43:18.193 New DB connection, total: 2
2009-01-11 17:43:18.193 Connected to database 'mythconverg' at host: localhost
2009-01-11 17:43:18.195 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-11 17:43:18.195 Enabled verbose msgs:  important general
2009-01-11 17:43:18.210 Starting mythlcdserver
2009-01-11 17:43:18.712 Connecting to lcd server: localhost:6545 (try 1 of 10)
2009-01-11 17:43:20.146 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-11 17:43:20.147 Primary screen 0.
2009-01-11 17:43:20.147 Using screen 0, 1280x1024 at 0,0
2009-01-11 17:43:20.147 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-11 17:43:20.148 Switching to square mode (G.A.N.T)
2009-01-11 17:43:20.312 Using the Qt painter
2009-01-11 17:43:20.314 lirc init success using configuration file: /home/yonah/.mythtv/lircrc
2009-01-11 17:43:20.314 JoystickMenuClient Error: Joystick disabled - Failed to read /home/yonah/.mythtv/joystickmenurc
2009-01-11 17:43:21.312 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-11 17:43:21.409 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-11 17:43:21.473 Registering Internal as a media playback plugin.
2009-01-11 17:43:21.527 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-11 17:43:24.131 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-11 17:43:24.132 Using protocol version 40
2009-01-11 17:43:28.663 Deleting UPnP client...
```

The screen resolution it's claiming to use is the same one that Gnome is claiming to use in the screen resolution widget: 1280x1024.

Has anyone else encountered this and have any suggested solutions?

Isn't it a potential weakness in MythTV if it can't be set up using a standard Ubuntu (or Xubuntu or whatever) dialogs without using the MythTV gui? Especially settings relating to display or appearance. My two cents worth... ;-)

---

### Post by BroadArrow on 2009-01-16
Still no replies so I thought I'd try to take a screenshot to show what it looks like but the screenshot resulted in a nice perfect picture of the myth home screen the way it should look and not the way it ended up being displayed on screen. Anyone encountered this before?

---

### Post by BroadArrow on 2009-01-31
I still haven't managed to fix this.

I tried editing the settings table in MySQL to replace all resolution settings to my correct screen resolution but that didn't work.

I then tried a complete uninstall (+manually deleting the MythTV database in MySQL) and reinstall and it still didn't work.

Any ideas?

---

### Post by canoemoose on 2009-01-31
AFAIK, if the screenshot shows the screen correctly without a problem, it's likely to be a graphics card or driver issue as ubuntu/mythbuntu thinks it is outputting the picture correctly.  Alternatively, it could be your TV/monitor/whatever you use.  Have you updated your graphics drivers recently or perhaps the kernel??

Just a thought,
Canoemoose

---

### Post by tgm4883 on 2009-01-31
Take an old school screenshot, that should capture the problem for us.

And by old school, I mean with a camera

---

### Post by BroadArrow on 2009-02-01
Very old school indeed!

Old school screenshot attached. Apologies for the flash reflecting in the screen. So much for LCD panels not being reflective. ;-)

---

### Post by BroadArrow on 2009-02-01
Perhaps I should add that I am using the TV's VGA input rather than HDMI, DVI, composite, &c.

Works fine with Linux (in fact better than DVI but that's an issue I have with my video card) but maybe that's confusing MythTV?

---

### Post by tgm4883 on 2009-02-01
> **BroadArrow said:**
> Perhaps I should add that I am using the TV's VGA input rather than HDMI, DVI, composite, &c.

Works fine with Linux (in fact better than DVI but that's an issue I have with my video card) but maybe that's confusing MythTV?

Take a look at [http://ubuntuforums.org/showthread.php?t=952252](http://ubuntuforums.org/showthread.php?t=952252)

Let me know if this works for you.

---

### Post by BroadArrow on 2009-02-04
> **tgm4883 said:**
> Take a look at [http://ubuntuforums.org/showthread.php?t=952252](http://ubuntuforums.org/showthread.php?t=952252)

Let me know if this works for you.

It does! At least, MythTV now displays correctly when started with:

```
mythfrontend -w -geometry 1024x768
```

Odd that is the same resolution I've been trying to use and manually entered into the settings table in MythTV's MySQL database.

I now have other set up issues but hopefully running the frontend and the backend setup with forced geometry will make it useable in the interim if it's not actually a permanent 'fix'.

---

### Post by BroadArrow on 2009-02-04
Update: that *only* works when run from the command prompt and not from a new item in the system menu, probably for some simple reason I've overlooked...

---

