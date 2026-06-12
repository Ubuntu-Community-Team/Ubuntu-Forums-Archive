---
title: "Geforce6100/Samsung 920N Resolution/Refresh Rates"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by txdmb on 2007-02-25
Hey all,

I recently installed Ubuntu, and used Envy to install the Nvidia drivers. I'm having problems with the screen resolution. When I go to Appliciations/System Tools/Nvidia Xserver Settings I have three options under Resolution 1280x1024 for the refresh rates at auto/60hz/75hz. (Also the Nvidia Xserver reads my monitor as Syncmaster Crt-0, when it should be read as an LCD) However, under System/Preferences/Screen Resolution I only have two choices at that resolution between 50hz and 90hz. Anytime I set the Nvidia Xserver setting to 60hz, the screen resolution settings under System/Preferences go to 90hz. I need the monitor, a Samsung Syncmaster 920n to run at 60hz at 1280x1024. Thanks for any help.

---

### Post by chewearn on 2007-02-26
No sure if this will help;  I have GeForce6150 / Samsung 205BW.  I install the stable nvidia driver in the repo version 1.0-8776.  After installation, I run this command:

```
sudo nvidia-xconfig
```

I am not familiar with Envy, so could not comment on your installation method, but I have no problem whatsoever with my graphics and resolution.

---

