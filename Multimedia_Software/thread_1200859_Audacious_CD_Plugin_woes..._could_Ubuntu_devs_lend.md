---
title: "Audacious CD Plugin woes... could Ubuntu devs lend a hand?"
date: 2009-06-30
forum: Multimedia Software
---

### Post by DancemasterGlenn on 2009-06-30
Recent development in the Audacious player has seen the player's stability and feature-set increasing by leaps and bounds. However, there is one area in which Audacious is not yet working properly: the playing of CDs.

Note: I have audacious selected in this case to handle cd audio in the "media handling" options pane.

The ideal behavior:
1) insert cd
2) audacious opens automatically (if not already open), and auto-adds/plays the cd with proper track names (generated from the cddb plugin)

The current behavior:
1) insert cd
2) audacious opens automatically, and does begin playing tracks properly. However, cddb info is not properly retrieved on auto-add: the tracks show up as wav files (see attached picture). The strange part about this is if the playlist is cleared and the cd added manually (right click->"plugin services"->"add cd"), track names are properly generated. Something about the auto-play behavior seems to be screwing up the data retrieval.

I filed a bug report on the audacious page (see [here]("http://jira.atheme.org/browse/AUDPLUG-28")). Unfortunately, none of the developers are running an Ubuntu machine, but here's what they had to say:
> The problem is that Ubuntu is wanting Audacious to play the CD through GVFS, which we don't support. I don't run Ubuntu, but apparently GVFS makes the files show up to Audacious as virtual .wav files. So they get played by not by our audio CD plugin but by our sndfile plugin, which doesn't know a thing about CD's. If Ubuntu can be configured not to run a specific command (such as "audacious2 cdda://") instead of using GVFS when a CD is inserted, we can support that.
So from this, it seems that the combination of Ubuntu's GVFS and Audacious' sndfile plugin are the culprits. Compiling Audacious without said plugin doesn't help much... it breaks auto-add, though auto-start and manual CD add still work as they did before.

So I guess the question is, can anything be done on either the part of the way the player is coded, or on the part of the Ubuntu code to rectify this issue? This is one of the only problems with Audacious at this time, and if anything can be done to make it run more smoothly it will benefit all users. If any Ubuntu developers can lend a hand with finding a workaround to this issue, please do post here, or better yet (so that I don't need to be a go-between quite so much), check out the bug that was filed on their page, which I previously linked to. I'll update this if I forgot anything important, or new discoveries are made.

Thanks in advance!

---

### Post by mc4man on 2009-06-30
Audacious 1.5 can be set up for true autoplay with proper track name, info ect., will have to install 2.x later and test.

While I normally use amarok (which also can be set up for true autoplay from **any** drive), I have a fresh install of hardy, so I gave aud a quick try.

The only difference from amarok is aud. will only autoplay from the default drive, the idea is basically the same.

The method for hardy is a bit more involved, in intrepid and I'd imagine jaunty a step or 2 could be removed.

If you set up the 'event' (inserting an audio cd) to call a script instead of a command or the default audacious.desktop then it will work perfectly.
 In other words the default for audio cd's should be the script, not the player (at least in aud 1.5
 
The simple script for aud.

```
#!/bin/bash
audacious -E cdda://

```


.............................................................................................

The slightly more involved hardy method, I make life easy by creating a bin folder in home and adding to PATH, that way just the name calls the script. (named the script audcd

```
cp /usr/share/applications/audacious.desktop ~/.local/share/applications/audacious-cd.desktop


```

```
gedit ~/.local/share/applications/audacious-cd.desktop
```

Changed the name to Audacious Cd Player
Changed the Exec= to Exec=audcd  (or if no ~/bin in path then Exec=/path/to/scriptname

Either browse to mimeapps.list or 
```
gedit ~/.local/share/applications/mimeapps.list
```

(if it vcomes up empty then the list needsto be created, easy to do

find this line 
x-content/audio-cdda= 
and add audacious-cd.desktop; to it, either at end or at front (first listed is default, no spaces in line, all .desktops end with a ;

Ex

```
x-content/audio-cdda=audacious-cd.desktop;rhythmbox.desktop;soundjuicer.desktop;
```

Then a log out and log in and aud will autoplay cd's, will be added as a right click choice on audio cd icon and Audacious Cd Plattyer will be a menu item in Sound & Video

(did have to go into ~/.config/audacious/config and set "shuffle" to false so it would start on the first track.

Edit
What the audacious-cd.desktop looks like

> [Desktop Entry]
Name=Audacious Cd Player
GenericName=Audio Player
Comment=Play music
Comment[hu]=Zene lejátszása
Exec=audcd
Icon=audacious
MimeType=application/x-ogg;audio/mp3;audio/mpeg;audio/mpegurl;audio/prs.sid;audio/x-flac;audio/x-it;audio/x-mod;audio/x-mp3;audio/x-mpeg;audio/x-mpegurl;audio/x-ms-wma;audio/x-musepack;audio/x-s3m;audio/x-scpls;audio/x-stm;audio/x-wav;audio/x-xm;application/ogg;audio/x-vorbis+ogg
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application



---

### Post by DancemasterGlenn on 2009-06-30
Thank you for the reply. It'll take a while to wade through it... am I correct in thinking this is all based on 1.5? 1.5 did work for me at one point, if I remember correctly, but recent changes were made to (I believe) both the Audacious cd plugin, and the way new versions of Ubuntu handle cds. If your ideas do work with the current beta of Audacious, in Jaunty, you will have effectively solved the problem (I think...).

---

### Post by mc4man on 2009-06-30
Tried aud2, no good on that command. The **change seems to be in aud itself**, 1.5 can autoplay properly in 8.10 as described and I'm pretty sure on 9.04 also.

Too bad they don't have a command similar to amarok 1.4's --cdplay (the --cdplay is gone in amarok2, never had it installed long enough to try 2.x for autoplay.
(if so probably for only one device


edit
> The problem is that Ubuntu is wanting Audacious to play the CD through GVFS, which we don't support. 

Well they do on 1.5, so it's not totally an ubuntu 'issue', maybe there's a workaround to aud2.x, maybe not. 
Maybe they can create a working command, maybe not, maybe they don't care to.

---

### Post by mc4man on 2009-07-01
> maybe there's a workaround to aud2.x

Note this was on the audacious-plugins-2.0.1 (got several wks. ago

So a temp workaround is to replace audacious-plugins-2.0.1/src/cdaudio-ng/cdaudio-ng.c with the same file from the 1.5 source, then build and install the plugins package. (easy way is to do a 

```
sudo checkinstall --fstrans=no --install=no
```

and then just "re-install" the package

Tested and working fine from Aud2.0 in 8.10

the only change (other than working right), is the plugin service shows 
"rescan cd" and "add cd" (to the extent I've looked at, seems good to go

used this as script, no change other than 2
```
#!/bin/bash
audacious2 -E cdda://
```

The only other different from prev. is
 ```
cp /usr/local/share/applications/audacious2.desktop ~/.local/share/applications/audacious2-cd.desktop

```

ect.

---

### Post by DancemasterGlenn on 2009-07-01
Good news, as of a few hours ago the plugin has been updated to work around these issues. Most likely starting in the next beta (and now, if one wants to check the mercurial repo), the cd plugin can be properly auto-started with this similar command to yours:
```
audacious2 cdda://
```
If you stick that in as custom code for wherever the option is in Hardy or wherever to handle cds (in Jaunty, go to edit->preferences in the file browser menu and go to "media"), and you should be good to go.

mc4man, thanks for your attention and going out of your way to look for solutions. I appreciate your taking time to help look at this issue.

---

### Post by philip5 on 2009-07-09
I have (among a bunch of other updated packages) the latest 2.1.0 version (for the moment) of Audacious and the plugins pack on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

