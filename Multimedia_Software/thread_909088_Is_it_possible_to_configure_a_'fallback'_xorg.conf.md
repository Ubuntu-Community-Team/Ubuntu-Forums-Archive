---
title: "Is it possible to configure a 'fallback' xorg.conf?"
date: 2008-09-03
forum: Multimedia Software
---

### Post by holr on 2008-09-03
Hi,
  I am a laptop user and when in the office, I use two screens. I have a macbook pro with nvidia 8600gt and use Nvidia's Twinview from their nvidia-settings tool. Its nice because I can have compiz enabled, even with two screens of different resolution.

  However, when I use the laptop at home with the builtin LCD screen, the desktop still appears stretched, in the configuration from the Twinview, even though no second monitor is connected. 

  I tried the 'Dual-Head' option with 'Xinerama Enabled' from nvidia-settings. This allowed two screens, but reverted to a 'fallback' of one screen when the laptop booted without an external monitor connected. However, compiz did not work in Xinerama mode.

  Is it possible to get a default fallback single-screen mode, like I described with Xinerama, but using Nvidia Twinview instead?

---

### Post by holr on 2008-09-12
I am currently using two different xorg.conf's for my different setups. Instead of configuring a fallback setup, is there a profile manager that I can easily switch between them?

---

### Post by RawMustard on 2008-09-12
Here's what I did to change configs easy.
I made two xorg.conf files and put them in /etc/X11
One's called xorg.conf.sv and the other is xorg.conf.tv

I then wrote 2 scripts (could be done in one) to change between both files.

I created launchers for these two scripts in System >Administration section in my menu.

Now when I want to run single monitor I just select the right script and when I want to run dual monitor I select that one.  As I don't do this very often it's worked great for me, perhaps it's all you need too?

Here's the code in my scipts
```
#!/bin/sh
foo=`gksudo -u root -k -m "enter your password to switch to TwinView" /bin/echo "Do you have root access?"`
sudo cp /etc/X11/xorg.conf.tv /etc/X11/xorg.conf
```

Hope this is usefull to you's :)

---

