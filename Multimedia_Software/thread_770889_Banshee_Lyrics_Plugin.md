---
title: "Banshee Lyrics Plugin"
date: 2008-04-27
forum: Multimedia Software
---

### Post by avelez89 on 2008-04-27
Hello everyone, thank you taking a moment to try and help me.

I recently installed the Banshee Lyrics plugin .deb from:
[http://www.gtk-apps.org/content/show.php/Banshee+Lyrics+plugin?content=64837](http://www.gtk-apps.org/content/show.php/Banshee+Lyrics+plugin?content=64837)
after installation I try to enable the plugin in Banshee but it tells me that "this plugin could not be initialized"

This is the error it gives me when ran in terminal:
> /home/andres/.config/banshee/plugins/lyrics/
creating plugin dir

** (Banshee:30354): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Plugins/Lyrics.dll could not be loaded:
     Assembly:   gtkhtml-sharp    (assemblyref_index=6)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee/Banshee.Plugins).


** (Banshee:30354): WARNING **: Could not load file or assembly 'gtkhtml-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Warning: [4/27/2008 12:42:17 PM] (Could not initialize plugin `Lyrics') - A type load exception has occurred.
Debug: [4/27/2008 12:42:17 PM] (Exception caught while initializing plugin `Lyrics') - System.TypeLoadException: A type load exception has occurred.
  at Banshee.Plugins.Lyrics.LyricsPlugin.InterfaceInitialize () [0x00000] 
  at Banshee.Plugins.Plugin.Initialize () [0x00000]

I have also tried installing the pluging from source with no luck either. The .deb used to work in gutsy for me.

I don't know what to do now. All I want is lyrics support in Banshee, any other method would be great. Thank you for your time!

---

### Post by avelez89 on 2008-05-22
anyone? please.

---

### Post by varomix on 2008-08-21
I had to compile it to make it work

---

