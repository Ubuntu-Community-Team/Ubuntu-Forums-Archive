---
title: "Problem playing DVDs in mplayer"
date: 2009-12-06
forum: Multimedia Software
---

### Post by Lyon on 2009-12-06
This is something I've done many times, and a DVD I've played thousands of times on Ubuntu before, but after doing a clean installation of Ubuntu on my laptop, for some reason I am having problems playing certain DVDs that I never had a problem with before.

I have installed libdvdcss2 and the gstreamer extra plugins from the software center. Every time I open the DVD in movie player it asks me to search for a suitable plugin. When I cancel, the first episode of the series begins, but I cannot get to the DVD menu. The episode just repeats once it's complete.

This is really frustrating, I've never had this kind of trouble with DVDs in Ubuntu before, and this is a DVD I've always played in ubuntu

---

### Post by wilee-nilee on 2009-12-06
w32

---

### Post by User3k on 2009-12-06
I use VLC, might work better if all else fails.

---

### Post by mc4man on 2009-12-06
vlc should work fine, as far as totem you'd need the bad and ffmpeg plugins

To d. check run this ( most of the useful plugins),  or look in synaptic.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Lyon on 2009-12-06
I tried vlc but for each episode, I have to go back to the main menu, it just stops at the end of each episode if I choose play all.

I don't know what w32 is but I assume it's a 32-bit library. I'm running on Ubuntu 9.10 64 Bit

---

### Post by JBAlaska on 2009-12-06
To get all the useful stuff do:
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdcss2
sudo /usr/share/doc/libdvdread4/./install-css.sh
```

---

### Post by Lyon on 2009-12-06
> **mc4man said:**
> 
To d. check run this ( most of the useful plugins),  or look in synaptic.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

Did the trick, thanks :)

---

### Post by mc4man on 2009-12-06
> sudo apt-get install ubuntu-restricted-extras

While running that in karmic isn't the worst thing, the package is slightly misconfigured. (& lucid

It will install the 'stripped' ffmpeg libs which may not be the intention of some for running it, for others it might not matter.

( whether it gets changed or not, who knows, a bug was filed/confirmed quite some time ago

---

### Post by dogscoff on 2009-12-06
> **mc4man said:**
> While running that in karmic isn't the worst thing, the package is slightly misconfigured. (& lucid

It will install the 'stripped' ffmpeg libs which may not be the intention of some for running it, for others it might not matter.

( whether it gets changed or not, who knows, a bug was filed/confirmed quite some time ago

OK, so what should Karmic users do instead? I have been having DVD troubles since Jaunty and Karmic hasn't fixed them. Maybe "stripped" lib this is the cause?

---

### Post by wilee-nilee on 2009-12-06
W32 codecs is in medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
So this with libdvdcss2, non-free-codecs, and the restricted extras of your distribution are generally what you need. Additionally as one poster suggested VLC is a good addition so is smplayer, which is attached to MPlayer.

---

