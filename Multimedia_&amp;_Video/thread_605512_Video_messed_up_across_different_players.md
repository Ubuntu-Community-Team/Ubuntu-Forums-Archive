---
title: "Video messed up across different players"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Sukarn on 2007-11-07
Take a look at these screenshots. The first one shows a screenshot taken from within totem, and the second one shows how the video actually appears on the screen. Changing the media players has no effect, whether I use mplayer, totem (xine) or vlc.
I have the same issue across the different formats that I have (avi, mpg, rmvb).
Could anyone help me out with what I can do to fix this issue?

Screenshot taken from within totem - [http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu-problems/Video1.png](http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu-problems/Video1.png)
How it appears on screen - [http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu-problems/Video.png](http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu-problems/Video.png)

Gutsy Gibbon (7.10) user.

---

### Post by Fire_Chief on 2007-11-08
Looks like a codec problem. You'll probably need to install the w32codec package. Here's some more information
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")

---

### Post by Sukarn on 2007-11-09
Thanks for the reply. It seems like this is caused by a bug in the newer nvidia drivers.

[http://ubuntuforums.org/showthread.php?t=594351](http://ubuntuforums.org/showthread.php?t=594351)
[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)
[http://ubuntuforums.org/showthread.php?t=597618](http://ubuntuforums.org/showthread.php?t=597618)

---

