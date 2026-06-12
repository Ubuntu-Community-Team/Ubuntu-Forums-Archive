---
title: "banshee gtk-sharp"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by SonicSteve on 2008-02-07
Afternoon,

I'm having problems loading banshee. It tries to load but then stops. When type "banshee" in a terminal I get this.

I used synaptic to install the GTK-sharp version 2 but it made no difference. I also uninstalled and re-installed banshee. Nothing changed.

I did install mono from the moonlight project [www.mono-project.com](www.mono-project.com) I'm wondering if installing it might have broken some mono packages that banshee uses. "MONO" is mentioned a few times in the error below. 

 [PHP]banshee

** (/usr/lib/banshee/banshee.exe:7201): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Base.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=4)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:7201): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at (wrapper managed-to-native) System.Object:__icall_wrapper_mono_delegate_ctor (object,object,intptr)
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000] [/PHP]

---

### Post by SonicSteve on 2008-02-07
From what I now understand about Banshee, and mono. I would be willing to bet that installing mono from the "mono-project" is the problem.

Now the next problem. I have no idea how to fix this. 
Can the mono-project be removed? Anyone know?


EDIT***
I tried another mono application we all know called Tomboy. It has a very similar error again relating to MONO. I do believe that Mono is broken on this system.

---

### Post by tgalati4 on 2008-02-07
It works fine in Linux Mint 4 XFCE (based on Gutsy).  Perhaps you can remove banshee in synaptic (choose complete removal), then remove mono.  Then reinstall mono and reinstall banshee in that order.

You may need to reinstall tomboy as well as both banshee and tomboy are popular applications that use mono.

Good luck.

---

### Post by SonicSteve on 2008-02-07
Your idea makes good sense. It's the how-to remove mono part I'm quite unsure about. I installed it from the install package from their site, not synaptic therefore ?????????
Unless you have ideas about this. I may have to wait for Hardy and use other apps till then.

---

### Post by tgalati4 on 2008-02-07
A simple way is to make a printout of the build files and carefully delete them from your system.  If you built mono from scratch, then you will have a directory from which you compiled the binaries.  If you downloaded a *.deb file then you can use:

>dpkg -r mono_files*.deb

---

### Post by SonicSteve on 2008-02-08
thanks, I'll give it a go.

---

### Post by flickerfly on 2008-02-10
Did this ever get resolved? I seem to be having an identical problem and I'm missing banshee very much. :(

Thanks :)

---

### Post by SonicSteve on 2008-02-11
Not yet, I haven't had the time to really give an honest go of it.

---

