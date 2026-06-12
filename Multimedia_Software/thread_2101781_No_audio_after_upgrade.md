---
title: "No audio after upgrade"
date: 2013-01-05
forum: Multimedia Software
---

### Post by ubu10 on 2013-01-05
I upgraded to Ubuntu 12.04. I do get welcome music while logging in but thereafter there is no audio at all. Apparently, the system fails to detect audio hardware. Everything is greyed out (inaccessible) in sound settings. Any help?

---

### Post by shantiq on 2013-01-05
hi ubu...  this has happened to me many times on various versions of Ubuntu at first
Later on it seems to settle once a few updates have gone through...


This sometimes works

reload 2 or three times ;  sometimes it clicks in sometimes not


===========

this also but probably not if greyed-out


once you have loaded Ubuntu
open your systems monitor gui or open
```
gnome-system-monitor
```   find pulse audio then right-click and kill  ...

it is very off-putting since sound is a basic need on a machine; i wish you the best...   someone will come along with cleverer tricks no doubt

---

### Post by Yellow Pasque on 2013-01-05
What shantiq refers to (killing/restarting) pulseaudio can be accomplished easily with one command:
```
pulseaudio -k
```

Indeed, it does sound like a pulseaudio issue since sound works before login (when pulse starts). Some folks who upgrade releases have to remove their pulseaudio user configuration files so that pulse will generate fresh ones. Use the following command and log out/in.
```
rm -rf ~/.pulse*
```

---

