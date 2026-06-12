---
title: "Sound card will only permit one sound to be played at a time(it blocks)"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by ravalox on 2005-12-23
I have an Intel Corp. 82801CA/CAM AC'97 Audio Controller sound card in my computer, in windows it was capable of many audio tracks simultaneously.  In linux, if I click on a menu item (say enemy territory) the Ubuntu drumbeat sound plays, and seems to usurp that applications use of the sound card.  ET loads without sound since on initialization access to the sound card was blocked.  The easy answer is to turn off Ubuntu's sound scheme, but this seems inelegant.  Is there an alternative driver I can use?

---

### Post by splater on 2005-12-23
Thank you for this thread it helped me to find what happend with the sound ....
I do not have any idea about resolve this problem.

Any one can help us ?

Thx in advance

---

### Post by jliedeka on 2005-12-24
It may have something to do with the way your apps are configured to use sound.  I have a similar chip (the 82801, mine says nothing about CA/CAM).  I have XMMS set to use the alsa output device.  I had to manually configure mplayer by setting the "ao=" line in its config file with "ao=alsa".

I don't use any sound daemons like esound or artsd.  If you have one of those running, it may b getting in the way.

---

