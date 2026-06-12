---
title: "Boxart and MythGame .22"
date: 2009-10-07
forum: Mythbuntu
---

### Post by Lepy on 2009-10-07
Does anyone know the secret to getting boxart working in MythGame .22? In .21 its was easy enough since the game path and cover art path are configurable in the player setting. Easy as pie.

However, in .22 this has been replaced with a catch all boxart path in the General Settings tab. Using playstation games as an example, I've placed the covers in the main specified directory (/video/boxart) and in a path specialized towards a particular player (/video/boxart/pSX) but neither work!

Does the boxart even work in .22 or is there something I am overlooking?

---

### Post by Lepy on 2010-04-19
After upgrading to .23 and 10.04, I'm still having mythgame issues!

First of all, games did not seem to scan unless file extensions were explicitly set in the game player setup, contrary to file extension setting description and how it worked in 9.10

After setting the extensions and scanning, games can be accessed and launched in the "By" categories (Genre, Year, Name, Publisher), but selecting All Games gives only a list of the players specified in setup. There is no way to advance into the system and then select a game. Example: Play Games -> By Genre -> Puzzle -> Select game and game will launch while Play Games -> All Games -> pSX (no way to go further into the menu or alphabetical list).

This can be cumbersome trying to find and start a specific game, like my playstation games which I have ripped and converted to pSX's proprietary cdz format, as they are no longer being sorted alphabetically under their respective systems in all games and do not have correct information, possibly because playstation games are not well supported in the romdb (unlikely since I remember seeing some while checking the mysqldb) or the crc values are off since I have converted them to cdz (most likely) 

From what I can tell, boxart is still not working, though the romdb table is populating many mame games just fine as it was in .22.

I'd really like to get my setup looking like the Arclight example: [http://www.fecitfacta.com/Arclight/Gallery.html#4](http://www.fecitfacta.com/Arclight/Gallery.html#4).
Does anyone know how the background and coverart were acquired? Was it manually set or is there a way to scrap scummvm games and the like?

Is it possible my whole mythgame database is fubar? If so, is there a way to drop the whole thing and start from scratch?

---

### Post by Lepy on 2010-04-22
It seems that disabling "Hash filenames in display" has fixed the issue of games not showing up in All Games -> Playername -> 
However, without the hash, advancing past Playername results in a list like Playername -> Gamename instead of Playername -> A-Z List -> Gamename

I also have a gameplayer for alephone, with the rom directory containing some .sh scripts, they were recognized and worked in .22, but won't scan in .23 no matter what I've tried.

Box art seems to still be broken. In a my psx dir, there is a file called "Sentient.cdz" and in the boxart dir, I have tried scanning with "Sentient.bmp/jpg/jpeg/gif/png" but none auto-detect. At least the game runs and is still really fun to play.

Setting the metadata by hand works fine, but this takes too much time. Plus, all art will stay static when switching through roms in the same Gamename level unless another rom with art is passed over.

It seems every upgrade of mythtv is breaking something in mythgame.
.20-.21 everything worked fine
.22 boxart stopped working
.23 boxart + hashing fail

There is only one strange error: 
~$ mythfrontend -v important mythgame
```
2010-04-22 04:23:33.153 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Arclight/game-ui.xml
2010-04-22 04:23:33.195 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythmythgame.so: cannot open shared object file: No such file or directory
2010-04-22 04:23:33.195 Unable to initialize plugin 'mythmythgame'.
2010-04-22 04:23:33.195 Unable to run plugin 'mythmythgame': not initialized
```

Could this be the source of the problem? Looks like the shared object that is being initialized is miss-named? Even though it spits out and error...mythgame basic functionality is still working. Other than the outdated mythgame guide...there really isn't much info on this plugin.

So, has anyone else encountered similar errors?

---

### Post by rokrep69 on 2010-05-15
I can't get any games to scan in mythgame. Nothing seems to help.
Apparently we are the only 2 people on the net who have issues/ use mythgame in 10.04.

I was trying to get Stella to work in mythgame. It works great on it's own, but no matter what emulator and setting I try, the games do not scan properly and the mythgame menu remains empty. I don't get it, and I'm not all that sure on where to look for the errors it logs.

---

### Post by egh on 2010-05-20
worked when I explicitly set extensions, so for .zip files set your extensions to:

  zip

(no leading dot).

---

