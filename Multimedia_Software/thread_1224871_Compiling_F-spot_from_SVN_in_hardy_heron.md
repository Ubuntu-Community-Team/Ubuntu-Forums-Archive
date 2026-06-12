---
title: "Compiling F-spot from SVN in hardy heron"
date: 2009-07-27
forum: Multimedia Software
---

### Post by misha680 on 2009-07-27
Dear All:

I have installed this repository:
[https://launchpad.net/~ruben/+archive/ppa](https://launchpad.net/~ruben/+archive/ppa)

and am running into these problems:
```

checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtk-sharp-2.0 >= 2.12.2 glib-sharp-2.0 >= 2.12.2 glade-sharp-2.0 >= 2.12.2 gnome-vfs-sharp-2.0 >= 2.12.2 gtk+-2.0 >= 2.14 mono >= 2.0.0 mono-cairo >= 1.2.4) were not met:

Requested 'gtk-sharp-2.0 >= 2.12.2' but version of Gtk is 2.12.1
Requested 'glib-sharp-2.0 >= 2.12.2' but version of GLib is 2.12.1
Requested 'glade-sharp-2.0 >= 2.12.2' but version of Glade is 2.12.1
Requested 'gtk+-2.0 >= 2.14' but version of GTK+ is 2.12.9
Requested 'mono >= 2.0.0' but version of Mono is 1.2.6

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

Any help much appreciated. Thank you

Misha

---

### Post by directhex on 2009-07-28
> **misha680 said:**
> Dear All:

I have installed this repository:
[https://launchpad.net/~ruben/+archive/ppa](https://launchpad.net/~ruben/+archive/ppa)

and am running into these problems:
```

checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtk-sharp-2.0 >= 2.12.2 glib-sharp-2.0 >= 2.12.2 glade-sharp-2.0 >= 2.12.2 gnome-vfs-sharp-2.0 >= 2.12.2 gtk+-2.0 >= 2.14 mono >= 2.0.0 mono-cairo >= 1.2.4) were not met:

Requested 'gtk-sharp-2.0 >= 2.12.2' but version of Gtk is 2.12.1
Requested 'glib-sharp-2.0 >= 2.12.2' but version of GLib is 2.12.1
Requested 'glade-sharp-2.0 >= 2.12.2' but version of Glade is 2.12.1
Requested 'gtk+-2.0 >= 2.14' but version of GTK+ is 2.12.9
Requested 'mono >= 2.0.0' but version of Mono is 1.2.6

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

Any help much appreciated. Thank you

Misha

SVN F-Spot needs Mono 2.0 or above. Hardy comes with 1.2.6. At best you can get 1.9.1 on there without major system surgery.

---

