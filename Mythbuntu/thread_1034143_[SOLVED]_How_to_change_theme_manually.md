---
title: "[SOLVED] How to change theme manually?"
date: 2009-01-08
forum: Mythbuntu
---

### Post by BroadArrow on 2009-01-08
Is there an easy way to change a front end theme manually (ie: other than via the setup menu inside the front end)?

I've been trying out the themes and for some reason myth now hangs whenever I enter the appearance option of the setup. So I can't change the theme and I don't particularly like the one I'm stuck on...!

---

### Post by BroadArrow on 2009-01-08
I have a partial solution, at least to changing the theme from outside the front end, and that is to uninstall all themes except one via the Mythbuntu control centre. A bit drastic but it seems to work.

However, it's still hanging whenever I go into the appearance option screen... all I can do is CTRL-ALT-BACKSPACE. Grr.

---

### Post by BroadArrow on 2009-01-09
In fact it appears to freeze when I enter any menu item at the end of the heirarchy. Has anyone struck this before?

---

### Post by EasyRiderOnTheStorm on 2009-01-09
You might want to check out/post here the front end log file, it should have some relevant information. You can find it at /var/log/mythtv/mythfrontend.log

---

### Post by BroadArrow on 2009-01-09
> **EasyRiderOnTheStorm said:**
> You might want to check out/post here the front end log file, it should have some relevant information. You can find it at /var/log/mythtv/mythfrontend.log

Thanks for that. Oddly enough, mythfrontend.log was empty but mythfrontend.log.1 wasn't. Wonder why the different name?

Anyway, here's what it had in it:

```
Starting mythfrontend.real..
2009-01-08 21:04:45.693 New DB connection, total: 2
2009-01-08 21:04:45.693 Connected to database 'mythconverg' at host: localhost
2009-01-08 21:04:45.694 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-08 21:04:45.695 Enabled verbose msgs:  important general
2009-01-08 21:04:45.710 Starting mythlcdserver
2009-01-08 21:04:46.212 Connecting to lcd server: localhost:6545 (try 1 of 10)
2009-01-08 21:04:47.159 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-08 21:04:47.161 Primary screen 0.
2009-01-08 21:04:47.161 Using screen 0, 1024x768 at 0,0
2009-01-08 21:04:47.161 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-08 21:04:47.162 Switching to square mode (G.A.N.T)
2009-01-08 21:04:47.353 Using the OpenGL painter
2009-01-08 21:04:47.354 JoystickMenuClient Error: Joystick disabled - Failed to read /home/yonah/.mythtv/joystickmenurc
2009-01-08 21:04:47.364 lirc init success using configuration file: /home/yonah/.mythtv/lircrc
2009-01-08 21:04:48.199 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-08 21:04:48.255 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-08 21:04:48.328 Registering Internal as a media playback plugin.
2009-01-08 21:04:48.508 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-08 21:04:48.786 Using ARB NPOT texture extension
2009-01-08 21:04:48.888 MythMusic adding CD-Writer: 3,0,0 -- DVDRAM GSA-H10N 
2009-01-08 21:04:48.937 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-08 21:04:49.084 No theme dir: /home/yonah/.mythtv/themes/G.A.N.T
2009-01-08 21:05:09.667 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-08 21:05:09.668 Using protocol version 40
ICE default IO error handler doing an exit(), pid = 6590, errno = 107
ICE default IO error handler doing an exit(), pid = 6565, errno = 11
```

Am I right in thinking the error is occurring when it tries to connect with the backend server? (I have a single box backend/frontend installation.)

---

### Post by gungfujoe on 2009-01-10
> **BroadArrow said:**
> In fact it appears to freeze when I enter any menu item at the end of the heirarchy. Has anyone struck this before?Yes, I was seeing the same problem on my AMD/ATI video card with the proprietary drivers and OpenGL rendering enabled.  I couldn't figure out how to change it back to Qt rendering (because it would freeze when I tried to go to the Appearance menu).  I solved it by disabling the proprietary drivers in Ubuntu, rebooting, changing the rendering method to Qt, and then reinstalling the ATI/AMD proprietary drivers.

I'm having other problems now (just installed last night, still working out initial setup), but if I can't figure them out, I'll ask in another thread rather than try to hijack this one. :)

Incidentally, MythTV isn't actually freezing when this happens, it's only failing to update the video display.  From any of the no-display menus, if I simply hit "Escape", I'd get back to the prior menu, and it'd work fine.  I had the same problem with the "Exit MythTV" screen (hitting left arrow from main menu).  The screen didn't display, but it worked fine, so hitting a down arrow and the Enter key successfully exits MythTV.

---

### Post by BroadArrow on 2009-01-10
> **gungfujoe said:**
> Yes, I was seeing the same problem on my AMD/ATI video card with the proprietary drivers and OpenGL rendering enabled.  I couldn't figure out how to change it back to Qt rendering (because it would freeze when I tried to go to the Appearance menu).  I solved it by disabling the proprietary drivers in Ubuntu, rebooting, changing the rendering method to Qt, and then reinstalling the ATI/AMD proprietary drivers.

Thanks, that did it!

So it looks like this is a AMD/ATI & OpenGL combination issue.

Let me know if you encounter any similar issues.

---

### Post by uMuppet on 2009-01-11
Most of the system settings are kept in the MySQL database.   The Paint engine type is there.  You can change these here without entering the frontend or the backend.  

Use the MySQL Query Browser to access them. .

---

### Post by BroadArrow on 2009-01-12
> **uMuppet said:**
> Use the MySQL Query Browser to access them. .

Thanks for that. Where can I find the browser? Doesn't appear in the menus anywhere. For those of us used to finding everything in the Linux menus MythBuntu's lean menus make it hard to find and run things. I know they're there but just kept invisible!

---

### Post by uMuppet on 2009-01-12
I'm not a fan of the XFCE desktop environment, I always use Ubuntu and load Mythtv/Mythbuntu on top of it.  Just my personal preference, I like the bells an whistles of Gnome

To install and run the MySQL Query Browser,
```

sudo apt-get install mysql-query-browser
mysql-query-browser 
```

If you have trouble using it let me know.

---

### Post by BroadArrow on 2009-01-12
Thanks for that. I'll try that.

I've done the same thing myself. I have machines Gnome and Xfce but only use Xfce on an older lower-powered machine which I use as a file server. After initially installing Mythbuntu I remembered why I only use Xfce on the server and then installed the Gnome desktop. Hopefully that round about route won't cause too many problems at the MythTV end of things.

I can't figure why Mythbuntu would be Xfce based when presumably it would normally be installed on machines with at least enough grunt to handle Gnome.

---

### Post by dkscudder on 2009-03-24
Or, the really easy way type:

 ```
mythfrontend -O ThemePainter=qt
```

Then go change the setting.

---

