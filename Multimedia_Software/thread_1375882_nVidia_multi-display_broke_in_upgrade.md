---
title: "nVidia multi-display broke in upgrade"
date: 2010-01-08
forum: Multimedia Software
---

### Post by HyperHacker on 2010-01-08
I had an older machine which ran Xubuntu 8.04 and hadn't been updated in a while. I put in an AGP GeForce FX 5200 and a PCI GeForce MX 400 (dual-head), and after tweaking for a few hours, I got three displays working.

Then I made the mistake of installing several package updates. After doing that the AGP card would not be detected anymore.

I hoped 9.10 might fix it, so I installed it fresh, and after a few more hours of tweaking, nvidia-settings can see both GPUs again. However one of the screens is no longer detected properly. It shows up as CRT-0 with a maximum resolution of 640x480, when its native resolution is 1280x1024. The program also doesn't work: when saving, it says it can't parse xorg.conf (although it looks just fine) and dies. So I'm stuck with one screen at 640x480, which isn't even big enough to see the OK buttons on some of these windows...

---

### Post by gsmanners on 2010-01-08
To save the "xorg.conf", you need to run nvidia-settings as root. That is:

```
gksudo nvidia-settings
```

---

### Post by HappyFeet on 2010-01-08
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
sudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button labeled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```

then paste what you copied from nvidia-settings. Save and reboot.


In the last line of code, you will have to change gedit to whatever the default text editor is in xubuntu.

---

### Post by HyperHacker on 2010-01-08
Thank you, that got it working. The resolution problem turned out to be a bad DVI->VGA adaptor. It had been working, then when I moved the machine I grabbed the wrong one.

---

