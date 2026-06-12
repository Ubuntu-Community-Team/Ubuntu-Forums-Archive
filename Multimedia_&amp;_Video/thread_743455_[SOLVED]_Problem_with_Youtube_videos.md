---
title: "[SOLVED] Problem with Youtube videos"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by bobbo85 on 2008-04-02
Videos will not play for me on firefox 3 beta 4 at youtube.

Using Gnash:  The video just doesn't load.  There is no error, just no video (not even a black box).

Using adobe non-free:  The video loads, the progress bar fills, and then about 1 second of video plays (no audio) before suddenly "pausing."  I can click on other parts of the video in the seek bar, and again about 1 second of video plays before coming to a halt.

As of now I have uninstalled Gnash altogether.
I have also reinstalled firefox, adobe non-free, and libflashsupport.

Any ideas?

---

### Post by warp99 on 2008-04-02
The beta has the same problem with me except the video will randomly freeze with the Adobe plug-in. Firefox 3 beta 5 just came out. See if that helps since there is suppose to be over 750 fixes from beta 4:

[http://www.mozillazine.org/talkback.html?article=23141](http://www.mozillazine.org/talkback.html?article=23141)

---

### Post by bobbo85 on 2008-04-02
You're right warp99, I tried firefox 3 beta 5 and youtube videos worked just fine again!  Of course, none of my add-ons work and I can't live without them!

One question i've always had about ubuntu and youtube:  whenever I try to go full screen, the video gets really choppy and goes out of sync with the audio... any ideas what that is from?  Normal sized is perfectly smooth and stays in sync...

---

### Post by warp99 on 2008-04-02
You can fix that by turning off compatibility mode off. 

Type about:config in the url and look for 'extensions.checkCompatibility'. If it's there change that to false, if not create the entry with a right click then choose Boolean, add the 'extensions.checkCompatibility' entry, then choose false. Restart Firefox.

Most of your plug-ins will work, but be warned it's a hit and miss thing. As far as the Flash plug-in and Ubuntu I have no idea since I use KDE (Kubuntu).

---

### Post by bobbo85 on 2008-04-02
Perfect!  Well, none of my plugins worked, but the one that I can't live without (fire gestures) I found a replacement for - all in one gestures works :-)  Thanks warp99

---

