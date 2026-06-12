---
title: "Help! Video stopped working in Lucid"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Biddlesby on 2010-05-03
Hi All,

I upgraded to Lucid, but now my video has stopped working...

YouTube and iPlayer work fine. The problem is with any videos (mp4, flv) opened in VLC or mplayer. I can hear sound fine but the screen is black. The same happens in Skype.

I followed the comprehensive guide and did all the steps, but no joy. Any ideas?

Thanks!

Harry

---

### Post by Biddlesby on 2010-05-04
[Found a solution](http://www.linuxquestions.org/questions/linux-software-2/vlc-wont-play-video-with-compiz-running-548270/):

Tools > Preferences > Video and  change the output to X11.

---

### Post by schnekri on 2010-05-21
I am having the same issue with Skype. Have you found a solution?

---

### Post by ticket on 2010-08-08
I had same problem - mplayer not playing mp4.

Then I found that sometimes it worked.
Investigating, mplayer was using the vdpau setting. For some reason, this isn't 100% reliable on my rig (but nice when it does work) - Lucid 10.4.

So for now I have switched back to using the XV setting (better performance than the X11 setting).

XV is 100% reliable on my rig.

SOLVED:
   Finger trouble here - vdpau was never working on 10.4.  But doing this fixes it:
   Use synaptic to install the package
               libvdpau1
   This apparently fixes a broken library link.
   See: 
       [http://ubuntuforums.org/showthread.php?t=1505854&highlight=lucid+mplayer+vdpau](http://ubuntuforums.org/showthread.php?t=1505854&highlight=lucid+mplayer+vdpau)
       [http://ubuntuforums.org/showthread.php?t=1473257&highlight=lucid+mplayer+vdpau](http://ubuntuforums.org/showthread.php?t=1473257&highlight=lucid+mplayer+vdpau)

    Just install the package - no need to fix any links manually.

---

