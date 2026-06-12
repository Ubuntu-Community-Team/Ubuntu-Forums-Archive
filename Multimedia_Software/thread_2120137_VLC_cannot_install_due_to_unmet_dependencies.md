---
title: "VLC cannot install due to unmet dependencies"
date: 2013-02-25
forum: Multimedia Software
---

### Post by rpk94 on 2013-02-25
I tried installing vlc, but I got the following error
> The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.5-0ubuntu0.12.04.1) but 2.1.0~~git20130225+r2486-0~r92~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.5ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.5ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.4 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

What can I do to solve this issue?

---

### Post by mc4man on 2013-02-25
> **rpk94 said:**
> I tried installing vlc, but I got the following error

What can I do to solve this issue?

I would think you know that you are or were using the videolan master daily ppa.

So if you **are using, (ppa enabled), & wish to continue doing so** then just run - 
```
sudo apt-get update && sudo apt-get install vlc
```  
(you may have updated before all the new packages were avail.

If you were using & **no longer have the ppa enabled & don't want to use **then - 
```
sudo apt-get purge vlc-data && \
sudo apt-get update && sudo apt-get install vlc

```

---

### Post by rpk94 on 2013-02-25
That worked thanks. But why doesn't it show the DBus interface option?

---

### Post by mc4man on 2013-02-26
> **rpk94 said:**
> That worked thanks. But why doesn't it show the DBus interface option?

That should be automatically enabled now.
If referring to being in the sound menu & not showing then,  either - 

Open vlc > Tools > preferences & change something, save. (Like only one instance, whatever. 
Then close & re-open vlc, should be there in menu.

Or > dconf-editor > com.canonical.indicator.sound > add vlc to "interested-media-players".  screen

---

### Post by rpk94 on 2013-02-26
I tried the dconf method and it worked. My original goal was to have it recognize the media keys on my keyboard. So I have achieved that too. Thanks.

---

