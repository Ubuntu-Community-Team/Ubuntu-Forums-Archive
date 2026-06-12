---
title: "Loading Compiz on Feisty Fawn"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by matteospqr on 2007-07-13
Hello!
I have installed Compiz and all the other things it needs but now when I try and start compiz from terminal I get this error message:

/usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

also when I run compiz-tray-icon I get this:

(compiz-tray-icon:6014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6014): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:6014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6014): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


I am not sure what to do!

I am running compiz on an amd64, ati video card, and fesity fawn 7.04!


THANKS ALOT

---

### Post by bdtgp on 2007-07-13
Try this
```
compiz --replace
```

Did you remove the other compiz effects before you installed the new ones?  If not do this first
```
sudo apt-get remove compiz-core desktop-effects
```

Then run the other command.

---

### Post by matteospqr on 2007-07-16
Ok I have removed what you have told me to remove and then I ran the command again (compiz --replace)
but now it does not find any such directory. This is what I get:

matteo@matteo:~$ compiz --replace
bash: /usr/bin/compiz: No such file or directory

what should I do now?

---

