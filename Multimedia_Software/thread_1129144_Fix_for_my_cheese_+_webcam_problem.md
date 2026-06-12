---
title: "Fix for my cheese + webcam problem"
date: 2009-04-18
forum: Multimedia Software
---

### Post by tidris on 2009-04-18
I am running ubuntu 8.10 with all the latest updates on a 2.4GHz Intel dual core2 laptop with a built-in usb 1.3 megapixel webcam. The graphics card is a 256MB nvidia geforce 8600m GT.

I have been experiencing an extremely slow webacam video frame rate on some programs such as cheese and luvcview. Many seconds go by between video frames instead of the expected many frames per second.

Today I discovered a way to work around this problem. What I do is open a terminal window and type the following followed by Enter.

 while true; do echo > /dev/null;  done

That line runs a script that keeps the CPU busy. As long as the script is running, both cheese and luvcview show video at a normal rate. Stop the script and video goes back to super slow mode.

I suspect the problem is related to the automatic CPU frequency adjustment on the laptop. When the script above is running the CPU usage goes way up and the CPU speed jumps from 800MHz to 2.4GHz according to the CPU frequency monitor applet. When the script is stopped the CPU speed stays at 800MHz even when cheese or luvcview are running and trying to capture video.

I hope that info helps someone.

---

