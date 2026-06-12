---
title: "DVD problems"
date: 2010-12-06
forum: Multimedia Software
---

### Post by M1C4HTRON13 on 2010-12-06
Why dose this happen when I try to play a DVD

---

### Post by sydbat on 2010-12-06
> **M1C4HTRON13 said:**
> Why dose this happen when I try to play a DVDHave you enabled the [Ubuntu Restricted Extras]("https://help.ubuntu.com/community/RestrictedFormats") repository? Added [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

If you have, then I am not sure. I have found that trying to play the individual files on a DVD from the folder *on the DVD* creates this problem, but using a media player to directly access the DVD *from the DVD drive* works fine...if all the proper codecs are installed.

---

### Post by gandaran on 2010-12-06
> **M1C4HTRON13 said:**
> Why dose this happen when I try to play a DVD
which player are you using? that problem could be due to the video output driver, look it up in the video player preferences » video output driver and change the output driver to x11.
and ensure you have 'libdvdcss2' installed.

---

### Post by M1C4HTRON13 on 2010-12-06
Ive try'd all that.

The screenshot is of movie player.

If I try to play it in vlc I get this  

Playback failure:
DVDRead could not open the disc "&#65533;d".
Your input can't be opened:
VLC is unable to open the MRL 'dvd://&#65533;d'. Check the log for details.

---

