---
title: "WinTV-HVR-1900 no picture in VLC"
date: 2011-02-13
forum: Multimedia Software
---

### Post by nLinked on 2011-02-13
I've connected a Hauppauge WinTV-HVR-1900 to my Ubuntu 10.10 PC and used the instructions [here]("http://cvs.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1900") to install the firmware and test that it is detected using **dmesg**. Detection is successful.

The WinTV is connected to my TV using component connections. I run this command to enable the component interface: **v4l2-ctl -i 1**.

Then I use **cat /dev/video0 > test.mpg**, and that file is created and plays perfectly with video and sound.

However, when I try to play /dev/video0 in VLC Player (and other players), I just get a black screen. I also try the **v4l2-ctl -i 1** command before I try it in VLC, but I still get a black screen, and when I use **v4l2-ctl -I**, it shows it has connection 0 again (Television), so it reverts back to connection 0 instead of connection 1 (component).

So I'm a little stuck with getting VLC to get a picture, even though the CAT command works fine. Anything I can try? :confused:

---

