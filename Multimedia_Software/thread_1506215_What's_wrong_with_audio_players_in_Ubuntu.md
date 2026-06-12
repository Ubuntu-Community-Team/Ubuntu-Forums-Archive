---
title: "What's wrong with audio players in Ubuntu?"
date: 2010-06-10
forum: Multimedia Software
---

### Post by RhapsodyOfFire on 2010-06-10
I have very strange problems with all the good audio mp3 players in Ubuntu. Not the bad programs only the good (whcich have good skins and library and so on). Amarok for some reason skips all the music files but only mp3 if I put m3u online radio it works. It doesn't show errors at all just skips the songs. I've never had issues with mp3 files before. The movie player works liek a charm but is too cheap (no library to browse files). Banshee was great and suddenly it stopped working just like the good old Rhythmbox... They appear to be starting in background but don't show nowhere. I cannot install XMMS players too it isn't found on the apt-get server. Also my packages are fully updated. Reinstalling the programs don't help at all! It must be some major issue with the programs not launching. It's not a single program Banshee, Rhythmbox and I think some other but don't remember the names. Movie player plays all but is too simple. I want something like Winamp with nice library please help. No need for movies just mp3.
P.M. Exaile works not fine with mp3 but I preffer how Rhytmhbox shows the music library with all the songs not like in seperate folders. I could try song shuffle. But why the other programs don't start what command can show what's happening?

---

### Post by blchinezu on 2010-06-10
Winamp is nothing like Amarok, Rhythmbox or other player like those two. It just can't handle too many songs loaded in the library. It lags a lot... I do believe you should stop comparing linux players with windows players. If you can't do that just run Winamp through WinE and that's that.
(Although i do believe Winamp isn't what it used to be. Best for windows would now be Foobar2000)
The amarok problem is certainly not because of the player... at least not if it's about the 1.4 version... i'm using it daily and i never had that problem

---

### Post by Yellow Pasque on 2010-06-10
It might be helpful if you started the problematic programs from the terminal. It sounds like rbox is crashing.
For Amarok, make sure you have this installed:
```
sudo apt-get install libxine1-all-plugins
```

---

