---
title: "mb890 garbled screen"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by HadroLepton on 2006-08-20
hi

i have the mb890
specs are here: [http://www.ibase-i.com.tw/mb890.htm](http://www.ibase-i.com.tw/mb890.htm)

monitor is LG L1710B connected per DVI

when i boot from the ubuntu 6.06 livecd i get a garbled screen so i cannot do anything

please help

---

### Post by tseliot on 2006-08-20
Try booting in Safe mode

---

### Post by HadroLepton on 2006-08-20
thanks for the suggestion. i tried that already. it behaves exactly the same in safe or in normal mode.

---

### Post by HadroLepton on 2006-08-21
i was able to switch to text mode console (ctrl+alt+f1) which works fine.
here are my xorg.conf and xorg.log

the forum forbid me to upload the log file because it is too large. i greped the log file for warnings and errors. there are two versions, one with only the warning/error lines, the other with five lines of context (grep -C 5).

the log file seems to suggest that the monitor is not able to show that resolution.
```
(WW) (1280x1024,L1710B) mode clock 157.5MHz exceeds DDC maximum 110MHz
```
i know that the monitor IS able to show that resolution. i also installed windows xp on the same machine with the same monitor, and with a bit of work (install latest driver manually) i was able to get windows to show 1280 x 1024.

i also tried PCLinuxOS and Freespire livecd, both showed the same garbled screen. PCLinuxOS started in 1024 x 768 which shows fine, but when i set the resolution to 1280 x 1024 it will garble.

---

### Post by HadroLepton on 2006-08-26
i conclude from the lack of replies that:
1. no one else has the mb890 board
2. no one else has the problems i am having

the second case would mean that my board is defective

either way i have submitted a bug report here
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/57767](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/57767)

---

