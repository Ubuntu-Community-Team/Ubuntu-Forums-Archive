---
title: "Unity does not start"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pivotraze on 2011-03-29
I can not start unity. I found out compiz wasn't installed. So I installed it.

When starting the "Ubuntu" session on the login screen, it loads without unity, so I type:
"compiz --replace"

The screen flashes, then it comes back, and terminal now has this in it:
"cody@cody-MX8734:~$ compiz --replace
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
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
Initializing scale options...done
Initializing session options...done
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
"

What is wrong here? It can't load unityshell or unitymtgrabhandles? What are these? :\

---

### Post by cariboo on 2011-03-29
Have you tried:

```
unity --reset
```

---

### Post by garvinrick4 on 2011-03-29
Maybe purge and reinstall:

```
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra
```

---

### Post by pivotraze on 2011-03-29
Funny thing is, it was neither one of those two things... Unity just wasn't installed?

I purged and reinstalled compiz like garvinrick asked..

I then tried starting unity again to no avail.

I ran "unity --reset" like cariboo907 asked... It told me Unity wasn't installed xD

So I installed it, and now it works again.

Thanks for the help :)

---

