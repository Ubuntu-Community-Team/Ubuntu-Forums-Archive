---
title: "Webcam black screen only"
date: 2008-03-17
forum: Multimedia Production
---

### Post by bill-linux on 2008-03-17
I'm using Dapper (6.06 LTS). I have a Logitech QuickCam Communicate STX (046d:08d7). At first dapper would not recognize the web can at all. I then compiled a new module for it following the instructions at 
[http://ubuntuforums.org/showthread.php?t=303330&highlight=logitech+webcam](http://ubuntuforums.org/showthread.php?t=303330&highlight=logitech+webcam)
I made only this change: The proper driver to use for my kernel is gspca rather than spca5xx. This worked fine in the sense that a) dmesg shows the webcam when I plug it in, and b) camorama, xawtv, and gqview not at least start ... but all show only a black screen! What gives. (And yes: I do have the lens cap off.) Is thre some kind of start switch on the webcam that I'm missing?

---

### Post by bill-linux on 2008-03-17
Ah ... problem solving ... kinda embarrasing ... need to plug the web can into the back of the computer and NOT the hub ... everyone knows this ... in fact even I knew this ... geeze. (BTW: Now works fine in Dapper 6.06 LTS)

---

