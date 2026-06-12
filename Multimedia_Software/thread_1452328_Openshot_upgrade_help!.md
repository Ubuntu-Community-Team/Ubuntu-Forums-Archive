---
title: "Openshot upgrade help!"
date: 2010-04-11
forum: Multimedia Software
---

### Post by blur xc on 2010-04-11
I had previously installed Openshot 1.0 and it's nice, but would crash hard when trying to render a project.  So, I thought I'd check and lo and behold v1.1 is out.  I downloaded the .deb (still on 9.04) and ran it, but now openshot would not start.  So, I un-installed it, deleted the .openshot directory, and tried running it- same error.  So one more time, I removed it, and this time downloaded the source code tarball and installed it that way.  The installation was successfull, but it still won't run.  And also, when I run it from the command line it says its starting Openshot 1.0.  I'm out of ideas.  In the end, I really want to just install Lucid and call it a day - but it's not ready yet and I want to finish this little video project ASAP (video of the baby to send to grandparents)...

Here's the terminal output:
```
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
--------------------------------
   OpenShot (version 1.0.0)
--------------------------------

(openshot:20524): libglade-WARNING **: could not find glade file '/usr/share/openshot/windows/glade/Main.glade'
Traceback (most recent call last):
  File "/usr/local/bin/openshot", line 50, in <module>
    main()
  File "/usr/share/openshot/openshot.py", line 57, in main
  File "/usr/share/openshot/windows/MainGTK.py", line 47, in __init__
  File "/usr/share/openshot/windows/SimpleGladeApp.py", line 102, in __init__
  File "/usr/share/openshot/windows/SimpleGladeApp.py", line 340, in create_glade
RuntimeError: could not create GladeXML object
```

Thanks,
BM

---

### Post by blur xc on 2010-04-12
bump

---

