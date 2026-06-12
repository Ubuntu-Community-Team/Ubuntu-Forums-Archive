---
title: "Banshee issue -- help appreciated :)"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Hammer89 on 2008-05-29
Howdy... I've been trying to get banshee to run on my computer for some time now... but for some reason, every time I try to run it, it returns this error:

> ** (/usr/lib/banshee/banshee.exe:20991): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:20991): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000] 

I've tried installing it via apt-get... tried installing .deb's I found online... tried compiling it from source... all with the same failing results. Anyone have any idea how to fix this?

---

### Post by micczu on 2008-08-14
I have the same problem with running FuriusISOMount. I think it could be the old gtk-sharp2 (in Feisty is version 2.10).

---

