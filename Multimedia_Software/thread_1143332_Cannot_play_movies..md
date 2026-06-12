---
title: "Cannot play movies."
date: 2009-04-29
forum: Multimedia Software
---

### Post by draperdt on 2009-04-29
I have couple of avi files. When I try to play them using VLC or XINE, the player starts,...... loads the avi file and then the player abruptly closes. I have all the latest codecs installed aswell. 

Any Ideas? I know I can play them on my windows box.

---

### Post by blastus on 2009-04-29
I would start by launching the movies from the command line. Just enter in vlc or xine followed by the filename of the .avi file. This will give you more detailed information as to why they do not play.

---

### Post by m_duck on 2009-04-29
Do you have the medibuntu repo's enabled and w32codecs (or w64codecs) installed? That should probably sort it. [Documentation](https://help.ubuntu.com/community/Medibuntu)

---

### Post by draperdt on 2009-04-30
OK. Turns out  I had to get rid of the proprietary fglrx driver for ATI and install the open source one. But it did piss me off for the past two days.

Reference: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

