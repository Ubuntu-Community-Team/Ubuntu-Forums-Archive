---
title: "Playing a DVD ?"
date: 2010-03-21
forum: Multimedia Software
---

### Post by lucasart on 2010-03-21
Hello everyone.

Sorry I'm going to ask a question that millions of people have asked before me. I can't play DVD with Ubuntu 9.10 out of the box. I have followed the "how to" section in sticky threads. It is incredibly long and complicated, gets you to install a millions things, and I don't have a clue what they are. In the end it simply doesn't work. Also I'm talking about encrypted DVDs of course.

Is it possible to install just a *few* free software and play my DVD with the built in Movie Player. Also, I am using the 64 bit version of Ubuntu Karmic Koala.

Thank you

---

### Post by hansdown on 2010-03-21
Hi lucasart.

Click system> administration> synaptic package manager.

Install

```
libdvdcss2

```
Also

```
ubuntu restricted extras
```

Should be good to go.

---

### Post by lucasart on 2010-03-22
Unfortunately that doesn't work either. In the packager ubuntu-restricted-extras there's probably 90% stuff that's irrelevant to DVD playing. And the package libdvdcss2 doesn't exist in the reposity for Ubuntu 9.10 x64 :(

---

### Post by mc4man on 2010-03-22
Assuming you didn't run the ubuntu-restricted-extras
(never use that here

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

Then to get libdvdcss2
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Your biggest issue may be that totem isn't the best dvd player - it may work ok or not very well

vlc is better for dvd's

```
sudo apt-get install vlc
```

---

### Post by lucasart on 2010-03-23
Thank you su much mc4man !!!
It's the kind of thing that's never documented properly anywhere. All these "how to" are riduculously complex and get you to install tonse of useless stuff you have no clue what it is. This is simply getting the CSS, the missing part from Ubuntu as I believe for legal reasons they couldnt package it in ubuntu

And to hell all the DRM ! I can't wait for the blue ray to be cracked too :)

---

