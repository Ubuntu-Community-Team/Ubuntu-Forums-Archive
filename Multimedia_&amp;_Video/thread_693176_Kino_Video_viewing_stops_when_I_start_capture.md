---
title: "Kino: Video viewing stops when I start capture"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by Hurons on 2008-02-10
Capturing video works, however I cannot watch the video while its capturing. This is problematic. I need to visibly see the video being captured.

Any ideas? Thanks in advance.

---

### Post by Hurons on 2008-02-10
Again, I can capture, but I cannot view the video WHILE its being captured. I am almost there...anyone?

Thank you and best regards.

---

### Post by ph3ar on 2008-02-18
What display method are you using?


//From kino help page:

XVideo (Xv) requires supporting hardware and X server (most non-generic video card drivers support it). Run 'xvinfo' from a terminal window to get information about support on your system. XVideo is very fast and Kino maintains proper display aspect ratio. _**You can not take a screen capture of the video preview in this mode.**_ XVideo is similar to Microsoft DirectDraw if you are familiar with Windows. 
Reduced XVideo is similar to XVideo with the same advantages and disadvantages. This variation, however, uses half of the data bandwidth that is needed for compatibility on some X servers and hardware. The reduction in data bandwidth does invoke a scaling CPU overhead thereby affecting performance.
Enable preview during capture : To reduce the chance of dropped frames during video capture to disk, disable this option. If you have a fast enough system, you can turn this on and get a live preview of the video being captured.
//

---

