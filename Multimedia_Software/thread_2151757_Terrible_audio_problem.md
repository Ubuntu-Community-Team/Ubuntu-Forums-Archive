---
title: "Terrible audio problem"
date: 2013-06-05
forum: Multimedia Software
---

### Post by red96123 on 2013-06-05
I've ubuntu 13.04 and I unfortunely touched some alsa settings, then audio doesn't work. I tried many ways to restore audio but it doesn't work. Oss don't work in this version on ubuntu. help

---

### Post by ohnonot on 2013-06-07
no, definitely not oss. ubuntu is using pulseaudio on top of alsa.

what exactly did you "touch" and how?

---

### Post by anpalcactus on 2013-06-07
Maybe try reinstalling drivers?
I had a problem like this and used (i think) both these commands in Terminal (i'm not sure which one helped actually, but they two did so)

```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```


```
sudo alsa force-reload
```

---

### Post by ohnonot on 2013-06-07
that long one-liner looks like overkill to me; you're basically reinstalling half of your system with that. this is doing much, much more than just 'reinstalling drivers' as anpalcactus stated.
it might work, it might not.
better to try to fix things first, before going in with a ball-and-chain.

---

