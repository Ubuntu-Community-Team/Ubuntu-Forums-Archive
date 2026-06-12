---
title: "Can't start X... Intel 845G"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by l4lucas on 2006-10-02
Hey, i have an intel 854g and ive been playing with many linux distros lately, and have not been able to start X with the one exception of getting knoppix to run in failsafe. Ive found some directions as to getting the drivers setup, but they seem to require being in X. ](*,)

---

### Post by foznot on 2006-10-02
I am struggling with my intel 845 also. I however, have X working. First I would try to change your video driver to "vesa" and that should work, though crappy. If you need instructions for that try: sudo nano /etc/X11/xorg.conf and then go down to video driver and change whatever is in there to vesa. It should be i810. Heads up though, the i810 driver does seem to be broke on some systems. If you want you can also just try to sudo apt-get install xserver-xorg-i810 and that will load it for you. Then you will need to make sure that your xorg.conf file is consistant with that driver and says "i810" in the video driver.

Hope some of this helps.

---

