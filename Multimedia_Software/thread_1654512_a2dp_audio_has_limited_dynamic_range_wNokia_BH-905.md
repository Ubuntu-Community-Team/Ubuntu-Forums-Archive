---
title: "a2dp audio has limited dynamic range w/Nokia BH-905 headphones"
date: 2010-12-28
forum: Multimedia Software
---

### Post by talmage on 2010-12-28
I need help improving the quality of the audio I get using A2DP and my Nokia BH-905 headphones.  I get stereo output but the music is telephone quality, not nearly up to the level of these headphones.

I used the suggestion from [this thread]("http://http://art.ubuntuforums.org/showthread.php?t=1596054") to install pavucontrol, which I use along with pacmd to select the A2DP profile for the headphones.

For Bluetooth, I'm using a brand new IOGEAR USB micro adapter that claims to be compatible with BT 2.1 and A2DP.

I'm using a fresh installation of 64-bit KUbuntu 10.10 with all current updates on a Toshiba Portege R-705 laptop.

---

### Post by talmage on 2010-12-28
I also installed bluez-btsco and set 

```
SCORouting=PCM
```

in /etc/bluetooth/audio.conf.

---

### Post by talmage on 2011-01-29
I fooled around with the KDE System Settings.  It seems that the VLC Phonon back end is better than than the Xine Phonon back end.  The VLC back end sounds much less compressed than the Xine backend, which I was using when I posted my request for help a few weeks ago.

At this point, I think A2DP is about as good as it's going to get on my little laptop. :guitar:

---

