---
title: "No Sound after dual boot from WIN 8.1 to Ubuntu 14.04 (possible work around)"
date: 2014-07-02
forum: Multimedia Software
---

### Post by cb41 on 2014-07-02
Hello all, 
I have a new ASUS N550JV Laptop, It came configured with Windows 8.1 which drives me crazy!  so I configured it to dual boot into UBUNTU 14.04 64 bit. 
After configuring dual boot and logging into ubuntu I discovered I had no sound even though the audio control appeared normal.
I played aroung with the installation and read a bunch of threads but nothing worked for me. 
Then I discovered that when I power the laptop completly off (shut down) and then turn it back on and boot directly into Ubuntu the bypassing windows sound is restored!

I was able to repeate this, if I boot into Windows 8.1 and soft reboot (restart) into Ubuntu 14.04 sound is once again gone however, when I powered the Latop down and booted directly into ubuntu.... Walla sound is back.

Any Ideas??

CB

---

### Post by lidex on 2014-07-02
This is fairly common. Usually reloading alsa brings it back:
```
sudo alsa force-reload
```

---

