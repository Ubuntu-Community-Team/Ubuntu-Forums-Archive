---
title: "Banshee Lyrics plugin not lauching"
date: 2008-04-26
forum: Multimedia Software
---

### Post by avelez89 on 2008-04-26
Hello everyone,
Thank for your time and interest in helping me. I recently upgraded to a clean install of 8.04 and I'm loving it so far.

I am trying to get Banshee's lyrics plugin to work but I can't. I downloaded the .deb plugin package from here:
> [http://www.gtk-apps.org/content/show.php/Banshee+Lyrics+plugin?content=64837](http://www.gtk-apps.org/content/show.php/Banshee+Lyrics+plugin?content=64837)
I then installed the .deb file. When I try to enable the pluging from within Banshee -> edit -> plugins -> lyrics (enable) it says that "this plugin could not be initialized"

after replicating the error while running banshee in terminal I get the following:

> /home/andres/.config/banshee/plugins/lyrics/

** (Banshee:7850): WARNING **: The following assembly referenced from /usr/lib/banshee/Banshee.Plugins/Lyrics.dll could not be loaded:
     Assembly:   gtkhtml-sharp    (assemblyref_index=6)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee/Banshee.Plugins).


** (Banshee:7850): WARNING **: Could not load file or assembly 'gtkhtml-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Warning: [4/26/2008 2:57:45 PM] (Could not initialize plugin `Lyrics') - A type load exception has occurred.
Debug: [4/26/2008 2:57:45 PM] (Exception caught while initializing plugin `Lyrics') - System.TypeLoadException: A type load exception has occurred.
  at Banshee.Plugins.Lyrics.LyricsPlugin.InterfaceInitialize () [0x00000] 
  at Banshee.Plugins.Plugin.Initialize () [0x00000]

I have no idea what to do now. The plugin used to work fine in Gutsy.

Thank you very much for your time!

---

### Post by varomix on 2008-08-21
I had to compile it to make it work here, it was actually very easy

---

### Post by Perez71 on 2009-05-12
Try here [http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/bansheelyricsplugin/](http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/bansheelyricsplugin/)
There's .deb packages.

---

### Post by dckirba on 2010-06-03
Hey guys,

I came across this thread while looking for the lyrics plugin for Banshee in Lucid (10.04). It's now actually quiet easy to install.

[LIST]
[*]Just go to [COLOR="DarkRed"]System>Administration>Synaptics Package Manager[/COLOR]
[*]Type banshee lyrics in the search box
[/LIST]

You should find the Banshee extension for lyrics. Just select for installation and click apply.

To enable the plugin in Banshee go to [COLOR="DarkRed"]edit>preferences[/COLOR] and click on the extensions tab. You should find the plugin installed. Just check the checkbox to enable it.

Hope that helps somebody.

Cheers,
David K

---

### Post by CFBauer on 2010-10-21
> **dckirba said:**
> Hey guys,

I came across this thread while looking for the lyrics plugin for Banshee in Lucid (10.04). It's now actually quiet easy to install.

[LIST]
[*]Just go to [COLOR="DarkRed"]System>Administration>Synaptics Package Manager[/COLOR]
[*]Type banshee lyrics in the search box
[/LIST]

You should find the Banshee extension for lyrics. Just select for installation and click apply.

To enable the plugin in Banshee go to [COLOR="DarkRed"]edit>preferences[/COLOR] and click on the extensions tab. You should find the plugin installed. Just check the checkbox to enable it.

Hope that helps somebody.

Cheers,
David K
Thanks, this helped! I'll also point out that in 10.10 the plugin is available for download from the Ubuntu Software Center.

---

### Post by fermin on 2011-02-12
It's not working anymore for me. I tried reinstalling it from the official repos through Synaptic and it doesn't work. Keeps saying I have to 'upgrade to version 0.4' of the Lyrics Plugin, but in the page [www.lyricsplugin.com](www.lyricsplugin.com) there only are versions of the plugin for WMP, Winamp and iTunes :S Anyone solved this problem lately? I use Ubuntu 10.10 Maverick (UNE).

---

### Post by frangoitia on 2011-03-07
In my case it always says "no lyrics were found"

---

### Post by Blueman090 on 2011-07-08
Don't ask me why this works, but it does.  You have to delete all the files in the lyrics folder.  For some reason, everything runs smoothly after that.  


Go to ~/.cache/banshee-1/extensions

Delete or rename the lyrics folder

Create a new folder named lyrics

Open Banshee and see what happens



I had a problem with every song saying "No lyrics found" (so it was not working at all), this solution cleared it up.  

I then had a problem where it managed to fetch some songs (so I know it was somewhat working), but couldn't find most others.  Same solution and now I managed to get about 90% of the songs I have.  




As a side note:  If you poke around the lyrics folder, its not hard to figure out how to create your own lyrics files.  

Google the lyrics and just cut and paste the lyrics and cut and paste them into a plain text file.  Save the text file in the format of [artist name]_[song name].lyrics

---

### Post by stillgale on 2011-09-28
This did it for me. Thank you _very much_.

---

