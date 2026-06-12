---
title: "Alternative to Amarok?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by GuiGuy on 2009-05-30
Hi,
It's sad they've taken out the functions in "Amacrok 2"  that made the previous version of Amarok so appealing to me; for example, it would shuffle my play list and I could then copy the music files from a right click menu to a USB storage device. It was a nifty way of preparing a randomised play list for the car's mp3 player.

So, any suggestions for an alternative player/ music file organiser? I tried Banshee, which goes close but I can't see a way to shuffle the play list or how to copy it to a USB device. 

Thanks

---

### Post by Girya on 2009-05-31
this is a bash script I wrote to create and transfer a random playlist to my mp3 player. its pretty simple, it does everything including unmount the player. It should work for you if you change the file paths to your music directory on your desktop and playlist directory on usb device. 


> #!/bin/bash
#script to generate a random playlist for export to mp3 player
rm -rf /media/disk/PLAYLISTS/random_playlist/*.ogg 
cd ~/Music
find -name *.ogg |shuf -n 50 -o ~/playlist.txt
for line in `cat ~/playlist.txt`
do 
	echo=`cp $line /media/disk/PLAYLISTS/random_playlist` 

done

umount /media/disk

---

### Post by konqueror7 on 2009-05-31
have you tried Exaile, seems to me a Amarok clone...:D

---

### Post by Fluffy13 on 2009-06-01
> **konqueror7 said:**
> have you tried Exaile, seems to me a Amarok clone...:D

Wow, great suggestion. I'm done trying to get Amarok working right. Thanks :)

:popcorn::p

---

### Post by rob1408 on 2009-06-01
Why don't you just uninstall Amarok 2 and install Amarok 1.4 ?  I messed about with various players after trying Amarok 2 and I couldn't settle on any, I now have 1.4 installed and it's perfect.

---

### Post by GuiGuy on 2009-06-01
> **Girya said:**
> this is a bash script I wrote to create and transfer a random playlist to my mp3 player. its pretty simple, it does everything including unmount the player. It should work for you if you change the file paths to your music directory on your desktop and playlist directory on usb device.

Thanks for the snippet. I'd already hacked a little Delphi application (under windows) together to do something similar. But the script is neat. 

**Makes mental note:** must get into linux programming, if only it had a decent RAD platform. ;)

Cheers

---

### Post by MichaelSammels on 2009-06-01
However, if you do not need the functions for copying to a USB stick try mocp :)

---

### Post by bgiannes on 2009-06-01
Yep amarok ver 2 should have been called .9beta haha, just joking!

amaork was/is being rebuilt from the ground up.  


the way the new one works is different, but it's still better the others, (that is with big libs mysql is a must)...

upset about musicbrainz being dropped... (but amaorks version did do some funny stuff sometimes).  


fyi see this [http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html#comments]("http://amarok.kde.org/blog/archives/809-Missing-features-in-Amarok-2.html#comments")

Features that will likely return in Amarok 2


Visualizations

Equalizer

**USB mass storage devices support** 

Crossfading

Stop after this track

Queue feature

Dynamic Collection

Cue file support

Collection statistics

Playlist sorting

Showing new tracks in collection

Labels

ReplayGain




Features which have been dumped. Good riddance!


Old style playlist, "Excel Look"

Support for Amarok 1 scripts

Multiple databases (SQLite and PostGreSQL)

Player Window (this can be implemented as a Plasmoid)

MusicBrainz (we have plans for something better)

Slowness with large collections *grin*

---

### Post by tex001 on 2009-06-01
If you try to synchronize meta-data between the music players, you could take a look at [bifroest]("http://developer.gauner.org/bifroest/").

---

### Post by aeiah on 2009-06-01
i think a lot of the main music players (amarok, exaile, rhythmbox, banshee) will let you treat a usb drive as a portable mp3 player. that should enable you to export things directly. ubuntu will see a mass-storage-device mp3 player the same as it would see a regular usb drive.

---

