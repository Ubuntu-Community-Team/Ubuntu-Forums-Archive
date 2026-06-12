---
title: "Kicked out to desktop when trying to watch tv"
date: 2008-08-20
forum: Mythbuntu
---

### Post by kristersaurus on 2008-08-20
Hey guys,

Im running the mythtv frontend on an old latitude c610. It works fine when I boot from the mythbuntu live cd, but from my HD install, I get kicked out to the desktop when I try to watch tv. It seems to be talking to the database just fine.

Here is my frontend log:Starting mythfrontend.real..
2008-08-20 21:29:11.134 New DB connection, total: 2
2008-08-20 21:29:11.136 Connected to database 'mythconverg' at host: 192.168.1.12
2008-08-20 21:29:11.176 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-20 21:29:11.176 Enabled verbose msgs:  important general
2008-08-20 21:29:13.019 Primary screen 0.
2008-08-20 21:29:13.021 Using screen 0, 1024x768 at 0,0
2008-08-20 21:29:13.026 Switching to square mode (G.A.N.T)
2008-08-20 21:29:13.067 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-08-20 21:29:13.070 lirc_init failed for mythtv, see preceding messages
2008-08-20 21:29:13.071 JoystickMenuClient Error: Joystick disabled - Failed to read /home/krister/.mythtv/joystickmenurc
2008-08-20 21:29:15.550 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-08-20 21:29:15.731 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-20 21:29:15.864 Registering Internal as a media playback plugin.
2008-08-20 21:29:39.533 Connecting to backend server: 192.168.1.12:6543 (try 1 of 5)
2008-08-20 21:29:39.535 Using protocol version 40
2008-08-20 21:29:39.541 Received a remote 'Clear Cache' request
2008-08-20 21:29:44.218 TV: Attempting to change from None to WatchingLiveTV
2008-08-20 21:29:44.221 Using protocol version 40
2008-08-20 21:29:45.467 New DB connection, total: 3
2008-08-20 21:29:45.469 Connected to database 'mythconverg' at host: 192.168.1.12
2008-08-20 21:29:45.596 Opening audio device 'default'. ch 2(2) sr 44100
2008-08-20 21:29:45.597 Opening ALSA audio device 'default'.

Thanks for your time.

---

### Post by SniperKIng on 2008-08-21
Hi i too was getting this problem on the new mythbuntu release just before it all crashed lol.

It never happened to me on previous releases once though.

Just letting you know your not alone :)

---

