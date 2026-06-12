---
title: "Can't play Quicktime videos after upgrade to Natty"
date: 2011-05-01
forum: Multimedia Software
---

### Post by felipelavinz on 2011-05-01
I recently upgrade to Natty (11.04) from Maverick (10.10) and suddenly I'm unable to play some Quicktime videos on Totem which I could previously play with no problem in Maverick.

I've installed everything I think it should be necessary (ubuntu-restricted-extras, gstreamer and even medibuntu's w32codecs) but still can't solve this.

When trying to play one of these videos, I get the codec search wizard but no results are found

Has anyone seen this issue? Any clues on how to solve it?

---

### Post by shaun_bc on 2011-05-01
|
|
v

---

### Post by shaun_bc on 2011-05-01
try this:

```
sudo apt-get update
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
sudo apt-get update
sudo apt-get -y --allow-unauthenticated install medibuntu-keyring
sudo apt-get update
sudo apt-get -y install w32codecs libdvdcss2 ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg vlc flashplugin-installer
echo "system needs to reboot to finish installation"
```

:)

---

### Post by felipelavinz on 2011-05-02
Thanks for your answer :-) 

... but I already had installed all of these packages (and the medibuntu repositories). Tried to re-install them but still can't get quicktime to play on Totem :-(

---

### Post by felipelavinz on 2011-06-04
It seems that there's a conflict between xbmc packages and some gstreamer codecs... I'll just use VLC instead

---

