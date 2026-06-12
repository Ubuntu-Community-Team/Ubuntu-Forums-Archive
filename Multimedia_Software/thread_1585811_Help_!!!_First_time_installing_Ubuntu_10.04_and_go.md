---
title: "Help !!! First time installing Ubuntu 10.04 and got no sound"
date: 2010-10-01
forum: Multimedia Software
---

### Post by nhianho on 2010-10-01
I have just installed Ubuntu on my laptop and everything seems to work well except the sound. There are waves on the speaker icon but I could not hear anything. I have been trying to adjust the options in Sound preferences but still no results show up.

I am truly a newbie with Ubuntu so any help will be truly appreciated.

PS: FYI, my laptop is a vaio eb1m1e, I think it has an onboard Realtek sound card. But in  the hardware tab (Sound preferences) , the two devices I see are Internal Audio and Redwood HDMI audio ( Radeon 5600 series).

---

### Post by nhianho on 2010-10-01
Anyone here can help me ?

---

### Post by |{urse on 2010-10-01
If you plug headphones in, do you hear sound?

---

### Post by |{urse on 2010-10-02
A little googling and it looks like there is already a solution to your problem.

open a terminal and enter this command

```
sudo apt-get install linux-backports-modules-alsa-2.6.32-21-generic
```

This solution can be found here 

[http://ubuntuforums.org/showthread.php?t=1468048]("http://ubuntuforums.org/showthread.php?t=1468048")

OH THIS IS MY 666th POST! wo0

---

### Post by |{urse on 2010-10-02
By the way, to open the terminal:
hit alt-f2 and type gnome-terminal then press enter.

---

