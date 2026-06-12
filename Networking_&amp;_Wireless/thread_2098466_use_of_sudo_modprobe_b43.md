---
title: "use of sudo modprobe b43"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by welshmike on 2012-12-26
Typing sudo modprobe b43 on a terminal once Ubuntu has completed booting gets a wifi connection of my PC to my router successfully.
Is there a way of doing this automatically such as running a bash script as a startup program?

I've tried a System>Preferences>Startup Applications>Startup Programs of bash /home/ross/Documents/connect where the connect file contains:
> ##!bin/bash

sudo modprobe b43

exit

but this does nothing.
Any advice welcomed please.

---

### Post by welshmike on 2012-12-26
Well the bash script was OK but I needed to invoke using
not
> bash /home/ross/Documents/connect
but
> xterm -e /home/ross/Documents/connect
My thanks to kerry_s [http://ubuntuforums.org/showthread.php?t=368812](http://ubuntuforums.org/showthread.php?t=368812) (message #2)

---

### Post by steeldriver on 2012-12-26
IMHO it would be better to put it (without sudo) in /etc/rc.local - or simply add the module name to /etc/modules - both of which would load it at boot time

---

### Post by welshmike on 2012-12-27
> **steeldriver said:**
> IMHO it would be better to put it (without sudo) in /etc/rc.local - or simply add the module name to /etc/modules - both of which would load it at boot time
My system does not have those folders so I guess I need to create one of them.

---

### Post by welshmike on 2012-12-27
Well being naive and totally ignorant I did
 
sudo gedit /etc/modules
This showed the following for editing:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

So below the lp I added b43

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43

I saved the file and rebooted.

**Hooray. Wireless connectivity to my router achieved. **:guitar::guitar::guitar:

Now why or why in everything I've read didn't the internet blurb state simply what to do. Grrr. ](*,)](*,)](*,)
.. or am I completely thick? :rolleyes::rolleyes:

---

