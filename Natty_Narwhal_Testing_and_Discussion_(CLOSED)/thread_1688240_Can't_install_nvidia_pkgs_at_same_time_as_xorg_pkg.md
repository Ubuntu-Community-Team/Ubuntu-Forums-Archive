---
title: "Can't install nvidia pkgs at same time as xorg pkgs."
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 1hutchy on 2011-02-15
I'm Using the "Development Release Ubuntu 11.04 Alpha2" & I have tried a number of times to install Nvidia pkgs through either Jockey,synaptic & command line etc..  & it will not allow nvidia & xorg-server pkgs to be installed at same time. If I try & install the xorg pkgs it then uninstalls the Nvidia pkgs & vice versa. I cannot get nvidia driver to work this way it seems Which means I cant use the "dpkg-reconfigure xserver-xorg" command if xorg is not installed at same time.
I dont remember this ever happening before with any other versions of Ubuntu I have used.
It doesnt matter what type of nvidia driver I try to install or what order the pkgs are installed it seems.
Any ideas anyone .Thanks

---

### Post by s.fox on 2011-02-15
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by ratcheer on 2011-02-15
The proprietary nVidia driver is currently incompatible with the current Natty Xorg. See all the gory details in this thread:

[http://ubuntuforums.org/showthread.php?t=1675614](http://ubuntuforums.org/showthread.php?t=1675614)

Tim

---

### Post by 1hutchy on 2011-02-15
Thanks for your time, I think I understand preety well, I may have to wait for a newer nvidia driver by the sound of it.Or experiment abit?

---

### Post by Yofel on 2011-02-15
You'll need to wait, nvidia hasn't released a compatible driver for xserver 1.10 yet.

---

### Post by VMC on 2011-02-15
> **Yofel said:**
> You'll need to wait, nvidia hasn't released a compatible driver for xserver 1.10 yet.

This appears to be Natty's mantra. I haven't had a display since before Alpha 2.

---

