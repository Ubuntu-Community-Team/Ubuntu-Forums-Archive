---
title: "myth frontend won't start"
date: 2010-02-26
forum: Mythbuntu
---

### Post by waldick on 2010-02-26
ok, i searched through the threads and could not really find any thing close...

when i try to start the frontend the screen flashes quickly then nothing...

i tried to run the setup for the backend and it tells me its running. when i try to shut it down i get "Would you like to run mythfilldatabase?",. i say yes, it executes and then i try to run the setup for the backend again and it tells me the backend is still up...

and of course the frontend still won't start. i had the thing running after initial setup today and then rebooted and now this...here is the error log :



Starting mythfrontend.real..
2010-02-26 22:12:44.546 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-02-26 22:12:44.546 Using runtime prefix = /usr
2010-02-26 22:12:44.546 Using configuration directory = /home/dad/.mythtv
2010-02-26 22:12:44.547 Configuration::Load - Error parsing: /home/dad/.mythtv/config.xml at line: 1  column: 1
2010-02-26 22:12:44.547 Configuration::Load - Error Msg: unexpected end of file
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2010-02-26 22:12:45.401 Empty LocalHostName.
2010-02-26 22:12:45.401 Using localhost value of dad-desktop
2010-02-26 22:12:45.401 Configuration::Load - Error parsing: /home/dad/.mythtv/config.xml at line: 1  column: 1
2010-02-26 22:12:45.401 Configuration::Load - Error Msg: unexpected end of file
2010-02-26 22:12:45.408 New DB connection, total: 1
2010-02-26 22:12:45.411 Connected to database 'mythconverg' at host: localhost
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2010-02-26 22:12:45.412 Closing DB connection named 'DBManager0'
2010-02-26 22:12:45.423 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-26 22:12:45.424 DPMS is active.
2010-02-26 22:12:45.426 Primary screen: 0.
2010-02-26 22:12:45.427 Connected to database 'mythconverg' at host: localhost
2010-02-26 22:12:45.428 Using screen 0, 1280x1024 at 0,0
2010-02-26 22:12:45.438 MythUI Image Cache size set to 20971520 bytes
2010-02-26 22:12:45.438 Enabled verbose msgs:  important general
2010-02-26 22:12:45.448 Primary screen: 0.
2010-02-26 22:12:45.448 Using screen 0, 1280x1024 at 0,0
2010-02-26 22:12:45.450 Using theme base resolution of 1280x720
2010-02-26 22:12:45.458 LIRC: Successfully initialized '/dev/lircd' using '/home/dad/.mythtv/lircrc' config
2010-02-26 22:12:45.459 JoystickMenuThread Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2010-02-26 22:12:45.638 Using the OpenGL painter
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x2c00014
mythfrontend.real: ../../src/xcb_io.c:542: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.



any help would be appreciated...

---

### Post by waldick on 2010-02-26
ok, if i type 

"mythfrontend -O ThemePainter=qt"

the frontend starts, but if i close it and try to open it again, i get the same problem as above...

how do i make the change permanent ?  i already tried rebooting...

also, still can't get the backend to shut down to do the setup utility.

---

### Post by waldick on 2010-02-27
SOLVED

started with above command line entry, then changed back to QT and lo and behold it all worked :)

now just trying to work little quirks out...

---

