---
title: "[SOLVED] MythTV upgrade, lost on-screen information"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by Dertiger on 2007-09-07
I upgraded mythtv to .20.2 on Edgy.  MythTV seems to have upgraded well despite other problems, save for one thing: I've lost all on-screen information that used to appear - ie the volume bar, the channel numbers, the play time when fast forwarding, the program guide, etc...nothing shows but the recorded show.  Everything seems to work from the remote...I can adjust the volume, but I don't see the display on the screen.  I can change the channel, but I can't see what I pressed.  I can't get to the info menu, and I can't see how far into the show I am.  Any ideas what could be missing?

---

### Post by rmcd on 2007-09-07
This may or may not help, but I was having bizarre problems with Live tv after upgrading. They were fixed when I changed the video driver (in one of the playback setup dialogs) from standard xvmc to libmpeg2, and then changed it back. I am guessing that some of the settings need reconfiguration after the upgrade.

If this doesn't help, I would suggest posting more details about your setup. Also, check the mythbackend logs for error messages. (In my case the logs were important because I could see that the frontend problems I had were not generating corresponding error messages in the backend.)

---

### Post by Dertiger on 2007-09-09
I found the problem.  The myth-themes package was not reinstalled on upgrade, so some config files must have been pointing to a non-existant theme.  Reinstalling solved the problem.  Another failure of searching Synaptic for "mythtv" instead of "myth"!

---

