---
title: "Problem with DVD playback after compiling FFMPEG"
date: 2011-02-14
forum: Multimedia Software
---

### Post by LinuxPhreak on 2011-02-14
Okay so I was able to play DVD videos by doing the following. 

```
sudo apt-get install ubuntu-restricted-extras
```then 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```DVD videos would play fine. Then I decided to compile FFMPEG by following the tutorial at [http://ubuntuforums.org/showthread.php?t=786095&page=1](http://ubuntuforums.org/showthread.php?t=786095&page=1)

After using the tutorial I was no longer able to play DVD's

Can someone tell me how I can fix this and keep my custom compiled FFMPEG at the same time.

---

### Post by mc4man on 2011-02-14
> After compiling FFMPEG by following this tutorial I no longer can play DVD movies...
Did you use --enabled-shared in your ffmpeg configure?

---

### Post by LinuxPhreak on 2011-02-15
> **mc4man said:**
> Did you use --enabled-shared in your ffmpeg configure?

No I didn't. I guess I should have done that. If I recompile it would it start to work again? Or would I have to do something else.

---

### Post by mc4man on 2011-02-15
> I guess I should have done  that
No, quite the opposite, enabling shared could affect other app/plugins that depend on ffmpeg shared libraries.
There is really nothing that a static ffmpeg build, following that guide, that could affect dvd playback.

For gstreamer players (totem, I guess banshee), ck that the gstreamer ugly, bad, and ffmpeg plugins are installed.

---

### Post by LinuxPhreak on 2011-02-16
After reinstalling gstreamer-ugly I tried and no luck. I then tried the bad and good. Still no luck. I then tried reisntalling the entire ubuntu-restricted-extras package. Still no luck. After ever reinstall I also install libdvdread4. 

I think it might be worth mentioning that I have a Dell Inspiron 8500 that require restricted drivers NVIDIA drivers.

---

### Post by mc4man on 2011-02-17
Maybe install vlc and start from terminal. Try to play a dvd and post the terminal output. (hopefully vlc will show some decent output as to your issue
Either just use vlc in the terminal and then Media > Open disc > dvd > play

Or if your drive is what vlc is set to as the default (/dev/dvd), then this in terminal
```
vlc dvd://
```

---

