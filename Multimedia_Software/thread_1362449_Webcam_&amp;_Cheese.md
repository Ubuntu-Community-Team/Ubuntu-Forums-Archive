---
title: "Webcam &amp; Cheese"
date: 2009-12-23
forum: Multimedia Software
---

### Post by YoBZH on 2009-12-23
Hello All

I have a problem with Ubuntu 64, and Cheese. I have 2 accounts on the station, mine, the first account, capable of administering the PC, and a second unprivileged.

1 - When I use Cheese with my account the webcam is available, and it works fine.
2 - When the second, unprivileged user tries, the web cam starts, but all he gets is rubish on the screen, and not a clear video.

I check user rights, group belonging (he is in Video group), and cannot identify the problem.

I would appreciate any help in trying to spot the problem.

Tanks

---

### Post by YoBZH on 2009-12-23
Hello

I managed to narrow down the problem.
- if I boot the PC, log in with the unprivileged user, launch Cheese, it works.
- I close the session, log in with the second user, it fails.
- close the session, log in with a privileged user it works.

I did the same test starting with my user instead of unprivileged one, and same behaviour. It seems that maybe modules are loaded by one user, in userspace, and then all other users are unable to use it.

Any Idea ? SHall I fill a bug report ? I do not have time unfortunately to go into the code...

Sincerely

---

### Post by YoBZH on 2009-12-23
And another point :

If I unplug the USB WebCam and plugit again, it seems to work...

Still investigating...

YOann

---

### Post by YoBZH on 2009-12-28
Hi All

Still no luck.
Actually,I realize, that it seems that the WebCam and USB couple is affected to a user session. Basically, I change session, thant unplug webcam and plug it to another USB port, and it goes OK. 

If I come back to my main user session, unplug the webcam again and replug it to first USB port and it works...

This is probably a user right thing.
Still looking...

---

