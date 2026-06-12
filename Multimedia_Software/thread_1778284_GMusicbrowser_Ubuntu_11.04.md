---
title: "GMusicbrowser Ubuntu 11.04"
date: 2011-06-08
forum: Multimedia Software
---

### Post by syoung27 on 2011-06-08
so i'm getting a playing error with gmusicbrowser it says there's problem in line 135.
This is my second time booting Ubuntu because of a partition error i now fixed. i did have this problem before but gstream and it's additions i think had taken care of it.
now im not sure where to go, synaptic manager had a ton of updates for gstream but selecting them all one at a time will suck..

---

### Post by Toz on 2011-06-08
Try installing **ubuntu-restricted-extras**

---

### Post by syoung27 on 2011-06-08
yeah i did that also, still nothing...very strange, or simple.

---

### Post by Toz on 2011-06-08
Can you post back the exact error message?

---

### Post by syoung27 on 2011-06-08
Playing error : Resource not found. at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 135.

---

### Post by Toz on 2011-06-08
What are you trying to play? Where is the file located?

---

### Post by syoung27 on 2011-06-08
various file formats, primarily mp3 and wav.
they're linked into my windows system, ill try from my external where it worked previously..

---

### Post by syoung27 on 2011-06-08
reloaded all songs, now working, tested different extensions:)

---

### Post by Toz on 2011-06-09
Makes sense. I've seen that error message if I either don't have the proper codecs installed or if the songs are not available (i.e. on another drive/share that isn't yet mounted).

---

### Post by syoung27 on 2011-06-09
Toz do you know anything about USB speakers with Ubuntu?
My problem is i just can't control the volume with hotkeys or the volume icon, i have to go into the mixer settings and select the device just to adjust the volume. ALSA has it checked as master also.
if you have any ideas would be much appreciated:)
It worked with Zorin and Fedora 15..
ALSA soundboard looked a bit different, if that's what was opening in my previous distros.

It's a Logitech USB Audiohub (soundbar with 3usb ports)

---

### Post by Toz on 2011-06-09
> **syoung27 said:**
> Toz do you know anything about USB speakers with Ubuntu?
My problem is i just can't control the volume with hotkeys or the volume icon, i have to go into the mixer settings and select the device just to adjust the volume. ALSA has it checked as master also.
if you have any ideas would be much appreciated:)
It worked with Zorin and Fedora 15..
ALSA soundboard looked a bit different, if that's what was opening in my previous distros.

It's a Logitech USB Audiohub (soundbar with 3usb ports)

Lets have a look. Open up a terminal window and type in:
1. ```
aplay -l
``` 
2. ```
cat ~/.asoundrc
```
3. ```
cat /etc/asound.conf
```
and post back the results.

---

### Post by syoung27 on 2011-06-09
i had Ubuntu 11.04 Server before, i just booted the desktop edition lol so getting plugins and such going again, will post back soon, might even work this time because i have the proper sound menu.

---

### Post by syoung27 on 2011-06-09
everythings good now:)

Setting up home server on old laptop is my next task:)

---

### Post by seiffs on 2011-06-27
I have the same problem, I believe it's because of some problem with ubuntu itself. Some packages seem to be installed properly (in ubuntu software center) but the libraries are broken (usually missing files). Once I download a library from packages.ubuntu.com and install it manually (dpkg -i) the problem disapperars.

I installed my amd64 Xubuntu today from usb stick and it is bad - in order to install and run Aptitude I had to manually reinstall libatkmm, libcairomm, libglibmm, libgtkmm, libsigc++ ...

I'm convinced that the problem with gmusicbrowser will be the same - reinstalling gstreamer libraries will probably solve it. But I'm rather thinking about reinstalling the whole Xubuntu, or at least all packages.

Hope this helps

---

### Post by syoung27 on 2011-06-27
i started using banshee, gmusicbrowser didn't load all my songs anyways.

---

### Post by seiffs on 2011-06-28
Well, reinstalling didn't help. Installing packages
gstreamer-plugins-ugly 
gstreamer-plugins-bad
helped.

---

