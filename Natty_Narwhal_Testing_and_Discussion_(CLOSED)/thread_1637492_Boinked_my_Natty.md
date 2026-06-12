---
title: "Boinked my Natty"
date: 2010-12-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nm_geo on 2010-12-04
Well that was easy.. I have apparently lost my Ubuntu button. Access to System, Places & others. I can use alt-f2 to get to FireFox and other applications but the Unity left panel is gone.  If I try  ```
compiz --replace
``` by using Cntrl-Alt-T  the terminal stops```
greg@greg-Latitude-D620:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Initializing staticswitcher options...done
Starting gtk-window-decorator
Setting Update "command_terminal"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"


``` can't close the terminal cleanly

If I try ```
gnome-panel &
```Can't because I have one running..

I would just like to get back to normal testing 
screenshot  I love Fractals

---

### Post by Harry33 on 2010-12-04
Compiz 0.9.21 and Unity 3.2.2 are not in a very good shape in Natty alfa1 now.
Try Gnome-Classic (Gnome-Panel).

---

### Post by ratcheer on 2010-12-04
> **Harry33 said:**
> Compiz 0.9.21 and Unity 3.2.2 are not in a very good shape in Natty alfa1 now.
Try Gnome-Classic (Gnome-Panel).

Really? I am just now getting to a usable Natty test system. Other than my grub2/os-prober problem, which I can work around by building grub with Maverick, my only real problem is that Natty hangs at shutdown because Compiz is not responding to the shutdown request.

Tim

---

### Post by efflandt on 2010-12-04
I just installed alpha1 on SSD yesterday it it was the first that I had seen Unity start automatically when logging into the desktop (without having to do compiz --replace).  It was a bit awkward for me at first, but now that Unitiy mostly works, it is starting to grow on me.

It is still a bit awkward not having application menus (just a directory of all launchers, some of which are duplicates with or without gksu).  But switching between applications is nice because I can have Firefox open in one workspace and a terminal, gedit, and file manager open in another workspace and switch between them instantly with one click on the terminal or Firefox Unity icons.

If you open nautilus using the File Manager icon and then close it, the File Manager icon no longer works (just glows a few times, then nothing happens).  But you can still open nautilus by clicking on the Ubuntu icon.  So I guess it is best just to leave it open in another workspace.

At one point when I was trying to fix that by right clicking on File Manager and click Pin to Launcher (maybe when already checked) Unity and all panels and window controls disappeared, all windows lost focus, and Ctrl+Alt+T would not bring up a terminal.  But I just did **sudo restart gdm** from the console, and I was able to log into GNOME Session again with everything back normal.  Although, doing anything from the console right now is a bit awkward because I have to do it blind (login is lower right and does not scroll up).

i5 650 3.2 GHz 8 GB, GT 430 w/nvidia 260.19.21 driver

---

