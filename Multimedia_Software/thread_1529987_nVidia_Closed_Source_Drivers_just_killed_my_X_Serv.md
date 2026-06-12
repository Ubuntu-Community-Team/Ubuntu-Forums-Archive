---
title: "nVidia Closed Source Drivers just killed my X Server :-/"
date: 2010-07-13
forum: Multimedia Software
---

### Post by beastrace91 on 2010-07-13
Okie dokie - so I have (had?) 10.04 up and running on my system with an nVidia 9600. Installed the recommended closed source driver from the hardware drivers wizard and everything was going swell - then I hooked up my second monitor. Now the monitor works great after I configure it via the nvidia-settings, but I did not want to have to go through this every time I boot the system.

So after getting everything set to my liking I click the "save to x configuration" button and give it my root password to save the file.

Upon rebooting to see if this had gone successfully, I now find my X server is frozen at the start up noise and it hangs there until I cold shut the system off playing the noise over and over again... I rebooted into a recovery kernel and told it to reset to use a generic X configuration - it made no difference. The thing still hangs at startup. I even got creative and ran **dpkg-reconfigure -phigh xserver-xorg** from a root shell and it also did not change anything upon rebooting :(

What on earth happened? How can I fix it? And how can I create a static setup for my two screen on Ubuntu?

Regards,
~Jeff

---

### Post by fh_scott on 2010-07-13
Try this:

1) login to shell
2) sudo service gdm stop
3) sudo mv /etc/xorg.conf /etc/xorg.conf.bak
4) reinstall Nvidia binary driver
5) restart gdm
6) login and setup twinview through nvidia-settings
7) Don't save the changes to xorg.conf in nvidia-settings. the settings are stored in your profile.

---

### Post by beastrace91 on 2010-07-13
> **fh_scott said:**
> 
7) Don't save the changes to xorg.conf in nvidia-settings. the settings are stored in your profile.

What do you mean by this? Every time I restart I have to reconfigure my nvidia settings... How do I save it to my "profile"?

~Jeff

---

