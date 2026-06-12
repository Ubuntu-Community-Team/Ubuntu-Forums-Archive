---
title: "Trick for dealing with multiple sound cards"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by badrunner on 2008-01-15
I was in the situation earlier where some apps (primarily wine) just refused to use my audigy as the default soundcard. I have the onboard one loaded for use with a headphone/mic setup, and use the audigy for everything else.

Regardless of what i did with asoundrc (setting audigy2 as default, much tinkering etc.) I couldnt get some wine apps (although some worked) to use the audigy, and sound would come through the phones. Even the Test button in winecfg would use the phones, so i decided to try forcing the audigy to be sound card 0.

Now there are a lot of posts reccomending blacklisting the driver for the onboard card etc. but thats useless when you want both cards to be available. In the end i found a neat little trick in /etc/modprobe.d/alsa-base

There are lots of lines like the following:

```
options snd-bt87x index=-2
```

Simply adding one for the onboard driver means i have my pci audigy as card 0 now and it loads the onboard as card 1, very very happy. In my case the line to add is:

```
options snd-hda-intel index=-2
```

---

### Post by mouseclone on 2008-02-12
This was just what I was looking for.  I also have an Audigy card as a secondary.  This worked great to get Wine playing sound on the Audigy.  Thanks for the tip.

---

