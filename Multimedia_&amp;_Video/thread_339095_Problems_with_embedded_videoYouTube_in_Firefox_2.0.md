---
title: "Problems with embedded video/YouTube in Firefox 2.0 (Edgy)"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by ftmichael on 2007-01-15
I'm using Edgy with Firefox 2.0.0.1.  A week or two ago, for no reason that I'm aware of, the video stopped working in YouTube.  It showed the freeze-frame bit like normal when stopped, but when playing, it was just black.  The audio still worked though.

A few days ago, the audio stopped working as well.  Embedded YouTube videos on other sites gave me this:
[http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot1.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot1.png)

When I hovered over the video, I got this:
[http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot2.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot2.png)
(Once I'd hovered, it stayed looking like that until I reloaded the page entirely.)  Clicking the play button did nothing at all.

I searched the forums and found a load of threads saying that installing the nonfree Flash plugin was the best idea for Edgy users, so I did, and now I get this:
[http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot3.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot3.png)

The same thing happens for other Flash items, not just YouTube videos.  The ever-glorious [http://www.cybermoonstudios.com/8bitDandD.html](http://www.cybermoonstudios.com/8bitDandD.html) , which is animation, gives me:
[http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot4.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot4.png)
which is normal, but hovering over PLAY<--- doesn't turn it into PLAY!!! the way it's supposed to, and clicking does nothing.  When I right-click, I get three options: Open in New Page, Report Bug, and Copy URL.  Clicking on Report Bug takes me to [http://www.schleef.org/swfdec/bugreport.html?8bitDandD.swf](http://www.schleef.org/swfdec/bugreport.html?8bitDandD.swf) , which gives me a 404 Not Found error.

When I go to youtube.com and try to view videos there, it says, 'Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest flash player. (link)'

When I go to video.google.com and try to view videos there, I get a little pop-up error that says I need Flash 7 or higher to view videos.  With the nonfree plugin installed, don't I have Flash 9?  What's the issue?

Also, around the time the video stopped working with YouTube (but audio still worked), all other embedded video stopped working.  (Sadly I don't remember if they stopped working at exactly the same time, but they may have.)  I have to download any .wmv, .mpg, etc. video file I want to watch, all of which play fine in standalone VLC.  I don't have the VLC plugin installed for mozilla/firefox, only the mplayer plugin.  Gstreamer plugins are all up to date.

Help!

Michael

---

### Post by Amaroq on 2007-01-15
You probably just need to install the flash plugin. I had flash 7 installed, but youtube wouldn't give me anything at all. I followed these instructions from ubuntuguide and everything was working fine. Installing this should let flash 9 things work for you. And who knows, maybe you didn't integrate the flash plugin with firefox after you installed it.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Those instructions are for edgy, the system you are using. For anybody using a different ubuntu, just go to the guide, select your version, and look up what you need.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by ftmichael on 2007-01-16
When I installed the nonfree Flash, it told me I had to first remove the plugin.  I've now reinstalled the plugin (with nonfree Flash still installed) and restarted Firefox, and we're back to [http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot1.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot1.png) and [http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot2.png](http://nbtsc.org/~ftmichael/storage/Pictures/Screenshot2.png) instead of Screenshot3.  And it's crashing Firefox now too.

[http://www.cybermoonstudios.com/8bitDandD.html](http://www.cybermoonstudios.com/8bitDandD.html) , however, works now, although it freezes Firefox momentarily while it attempts to load, and slows my system waaaaaay down.  And some of the animation doesn't show up - it'll show me the man's mouth (which is moving) for a moment before his face (which is still) appears, and there's a spot where we're supposed to zoom in a bit on his face, and that doesn't happen at all; he stays the same size.  The sound works fine though.

youtube.com gives me the same message: 'Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest flash player. (link)'

Michael

---

### Post by philh99 on 2007-01-16
You need to use Adobe Flash Player 9 Beta.
Download it from here - [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")
Then, extract the file to your home folder/.mozilla/plugins.

If the file directory doesn't exist, then you will need to create.
If the file exists, back it up and replace with this one.

It will now work fine.

---

### Post by ftmichael on 2007-01-16
Just tried that; it didn't change a thing.

Michael

---

### Post by philh99 on 2007-01-16
Did the file already exist?
Did you close all  instances of firefox, then restart one?

---

### Post by ftmichael on 2007-01-16
The plugin had been uninstalled so it wasn't present.  I reinstalled it.

I did close Firefox entirely and restart it.  Nothing changed.

Michael

---

### Post by ftmichael on 2007-01-17
**PROBLEM SORTED!**

Adobe released the final release (redundant, I know) of version 9 today.  I uninstalled everything to do with Flash (except RealPlayer) via Synaptic, and then did the following:

* Went to [http://www.adobe.com/](http://www.adobe.com/)

* Downloaded the .tar.gz install file to my Desktop

* Used Archive Manager to extract the .tar.gz file to my Desktop

* In terminal, went into the newly created directory with the extracted files in

* Ran sudo ./flash <tab> <enter>

* Specified the install directory as /usr/lib/firefox

That was it!  All done!

Thanks to everyone who offered suggestions.

Michael

---

