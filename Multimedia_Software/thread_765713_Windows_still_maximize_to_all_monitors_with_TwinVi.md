---
title: "Windows still maximize to all monitors with TwinView (Nvidia, 8.04)"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Deiz on 2008-04-24
I've had this problem since 7.04 - Every time I install, windows will maximize to both monitors instead of one. In 7.04 and 7.10 I was able to fix this by enabling TwinView, disabling TwinView, enabling Xinerama, restarting X, and then going back to TwinView, but that's not helped yet in 8.04.

Any less hacked-together solutions are greatly appreciated.

---

### Post by ztheory on 2008-04-25
Assuming you have the nvidia-settings application installed, enter nvidia-settings via command line using sudo

#sudo nvidia-settings

Go to X Server Display Configuration, and set both monitors to Position: Absolute.

Once you've done this, make one of your monitors the "primary display screen", mine is to the left.

Determine the resolution you are using. In my case, 1680x1050. On the monitor you did NOT choose for the primary display, make sure in the position field it looks like this (assuming my config): +1680+0

This should fix the problem. I have also included my xorg.conf:

[http://pastebin.com/fe54a96e](http://pastebin.com/fe54a96e)

---

### Post by Deiz on 2008-04-25
I tried that and at first it didn't work - However, one X restart later, I've now got two separate monitors.

Thanks for the help.

---

### Post by Alex6969 on 2008-04-26
Worked for me as well. I had to manually restart X to get the settings to work.

Thanks!

---

