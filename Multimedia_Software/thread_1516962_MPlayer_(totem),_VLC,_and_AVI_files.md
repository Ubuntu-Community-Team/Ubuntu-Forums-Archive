---
title: "MPlayer (totem?), VLC, and AVI files"
date: 2010-06-24
forum: Multimedia Software
---

### Post by DThurman on 2010-06-24
I have spent some time going over all advices on this forum
and the Internet and could not resolve my avi issues.

The advices in regards to video settings (and sounds)
does not include Lucid (10.4) support and certain packages
are no longer available (non-free-codecs, w32codecs, etc.)
I was able to get avi files to play on MPlayer, but not on
Totem, VLC does play avi files, but sound does not work. Attempts
to save VLC Audio Preferences hangs, does not fix the audio.

Finally, I cannot locate the menu that sets the preferred
application defaults, particularly the Video/DVD applications,
so I was forced to edit the /etc/gnome/defaults.list file, tried
replacing totem.desktop with mplayer.desktop, and it fails
with an error message: "error opening/initializing the selected
video_out (-vo) device.", and fails to bring up the video, but
plays the audio.  But manually starting mplayer and opening
the file via the menu works.  Sigh....

What can I do at this point, please?

[Fixed VLC]
  1) Fixed VLC audio: As non-root:
     # vlc --reset-config
  2) Edited as root:
     # gedit /etc/gnome/defaults.list
       ^h (Find & replace-all) totem.desktop with vlc.desktop
       ^s (save file)
  3) Issues with Totem & Mplayer still remain.

---

### Post by mc4man on 2010-06-24
First off you should refrain from making edits in defaults.list - edit the same line to many times and you will get bad behavior.

The defaults for many things are set in file management which is not enabled by default (ubuntu treats new users like they're idiots

Many ways to get to, -  2 of them
In terminal
```
nautilus-file-management-properties
```
look under media

To enable in System > Preferences menu
```
alacarte
```
highlight preferences - you'll see what to do

For files - to set an association just right click on a filetype -> properties -> open with

Some other system A/V (gstreamer) settings are available under Multimedia Systems Selector which isn't included by default
```
gstreamer-properties
```

w32codecs is still available - add [medibuntu to sources]("https://help.ubuntu.com/community/Medibuntu") or get directly here
[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

You should make the distinction between mplayer and Movie Player (totem) - not the same thing.

---

### Post by DThurman on 2010-06-26
The above information worked!
Thanks!

---

