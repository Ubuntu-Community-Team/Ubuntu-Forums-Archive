---
title: "Mplayer Divx video output issue."
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by buzz13 on 2007-11-01
[IMG]http://i14.tinypic.com/67ov8yq.png[/IMG]

The problem is with the divx videos from anywhere.

As you can see from the screenshot, The video plays way below the area it is supposed to show the image.
When i go for full screen, around 1/4 of the screen remains dark and the video plays below it, Thereby not showing the complete image.

iam using gutsy right now and as far as i can remember the divx videos played flawlessly in feisty fawn and dapper.

Any help would be appreciated.

---

### Post by dulbirakan on 2007-11-02
I have the same problem. Does anyone have a solution?

---

### Post by dulbirakan on 2007-11-02
Installing ATI binary driver solved the problem!

---

### Post by buzz13 on 2007-11-02
Solution:
I changed the monitor aspect to 16:9(mplayer conf file) and changed the screen resolution to 1680X1050(my actual resolution). In mplayer conf , i added "fullscreen=false". Finally..I am using gl driver for online video play.

---

