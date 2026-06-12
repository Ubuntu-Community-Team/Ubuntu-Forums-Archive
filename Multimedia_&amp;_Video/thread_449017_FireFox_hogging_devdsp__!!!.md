---
title: "FireFox hogging /dev/dsp  !!!"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by vronp on 2007-05-19
Hi all,

Running Feisty here.

In general, my sound setup works.  However, Firefox seems to grab hold of /dev/dsp when I go to YouTube or something similar and I can't use Skype.

I am getting this error in my terminal window:

/dev/dsp: Device or resource busy

Also, in Skype I get:

Problem with sound device.

This can be fixed by killing Firefox.

Please note, that it's only when Firefox is playing a flash movie or something like that.  Even after I kill that tab, it's still got a grip on /dev/dsp

Any ideas?

thanks

---

### Post by strungoutfan78 on 2007-05-28
I'm having the exact same problem.  It also happens with email notifications in Thunderbird.  The videos will play fine in swiftfox for a while but like you said it eventually grabs hold of /dev/dsp and all sound is gone.  Sometimes I can fix it by restarting the sound server, but generally I have to kill swiftfox/thunderbird, whichever one it was that caused the lock-up.

---

### Post by strungoutfan78 on 2007-05-30
I've noticed that in my case it seems to be the FoxyTunes plugin thats doing it.  If I open ksysgaurd and look at th e process table there are several instances of "**FoxyTunesDCOP**".  By killing the multiple instances it instantly frees up my system.  I've yet to pinpoint exactly when or why it does this.

---

