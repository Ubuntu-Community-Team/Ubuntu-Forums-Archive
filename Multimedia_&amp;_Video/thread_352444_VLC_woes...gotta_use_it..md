---
title: "VLC woes...gotta use it."
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by wickstopher on 2007-02-03
Hey, there folks.  I recently had to download the VLC media player, as I couldn't get audio and video to synch up in totem-xine (or ANY other player, for that matter) when playing DVDs and even .iso images of DVDs.  VLC is the first player I've tried that actually synchs DVD audio and video (if someone could explain to me why this is, I'd love to know....even .iso images are out of synch in other programs).  Apparently I'm not the only one with this problem (see [nabble.com ]("http://www.nabble.com/--xine-Bugs-1544349---DVD---Audio---Video-out-of-sync-t3045795.html")), and hopefully they'll fix it in future versions of xine.

Anyhow, I've gone and downloaded VLC, and I really don't like it, but it looks like I'm stuck with it for now.  My question is this:  there HAS to be a way to save settings and such in VLC.  But I can't seem to figure it out.  Every time I change my settings (namely in the extended GUI, changing the gamma/brightness/contrast settings), it reverts back to the default settings after I close the program.  Very annoying to have to fine-tune gamma settings every time I start up a movie.

If anyone knows how to do this, please respond!  And I'll keep waiting patiently for a version of xine that works.  Thanks!

---

### Post by pseudonym on 2007-02-03
In VLC Settings>Settings (ie. the main settings section) there should be a "Save" button in the bottom left corner.

btw, you can also try mplayer and ogle for DVD playback (or other versions of xine like gxine and xine-ui).

---

### Post by wickstopher on 2007-02-03
Thanks for the tip!  I've tried it all...mplayer, gxine, ogle, totem-xine.  It seems to be a problem with xine itself, but I'm really not sure.

---

### Post by wickstopher on 2007-02-03
Scratch that...upon trying again, Ogle seems to be working well.  The only problem with ogle is that I can't seem to find an option for setting gamma/brightness/contrast.  Gxine, on the other hand, doesn't work (at least with .iso files) stating: "No demuxer found - stream format not recognised."

---

### Post by pseudonym on 2007-02-04
Just a tip - you're better off controlling gamma/brightness/contrast from 1. your video card driver settings utility; or 2. your monitor. The controls which exist in some applications can be unreliable.

FWIW, I have no problems with xine (gxine and xine-ui) for DVD playback. Verify that you have the packages 'libxine-extracodecs' and, for good measure, 'libxine-main1' installed.

---

### Post by wickstopher on 2007-02-04
I have both installed, and it still doesn't work.  Also, I'm not sure how to access my video card settings, but I have my monitor and xgamma configured the way i like it, but video ends up extremely dark without configuring gamma, brightness and contrasts settings from within a program.

---

### Post by pseudonym on 2007-02-04
If you have an Nvidia card you can use the 'Nvidia Settings' utility which comes with the binary driver from nvidia.com, if you're using that driver. A menu entry should have been created, but if not, just type 'nvidia-settings' from the terminal.

ATI drivers have a similar utility, I'm sure. And Matrox has 'Powerdesk', the Linux version of which is in the Ubuntu repositories IIRC. I don't know about other cards.

---

