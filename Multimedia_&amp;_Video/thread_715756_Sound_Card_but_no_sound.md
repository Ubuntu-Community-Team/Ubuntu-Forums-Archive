---
title: "Sound Card but no sound"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by sarah.love on 2008-03-05
I've just uploaded ubuntu, and my sound is not working. I've followed other instructions and the terminal shows that it does recognise my soundcard [HDA Intel?] but still there is no sound. And I have double checked a million times to see if its not muted or anything.

---

### Post by sarah.love on 2008-03-05
That would be Ubuntu 7.10

---

### Post by Eisenwinter on 2008-03-05
Open up terminal, and type asoundconf list.

If a sound card is listed, type alsamixer, and change the master volume, it may be muted.

---

### Post by sarah.love on 2008-03-05
I did that, Its not muted...

---

### Post by Eisenwinter on 2008-03-05
Have you checked that you have all the codecs installed?
My suggestion is to open up terminal, and type sudo apt-get install gstreamer*

When it's done, try playing again.

---

### Post by sarah.love on 2008-03-05
Thanks, I just did that, and again there was no change

---

