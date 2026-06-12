---
title: "Rhythmbox question"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by fettuohi on 2007-05-16
Can anybody get the visualization plugin to run correctly when desktop-effects are turned in Feisty? In my case  when visualization runs I just have grey screen and some flickering of the visualisation but when I turn the desktop-effects off then it runs fine. Is this a bug or wrong configuration of xorg or something?

Kind Regards

André

---

### Post by LuisGMarine on 2007-05-16
Please refer to my post in [this thread]("http://ubuntuforums.org/showthread.php?t=429027"), and see if the fix works for you.

This fixed all my problems with the content of windows running weird when I had beryl/compiz enabled.  Just subsitute the */usr/bin/gaim*, with the proper rhythmbox path.  I think its just plain old simple */usr/bin/rhythmbox*.

So in the end, the script should look like this:
```
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/rhythmbox

```

Hope this helps!

---

### Post by fettuohi on 2007-05-17
Thanks, I tried but it didn't work :(. But many thanks for the tip :).

Regards

André

---

### Post by fettuohi on 2007-05-18
I got it to work I simply switched to beryl. Compiz was sucking to much CPU power from my computer (20% in idle). I tried to upgrade compiz to 0.5 but I couldn't get it to start so i switched to the latest beryl (svn) and it worked :).

Regards

André

---

