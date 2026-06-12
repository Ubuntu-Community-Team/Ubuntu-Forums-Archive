---
title: "Acer Orbicam Problems"
date: 2009-03-11
forum: Multimedia Software
---

### Post by onesadpenguin on 2009-03-11
My Acer Aspire 5670 uses a Logitech Orbicam, and for the life of me, I cannot get it working. I feel like I've tried everything, but it still won't work, at least not in cheese or camorama. I can see the video stream in Ekiga, but that's it.

lsusb:
```
Bus 005 Device 002: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg gives me lines and line of this:

```
[26477.848989] gspca: frame overflow 616402 > 614400
[26477.909017] gspca: frame overflow 617426 > 614400
[26477.967737] gspca: frame overflow 615378 > 614400
[26478.027785] gspca: frame overflow 615378 > 614400
[26478.087727] gspca: frame overflow 615378 > 614400
[26478.147764] gspca: frame overflow 616402 > 614400
[26478.206525] gspca: frame overflow 617426 > 614400
[26478.266486] gspca: frame overflow 617426 > 614400
[26478.326496] gspca: frame overflow 615378 > 614400
[26478.386517] gspca: frame overflow 615378 > 614400
```

Of course, if there is anything else you need to help, please just ask and I'll provide it ASAP.

Any help would be greatly appreciated. Thanks in advance for any help anyone can give.

---

### Post by onesadpenguin on 2009-03-11
After looking around more, I found that helpful people have requested dmesg log file in a zip, so here is mine.

---

### Post by frfr on 2009-03-13
hi penguin,

i seem to have the same problem with the same computer and my artistic work is depending on the webcam working. neither in tss nor in pd it works. but as i am such a greenhorn with the system i don't even now what to do exactely with the attached dmesg log file. -just to see if i get something fixed with that.
can you please explain what to do!

thank you very much in advance

---

### Post by onesadpenguin on 2009-03-13
frfr-

the log file won't tell you much, unless you know what you're looking for. on an up side, I got my  webcam working with cheese, but it's pretty dark. I'm not at home with my laptop, so I can't tell you what drivers I used to make it work, but know that it can be done!

Problems with my webcam now:
-doesn't work with Camorama
-much to dark
-contrast is very high
-white balance doesn't work, if not natural light, it looks horrible.

I'll try to keep this updated for anyone who might be having the same problems.

---

### Post by Kiwi Jono on 2009-10-19
Same issues (gspca frame overflow etc) here with Jaunty 

My main issue is not being able to see the orbicam in Skype but works with Ekiga (only on one video resolution though).

Spent ages trying to find a solution but so far none of the suggestions have helped.

---

