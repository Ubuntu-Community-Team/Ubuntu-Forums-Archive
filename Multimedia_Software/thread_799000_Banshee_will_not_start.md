---
title: "Banshee will not start"
date: 2008-05-18
forum: Multimedia Software
---

### Post by notmatt on 2008-05-18
I have just installed Banshee and it will not start.  When I click on it from the application menu, nothing happens.  When I type 'banshee' from the command prompt I get the following:
```

** (/usr/lib/banshee/banshee.exe:10464): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:10464): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at (wrapper managed-to-native) System.Object:__icall_wrapper_mono_delegate_ctor (object,object,intptr)
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000]

```

---

### Post by garyedwardjohnston on 2008-05-18
Why are you running the Banshee Windows version?

Download and install Banshee for Ubuntu.

[http://www.banshee-project.org/Main_Page](http://www.banshee-project.org/Main_Page)

---

### Post by notmatt on 2008-05-19
That is the version that I installed through Synaptic.  I didn't download and install the windows version incase you were wondering that.  I had been wondering about the .exe as well.  I tried to uninstall and then reinstall the app, but no luck.  It seems to use mono and I think that might be the problem.

Any ideas?

---

### Post by notmatt on 2008-05-23
Sorry about this, but *bump*.  I've only ever installed this through Synaptic, I've not installed the windows version.  The messages I get are the ones I get when starting it through the terminal.

Any ideas?

---

### Post by ubuttu on 2009-11-16
reboot the buttu...

---

### Post by directhex on 2009-11-16
Missing assembly references errors are usually caused by users compiling their own Mono into /usr/local or some other place in $PATH

---

