---
title: "No sound after mess with i386 and amd64 packages"
date: 2013-05-14
forum: Multimedia Software
---

### Post by daniel488 on 2013-05-14
Hi,

couple of days ago I realized that I can't install one deb package, because it couldn't install ia32-libs. I started googling and tried some solutions. Some of them forced to install a few packages, I remember that there was also something with Alsa.
After this modifications and reboot I don't have sound in system. In sound settings the sound output at the bottom of the window is not enabled (greyed). In alsamixer it looks good, master is not on 0 level. From this steps: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") the long command from 1. step helps me:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

 But the sound is only after first reboot, after next one I don't have sound again. 

Can you help me? My system is Ubuntu 13.04 64bit.

---

