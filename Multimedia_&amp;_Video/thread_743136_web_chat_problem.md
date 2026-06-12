---
title: "web chat problem"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by mandeep609059 on 2008-04-02
hi  have a problem in kopete not able to see any image when someone send me webcam request what to do..................  when i click on the request for web cam it says kopete error ----  
[I][B]"- I cannot find the jasper image convert program.
jasper is required to render the yahoo webcam images.
Please see [http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support](http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support) for further information"[/B][/I]

---

### Post by wolfen69 on 2008-04-02
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults for every screen except when you get to video modes. make sure v4l is selected. use tab, up/down arrows, space bar (to check things off) and enter to navigate.

---

