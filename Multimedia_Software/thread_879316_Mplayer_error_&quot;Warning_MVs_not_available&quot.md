---
title: "Mplayer error &quot;Warning MVs not available&quot;"
date: 2008-08-03
forum: Multimedia Software
---

### Post by skywarp04 on 2008-08-03
When ever I play a DVD with Mplayer it plays just fine, but I get a warning right after pushing play that says "Warning MVs not available".  Does anyone know what this means?  I assume that is referring to motion vectors maybe?  But why does it play fine and I don't get the same warning with other players like Kaffeine.  I use Kubuntu 8.04 by the way.  Thanks for any assistance.

---

### Post by skywarp04 on 2008-08-04
"Bump"  Anyone have any ideas? :confused:

---

### Post by rileyrg on 2008-09-21
I get the same. Also it seems incredibly difficult in gnome to get mplayer (fs)to play when I insert a video dvd. Anyone have any good pointers?

---

### Post by frankleeee on 2008-09-21
smplayer in add remove seems to work better for some media.

---

### Post by mc4man on 2008-09-21
> Warning MVs not available I've asked about that in various places and never gotten an answer. I'm guessing it means 'motion vectors'. In any event it's seems to be a harmless warning.
(started showing up with rev.'s around April this year.

> Also it seems incredibly difficult in gnome to get mplayer (fs)to play when I insert a video dvd

Can you expand upon this? Do you mean gmplayer or mplayer? (gmplayer is from the application menu, mplayer from the cli.
Are you using gnome in ubuntu or kubuntu? (see thread tag

---

### Post by skywarp04 on 2008-10-12
In my case I have mplayer.  I have also noticed that it doesn't always auto detect and play a dvd.  That problem doesn't bother me too much, just like the "MV's not available message", they are just annoyances.  I did some research though and I did find out that apparently MV stands for motion vector.  I also managed to get the message to quit appearing by using mplayer from the command line.  When you use it from there mplayer will output any errors that it encounters and mine has a scaling error of some sort for which mplayer suggests using a switch to fix. I tried it and the "MV's not available" error goes away.  Mplayer still rocks though, it's the best player for watching movie trailers on Apple's Quicktime site.  :popcorn:  Hopefully these little annoyances will be fixed in the next release.

---

### Post by mc4man on 2008-10-12
If you want to set up mplayer (technically gmplayer) to autostart and play dvd's upon inserting see here. 
Easy to set up.
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by helamsirrine on 2009-11-15
I discovered this same problem when I tried to encode a subtitled dvd with OGMRip, which uses Mencode. I tried to open a subtitled dvd with Mplayer, I get this message and my subtitles fail to load. When I tried enabling the subtitles from the menu, I get the same error and the video restarts. 

Any help here? I would like to encode my multi languge dvd's and I believe that the problem with OGMRip is linked to the Mplayer backend.

---

### Post by skywarp04 on 2009-11-15
What happens if you try playing the DVD in a different player like Xine?  I like mplayer, but for general playback I prefer Xine or VLC.

---

### Post by helamsirrine on 2009-11-15
no problems with dvd playback using vlc, I think I had some general dvd playback issues with totem, runs ok in gxine.

My only problem is with Mplayer and then only with subtitles. The problem is that my video encoder uses an Mplayer backend, and is failing to encode subtitles.

---

