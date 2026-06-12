---
title: "Sound problem"
date: 2013-04-18
forum: Multimedia Software
---

### Post by silviutp on 2013-04-18
I have recently removed bluez and I think that's the cause for my sound problem. I cannot here any sound now. I also removed other services since I'm trying to reduce memory usage but none were related with sound (I think).
I have re installed bluez but still no sound. I use Ubuntu 12.04 with xfce.

Any help would be appreciated.

---

### Post by anandu on 2013-04-18
Please go through these links

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#)

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)


Hope this will sort out the issue

Anandu
[www.ananduvr.com](www.ananduvr.com)

---

### Post by silviutp on 2013-04-22
I used the third link and the commands bellow solved the problem. Thank you.
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```


i am unable to mark the thread as solved. maybe an admin can do it, or move it to a more relevant place.

---

### Post by Toz on 2013-04-22
Thread marked as solved.
For future reference, to close a thread, Edit the first post in the thread, select the Go Advanced button and change the Prefix to [SOLVED].

---

