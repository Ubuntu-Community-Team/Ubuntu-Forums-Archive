---
title: "DVD playback broken in mythtv."
date: 2010-03-29
forum: Mythbuntu
---

### Post by acsidental on 2010-03-29
I cannot play DVDs from within MythTv. I keep getting No Demuxer errors.

If I load Xine from a terminal window it plays back fine.

Any ideas?

---

### Post by phroman on 2010-03-29
Hi, in the Mythbuntu Control Center, Proprietary Codecs, did you enable medibuntu support?  I think you have to do that, apply it, then add the rest of the codecs.  Let me know if that helps.

---

### Post by acsidental on 2010-03-29
Hi,

Yep w64codecs, ffmpeg and libdvdcss2.

It used to play up until a few months ago when I did an update. 

I used to get a plugin not found error until I symlinked /dev/scd0 too /dev/dvd.

Now I get the No Demuxer error but can play from a terminal.

Play command in Mythtv is

xine -pfhq --no-splash %d

---

### Post by xinix on 2010-03-29
> **acsidental said:**
> 
Play command in Mythtv is

xine -pfhq --no-splash %d

Does it play if you set the command to "internal"?

---

### Post by acsidental on 2010-03-30
Only as far as the Copyright Warning message and then it locks up. Backend and Mythweb still function but cannot get back to the menu's without rebooting.

---

### Post by xinix on 2010-03-30
Is there anything in the logs that would show an error message?
If the backend and mythweb are still running then it should be possible to get back to the menu (maybe).  Have you tried switching to a terminal window (eg CTRL+ALT+F1) and restarting gdm?

---

### Post by acsidental on 2010-03-31
Hi,

Couldn't see anything in mythbackend.log. Does xine have a log somewhere else?

---

### Post by xinix on 2010-03-31
If you append '--bug-report' to the end of you xine command it will  create a file called BUG-REPORT.TXT, this will have all the output from xine.  I'm not sure where it would be placed when you run xine from myth though.

> 
It used to play up until a few months ago when I did an update
Do you remember what you updated?

---

### Post by shonan_surf on 2010-04-01
I'm having a similar issue (Mythbuntu 9.10), although I've never gotten DVD playback to work beyond the copyright screen. I've loaded all codecs within the MythTV Control Center. I've been trolling the forums for a couple of weeks looking for a fix. Thx.

---

### Post by acsidental on 2010-04-01
> If you append '--bug-report' to the end of you xine command it will create a file called BUG-REPORT.TXT, this will have all the output from xine. I'm not sure where it would be placed when you run xine from myth though.

Couldn't find the bug report file.

> Do you remember what you updated?

I think it was a mythbuntu update to 9.1 but can't remember exactly. It would have also included any other updates at the time. 
I have tried another update but to no avail.

---

