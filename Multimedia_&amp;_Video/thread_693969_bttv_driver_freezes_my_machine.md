---
title: "bttv driver freezes my machine"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by mr_fong on 2008-02-11
My webserver is equiped with a Pinnacle PCTV Pro TV card which I use to pull in images from an old CCTV cam. It works, but the server freezes randomly and after checking all the logs the culprit I can find is the bttv driver. This is in /var/log/messages....

[I]Feb 11 04:56:21 neo kernel: bttv0: timeout: drop=691 irq=2065488/2065488, risc=070af03c, bits: HSYNC OFLOW
Feb 11 04:59:52 neo kernel: bttv0: reset, reinitialize[/I]

When the bttv driver resets and reinitializes there is no problem, but for some reason this doesn't always happen and the server freezes.

[I]Feb 11 08:39:35 neo kernel: bttv0: timeout: drop=887 irq=2800261/2800261, risc=070af03c, bits: HSYNC OFLOW
Feb 11 18:56:51 neo syslogd 1.4.1#18: restart.[/I]

Can anyone enlighten me on what is exactly going on here and if there is a solution to the problem? If not, what is a good place to put this problem down with the experts? Thanks for the help.

Hans

---

### Post by mr_fong on 2008-02-20
To answer my own question: the culprit was the camera hooked up to the card. It can to 640x480, but then bttv has trouble reinitializing sometimes, hence locking up the box completely. Switching to a lower resolution solved the problem. Pity, because 640x480 provided me with some nice photo's. --Hans

---

