---
title: "alsa-utils not starting"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by t.achim on 2007-05-13
Hi,
After rebooting, I didn't have any sound. I looked in System Services, and alsa-utils wasn't running. After trying to start it, I get the following error:
```

tudor@tudor-desktop:~$ sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                                   * warning: 'alsactl restore' failed with error message 'alsactl: set_control:991: warning: name mismatch (Master Playback Volume/Master Playback Switch) for control #1
alsactl: set_control:993: warning: index mismatch (0/0) for control #1
alsactl: set_control:1106: bad control.1.value.0 content'...             [ OK ]
tudor@tudor-desktop:~$

```

---

### Post by deadgobby on 2007-05-13
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by t.achim on 2007-05-13
Solved...
```

sudo alsactl store
sudo /etc/init.d/alsa-utils start

```

---

