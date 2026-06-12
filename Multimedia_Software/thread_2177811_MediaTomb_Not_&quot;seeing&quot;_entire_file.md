---
title: "MediaTomb Not &quot;seeing&quot; entire file"
date: 2013-09-30
forum: Multimedia Software
---

### Post by Magellan on 2013-09-30
I set up MediaTomb this weekend in 12.04 LTS.  Seemed to work fine out the box.  I was able to add my music folder to Mediatomb and browse it from my Android phone running MediaHouse.
mp3s played fine, but when I went to play some high bit rate flac file only the frist second or so would play.

Checking the UI, when I select the file from the database tree, it only shows the file as being about 92kB.  The actual file size is about 80MB.

I'm not sure where I should look for the problem.

Thanks,

mag

---

### Post by tgalati4 on 2013-09-30
Have you tried different players on Android?  Perhaps it is a problem with the MediaHouse app.  Have you tried DLNAplay?  Is there an error log or message box in MediaHouse settings? Can you play the file from another linux machine?

---

### Post by Magellan on 2013-09-30
I haven't tried another player, but given that the MT UI itslef shows the file as too small, I think the problem lies in MT.
I will try another player though to verify.  That's a good idea.

---

### Post by Magellan on 2013-10-01
I tried it with Bubble UPNP and had the same result.

---

### Post by Magellan on 2013-10-05
Solved:  I had more some corrupt copies of the file in another directory.  That is what MT was reading.  Deleted those files and updated the driectoreis for MT and it's working.

---

