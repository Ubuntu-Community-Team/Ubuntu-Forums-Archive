---
title: "flash sound"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Moosferatu on 2006-06-02
I'm having trouble with getting sound from flash videos in Firefox.  It usually doesn't work at all, but if I restart the computer and immediately try again it works.  Anyone else have trouble with flash movies?

---

### Post by DarkStarDeity on 2006-06-02
Yes, and the fix as described in [this thread]("http://ubuntuforums.org/showthread.php?t=187207") of installing alsa-oss fixed the problem. However, I found that I had the problem described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=89827") that flash was causing Firefox to freeze on some sites (usually games), and I found that the fix described there (installing arts) worked to fix both problems. So there are two things I know that you can try, either might work for your situation. 

If you're on Dapper, you need to modify the instructions in the second thread slightly -
flashplayer-mozilla is no longer recognised, it's now flashplugin-nonfree
and the Firefox rc file is now in /etc/firefox/firefoxrc

---

