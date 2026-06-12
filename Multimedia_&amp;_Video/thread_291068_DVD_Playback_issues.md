---
title: "DVD Playback issues"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by saitoh on 2006-11-02
I recently installed Ubuntu 6.10 and I am trying to enable the libdvdread3 package. I am in the directory and I can see the file install-css.sh, I have execute permissions. But whenever I try sudo install-css.sh it says command not found. What am I doing wrong?

---

### Post by yabbadabbadont on 2006-11-02
sudo ./install-css.sh

The current directory is not in the root user's path.

---

### Post by oryaaaaa on 2006-11-02
~$ sudo apt-get install libdvdread3
~$ sudo /usr/share/doc/libdvdread3/install-css.sh
~$ sudo apt-get install totem-xine

---

### Post by saitoh on 2006-11-02
Thanks for the help guys.

---

