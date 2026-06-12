---
title: "Banshee 1.0 wont start."
date: 2008-06-13
forum: Multimedia Software
---

### Post by mcorcoran on 2008-06-13
I've installed Banshee 1.0 from Banshee Team PPA but whenever I try to run it I get the following error:

```

** (/usr/lib/banshee-1/Nereid.exe:27834): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Nereid.exe could not be loaded:
     Assembly:   gdk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1).


** (/usr/lib/banshee-1/Nereid.exe:27834): WARNING **: Could not load file or assembly 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/banshee-1/Nereid.exe:27834): WARNING **: Missing method InitCheck in assembly /usr/lib/banshee-1/Nereid.exe, type Gdk.Global

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
mcorcoran@mcorcoran-desktop:~$ banshee-1

** (/usr/lib/banshee-1/Nereid.exe:28695): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Nereid.exe could not be loaded:
     Assembly:   gdk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1).


** (/usr/lib/banshee-1/Nereid.exe:28695): WARNING **: Could not load file or assembly 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/banshee-1/Nereid.exe:28695): WARNING **: Missing method InitCheck in assembly /usr/lib/banshee-1/Nereid.exe, type Gdk.Global

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'

```

I've searched Synaptic for gdk-sharp and it is installed (libgtk2.0-cil version 2.12.0-2). Any ideas on what I'm missing in order to get it to run? I had a previous version installed at one time but I've completely removed it so I don't think that would interfere.

---

