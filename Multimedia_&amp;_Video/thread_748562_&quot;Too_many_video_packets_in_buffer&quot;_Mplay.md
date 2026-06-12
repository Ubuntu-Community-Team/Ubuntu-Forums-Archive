---
title: "&quot;Too many video packets in buffer&quot; Mplayer"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by Kenjitamura on 2008-04-07
Although no one has ever responded to one of my posts on this forum what the hell i'll give it another try.  The forum has this problem posted a few times with no helpful support.  Googling it just comes up with people getting the error while trying to watch DVD's.  I'm trying to watch a 1280x720_h264 .mkv.  I have to play my videos under OpenGL because in Xv the colors are swapped and going into gstreamer-properties and trying the custom output fix doesn't change it.  Mplayer keeps giving the error "Too many video packets in the buffer" and VLC shuts down on its own.  VLC is crap so I don't want to rely on it anyway.  In totem the playback is very slow and I can't figure out how to change the output to Opengl because the .gnome2/totem config file isn't in Hardy.   Running Hardy 64 bit.  System specs are AMD 9500+ Quad Core, 4 gb DDR2-800, Nvidia 8800 GT with 169.12 drivers.  Direct Rendering does work.

---

### Post by Het Irv on 2008-04-07
If you were to try to play the movie after restarting your computer (i.e. clearing your RAM), would you get the same error?  Can you change the size of Mplayer's buffer?  I am not in Ubuntu and don't know Mplayer that well, but I think it has something to do with RAM and Mplayer.

---

### Post by cor2y on 2008-04-07
To fix your color output launch totem and go to Edit->Preferences->Display tab and adjust the Hue settings either all the way to the left or right (maximum or minimum) that should get your color settings back to the correct option, its the nvidia driver hue settings its been swapped you only get this problem if its the closed drivers , the open source ones are set correctly.
Set your video output back to xv and now hidef video playback should work without that error, you certainly have the hardware for it.

---

### Post by beefcurry on 2008-07-23
I get this problem running mplayer in openGL and xv.

Totem plays videos really slowly and sometimes refuses to work, I have long since lost hope in it as a media player.. but not mplayer is running into problems.

I never had this problem before but I did a fresh install of Hardy before this came up, I am using the nVidia restricted drivers.

Any ideas whats wrong?

---

