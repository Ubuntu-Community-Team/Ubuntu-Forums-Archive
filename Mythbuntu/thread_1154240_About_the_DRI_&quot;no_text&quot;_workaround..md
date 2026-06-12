---
title: "About the DRI &quot;no text&quot; workaround."
date: 2009-05-09
forum: Mythbuntu
---

### Post by CaptainPatent on 2009-05-09
Hey everyone, I recently upgraded to Mythbuntu Jaunty (9.04) and did a clean install. I ran into the same no-text error everyone has run into with no text showing in the text boxes and the frontend and backend setups hanging.

I fixed that by using the Option "DRI" "off" workaround in xorg.conf and everything displays correctly, but there is a noticeable slowdown in the program guide. In fact, it's nearly unusable due to how slow it runs.

I was wondering if DRI deals with hardware acceleration (I believe it's related to OpenGL rendering in X, but I'm not completely sure) and if the workaround is causing the slowdown, if all Jaunty users were experiencing the same slowdown in the guide, or if nobody else is and this problem is restricted to my own computer hardware or a different set of computer hardware. If it's unrelated to the DRI workaround, a bug report may need to be filed.

---

### Post by superm1 on 2009-05-09
It's only on AMD/ATI graphics hardware.

There is an open bug already, and an alternative workaround that involves modifying etc/mythtv/session-settings with an env variable.

---

### Post by CaptainPatent on 2009-05-09
I know there's an open bug - I was just wondering if Option "DRI" "off" deals with hardware acceleration.

I just wanted to know if that was causing the slowdown or it was something else.

---

### Post by superm1 on 2009-05-13
Yes, that turns off hardware acceleration.  I'd recommend using the other workaround instead for now.

---

