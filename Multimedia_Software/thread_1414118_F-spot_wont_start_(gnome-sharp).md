---
title: "F-spot wont start (gnome-sharp)"
date: 2010-02-23
forum: Multimedia Software
---

### Post by cafeschintze on 2010-02-23
Hi there,

I upgraded to Ubuntu9.10 recently. Just wanted to open F-spot and it wont start any more. Here is what happens:


```
gromit@wendolene:~$ f-spot

** (/usr/local/lib/f-spot/f-spot.exe:14603): WARNING **: The following assembly referenced from /usr/local/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=14)
     Version:    2.20.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/f-spot/).


** (/usr/local/lib/f-spot/f-spot.exe:14603): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gnome-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gnome-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
gromit@wendolene:~$ 
```


I rebuilt libmono, I reindexed gac, still no success.
Does anyone have a similar problem? Does anyone have an idea what to do?

regards, Stefan

---

