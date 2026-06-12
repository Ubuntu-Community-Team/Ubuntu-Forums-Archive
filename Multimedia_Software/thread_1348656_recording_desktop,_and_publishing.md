---
title: "recording desktop, and publishing"
date: 2009-12-07
forum: Multimedia Software
---

### Post by gcbzzzz on 2009-12-07
install:
- ffmpeg
- gtk-recordmydesktop

open gtk-recordmydesktop.

click advanced.

go to performance tab.

move frames per second to 24. close that window.

select window, and record.

press the "stop" icon on the gnome notification area.

now, open a terminal. go to the same dir where you saved your video.

and run:

ffmpeg -i out.ogv my_desktop.mpg


that's it. now you can publish your recording to other people on the mpg format.

---

