---
title: "Resolution changes after login"
date: 2008-05-05
forum: Multimedia Software
---

### Post by AnomalyDetected on 2008-05-05
I am using Ubuntu 8.04 with an Nvidia 8800 GTS 512MB graphics card, and am using the Nvidia 169.12 drivers that I loaded with EnvyNG.

Everything is working fine, except that when I log in to X, the resolution changes from the 1280x1024@60 that I set it to back to 800x600. I am able to set it back again using the NVidia X Server Settings control panel, but next time I boot the same thing happens.

The bootup screens look good, and even the X login screen is at 1280x1024, but a few seconds after logging in (before my desktop background appears), the screens goes black and then comes back in 800x600, and I must once again manually change it. Also, the command "nvidia-settings --load-config-only" has no effect - I must change it through the Nvidia control panel.

Attached are my current xorg.conf and .nvidia-settings-rc files (I've tried playing with them a lot so far to no avail).

Anyone else run into this, or have any ideas for me?

---

### Post by blathers16 on 2008-05-06
Are you running nvidia-settings as root?  If you aren't then the configuration changes are not saved.

Hope that helps.

---

### Post by AnomalyDetected on 2008-05-06
Thanks for the reply.

I believe I did try doing a "sudo nvidia-settings", but I've messed around with it so much now that I forget what I've already done. And even if I did, maybe it wasn't on my most recent configuration.

I will try that post the results here.

---

### Post by peakshysteria on 2008-05-06
run sudo displayconfig-gtk or gksudo displayconfig-gtk from a terminal (without -gtk in Kde i think).

---

### Post by AnomalyDetected on 2008-05-07
No change with either suggestion, unfortunately.

---

### Post by peakshysteria on 2008-05-08
How about some of these:

[https://help.ubuntu.com/community/Bi...esearch=Titles](https://help.ubuntu.com/community/Bi...esearch=Titles)

[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)

[http://ubuntuforums.org/search.php?searchid=40794148](http://ubuntuforums.org/search.php?searchid=40794148)

[http://tuxicity.wordpress.com/2008/0...and-craziness/](http://tuxicity.wordpress.com/2008/0...and-craziness/)

[https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

---

