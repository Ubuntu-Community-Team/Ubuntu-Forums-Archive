---
title: "trouble playing dvd's, scrambled?"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Kilarin on 2007-11-08
I'm using Ubuntu 7.10  on an 
HP Pavilion a1600n AMD Athlon 64 X2 Dual core Processor 3800+ 2.00 GHz
1024MB of Ram,  NVIDIA GeForce 6150LE graphics card

I'm using the restricted NVIDIA accelerated graphics driver.  I have visual effects set to NONE right now due to the problem I addressed in [this thread](http://ubuntuforums.org/showthread.php?t=585672).

I can download and play video's from the net just fine.  But when I try to play a DVD, I get this:

[[IMG]http://img215.imageshack.us/img215/8225/screenshotdvdkr5.jpg[/IMG]](http://imageshack.us)

Note: I don't get the normal DVD "chapter headings/play/special features" menu at all, it just goes right into playing the first show.

The Audio is hinky as well.  But you can make it out enough to identify the episode and that the actor commentary is on for some reason.  You can make out a little bit of the action going on in the vid, and every so often part of a picture will suddenly flash through clear for just a fraction of a second.  But it generally looks like the above.

I tried this in Gnome MPlayer, and plain old MPlayer.  Results are identical.  Totem just says it doesn't have the right plugins to be able to read from the disk.

Am I hitting some kind of copy protection scheme?  I can boot to windows and play this DVD on my computer just fine.

Thanks!

---

### Post by Fire_Chief on 2007-11-08
It's most likely a codec issue. See these links for more info.
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

You may want to try VLC. I've never had it fail yet.```
sudo apt-get install vlc
```

---

### Post by Kilarin on 2007-11-08
thank you for the reply!

VLC does attempt to run the dvd menu, but the result looks just like the MPlayer results.  All blocky and scrambled.  BUT, the [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) link you suggested led me to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) which had the fix!

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Thank you VERY much, I'm up and running now.  I appreciate the help!!!!!

---

### Post by ceo51378 on 2008-04-28
I am having the exact same issue with both "Movie Player" and VLC. I am running Hardy on a Dell D620 w/2 gigs RAM.  I had no issues with Gutsy.

---

