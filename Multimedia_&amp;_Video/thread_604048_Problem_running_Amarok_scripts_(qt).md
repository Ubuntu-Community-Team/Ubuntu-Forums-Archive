---
title: "Problem running Amarok scripts (qt?)"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by sprice on 2007-11-05
Ubuntu Feisty 64bit
Amarok 1.4.7

Here's the error message when I try to run the Web Control Script in Amarok
First it says ```
PyQt (Qt bindings for Python) is required for this script.
```

Here's the details of the error
```

Traceback (most recent call last):
File "/usr/share/apps/amarok/scripts/webcontrol/WebControl.py", line 43, in ?
from qt import *
ImportError: No module named qt

```

Version of Python
```

#dpkg-query -l "python"
--
ii  python         2.5.1-0ubuntu3 An interactive high-level object-oriented la
--

```

I believe I have the necessary QT bindings, here's everything
```

#dpkg-query -l "*qt*"
--
un  dbus-qt-1            <none>               (no description available)
un  dbus-qt-1c2          <none>               (no description available)
un  gtk2-engines-qtpixma <none>               (no description available)
ii  libavahi-qt3-1       0.6.17-0ubuntu3      Avahi Qt3 integration library
un  libdbus-qt-1-1       <none>               (no description available)
ii  libdbus-qt-1-1c2     0.62.git.20060814-2b simple interprocess messaging system (Qt-based shared li
un  libqt-dev            <none>               (no description available)
un  libqt-mt-dev         <none>               (no description available)
un  libqt-perl           <none>               (no description available)
un  libqt0-ruby1.8       <none>               (no description available)
un  libqt3               <none>               (no description available)
ii  libqt3-compat-header 3.3.8really3.3.7-0ub Qt 1.x and 2.x compatibility includes
un  libqt3-dev           <none>               (no description available)
un  libqt3-emb           <none>               (no description available)
ii  libqt3-headers       3.3.8really3.3.7-0ub Qt3 header files
un  libqt3-helper        <none>               (no description available)
un  libqt3-i18n          <none>               (no description available)
ii  libqt3-mt            3.3.8really3.3.7-0ub Qt GUI Library (Threaded runtime version), Version 3
ii  libqt3-mt-dev        3.3.8really3.3.7-0ub Qt development files (Threaded)
un  libqt3-mt-mysql      <none>               (no description available)
un  libqt3-mt-odbc       <none>               (no description available)
un  libqt3-mt-psql       <none>               (no description available)
un  libqt3-plugins-heade <none>               (no description available)
un  libqt3c-mt           <none>               (no description available)
un  libqt3c102-mt        <none>               (no description available)
ii  libqt4-core          4.3.0-4ubuntu1~feist Qt 4 core non-GUI functionality runtime library
un  libqt4-debug         <none>               (no description available)
un  libqt4-designer      <none>               (no description available)
ii  libqt4-gui           4.3.0-4ubuntu1~feist Qt 4 core GUI functionality runtime library
un  python-qt-dev        <none>               (no description available)
ii  python-qt3           3.17-0ubuntu3        Qt3 bindings for Python
un  python-qt3-dbg       <none>               (no description available)
un  python-qt3-doc       <none>               (no description available)
un  python-qt3-gl        <none>               (no description available)
ii  python-qt4           4.1-0ubuntu6         Python bindings for Qt4
un  python-qt4-dbg       <none>               (no description available)
un  python2.3-qt3        <none>               (no description available)
un  python2.3-sip4-qt3   <none>               (no description available)
un  python2.4-qt3        <none>               (no description available)
un  python2.4-qt4        <none>               (no description available)
un  python2.4-sip4-qt3   <none>               (no description available)
un  python2.5-qt3        <none>               (no description available)
un  python2.5-qt4        <none>               (no description available)
ii  qt3-dev-tools        3.3.8really3.3.7-0ub Qt3 development tools
un  qt3-doc              <none>               (no description available)
un  qt3-tools            <none>               (no description available)
un  qt4-designer         <none>               (no description available)
un  qt4-qtconfig         <none>               (no description available)

--

```

---

### Post by sprice on 2007-11-06
*bump*

---

### Post by Atmuh on 2008-01-23
I have the exact same problem

---

### Post by dzark on 2008-02-01
Me too. No solution :(

---

### Post by SFN on 2008-02-07
Same problem here trying to run the Amarok XM Tuner Script.. Here's how I fixed it.

That particular script needs python-qt3. I'd imagine which version you would need would vary based on what you're trying to run so you may need python-qt4. In any even, I did:

```
sudo apt-get install python-qt3
```

This script also needs pycurl so I also did:

```
sudo apt-get install python-pycurl
```

That script works now.

Hope this helps.

---

