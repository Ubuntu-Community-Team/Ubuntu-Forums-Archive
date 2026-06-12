---
title: "Adobe Flash + Radeon driver doesn't work properly"
date: 2010-02-16
forum: Multimedia Software
---

### Post by Eril on 2010-02-16
Hello,

I've stumbled on a rather weird issue. If I use the Radeon graphics driver, and afterwards install Adobe Flash, Flash behaves really weird in Firefox. Clips on YouTube for example play fine, but I can't interact with any of the buttons in some of the clips. If I reboot with the Radeon driver enabled and Flash installed, the screen goes into stand-by mode (no signal) after the splash screen. What's more is that if I use the Vesa driver in xorg.conf, Flash works properly and booting is fine. So it seems Flash just doesn't work with the Radeon driver. Is there any known incompatibility with Flash and the Radeon driver? If not, is there any way to make Flash work with the Radeon driver?

Any help is welcome.

---

### Post by Eril on 2010-02-16
I just figured something out, if I boot with the vesa driver, login to desktop and then change the driver to the Radeon display driver and restart x-server (with alt-printtscreen-K) I can login fine. But that's not a full reboot.
The screen only goes into stand-by mode with the Radeon driver when booting, the vesa driver is fine.

I've also tried removing xorg.conf to autodetect settings - but the Radeon driver loads when booting up resulting that my screen goes into stand-by after the splash screen. The drum sound does play after booting up. So it's just no signal (or the wrong signal) to the monitor.

---

### Post by HappyFeet on 2010-02-16
Are you using 64bit ubuntu?

---

### Post by Eril on 2010-02-16
> **HappyFeet said:**
> Are you using 64bit ubuntu?

Yes, I'm using 64 bit.

---

### Post by HappyFeet on 2010-02-16
First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

---

### Post by Eril on 2010-02-16
Thank you for your reply. When I tried to run the first command I got an error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```I've made sure to double check that "libflashplayer.so" is in the right plugins directory. Restarted Firefox, but when I try to watch a Youtube clip, there's just a blank window where the Flash player is supposed to be.

I've also noticed that it doesn't matter whether I have Flash installed or not, I can't get passed the splash screen because the monitor goes into stand-by mode with the Radeon driver either way.

On a side note, I previously installed Flash from the Synaptic Package Manager.

Edit: sorry, right when I posted this message I figured that error was because I still had Synaptic open. I'm going to retry.

---

### Post by Eril on 2010-02-16
Unfortunately Youtube still doesn't show any Flash, it's just blank where the Flash player should be. It's also very slow, it takes a good 10-15 seconds to open a video on Youtube and Firefox gets unresponsive.

---

### Post by HappyFeet on 2010-02-16
You didn't install gnash or any other flash replacement, did you?

---

### Post by Eril on 2010-02-16
> **HappyFeet said:**
> You didn't install gnash or any other flash replacement, did you?

Nope, haven't installed any others besides Flash. Flash works fine with the vesa drivers and boots normally as well. It's just the Radeon drivers that don't boot normally and corrupt Flash. I have the Radeon x1950xt video card, which is fully compatible with the Radeon driver according to the documentation. And I want to run Compiz so the Radeon driver is necessary.

I've freshly reinstalled Ubuntu earlier today (technically yesterday, been working on this for hours now, getting sleepy now :icon_frown:) because of the same problem.

---

### Post by Eril on 2010-02-20
Marked thread as solved, as I just solved the issue. :D

---

