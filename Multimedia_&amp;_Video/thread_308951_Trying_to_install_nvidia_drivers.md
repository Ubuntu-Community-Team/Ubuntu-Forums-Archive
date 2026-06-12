---
title: "Trying to install nvidia drivers"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by ugarth on 2006-11-28
When following [these instructions (step 2)](http://ubuntuforums.org/showthread.php?t=263851), on how to install the latest nvidia drivers.
I get this output from apt-get```
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9629
              Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
              Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
              Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
              Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1 is to be installed
              Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed

```Doing ```
apt-get dist-upgrade
``` does no good.
I downloaded the drivers from the nvidia website, and installed them as instructed.
Then I tried to install xgl following [these instructions]("http://www.linuxjournal.com/node/1000081"), but it failed. I think it was I copy pasted those commands and they had nvidia-glx too in there.

Conclusion: after some trouble, I still can't install nvidia-glx package, so what do I need to clean and reinstall ?
And, more odd, pressing Alt+Ctrl+(F1-F4) doesn't show me any linux xonsole. Pressing Ctrl+Alt+F7 brings me back to gnome again. What's happened ? I want to console back.

---

### Post by ugarth on 2006-11-29
Oh my ! The console stuff fixed itself :p

Anyway, I still can't install the nvidia drivers...

---

### Post by tseliot on 2006-11-29
> **ugarth said:**
> Oh my ! The console stuff fixed itself :p

Anyway, I still can't install the nvidia drivers...

Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ugarth on 2006-11-29
> Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)I tried, but it installed packages, which dependancies got broken...

---

### Post by ugarth on 2006-11-30
ok nevermind.
I've just installed a fresh copy of 6.10 and got no problems so far.

---

