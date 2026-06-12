---
title: "Compiz crashes on load due to Unity accessibility issue."
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mick8985 on 2011-02-24
```
michael@michael-server:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing gnomecompat options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing session options...done
Initializing snap options...done
Initializing staticswitcher options...done
Initializing vpswitch options...done
Initializing wall options...done
Initializing animation options...done
Initializing expo options...done
Initializing fade options...done
Initializing scale options...done
Initializing workarounds options...done
** (<unknown>:5096): DEBUG: Unity accessibility initialization

GLib-GIO-ERROR **: Settings schema 'org.gnome.desktop.interface' does not contain a key named 'accessibility'
aborting...
Aborted (core dumped)

```

After an upgrade I can no longer run compiz, it immediately crashes at login, when I run compiz manually I get that error.

---

