---
title: "What web browser will Ubuntu Phone OS use?"
date: 2013-01-28
forum: Mobile Technology Discussions (CLOSED)
---

### Post by CoreyB. on 2013-01-28
I haven't seen anywhere and am really curious...what web browser will Ubuntu Phone OS use? Regular Firefox, Firefox mobile, something else?

Thanks in advance if anyone has any info!!

---

### Post by Copper Bezel on 2013-01-29
Presumably, regular Firefox, just compiled for ARM and presumably with some UI tweaks, since Android apps can't run on Ubuntu Phone. But I imagine Mozilla will eventually build a mobile version for Ubuntu Phone more similar to Firefox Mobile.

---

### Post by josephmills on 2013-01-30
Right now the phone uses snowshoe 
[http://snowshoe.openbossa.org/](http://snowshoe.openbossa.org/)

But you can make a browser in QML real fast in easy here is how 

```

 import QtQuick 2.0
 import QtWebKit 3.0

 WebView {
     url: "http://ubuntuforums.org/"
     width: 490
     height: 400
     smooth: false
 }






```

---

