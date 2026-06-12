---
title: "MPlayer, TV out, DPMS, blue screen"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by rrwood on 2008-02-06
I have set up a mythtv box and have just about everything working perfectly.  The one remaining problem is that when I play back videos using MPlayer, the TV screen turns blue after a while.

I have disabled DPMS both in my xorg.conf file and via xset in my .xsession file.  As well, I have disabled the screensaver via xset from my .xsession file.  Oh-- and I have checked the BIOS settings and disabled DPMS there.

I am pretty sure this is a DPMS problem and not a screensaver issue, since the xscreensaver does not kick in, and this also happens if xscreensaver is not even running.

Most peculiarly of all, this appears to only happen when MPlayer is running-- not if I am sitting at an xterm or sitting in mythfrontend.

I suspect it may be a bug in the driver for my card (an old ATI 7500,  RV200 QW).  Very odd that the problem only occurs when MPlayer is running though.

I have also tried running MPlayer both with and without the -stop-xscreensaver flag (also commented that out in /etc/mplayer/mplayer.conf and made sure it wasn't in ~/.mplayer/config).


So, after Googling like crazy, I think I've covered all the things that I'm supposed to do to keep DPMS from kicking in, but it still does it.


Any suggestions, folks?

---

### Post by rrwood on 2008-02-06
More info.....

Looks like the blue screen on the TV-out also occurs using the "Internal" player on mythtv.  I had a test running, and DPMS kicked in after an hour of playback.  :-(

The relevant bits from xset are:

Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  0
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled


( Obtained by ssh onto the mythbox and then xset -d :0 -q )


Weird, and annoying for sure....

---

