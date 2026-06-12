---
title: "Nvidia &quot;display outside of range&quot;"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by bholstege on 2007-12-27
I recently got an 8800gt and installed the drivers with envy, since they are not in the restricted driver section yet. I then set my resolution to 1680x1050 (through Display Settings), which is the native resolution on my monitor. It worked fine, until I rebooted my computer.

Now when I load Ubuntu, I get a message on my monitor saying the "display is outside of range".

So, why did it do this, and how can I fix it?

---

### Post by taurus on 2007-12-27
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again at the prompt.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to the GUI login screen and restart X again with <Ctrl><Alt>Backspace.

---

### Post by hp59dk on 2008-01-05
This solved my problem: [http://ubuntuforums.org/showthread.php?t=594915](http://ubuntuforums.org/showthread.php?t=594915) 
Thank You very much :)

---

