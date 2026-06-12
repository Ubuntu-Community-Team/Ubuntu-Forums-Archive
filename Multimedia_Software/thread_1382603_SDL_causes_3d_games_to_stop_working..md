---
title: "SDL causes 3d games to stop working."
date: 2010-01-16
forum: Multimedia Software
---

### Post by Abhijit Navale on 2010-01-16
All my 3d games were working fine.  But then I mess up with SDL library files. I want to install Excalibur: Morgana&#8217;s Revenge v3.0. But it is not installing by itself. I got info in their README that i should first install and set SDL libraries. so from their web site i downloaded source package and install it. after that no 3d game is starting including, wideland,torcs, Balazar,Battle for Wasnoth. Someone should diagnos the problem with SDL libraries. let me know if anyone of u have some sort of solution or workaround.  Is there any other way to get all these games working? (e.g. reinstalling game or something like that???)
 ```
When tried to run each game from terminal I got these errors:
1.WIDELANDS  

Caught exception (of type '11_wexception') in outermost handler! 
The exception said: [src/wlapplication.cc:748] Failed to 
initialize SDL: No available video device  
This should not happen. Please file a bug report 
on version: UNKNOWN-REVISION.  

2. NEXUIZ  

Nexuiz Linux 08:21:26 Jun  6 2008 Trying to load library... &quot;libz.so.1&quot; - loaded.
 Added packfile /usr/share/games/nexuiz/data/data.pk3 (4066 files)
 Added packfile /usr/share/games/nexuiz/data/music.pk3 (10 files)
 Trying to load library... &quot;libcurl.so.4&quot; - loaded. 
Quake Error: Failed to init SDL video subsystem: No available video device  

3. BATTLE FOR WESNOTH  

Battle for Wesnoth v1.6 Started on Sat Jan 16 19:17:10 2010 
 20100116 19:17:10 error display: Could not initialize SDL_video: No available video 
device Could not initialize video. Exiting.
```  Because of this my virtual box computer screen is also gone blank!

---

### Post by Abhijit Navale on 2010-01-16
Please help me as early as possible.

---

### Post by Abhijit Navale on 2010-01-17
No One? The Life without games is going very horrible.

---

### Post by Abhijit Navale on 2010-01-17
Solution:

I installed all xorg-dev and related libraries.

Then I recompile the SDL-1.2.14 source.

And then all my games are working fine!

Thanks to <boss_mc> for helping me because my life without all those games were just horrible.

Thank you <boss_mc> !

---

### Post by Abhijit Navale on 2010-01-18
PRECAUTION : 

DO THIS ON YOUR OWN RISK!

Because in the excitement I installed some unnecessary xorg driver, may be of nvidia or others (actually they are not needed for my pc) due to which at ubuntu startup my screen flickers and ubuntu cannt start.

As I am a newbie I am not sure that this is happening because of installing some extraa xorg libraries. 
 
But now I have to do reinstallation.

---

