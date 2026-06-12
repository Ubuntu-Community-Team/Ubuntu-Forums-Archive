---
title: "How to switch video cards?"
date: 2018-10-22
forum: Multimedia Software
---

### Post by linuxhippy on 2018-10-22
I installed Mythbuntu 16.0.4.5 fresh from an AMD64 DVD last week.  At the time I only had integrated video which worked but was choppy and this is the video setup that mythbuntu automatically detected.  Today I got an old PCI ATI Radeon 9250 video card that seems to work but it's even more choppy than the integrated video and I imagine it needs a driver.  How do I switch cards without doing a fresh install so it's automatically detected?  I recorded some shows I'd like to watch so I don't want to reinstall again.

Marty

---

### Post by linuxhippy on 2018-10-24
I wound up doing a fresh install to see if it automatically got the driver and it did not.  I see there's a bunch of packages for xorg xserver in the synaptic repos and there's a lot for ATI.  I tried to install one that had ATI Radeon cards in it but couldn't and I think it's because it wanted to uninstall packages the upgraded system had installed.  How can I install the needed ATI Radeon9250 drivers?  

Maybe I have to build them from source?  I found this page:

[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI")

Marty

---

### Post by QIII on 2018-10-24
Note the last time that the cited page was updated -- 10 years ago.  Just the fact that it still has ATI branding is a tell.  It took only a few years after AMD bought ATI for that branding to be discontinued.

The fact is that with modern Linux releases, that card will just not have a proprietary driver that will work with modern X Server.  That's not just Ubuntu.

AMD stopped supporting those cards years ago.

You are probably running the default open-source Radeon driver, which is good, but the card is very long in the teeth and probably not up to modern demands.

Unfortunately, there is likely little you can do about it.

Just to be sure, would you please post the results of 
```
lsmod | grep radeon
```

---

### Post by linuxhippy on 2018-10-24
Looks like it is running radeon modules already.  Here's the output u asked for:

radeon               1478656  6
i2c_algo_bit           16384  3 cx88xx,cx88_vp3054_i2c,radeon
ttm                   106496  1 radeon
drm_kms_helper        172032  1 radeon
drm                   401408  9 drm_kms_helper,radeon,ttm


So, is there a video PCI card that would still work with TV and Mythbuntu?

Marty

---

### Post by QIII on 2018-10-24
There may be, but I wouldn't hold my breath.  PCI is old and slow.  Any card that you might still find would be fine for office tasks, but I'm not sure you would find one that would be up to our expectations for video these days.

---

### Post by linuxhippy on 2018-10-25
Looks like upgrading my PVR box to a new motherboard with PCI express slots is in my future.  Now I'm wondering if PCI tuner cards are less receptive than newer PCI express tuner cards since I'll probably have to replace those too.  

Marty

---

