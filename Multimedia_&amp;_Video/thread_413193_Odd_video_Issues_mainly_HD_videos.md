---
title: "Odd video Issues mainly HD videos"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by lando786 on 2007-04-18
Hello, 
I have got some really weird video issues on my laptop, ive been using Ubuntu for a while and ive installed several video players and codecs (i hope this mixing and matching has nothing to do with it). My problem is that with both HD wmv and mov files i cant seem to run them, now the wmvs never worked but the movs worked and do work sometimes under VLC other times it just runs and the program crashes and closes really fast, this is really frustrating as i dont wanna reboot into windows and itd be great if i can stay away from windows completly after fixing this. Any help would be appreciated

---

### Post by crispy_420 on 2007-04-19
If they crash, launch the media player from command line/terminal. If it crashes you will see a reason for it. Post that here.

---

### Post by lando786 on 2007-04-19
```
lando@lando-laptop:~$ wxvlc
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

---

### Post by crispy_420 on 2007-04-19
what about if just issue vlc?

---

### Post by lando786 on 2007-04-19
you mean like this? or are you suggesting changing program cuz mplayer and all the others do the same
```
lando@lando-laptop:~$ vlc
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

---

### Post by crispy_420 on 2007-04-20
In System -> Preferences -> Multimedia Systems Selector what is your video set to?

---

