---
title: "DVD playback"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Mr_Knuckles on 2008-06-14
I'm having problems with DVD movie playback. Apparently my system mounts the DVD, as the icon pops up on the desktop, but when I try to watch the movie it says "an error occoured, cannot read from resource". I can browse the the DVD files, so this is most likely a problem with totem. I have no clue on why, or how to begin troubleshooting. =/ Help?

My system is a Gateway c-141 XL convertible running Ubuntu 8.04 with a 8x Multi-Format Dual Layer DVD-RW with DVD-RAM. Don't really know if this is relevant.

---

### Post by mc4man on 2008-06-14
Why don't you run thru this and then ck. playback. Will also add vlc - you may like it better as player. If after you don't have playback start vlc from the terminal and post any error messages
[http://ubuntuforums.org/showthread.php?t=828342](http://ubuntuforums.org/showthread.php?t=828342)

---

### Post by rodo-&gt;dave on 2008-06-14
I had this problem so I ran this command and it fixed it:
> 
sudo /usr/share/doc/libdvdread3/install-css.sh


---

### Post by Lantesh on 2008-06-15
Have you installed the ubuntu-restricted-extras package?  If not that should be your next step.  Do that and things will probably work.  If you still have trouble you will want to add Medibuntu as a repository, and then install libdvdcss2.  If you aren't sure how to do any of this run a search on the forums here, and you will find plenty of tutorials.  Good luck.

---

### Post by Mr_Knuckles on 2008-06-15
> **mc4man said:**
> Why don't you run thru this and then ck. playback. Will also add vlc - you may like it better as player. If after you don't have playback start vlc from the terminal and post any error messages
[http://ubuntuforums.org/showthread.php?t=828342](http://ubuntuforums.org/showthread.php?t=828342)


Thanks a lot, this helped.

---

