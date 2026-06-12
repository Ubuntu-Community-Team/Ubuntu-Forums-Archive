---
title: "No colour in video playback"
date: 2008-06-21
forum: Multimedia Software
---

### Post by TMC on 2008-06-21
This is a problem I've had for a while - when I playback any video, whether from a file or a DVD, the playback is monochrome only.  This happens whether I use totem, vlc or mplayer.  The problem was solved - temporarily - by nuking the hard drive and reinstalling Ubuntu 8.04 (note:  I had a lot of other problems as well, I didn't nuke the HD just to get colour back in my video, that was just a lucky side-effect.)

Anyway, a short while after reinstalling, the colour went away again.  I have tried apt-get purge and reinstall of all video related files, but this has made no difference.

Can anyone suggest anything else I can try to get my colour back?  I really can't face reinstalling the system just to reset this.

Many thanks,

David Shaw

---

### Post by Pjotr123 on 2008-06-21
I'd disable the visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )


Plus: make sure you've got 100 % multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will probably help.  :-)

---

### Post by TMC on 2008-06-21
Thanks for coming back to me on this - unfortunately, it hasn't worked.  I still have monochrome video playback  :-(

Any more ideas what I can do?

David

---

### Post by mc4man on 2008-06-21
you could ck. thru here several possible solutions
[http://ubuntuforums.org/showthread.php?p=5035483#post5035483](http://ubuntuforums.org/showthread.php?p=5035483#post5035483)

---

### Post by TMC on 2008-06-21
Many thanks, mc4man, changing the hue/contrast/saturation/brightness in totem did the trick  :-)

What I don't understand is how they got changed in there as I have vlc set to do everything video related - and changing those settings in vlc made no difference  :-S

Anyway, now I know how to fix it, I'm happy  :-)

Again, many thanks,

David

---

### Post by mc4man on 2008-06-21
> What I don't understand is how they got changed in there The link out from the thread I gave you mentions a bug in nvidia drivers. 
If that's what you have as a video adapter then stay away from totem-gstreamer. I believe installing totem-xine and setting it as the default totem player may help. At bottom of this post if interested
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

