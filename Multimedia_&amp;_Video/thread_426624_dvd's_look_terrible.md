---
title: "dvd's look terrible"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by redneckracin on 2007-04-28
Ok so i downloaded and installed the DVD codecs and such...but when i view a dvd the quality just isn't there. It looks blocky almost. So thinking it was my drivers I used envy to download the latest nvidia drivers (using a 8600GT btw). But when i restarted my xserver crashed so i had to do a restore.

So my question is how can improve the quality that im getting from DVD's?

---

### Post by AR_Kozz on 2007-04-29
if you haven't looked at glxinfo, type in terminal

glxinfo | grep rendering

if it says "direct rendering: Yes" the driver isn't the issue.

but if it says no, you've got a chore ahead of you, to get the nvidia driver installed and working. I use ATI so I have no idea how to go about that. Fortunately there's  plenty of help you can get for doing that, besides envy.

---

