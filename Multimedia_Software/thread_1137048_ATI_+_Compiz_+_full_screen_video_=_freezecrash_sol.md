---
title: "ATI + Compiz + full screen video = freeze/crash solution with 9.04"
date: 2009-04-25
forum: Multimedia Software
---

### Post by PageMaster86 on 2009-04-25
I haven't seen anyone else with this issue, but it took me many reboots until i found a solution. 

I've got an ATI card, and after installing the fglrx package, setting up compiz, and all the necessary extras, all videos caused an immediate freeze/crash when attempting to full screen. This problem only occurs under Compiz, and not under Metacity. If your problem is not related to Compiz, this will not solve it. 

Go to terminal:
gstreamer-properties

a box will pop up, click the video tab 
under output, choose "no xv" option for the plugin                                          

been flawless since. for anyone who had a similar ATI and video problem on 8.10, this was the solution used for video flickering in 8.10.

---

### Post by dazzlingtanish on 2009-04-25
I had the same problem and I tried what you said. But still no luck :(

---

### Post by heypaisa on 2009-04-27
I have the same problem.  Selecting "no XV" solved the problem.

CPU: AMD Phenom Quad Core 9600 (2.3GHz) AM2+
Motherboard: ECS A780GM-A AMD 780G

---

### Post by heypaisa on 2009-04-27
Might be related to this bug,

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/333027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/333027)

---

### Post by Cuve on 2009-05-12
> **dazzlingtanish said:**
> I had the same problem and I tried what you said. But still no luck :(

Check this site:
[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

"no XV" didn't work for me too. I use VLC and fullscreen caused compiz crashes. Explicit configuration for VLC did the trick :-)

---

### Post by elustran on 2009-07-22
Am I to understand that this problem still hasn't been resolved?  I was seriously hoping that it would be fixed in 9.04.

I'd like to be able to render video with openGL (or at least something that will scale video properly) rather than be stuck with blocky X11 rendering, and I'd also like to be able to run desktop effects at the same time.

---

### Post by permant on 2009-07-23
> **PageMaster86 said:**
> I haven't seen anyone else with this issue, but it took me many reboots until i found a solution. 

I've got an ATI card, and after installing the fglrx package, setting up compiz, and all the necessary extras, all videos caused an immediate freeze/crash when attempting to full screen. This problem only occurs under Compiz, and not under Metacity. If your problem is not related to Compiz, this will not solve it. 

Go to terminal:
gstreamer-properties

a box will pop up, click the video tab 
under output, choose "no xv" option for the plugin                                          

been flawless since. for anyone who had a similar ATI and video problem on 8.10, this was the solution used for video flickering in 8.10.


Yes ,It did work! Thank you for sharing your experience

---

### Post by jacks2k on 2009-07-30
Thanks for the trick. Works for me!

---

### Post by Thanh-BKK on 2009-11-30
Hi :)

I just came across that same problem with my new laptop and your solution worked perfectly :)

Kind regards.....

Thanh

---

### Post by soul_rebel on 2010-01-02
Do not disable xv. Do not do stuff you don't know.
With xv disabled CPU usage will go through the roof and some heavy media won't even play decently.

---

### Post by Thanh-BKK on 2010-01-03
Hi.

Can't complain - my laptop plays all sorts of videos and i haven't noticed particularly high CPU loads on it's single-core Athlon. 15-20% at max when playing full screen (system monitor in the background). 

Best regards.....

Thanh

---

### Post by opiumpoetry on 2011-03-02
here's the real solution [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1686561&highlight=fullscreen+freezes[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1686561&highlight=fullscreen+freezes")

---

