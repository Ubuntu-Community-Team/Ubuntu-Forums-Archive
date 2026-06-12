---
title: "strange parole behavior and one remaining problem"
date: 2014-05-02
forum: Multimedia Software
---

### Post by il lupo on 2014-05-02
Hello, All--

i've upgraded to xubuntu 14.04 and installed Ubuntu Studio underneath.  Things are finally near where i had them in 12.04, but for a few things.  It took some searching, but i finally got parole to make sound and play DVD's.  The DVD's were a matter of getting the correct packages.

The sound was a little trickier.  My computer has the regular sound card and an NVidia card for hdmi output.  When I opened pavucontrol with parole running, i saw that parole was using my NVidia card.  While my built-in analog-stereo card was listed as an option, parole would not make the switch when i opted for it.  In the Configuration tab, i turned off the NVidia option.  Now i have sound, even after a reboot.  i turned the NVidia card back on, and while i still have sound, now parole won't let me choose NVidia for output.  What is going on, here, and how can i learn more about it?  Also, could this be as simple as the fact that i've also installed vlc, and parole and vlc don't play well together (even though they did in 12.04)?

Finally, i cannot play CD's--at least, from the drop-down menu underneath Media.  If a track from a CD makes it into the playlist, then parole will access the CD.  In the first instance, i get something like "Gstreamer backend error:  cannot handle stream CDDA URI."  That's close, if not exact.

i hope that was clear.  i look forward to everyone's suggestions.  Take care.

bill

---

### Post by Yellow Pasque on 2014-05-02
I assume you have the appropriate plugin package installed for gstreamer CD? (gstreamer1.0-plugins-ugly)
```
$ gst-inspect-1.0 cdio
Plugin Details:
  Name                     cdio
  Description              Read audio from audio CDs
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcdio.so
  Version                  1.2.4
  License                  GPL
  Source module            gst-plugins-ugly
  Source release date      2014-04-18
  Binary package           GStreamer Ugly Plugins (Debian)
  Origin URL               http://packages.qa.debian.org/gst-plugins-ugly1.0

  cdiocddasrc: CD audio source (CDDA)
```

---

### Post by il lupo on 2014-05-02
Yes, Juan, they are.  However, gst-inspect-1.0 cdio only returned that "cdio" was an invalid option.  Aptitude search returned that i have ugly plugins installed from both the 0.10 and 1.0 sets.

Unfortunately, i have to start a busy weekend.  i may have some time, tonight, after teaching.  i may get rid of vlc and start over with parole.  After updating and copying my old files back into /home, some older, incompatible configuration settings may have started the conflict.  Perhaps simplifying and beginning again will resolve the issue.

Thanks for the response, Juan!  Take care.
bill

---

### Post by Yellow Pasque on 2014-05-02
Also, make sure you have gstreamer1.0-pulseaudio installed (I thought it would come standard with Xubuntu, but apparently it doesn't): [https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1309951)

My output above was from Debian. I don't see why it would be different on Ubuntu though.

---

### Post by il lupo on 2014-05-03
Hmm....Thanks, again, Juan.  You were correct.  gstreamer1.0-pulseaudio Was not installed.  Unfortunately, that didn't solve the problem.  Xine comes with Studio, and i was just using it to play a CD.  That's odd.  vlc Isn't playing CD's, either.  i'm still struck by the fact that parole won't switch between sound cards.  Unfortunately, i have no time to think this through until tomorrow afternoon.

Thanks, again!
bill

---

### Post by apsaras on 2014-05-22
I made a bug report here: [https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384) 

(I hope it's the same bug.)

---

### Post by alfh on 2014-09-21
The bug report referred to above says that a fix is released (as per 2014-06-13). Anyone know when that fix will be available in the repo's?

---

### Post by Yellow Pasque on 2014-09-21
Probably In Ubuntu 14.10. You should ask (Sean Davis) in the bug report if he plans on having the fix backported to Trusty.

---

