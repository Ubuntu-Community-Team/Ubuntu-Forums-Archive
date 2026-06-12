---
title: "Amarok doesn't play, then crashes"
date: 2008-05-12
forum: Multimedia Software
---

### Post by alex.house on 2008-05-12
Hey,
recently got annoyed at Vista Business and installed Ubuntu 8.04 since it just works and doesn't require horribly fiddling to get VPNs to work.

Aaaaaaanyway, a friend highly recommended Amarok as it's apparently very easy to get to work with Last.FM and Audioscrobbler. I tried using Audacious and Rhythmbox but couldn't get Last.FM to work - things just wouldn't Scrobble!
Installed Amarok alright alright with no problems but for some reason it just doesn't play any tracks. It loads up okay and gets to the main screen, but when I try to play a track it starts off acting as if it is playing, but doesn't.... and then when I try and pause/stop/restart/etc, it freezes up.
Any thoughts?


This is what I get in the terminal when started:
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809cc30 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809cc30 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
alex@NOSTRADAMUS:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
```


Bit of a newbie when it comes to this kind of thing!
Cheers for any help



**Edit** No idea what changed...but it now works :-/

---

### Post by ZAxisMapping on 2008-06-25
I'm having an identical problem.  I'm having trouble figuring out exactly what's going on.  I'm thinking about compiling from scratch with full debug...but I don't have the time to do that now.  Let me know if you find a work around.  Thanks...

---

### Post by ZAxisMapping on 2008-06-25
More specifically, this is what I'm seeing:

```
$ Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/user/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/user/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bfb8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bfb8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Could not write data
kio (KLauncher): ERROR: SlavePool: No communication with slave.
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.

```

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Use vlc player next time. It doesn't have major problems like amarok and audacious with getting streams from net. Pity xmms is not longer supported by Ubuntu. Great audio app. Xmms2 is just unfinished program imho.

---

### Post by lucthegreat on 2008-07-05
It seems that I have the same problem. It displays the track information as if it's going to play, and the bar at the bottom (I don't know what it would be called) starts moving as if it's playing music, but always freezes within a second or two. When it worked for me, Amarok was wonderful, and if there's anyway of fixing it I would love to be able to stick with Amarok. If anyone finds a fix, please let me know.

Thanks

---

### Post by justin whitaker on 2008-07-05
Amarok scrobbles. 
Banshee scrobbles. 
Rhythmbox also scrobbles. 
MPD scrobbles.

I wish Pandora had an open API so we could Pandora too. :)

---

### Post by aimaz on 2008-07-10
I'm having this problem as well.

Terminal output:
```
$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d030 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d030 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
stephen@sprocket:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c0009a
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )

```

Rhythmbox is also failing to play music but there are no messages output to the terminal. So I'm guessing the problem is something that is common between the two. The same file works fine being played by mpg123.

Any clues on this one would be appreciated.

---

### Post by konungursvia on 2008-07-10
I would try quickly stopping amarok when it runs, then clearing the playlist, and try building another playlist, first making sure the drives the files are on are cleanly mounted.

---

### Post by aimaz on 2008-07-10
In another thread it suggested telling Amarok to use ALSA explicitly.

I tried that and it fixed amarok.

To fix rhythmbox I used gnome-sound-properties (System->Preferences->Sound) to set ALSA as the default playback plugin. Everything seems to be working now. So I guess I was having a problem with pulseaudio and autodetect was trying to use that one.

---

### Post by sur on 2008-07-12
I had the same problem even when the system's sound preference was set to use alsa. 

I got it fixed by setting amarok's sound output to alsa.
Do it as like this...

[B]
Settings -> Configure Amarok -> Engine -> Output Plugin(select alsa from dropdown)
[/B]
don't forget to press 'Apply' button.


Thanks.


Sur
[http://expressica.com](http://expressica.com)

---

### Post by ZAxisMapping on 2008-07-17
Looks like this did the trick for me as well.  Many thanks!  

So frustrating, considering it worked perfectly before updating (just like my imac aluminum keyboard - one step forward, two steps back - still working on getting this going correctly).

---

### Post by suavemart on 2008-09-15
Worked for me too, thanks.

---

### Post by mooredar on 2008-09-15
This worked for me as well

---

### Post by alexebird on 2008-10-10
This problem has been killing me!  Thanks for the fix.

---

### Post by almozavr on 2009-11-03
**Amarok** won't play (you'll hear no sound) on Ubuntu without **xine1-ffmpeg** library installed
It could be simply installed from synaptic ;)

---

### Post by Noob4Ever on 2010-02-08
> Amarok won't play (you'll hear no sound) on Ubuntu without xine1-ffmpeg library installed
It could be simply installed from synaptic 
worked like a charm. thanks a lot!

---

### Post by mishkind on 2010-03-12
> Settings -> Configure Amarok -> Engine -> Output Plugin(select alsa from dropdown)


THANK YOU!
This worked for me on ubuntu 8.04 and amarok 1.4.9.1 (using KDE 3.5.10).

---

### Post by kio_http on 2010-03-21
Try updating to the [latest Amarok release.]("http://www.kubuntu.org/news/amarok-2.3.0") 

Also: Have you installed the multimedia codecs?

---

### Post by dimk1 on 2010-12-15
Amarok crushes for me in 10.10. Here is what i get

KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/mimis/.kde/socket-mimis/kdeinit4__0

Any ideas?

---

