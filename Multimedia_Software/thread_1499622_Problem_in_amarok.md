---
title: "Problem in amarok"
date: 2010-06-02
forum: Multimedia Software
---

### Post by shaquille on 2010-06-02
I have just installed Amarok media player from synaptic package manager. It downloaded 115 files of 105 mb. It opens, I can add music files but the files don't play. What should I do?

Thanks
Shaquille

---

### Post by hansdown on 2010-06-02
Hi shaquille.

You may need to add two things from synaptic.

```
 libxine1-ffmpeg
```


 ```
gstreamer0.10-plugins-ugly
```

See if they are installed.

There is a new release of amarok on may 31. It probably won't be in synaptic for a while.

[http://amarok.kde.org/](http://amarok.kde.org/)

---

### Post by cybrsaylr on 2010-06-02
I put this code in terminal to get Amarok to play music:

> sudo apt-get install libxine1-plugins

When I installed 64 bit Karmic Koala and Amarok wouldn't play any music files.
Put above code in terminal and Amarok plays music files again as it did with Jaunty.

---

### Post by shaquille on 2010-06-02
Thanks, it worked.

---

