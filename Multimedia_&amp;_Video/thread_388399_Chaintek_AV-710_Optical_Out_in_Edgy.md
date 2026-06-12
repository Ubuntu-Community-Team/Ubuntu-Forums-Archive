---
title: "Chaintek AV-710 Optical Out in Edgy"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Jbloudg20 on 2007-03-19
I have tried and tried to get the optical out form my AV-710 to work. I have used the guide found on this site, and any other guide I can google, to no avail. No matter what, I cannot get sound out of my optical port to my DAC. This works fine under windows. Can someone please help me out?

Thanks in advance.

---

### Post by Jbloudg20 on 2007-03-19
Just a bump for the night crowd. Please help!!

---

### Post by Jbloudg20 on 2007-03-20
So I think it is because the soundcard is not set to default. I got sound out a couple times, but have had nothing since. I have tried the easy method:

sudo asoundconf list

then:

sudo asoundconf set-default-card AV710

and it does not set the card as default.

---

### Post by Jbloudg20 on 2007-03-20
I just got it working using this:

[http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551)

now I just have to figure out why it wont let me set the clock to 48k?

This may help (this is more for my help in the future) [http://amarok.kde.org/wiki/FAQ](http://amarok.kde.org/wiki/FAQ)

---

