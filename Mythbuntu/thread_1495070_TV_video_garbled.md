---
title: "TV video garbled"
date: 2010-05-27
forum: Mythbuntu
---

### Post by heraldo on 2010-05-27
Hi all,

have just installed a fresh Mythbuntu 10.04 on my PVR-500, but the same old problem came back (has been there every time I tried MythTV): the TV video is garbled. Please help, I am losing hope.

---

### Post by heraldo on 2010-05-31
Nobody? Anybody?

---

### Post by skompier on 2010-06-02
I had a similar problem when I set up my HVR1600. In the MythTV backend, under Videos Sources, I changed the channel frequency of my card source from us-cable to us-cable-hrc and all was good. This is of course assuming that you're in the US and on a cable system.

---

### Post by heraldo on 2010-06-06
Well, after trying all the forums and the mailinglist (without any success, I must say) I have figured out the solution myself. It was the screen resolution in ubuntu which caused all the trouble. For the life of God I have no idea how screen resolution can scramble the TV capture signal, but it's a fact. With the "wrong" screen resolution the captured mpeg (using cat /dev/video0 >test.mpg) was playing back scrambled even on a windows xp computer!
Now everything works well. Hopefully this helps somebody else (leave a note if it does!)

---

