---
title: "MP3 and DVD problems"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by bg1256 on 2007-07-20
I know there are several threads about this, but I am suddenly having problems after having mp3 and dvd support on this machine for several months now.

I previously installed the codecs, etc. using Automatix; however, today when I attempted play an mp3 in Amarok, it said mp3 support was missing.  So, I thought I'd remove Automatix and attempt to install mp3 support following the instructions in the official documentation.  So, I uninstalled everything I had installed in Automatix and followed the instructions to the letter.

However, Adept Package Manager will not allow me to install libdvdcss2.  I click on it and select install, and it simply won't let me.

I also installed every relevant codec, and I am still unable to play mp3's in any media player.

If anyone knows of anything I might be overlooking, I'd love to hear it.

Running Kubuntu Feisty.

Thanks!

---

### Post by benx009 on 2007-07-20
do u have the [repos at medibutu]("http://medibuntu.sos-sts.com/") enabled?  that's where i installed libdvdcss2 from.  if u've been using automatix for months up to this point, then it's only to be expected that problems might occur from uninstalling it...

---

### Post by kngunn on 2007-07-20
Try cleaning out packages that were installed previously to satisfy dependencies:

sudo apt-get autoremove

Sometimes that's fixed re-install problems for me.

---

### Post by bg1256 on 2007-07-20
I've now added the medibuntu repos... thanks for pointing that out to me.  That allowed me to install libdvdcss2....

But, I'm still not sure what's going on with mp3 support.

I have the lame pacakges installed, the gstreamer packages installed, as well as the ubuntu restricted package.  I'm clueless on that one... and it just seemed to stop working. I don't know that I installed anything that should have changed it...

---

### Post by bg1256 on 2007-07-20
> **kngunn said:**
> Try cleaning out packages that were installed previously to satisfy dependencies:

sudo apt-get autoremove

Sometimes that's fixed re-install problems for me.

Yeah... I did that.  But then it uninstalled so much that I did not, such as flash, java, and dvdauthor.  I went ahead and reinstalled those, though.

Thanks for the speedy responses.


I still can't seem to get mp3 support... And I've installed all the pacakges that would be relevant... maybe I should resort to Automatix again.

---

### Post by benx009 on 2007-07-20
hmmm, if i were u, i would try completely removing amarok and then reinstalling it again if u haven't done so already.  srry i can't help out much here, mp3 support was never much of a problem for me.... but if that doesn't work, then, yh, probably best to give automatix another shot...

---

### Post by stmiller on 2007-07-20
Automatix is bad and not recommended. Have you searched for all of the good, bad, and ugly codecs?

---

### Post by bg1256 on 2007-07-20
> **stmiller said:**
> Automatix is bad and not recommended. Have you searched for all of the good, bad, and ugly codecs?

I sure have, and they are all installed... which is strange methinks.  I could remove and purge amarok, but if that doesn't work, I guess I can only assume Automatix borked my system...??

---

