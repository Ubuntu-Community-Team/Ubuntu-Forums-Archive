---
title: "Out of scan range on Compaq CV743 monitor"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by Shawnp on 2005-11-25
I have a little problem that has me perplexed , hopefully someone can help me . I have 2 pc'c hooked up to one monitor useing a trendnet TK-206i kvm switch. On my XP machine i don't get the "out of scan range" message on my display , but when i switch over to my linux machine running ubuntu breezy badger i get the message. I have tried bringing the resolution down to 1024x768 and i still get the message only on the linux box. Anyone have any idea what causes this. I honestly don't think it is my linux box because it runs fine with another monitor, but , what do i know :) any help or explaination would be appreciated:confused: :confused:

---

### Post by teaker1s on 2005-11-25
you will find that it could be horizontal and vertical  settings in xserver -linux isn't as plug and play as windows try dropping the refresh rate down in system-preferences-screen resolution

to make it work if that doesn't type sudo dpkg-reconfigure xserver-xorg 
then you can go through the settings and make sure the monitors refresh rate horizontal sync and vertical refresh etc is okay

---

### Post by Shawnp on 2005-11-27
Thank you much Teaker. this did the trick . I used a variant of this command before when i changed the video card , didn't realize i could do this to tweak other settings.

:KS :KS :KS :KS :KS  for you!!

---

