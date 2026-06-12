---
title: "v4l-DVB driver on Ubuntu 11.04 | /dev/dvb not found"
date: 2011-07-06
forum: Multimedia Software
---

### Post by muzartior on 2011-07-06
I tried to use my prof-7500 dvb card on ubuntu but...

-Desktop specifications:

Distro: Ubuntu 11.04 
Kernel: 2.6.38-8-generic & 2.6.38-8-generic-pae
Graphic card: geforce 7400

-Installed drivers ( Additional Drivers ):

NVIDA accedlerated graphics driver (version 173)
Firmware for DVB cards

-lsusb 

Bus 001 Device 002: ID 3034:7500 (I think this is my prof-7500)

==========

1. the latest driver dwonloaded from [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)
2. extract & moved it to /usr/src
3. sudo apt-get install build-essential mercurial linux-headers- `uname -r`
4. reboot
5. terminal > uname -r > 2.6.38-8-generic-pae (before installing the above packages it was 2.6.38-8-generic)
6. cd /usr/src/v4l-dvb*
7. sudo make > output -> [http://paste.ubuntu.com/638998/](http://paste.ubuntu.com/638998/)
8.google google and google again -->found [http://ubuntuforums.org/showthread.php?t=1305228](http://ubuntuforums.org/showthread.php?t=1305228) & [http://ubuntuforums.org/showpost.php?p=10962665&postcount=17](http://ubuntuforums.org/showpost.php?p=10962665&postcount=17) 
9. git clone git://linuxtv.org/media_build.git
10. cd /media_build
11. ./build.sh | --> completed
12. sudo make & sudo make install
13. reboot
14. ls /dev/dvb --> ls: cannot access /dev/dvb: No such file or directory
15. ls /dev/v4l --> ls: cannot access /dev/v4l: No such file or directory
16. terminal > modprobe -l > output -> [http://paste.ubuntu.com/638995/](http://paste.ubuntu.com/638995/)
17. hope somesone can help
18. sorry for my bad english

---

