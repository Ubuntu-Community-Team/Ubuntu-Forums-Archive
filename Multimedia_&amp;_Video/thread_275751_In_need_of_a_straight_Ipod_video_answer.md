---
title: "In need of a straight Ipod video answer"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by kerme8503 on 2006-10-11
Hey all. I am in dire need of some clarification here. I have an Ipod video and need to be able to put tv series on because i need to free up some HDD space. (i have a 40 gb HDD...sad i know...) I found the "how to encode videos for ipod video" or whtever, but its like my comp cannot compile or something becuase it wouldnt compile the programs needed there or Mplayer. Its getting frustrating because i put hours at a time into this and i end up with a half finished projact that is not functional. I finaly saw the "vive" thing on the top of the How To and gave that a shot. I "tar xzf vive-1.0.2.tar.bz" or whatever the file name is and "./configure" 'd it and "make" then "sudo make install" and when i try to run it in terminal i get something like

"use of unintialized value in pattern match (m//) at /usr/bin/vive line 368"

I did everything fine and i never got any errors...please help!!
Edit/Delete Message

---

### Post by meng on 2006-10-11
Okay, assuming that your main problem is wanting to install mplayer, I would not recommend compiling from source unless you're very experienced/comfortable with that method of installation. Instead, install from repositories, you need to have extra repositories enabled.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

