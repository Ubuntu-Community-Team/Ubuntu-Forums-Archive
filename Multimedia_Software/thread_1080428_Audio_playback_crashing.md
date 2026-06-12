---
title: "Audio playback crashing"
date: 2009-02-25
forum: Multimedia Software
---

### Post by gurkelur on 2009-02-25
Hellew,

Ubuntu 8.04 worked like a charm installed from windows. Now, with it's own partition, I've never had so many problems.

After some hours of use, the audio disappears from videos. Even worse, no media player is able to play mp3s. Amarok freezes, mplayer freezes, exaile has the time marker set on zero, vlc gives nothing. After a restart, everything goes back to normal. For some hours, until a new restart is required.

Audio works in youtube all the way.

This is what amarok said, if it's any help:

```
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
gurkelur@comatorium:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3600004
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x380009a
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
DCOP Cleaning up dead connections.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
DCOP Cleaning up dead connections.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/gurkelur/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
DCOP Cleaning up dead connections.

```

Thanks a lot, anyone =)

---

### Post by gurkelur on 2009-02-26
I've found the cause, but not the cure =\

The audio playback for media players crashes if flash with audio has been used any time before. Even if I close my web browser after playing a clip on youtube, the media players will freeze upon 'play', and require a restart to work.

I've tried reinstalling flashplugin nonfree and restricted plugins, but it's the same as before.

I'm using a Intel Quad CPU on a motherboard with integrated audio, and it's 32bit Ubuntu.

Any suggestions?

---

### Post by markbuntu on 2009-02-26
Try this first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that doesn't work you need to go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by gurkelur on 2009-02-26
Thanks for the help, though it didn't solve my problem. 

With the PulseAudio sounddriverthing, youtube lost it's audio and some games started crashing. I changed back to ALSA and restarted.

It seems Opera is the villain. Now I tried watching youtube on firefox and switching to my media players. And they worked! But as soon as I tried watching youtube on Opera, media players would stop being able to play audio. It's such a shame. I'm gonna miss using Opera.

Should I report this as a bug somewhere? On Opera's pages?

---

### Post by markbuntu on 2009-02-27
I,m not very familiar with Opera, I only used it for a little bit, but you should check first if there is some configuration option for the sound, if there is choose alsa or pulseaudio or make sure it is using the same flashplayer. Just some suggestions.

---

### Post by gurkelur on 2009-02-27
I think I may have solved the problem.

Tools > Preferences > Advanced > Content > Plugin-in options > Change path > and leave only the mozilla plugin checked. 

Youtube videos now play only in normal quality, but media players won't crash of playing audio.

Thanks =)

Edit: Nope, it's not solved. Though it lasted much longer, and I played several youtube videos. Now, rythmbox works, and the preview player in nautilus. Amarok is still crashing, and vlc can't play mp3s or audio on film files.

---

