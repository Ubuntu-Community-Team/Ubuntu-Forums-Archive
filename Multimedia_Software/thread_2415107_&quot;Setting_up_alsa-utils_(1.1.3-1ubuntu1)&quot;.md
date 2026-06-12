---
title: "&quot;Setting up alsa-utils (1.1.3-1ubuntu1)&quot; never succeeds or ends"
date: 2019-03-20
forum: Multimedia Software
---

### Post by rachelwu21 on 2019-03-20
Hi, I've been trying to get my Ubuntu 18.0.4 desktop to detect headphones. I tried to fix it by installing the top package from [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages) , but that only broke all my sound so it showed "Dummy Output".

I've tried to fix it in several ways, but every time I try something it gets stuck at the line "Setting up alsa-utils (1.1.3-1ubuntu1) ..." and never proceeds.

My latest attempt is running 
```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`"
```

But the result is the same. Nothing happens when I try running "alsamixer", I can't even stop it with Ctrl+C, I just have to close the terminal. The pacmd daemon doesn't respond. And every time I try to fix it with a command form somewhere it gets stuck at "Setting up alsa-utils (1.1.3-1ubuntu1) ...". Does anyone know how to fix this?

---

### Post by slickymaster on 2019-03-20
Thread moved to **Multimedia Software** for a better fit

---

