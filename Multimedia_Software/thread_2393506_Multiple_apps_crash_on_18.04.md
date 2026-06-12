---
title: "Multiple apps crash on 18.04"
date: 2018-06-04
forum: Multimedia Software
---

### Post by bhechinger on 2018-06-04
This was previously non-Studio 17.10 upgraded to 18.04 and then I converted it to Studio.

So far it's been amazing. I struggled with Jack on 17.10 and have had zero struggle with it so far with the switch to Studio.

That being said I'm experiencing a really odd set of issues. Several apps crash at startup. They all do so in a similar manner as well:

```

free(): invalid pointer
Aborted (core dumped)

```

The apps that do this that I've found so far are:

Ardour
Hydrogen
Non-Mixer
LMMS

This is driving me crazy because I'd really like to use those apps!

Thanks!

-brian

More details follow:

```

bind txt domain [gtk2_ardour5] to /opt/ardour/share/locale
Ardour5.12.0 (built using 5.12 and GCC version 5.2.1 20150903)
ardour: [INFO]: Your system is configured to limit Ardour to only 1048576 open files
ardour: [INFO]: Loading system configuration file /opt/ardour/etc/system_config
ardour: [INFO]: Loading user configuration file /home/wonko/.config/ardour5/config
ardour: [INFO]: CPU vendor: GenuineIntel
ardour: [INFO]: AVX-capable processor
ardour: [INFO]: CPU brand: Intel(R) Xeon(R) CPU E5-2695 v3 @ 2.30GHz
ardour: [INFO]: Using SSE optimized routines
Cannot xinstall SIGPIPE error handler
ardour: [INFO]: Loading default ui configuration file /opt/ardour/etc/default_ui_config
ardour: [INFO]: Loading user ui configuration file /home/wonko/.config/ardour5/ui_config
Gtk-Message: Failed to load module "canberra-gtk-module"
Color shuttle bg not found
ardour: [INFO]: Loading color file /opt/ardour/share/themes/dark-ardour.colors
ardour: [INFO]: Loading ui configuration file /opt/ardour/etc/clearlooks.rc
ardour: [INFO]: Loading ui configuration file /opt/ardour/etc/clearlooks.rc
Found nothing along /home/wonko/.config/ardour5/templates:/opt/ardour/share/templates
run dialog
protocol Wiimote not found
free(): invalid pointer
Aborted (core dumped)

```

between "run dialog" and "protocol Wiimote not found" I'm starting a new session, setting the audio system to Jack and clicking the connect to jack button.

```

Gtk-Message: 14:04:33.188: Failed to load module "overlay-scrollbar"
Gtk-Message: 14:04:33.205: Failed to load module "canberra-gtk-module"

Hydrogen 0.9.7 [Apr 14 2017]  [http://www.hydrogen-music.org]
Copyright 2002-2008 Alessandro Cominu
Copyright 2008-2016 The hydrogen development team

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

free(): invalid pointer
Aborted (core dumped)

```

```

The Non-Mixer 1.2.0  -- Copyright (c) 2008-2013 Jonathan Moore Liles
WARNING: Could not open path /home/wonko/.ladspa/
OSC=osc.udp://deepthought:14893/
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x0
free(): invalid pointer
Aborted (core dumped)

```

```

14:06 $ lmms
Gtk-Message: 14:06:11.011: Failed to load module "overlay-scrollbar"
Gtk-Message: 14:06:11.023: Failed to load module "canberra-gtk-module"
VST sync support disabled in your configuration
free(): invalid pointer
Aborted (core dumped)

```

---

### Post by monkeybrain20122 on 2018-06-04
Sounds like a broken upgrade. Try deleting the config files (in your $HOME, either hidden files with the name of the software like ".foo" or in .config) of all these and reinstall them.

---

### Post by bhechinger on 2018-06-04
> **monkeybrain20122 said:**
> Sounds like a broken upgrade.

Hrm, that's what I was afraid of. I was half tempted to just back everything up and do a fresh install of Studio 18.04. This only helps to motivate me to do so.

Would really prefer not to, however. :)

-brian

---

### Post by bhechinger on 2018-06-04
> **monkeybrain20122 said:**
> Sounds like a broken upgrade. Try deleting the config files (in your $HOME, either hidden files with the name of the software like ".foo" or in .config) of all these and reinstall them.

Ha, you edited! Will give that a go.

---

### Post by monkeybrain20122 on 2018-06-04
See the edited post.

---

### Post by bhechinger on 2018-06-04
Yeah, that didn't seem to help. I'm starting to seriously consider a fresh install of Studio.

---

### Post by bhechinger on 2018-06-05
Looks like the problem is with csladspa. Once I remove that package things start working.

This has been broken since 17.10. No idea on a resolution.

I've opened a ticket: [https://github.com/csound/csladspa/issues/1](https://github.com/csound/csladspa/issues/1)

---

