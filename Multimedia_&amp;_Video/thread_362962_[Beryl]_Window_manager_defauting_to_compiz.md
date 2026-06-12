---
title: "[Beryl] Window manager defauting to compiz?"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by Loonux on 2007-02-16
For some reason when i start beryl-manager (or KDE starts it with autostart), it is choosing Compiz as the window manger which means nothing works. If i right click on the diamond and manually set it to beryl, everything works fab.

Is there any way to remove compiz from this list or at least force it to be Beryl every time?
For some reason under 'select window manager' i have:

Beryl (works and want this to be the default for my xGL sessions)
Compiz (Doesn't work)
Compiz with COW (dont know what COW is but haven't tried this option)
KWin (want this to be the default for a nonXGL KDE session)

even though i have never installed Compiz (looking at Adept package manager, while it appears compiz ISNT installed, comp-z-core and compiz-plugins are! When i try to remove them i get an error)

Thanks

---

### Post by Loonux on 2007-02-27
Anyone able to offer a suggestion on this one/

Thanks

---

### Post by Loonux on 2007-03-02
Anyone?

Can I, for example, remove all files with the word compiz in them? Not very elegant I know but if it solves the issue and gets Compiz off my system i dont really care!
Can belive the package manager cannot forcefully remove them!!! :(

---

### Post by Martin A on 2007-03-02
can you forcefully remove them with apt-get??

---

### Post by Loonux on 2007-03-03
How can you force remove with apt-get?

---

### Post by Loonux on 2007-03-04
I have tried
```
sudo apt-get remove -f compiz-core compiz-plugins
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-core
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz-core compiz-plugins
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2273kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 105062 files and directories currently installed.)
Removing compiz-plugins ...
/var/lib/dpkg/info/compiz-plugins.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-plugins (--remove):
 subprocess pre-removal script returned error exit status 127
dpkg: compiz-core: dependency problems, but removing anyway as you request:
 compiz-plugins depends on compiz-core (= 1:0.3.3-0ubuntu2~git2006112~edgy1).
Removing compiz-core ...
/var/lib/dpkg/info/compiz-core.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-core (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 compiz-plugins
 compiz-core
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

And it just falls over as detailed above...

---

