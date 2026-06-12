---
title: "No Sound"
date: 2010-01-03
forum: Multimedia Software
---

### Post by torch1001 on 2010-01-03
Hello I upgraded to UBUNTU 9.10 and now my sound card is not working. The card is listed in the sound preferences Hardware but not in the input or output sections. How do I fix this?    Ron

---

### Post by suncross on 2010-01-03
I have the same problem, however I dont have anything listed under hardware.

---

### Post by RedSingularity on 2010-01-03
In a terminal type 

alsamixer

and make sure the volume is all the way up.

---

### Post by suncross on 2010-01-03
I did that.  The volume is at max, and I still have no sound.

---

### Post by RedSingularity on 2010-01-03
Do you have pulseaudio installed?

---

### Post by suncross on 2010-01-03
I am not sure.  How can I check?  When I typed that command in, it gave me options as to change audio levels, so I believe I do have it installed (if that is in fact the case).

---

### Post by RedSingularity on 2010-01-03
Well do 

sudo apt-get install pulseaudio

and see what output it gives you.

---

