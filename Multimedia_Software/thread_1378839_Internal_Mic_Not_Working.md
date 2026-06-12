---
title: "Internal Mic Not Working"
date: 2010-01-11
forum: Multimedia Software
---

### Post by adam22 on 2010-01-11
Hey guys. I have a Gateway NV52 with an internal microphone and internal webcam. On Windows, both work fine, but on Ubuntu I can only get the webcam to work. I never used one on Ubuntu (using Karmic Koala 64 bit) before, so I may be overlooking something.

```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```

Here are some screenshots:

[[IMG]http://img710.imageshack.us/img710/8140/screenshotiz.th.png[/IMG]](http://img710.imageshack.us/i/screenshotiz.png/)

[[IMG]http://img710.imageshack.us/img710/7802/screenshot1ot.th.png[/IMG]](http://img710.imageshack.us/i/screenshot1ot.png/)

[[IMG]http://img710.imageshack.us/img710/9052/screenshot2zd.th.png[/IMG]](http://img710.imageshack.us/i/screenshot2zd.png/)

---

### Post by HappyFeet on 2010-01-11
Run
```
alsamixer
```
in the terminal and see if the levels are correct.

---

### Post by adam22 on 2010-01-11
Thanks for the reply...maybe this helps?

[[IMG]http://img14.imageshack.us/img14/6083/screenshot3b.th.png[/IMG]]("http://img14.imageshack.us/i/screenshot3b.png/")

Edit: It seems from all of these screen shots that the internal mic isn't listed and I'm not sure why. I tried a USB mic and that showed up in the Input tab and worked with Skype, but it's not practical. I need to get this internal working.

---

### Post by adam22 on 2010-01-11
My friend found this: [http://jake.wasdin.net/blog/archives/84](http://jake.wasdin.net/blog/archives/84)

That's the exact model I have and he has listed a script for the internal microphone. Can anyone verify the integrity of that for me?

There's also this: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by HappyFeet on 2010-01-12
I would give it a shot, since it is a newer version of alsa. So you don't have to go back to the site, here it is again.
```
wget http://tan-com.com/tyler/files/AlsaUpgrade-1.0.x-rev-1.17.tar
tar -xf AlsaUpgrade-1.0.x-rev-1.17.tar
sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di

```
Then reboot.

---

