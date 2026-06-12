---
title: "Natty beta gpu crash loop"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ayle on 2011-03-31
Hi, when I was trying out alpha 3 there were no ati drivers for my mobility hd5850 so I think it defaulted to the basic framebuffer. BUt I've just downloaded beta 1 and tried to start it but it doesn't work. It freezes at the splash screen with ubuntu boot sound playing in the background then it goes to the desktop and it crashes again then 10 seconds later it crashes again and so on and so on. I dropped to shell mode and typed dmesg and the output indicated that my gpu kept crashing and resetting itself and crashing again until i got into shell mode. Does any one have a fix or should I just wait for the RC releases?

---

### Post by GreenRaccoon on 2011-04-01
I have the same problem from installing some updates for Alpha 3.

---

### Post by gunashekar on 2011-04-01
Please see this for the solution . It is a problem with the touchpad. 
[http://ubuntuforums.org/showpost.php?p=10625321&postcount=3](http://ubuntuforums.org/showpost.php?p=10625321&postcount=3)

---

### Post by Ayle on 2011-04-03
How am I supposed to apply that if I can't even get the livecd to launch?

---

### Post by cariboo on 2011-04-03
Try using the nomodeset option when using the Live CD. Press the any key when you see the initial screen, select your language, then press F6 and select nomodeset. Press Eac, then Enter.

---

### Post by Ayle on 2011-04-04
> **cariboo907 said:**
> Try using the nomodeset option when using the Live CD. Press the any key when you see the initial screen, select your language, then press F6 and select nomodeset. Press Eac, then Enter.

That did the trick. Thank you.

---

