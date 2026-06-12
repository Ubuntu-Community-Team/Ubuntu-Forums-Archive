---
title: "problem changing default resolution with nvidia settings"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by painterh on 2007-08-16
Hello;  I have a problem with my default resolution for my flat panel monitor.  I am using the latest nvidia drivers, and have used the nvidia settings panel to change the resolution from the default 1024x768 to 1440x920 which is my the native for my widescreen monitor.  After changing the resolution and applying the changes, I try to save the changes in my /etc/x11/xorg.conf. but I get a message saying "unable to remove old x-config backup file,  '/etc/x11/xorg.conf backup'".  Then as soon as I boot up again the resolution goes back to 1024x768.  How can I remove the backup file in order to save a new one?  I have an Nvidia 7600gs.

---

### Post by Gausian on 2007-08-16
you need to sudo before changing the settings

```
sudo nvidia-settings
```

---

### Post by painterh on 2007-08-16
Thanks for the reply.  Starting nvidia setting applet using sudo from terminal did the trick.

---

