---
title: "split /dev/video0"
date: 2009-06-20
forum: Multimedia Software
---

### Post by sirjask on 2009-06-20
I need your help with a USB video gabber device: it has 4 input channel, but my operating system see only /dev/video0;
many programs like skype, motion, xawtv, menage its 4 different input, but other programs not, so I would like to split the /dev/video0 in sometingh like:

/dev/video0_ch1
/dev/video0_ch2
/dev/video0_ch3
/dev/video0_ch4

Can you help me? please....

thanks in advance.

JK

---

### Post by MediaXG on 2009-06-20
Hey, I only just started looking at Ububtu, but I think what you have here '/dev/video0' is the folder location of your device, so you need to have /dev/video0, /dev/video1, /dev/video2 etc. - or maybe like /dev/video0/01, /dev/video0/02, etc, etc. What I hope is someone will correct my information if I am wrong, but maybe you can read up on this while you are waiting.:) - ...and maybe I don't know at all. :-s

---

