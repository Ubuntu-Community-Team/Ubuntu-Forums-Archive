---
title: "SMPlayer 0.6.6 released"
date: 2008-12-31
forum: Multimedia Software
---

### Post by rvm4000 on 2008-12-31
[SMPlayer](http://smplayer.berlios.de) 0.6.6 has been released.

Most important changes:
> 
* Added an option to generate a preview (thumbnails) of the video.
* Added a new gui (mpcgui, a media player classic clone) developed by Matthias Petri.
* Added some auto zoom options, to display the video without black borders.
* Implemented a new (and optional) method to save the file settings. This method uses an ini file per each played file. It's faster than the old one.
* Added a new option in Preferences->Video: add black borders on fullscreen. If this option is enabled, black borders will be added to the image in fullscreen mode. This allows subtitles to be displayed on the black borders.
* Increased the resolution of the seekbar. Allows a more accurate seeking.
* Added 3 modes for the stay on top option: always, never and while playing.
* Added a history to the open URL dialog.
* Added new action to cycle through all aspect ratios. Assigned by default to key "A".
* It's possible to run some specified actions every time a file is loaded.
* Possibility to set up a proxy for internet connections (used for subtitle downloading).

You can get packages for hardy and intrepid here:
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

---

### Post by SuperSonic4 on 2008-12-31
I already have it :) 
It's very useful especially the aspect ratio

---

### Post by rvm4000 on 2009-01-11
I hope version 0.6.7 will have support for dvd menus.

If you don't to want to wait until then and want to test what it has already been done:

* download the deb package for r2660 from [here](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)
* go to Preferences->Keyboard and mouse->Mouse and select "Activate option in DVD menus" for the left mouse button (so you can select the options in the menus with the mouse)
* go to Preferences->Drives and check the option "Enable DVD menus" 

Now when you select Open->DVD from drive or Open->DVD from folder, it will be played with dvd menus.

BTW, this requires a recent version of mplayer compiled with dvdnav support. You can get suitable packages [here](https://launchpad.net/~rvm/+archive).

---

### Post by binbash on 2009-01-11
> **rvm4000 said:**
> I hope version 0.6.7 will have support for dvd menus.

If you don't to want to wait until then and want to test what it has already been done:

* download the deb package for r2660 from [here](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)
* go to Preferences->Keyboard and mouse->Mouse and select "Activate option in DVD menus" for the left mouse button (so you can select the options in the menus with the mouse)
* go to Preferences->Drives and check the option "Enable DVD menus" 

Now when you select Open->DVD from drive or Open->DVD from folder, it will be played with dvd menus.

BTW, this requires a recent version of mplayer compiled with dvdnav support. You can get suitable packages [here](https://launchpad.net/~rvm/+archive).

it works quite perfect here.Thanks for the links

---

### Post by mc4man on 2009-01-11
> if you don't to want to wait until then and want to test what it has already been done:

It seems to work fairly well though has the same minor issues audio wise that a dvdnav mplayer does. (or at least in the rev's I've had (r28108 last I've tried

Basically because menus are always 2 ch. that's what mplayer starts in and won't switch to 6 ch. when the main movie starts.
If there is more than 1 audio stream in the main movie than switching back and forth once will enable 6 ch. output. (if -channels 6 is in the launch command

The only problem is when there is only 1 stream available, then there is no streams to switch to.
In those cases you have to start in the main movie. (from what I've seen

A good example would be 'No Country for Old Men'

Also the dvdnav mplayer is more susceptible to fail on some structure protected titles, starting on main movie usually solves

---

### Post by rvm4000 on 2009-02-18
Version 0.6.7 is to be released soon. Packages (svn r2787) are available for testing (hardy and intrepid):

[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

Most important changes since 0.6.6:
> 
* Added experimental (and uncomplete) support for dvd menus. Requires a mplayer build compiled with dvdnav support. Please read dvdmenus.txt to know how to enable it.
* Now loading an external subtitle file doesn't require to restart the mplayer process (except for idx/sub subtitles).
* (Playlist) When a file is added to the playlist, if it was already in the list, it's moved to the end of the list.
* Options for mplayer: finally spaces in arguments between quotes are handled properly.
* Added two options (in the audio and subtitle menus) to allow the user to enter the audio and subtitle delay (in milliseconds).
* (*** subtitles) The outline and shadow options now accept values with decimals.
* Now the default value for the "correct pts" option is auto.
* Now the default cache for files is 0, as it seems setting a cache cause problems with some formats (like mp4 and mov).


---

