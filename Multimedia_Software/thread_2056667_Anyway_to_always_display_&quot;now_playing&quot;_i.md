---
title: "Anyway to always display &quot;now playing&quot; info?"
date: 2012-09-11
forum: Multimedia Software
---

### Post by MattVogt on 2012-09-11
Using any music player, I would like to always be able to see the details of the current track that is playing, without interrupting my other work, and preferably without any distracting OSD popups appearing unsolicited.

Is there any way I can configure this using Unity? Or, if not Unity, then with Gnome Fallback?

Thanks!

---

### Post by qyot27 on 2012-09-12
I doubt it.  It would require *all* (since that's what you said) of these players to support the exact same method of sending that information to the selected display point, whatever that might be.  It's not impossible that a standard API exists for this purpose, but even if one does exist, it still has to be implemented in the players themselves...and that's where it would fall apart.

The best you can get is probably targeted player-display pairs, like Rhythmbox and the panel applet that would display the info on song change (or the info replacing the program's title bar, which would cascade the info into any taskbar listing or mouse-over on an app list or dock).  Or a dedicated tool exporting the data from the program, like audtool does for audacious - audtool can be paired with Conky to display the info, and Conky is pinned directly to the desktop...as long as no program window is maximized or sitting over it, it's visible.  The screenshot says it better:
[[IMG]http://img521.imageshack.us/img521/3576/ubudesklxde20120820.th.jpg[/IMG]](http://img521.imageshack.us/img521/3576/ubudesklxde20120820.jpg)
Conky on the upper right, with the audtool info displayed toward the middle of the screen.  Conky requires tweaking a config file to get it to look like that (or to look like *anything*, actually; that's why the 'post your .conkyrc' thread exists).

---

### Post by MattVogt on 2012-09-12
Ok, I didn't mean *all* players; I meant that I would use (or at least consider using) any player that allowed me to have this functionality.

In fact there is an existing method for sending the information from the player to a third party app - the MPRIS specification, which is fairly widely supported.  So my question is really, is there some way to configure an always-visible component of the desktop that can report the current now-playing information from an MPRIS-compliant player?

Conky is interesting, but not usable for me, unfortunately, because I nearly always have a full-screen application running.

---

### Post by Merrattic on 2012-09-12
Audacious has a highly configurable OSD that can be positioned anywhere on screen and sized/coloured discreetly. It also has an indicator plugin which you can hover over to see the current track.

---

### Post by shantiq on 2012-09-12
hi Matt


well cueinfo on [**xmms**]("http://ubuntuforums.org/showthread.php?t=1525072&highlight=xmms+shantiq") can be set to always on top ; but of course only for cuefiles and shows up only on wav ape mp3 aac and shn... not wv or flac   so maybe not what you are after   but some way there  [i use it a lot]




also   [and clicking the always on top ption] you can use players like **Vlc or Esperanza** [a client for [**xmms2**]("http://xmms2.org/wiki/Main_Page")]and make them really small see images below

> sudo apt-get install xmms2 esperanza xmms2-plugin-all

[CENTER]
[ATTACH]224090[/ATTACH]   save to make a nice desktop icon
[ATTACH]224047[/ATTACH][ATTACH]224048[/ATTACH]   **see post below for image of esperanza**[/CENTER]


maybe the vlc is still too big but esperanza fine-sized...

---

### Post by MattVogt on 2012-09-12
Thanks, Audacious' OSD seems usable.  Now I will see if I can live with the rest of it :)

---

### Post by MattVogt on 2012-09-12
Thanks Shantiq.  XMMS is not my cup of tea, and while VLC is great, I don't really like it as a music player.  Esperanza looks interesting, I will look at that if Audacious doesn't work out.

Thanks for your suggestions!

---

### Post by shantiq on 2012-09-12
agreed on vlc good for movies not as a music player :::]]]   alto ace as nvlc as a terminal music player



  trying a bit further with esperanza you can even have album cover showing    not bad   [Ctrl+Shift+C  to pause and play   Ctrl+Shift+V  to play next  Ctrl+Shift+X   to play previous]   those are set globally by default    best to replace for Ctrl+Alt+C etc   if you use terminal habitually  :::]]]


> Wide format support 

Play mp3, mp4, vorbis, aac, alac, wma, mac, sid, mod, wav, flac, mpc, speex, wavpack, flv, nsf, spc, nsfe, gbs, gym, vgm, sap, ay, tta and shn files.


[IMG]http://img716.imageshack.us/img716/3778/esp2y.png[/IMG]

---

