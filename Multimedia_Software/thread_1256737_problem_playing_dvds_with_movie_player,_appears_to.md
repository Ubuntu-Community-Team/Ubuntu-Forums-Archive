---
title: "problem playing dvds with movie player, appears to buffer? gstreamer issue?"
date: 2009-09-03
forum: Multimedia Software
---

### Post by SirWeazel on 2009-09-03
When i play a dvd with other movie players vlc, mplayer, and movie player (totem-xine) everything is fine.  When i play a dvd with default movie player, it plays but pauses and needs to buffer, or i need to skip to a chapter ect. It is like it is reading the dvd as it plays it. If i click on the slider bar and try to slide the bar further into the movie it just resets back to where it was playing from. Playback will pause sometimes for no apparant reason, and then is a pain to start playing again.

These issues occur when using the default movie player (Totem Movie Player 2.26.1, Movie Player using GStreamer 0.10.22) (playing any type of dvd's, home made dvds i made from some avi's, store bought dvds, ect.)

Any ideas how to fix? - please note, i have medibuntu repos and stuff installed. It's not a region or encrypted thing as far as i know.  Other players play fine.  Movie player also  plays avi's and other video formats fine)

If i can't fix, how can i make movie player -xine my default movie player?

---

### Post by mc4man on 2009-09-03
> If i can't fix, how can i make movie player -xine my default movie player?

What you have as far as totem-gstreamer is pretty much what  you will get, it's not well suited for movies, particularly dvd's

As far as default

you have several choices from switching your default totem player to xine or just doing on an individual basis

for dvd's only you could run this in a terminal and under the media tab -> DVD Video look for Movie Player (xine)
```

nautilus-file-management-properties
```

It may not be there, if not, the *quickest* way would be to use the "open with other application' box below the choices and pick Movie Player (xine).
If for some reason it's not there then choose 'use custom command' and enter ```
totem-xine
```

If you wanted to do a system switch for totem from gstreamer to xine then run this and choose 2 (now 'Movie Player' will use totem-xine, your audio-preview will use totem-xine, ect.
```

sudo update-alternatives --config totem
```

As far as the above...
I don't use the totem-mozilla plugin, but if you switch the  totem default from gstreamer to xine than that may affect that plug-in. It's been suggested gstreamer works better than xine in that regard, myself I don't know (or really care), but something to keep in mind

---

### Post by SirWeazel on 2009-09-03
Mc4man, Thank you for your quick reply. You seem very knowledgeable, What do you suggest to use, or is the best video player for dvds. I've tried VLC and Mplayer, but when the video is full screen it is difficult to navigate the movie (no controls when moving the mouse around on the screen, other then right clicking). I tried smplayer, but i couldn't get any video. Smplayer was translucent and i could see my desktop background, but no video. 

As far as  the mozilla plugin, i don't think i use that part. I rarely use firefox, and i use opera 10 for my browsing, but i'm not sure what plugins are used for youtube, flash, ect., but whatever plugins are installed, so far seem to work ok.

I'm just trying to make my system the most user friendly for my girl who has no computer knowledge what so ever. So she can switch to her user account, put dvd in, and start watching a movie. With very few user input choices such as selecting a media player from a list of 3 or 4, especially when the first one on the list doesn't work very well.

---

### Post by mc4man on 2009-09-03
While there are several options available to you like get a newer vlc from a ppa or explore why smplayer isn't displaying properly, ect. the simplest for now would just be to set totem-xine as the default dvd video (movies) player.
You could then explore any of the other options if desired.

I use hardy so the I made a small mistake in saying how to set totem-xine in the file management settings if it wasn't shown, edited in more complete wording.

For the moment to set totem-xine for your friend as default (so she'd just pop in a disk and the movie would start), **log in to her account**, get to the file management settings as described before or..

There are many ways to open 'file management', it's a menu item in system preferences that disabled by default

So you could use system -> main menu and then enable it there.

Or open home folder and in task bar go 'edit' -> preferences

Or just put a dvd in the drive and hold down the shift button till you get a pop up and make choice there

(it seems overly cautious that file management is disabled as a menu item, could save alot of typing and aggravation if it was there

screens should show you what to expect, screen 1 from the pop up , 2 from file management

---

