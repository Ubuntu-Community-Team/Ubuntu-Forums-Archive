---
title: "Lucid fresh install Totem won't play DVD iso"
date: 2010-05-10
forum: Multimedia Software
---

### Post by nowhere@cox.net on 2010-05-10
Hey all,

Just upgraded 4 machines from Karmic to Lucid. 2 of them I used synaptic to install ubuntu-restricted-extras and two I used apt-get from command line. The synaptics will not play a DVD iso in totem while the two from the command line will just fine. If I install VLC on the two that don't work, it plays the iso just fine.

I have purged libdvdread4 and reinstalled with no luck. It offends my sense of perfectness that two machines that used to run dvd iso's fine no longer do.

I did read a blog post somewhere that ubuntu-restricted-extras installed via synaptic does not get everything.

Anyone have any insights?

---

### Post by cchhrriiss121212 on 2010-05-10
Open synaptic and check whether libdvdcss2 is installed, if not install it.

---

### Post by wojox on 2010-05-10
It should be:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by nowhere@cox.net on 2010-05-10
Thanks for the replies.

libdvdcss2 IS installed and I did follow the instructions in the second reply about libdvdread4 before posting. No effect. Totem for some reason will not play the DVD iso's. I haven't tried an actual DVD in the drive yet but I will today. This is bizarre...

Any other ideas?

---

### Post by wojox on 2010-05-10
You could try installing medibuntu and non-free-codecs [http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

---

### Post by cchhrriiss121212 on 2010-05-10
If you play the dvd from terminal you will get specific error messages, so try this:
```
totem dvd://
```
Is there any reason why you have to use totem over any of the other video players? If I were in your position I would just switch to vlc.

---

### Post by Stason on 2010-05-10
It'a bug and they do not want to fix it. Use any non-dvdnav/gstreamer player to work around. Xine does fine for me.

---

### Post by Stray Wolf on 2010-05-10
Before the update I had Totem playing dvd's and burning them as iso's which it also played fine.  That was on Karmic.  When Karmic was new digitized lines would appear during dvd/iso play but that went away with a month or two of updates.  Now Totem in Lucid has lines, plus navigating causes it to crash.  I think I'll try VLC too.  Unrelated - if you have lots of photos F-spot is no good...I suggest digikam.  Trust me.

---

### Post by nowhere@cox.net on 2010-05-10
I'm not adverse to other players. I like VLC except I cannot use the arrow keys to skip forward and backwards. 

The main thing is that Totem will play the iso files fine on two machine and not on the others. This means something is not right with two of them that may lead to other problems.

I'm finding a LOT of regressions in Lucid....

---

