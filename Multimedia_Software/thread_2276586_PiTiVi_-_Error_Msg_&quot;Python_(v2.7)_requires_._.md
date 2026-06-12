---
title: "PiTiVi - Error Msg &quot;Python (v2.7) requires . . &quot;video/x-gst-fourcc-apcn decoder&quot;"
date: 2015-05-03
forum: Multimedia Software
---

### Post by mark bower on 2015-05-03
I am trying to get PiTiVi and mPlayer up and running for use with ProRes 422 files.  When opening the apps I get the error msg "Python (v2.7) requires to install plugins to play media files of the following type:  Video/x-gst-fourcc-apcn decoder".

Where and how do I get the plugins, and what are the steps to install them?

---

### Post by mc4man on 2015-05-03
you may want to say what version of Ubuntu (your info says 12.04
A simple test may be if you can play the file in totem then pitivi should work, if you can't then pitivi won't.

---

### Post by mark bower on 2015-05-03
mc4man

Glad to have your help again.  O.K., you put me onto looking at the problem on different versions of Ubuntu:  "you may want to say what version of Ubuntu (your info says 12.04"

I "loaded" up all my computers, 2X 12.04 and 2X 15.04 with SMPlayer,Openshot,Videos(alias Totem,Movie Player), and PiTiVi.  In all cases SMPlayer and Openshot played the ProRes422.mov clip.  Videos and PiTiVi loaded on 15.04 without the Python error msg.  Only on 12.04 did Videos and PiTiVi balk with the error message.  I can live with using 15.04, so no further help requested re 12.04 which is the version that prompted this thread. 

I have more posts "in the production path" since I am headed towards editing yet to be digitized home super 8mm.  I am trying to learn the software I plan on using before committing to the digitizing expense:  $.50 per foot.

---

### Post by mc4man on 2015-05-03
Yeah - gstreamer in 12.04 likely can't handle prores , would be provided via the  gstreamer0.10-ffmpeg package if you wanted to d. check.

---

