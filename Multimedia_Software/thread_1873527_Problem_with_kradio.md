---
title: "Problem with kradio"
date: 2011-11-01
forum: Multimedia Software
---

### Post by jkapsi on 2011-11-01
Hi!

I try to open kradio and it starts and load the plugins. But after that it minimizes itself and when I right-click at the indicator icon no options are revealed.
Do you have any idea how to solve this?

I tried to load it from terminal. I post here the results:

```

initializing kradio lirc plugin
kradio: could not connect to socket
kradio: No such file or directory
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
kbuildsycoca4(9962) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/autodesk/maya2012-x64/desktop/Autodesk-Maya.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kradio4(9943): ""geometry" - conversion of "0,0,0,0" to QRect failed" 
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.374'
kradio4(9943): ""geometry" - conversion of "0,0,0,0" to QRect failed" 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5400051
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5400051
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5400012
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5400012

```

Thank you in advance for every advice

---

### Post by gordintoronto on 2011-11-01
Are you using KDE? What version? What V4L or V4L2 radio receiving hardware is installed in your computer?

---

### Post by jkapsi on 2011-11-01
No i'm not using kde. I have ubuntu 11.10 with unity.
I have a pixelview playtv pro with radio. It was working with gnomeradio in older versions.

---

### Post by gordintoronto on 2011-11-01
Have you tried gnuradio?

---

### Post by jkapsi on 2011-11-03
I installed gnuradio but i didn't find new installed software. Did i install new program or just libraries?

Thx for the help so far!

---

### Post by jkapsi on 2011-11-03
And gnomeradio has disappeared from repositories and from my programs after updating in ubuntu 11.10!

---

