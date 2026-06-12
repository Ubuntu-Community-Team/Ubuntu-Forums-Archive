---
title: "Control key not working with Blender 2.57"
date: 2011-05-01
forum: Multimedia Software
---

### Post by TheChewanater on 2011-05-01
I'm running Natty with the official Blender 2.57 32-bit build.  This same problem occurs with previous version of Blender and Ubuntu, although not with Blender 2.4x or any other programs.

Pressing the control key does nothing in Blender.  Pressing 'Ctrl+S' causes the active object to scale, as if I just pressed 'S'.  If I run 'killall gnome-settings-daemon', it temporarily works normally, but then I lose Gtk themes and icons and stuff.

I'm on a Dell Latitude D620, and I haven't messed with any keyboard settings.  I know people using the same hardware and OS that can use Blender fine, so I'm guessing there's some sort of xinput configuration or something that got messed up somehow.

---

### Post by Ian47 on 2011-07-16
In the mouse settings uncheck "show position of pointer when the control key is pressed"

Found the answer here [http://blenderartists.org/forum/showthread.php?216299-Ctrl-hotkey-functions-won-t-work-Blender-2.57-Ubuntu-10.10](http://blenderartists.org/forum/showthread.php?216299-Ctrl-hotkey-functions-won-t-work-Blender-2.57-Ubuntu-10.10). I didn't need to restart gnome though.

---

