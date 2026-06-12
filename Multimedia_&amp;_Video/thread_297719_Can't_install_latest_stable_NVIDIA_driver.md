---
title: "Can't install latest stable NVIDIA driver"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Dave_Jackson on 2006-11-11
Since the latest NVIDIA drivers came out a few days ago, I have been attempting to install them on my Kubuntu Edgy installation with no success. I downloaded the .run file from the NVIDIA driver site. I then stopped the X server (stopped KDM) and installed it. Afterwards, when it reboots, the X server won't start at all. I am faced with just a console. 

This is after I have told the NVIDIA install program to alter my XOrg.Conf file. I reinstall Kubuntu and try again, this time altering the XOrg.conf file myself, taking out the "Load DRI" line and changing it to Driver "nvidia". Still no sucess and no X server. What am I missing? This was never that difficult before. ](*,)  Thanks in advance.

---

### Post by skunkworks on 2006-11-11
It is recommended to enable the "restricted" repositories and install the ubuntu package via apt-get.  Open a terminal and type:

```

sudo nano /etc/apt/sources.list

```

And insert these lines:

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy restricted

```

Or if you use Dapper Drake:

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper restricted

```

Save that, then do:

```

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig

```

---

### Post by Dave_Jackson on 2006-11-11
Thanks for your reply, but will this get me the latest stable version 9629 of the drivers that came out a few days ago?

---

### Post by tseliot on 2006-11-11
Try Envy 0.7.1:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Dave_Jackson on 2006-11-11
Thanks very much, tsEliot. The envy program worked flawlessly and all is great now. I really appreciate you taking the time to respond.

---

