---
title: "Qt4 problems with VLC"
date: 2010-05-15
forum: Multimedia Software
---

### Post by Peedjay on 2010-05-15
Since my latest update to Ubuntu Lucid, VLC is no longer working. When starting VLC, I get an impractical dark interface that doesn't response to any command.
vlc -v gives this output:

```
VLC media player 1.0.6 Goldeneye
    [0x9d7f668] main libvlc warning: cannot load module `/usr/lib/vlc/gui/libqt4_plugin.so' (/usr/lib/vlc/gui/libqt4_plugin.so: undefined symbol: _ZN9QListData7append2ERKS_)
    [0x9e2e6d0] main demux warning: no access_demux module matching "file" could be loaded
    [0x9d7f668] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
    [0x9e5bfa0] main generic error: no dialogs provider module matched "any"
    [0xb7400e48] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
    [0xb7400e48] skins2 interface: skin: subX author: Martin Poehlmann
    [0xb7400e48] skins2 interface warning: non-unique id: time
    [0xb7400e48] skins2 interface warning: non-unique id: songticker
    [0xb7400e48] skins2 interface warning: non-unique id: main.normal.dbuttons.info
    [0xb7400e48] skins2 interface warning: non-unique id: eq.onoff.lef
    [0xb7400e48] skins2 interface warning: non-unique id: eqwin.normal.titlebar.menu
    [0xb7400e48] skins2 interface warning: non-unique id: eqwin.normal.titlebar.clos


```

it looks like a Qt4 problem, I have installed Qt4 with all possible dependencies, re-installed vlc several times but no effect! cvlc as proposed doesn't react :(
Can someone give me a hint here? Thanks for your help!

---

### Post by mc4man on 2010-05-15
try starting vlc as such and see
```
vlc --reset-config --reset-plugins-cache
```

---

### Post by Peedjay on 2010-05-16
Thanks for the hint, mc4man, but no fully positive reaction! The interface reacts a bit better (equalizer and play-list show up) but e.g. selecting a folder to open, is still impossible.

Your code gives this output:
```
VLC media player 1.0.6 Goldeneye
[0x8551668] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
[0x8718410] main generic error: no dialogs provider module matched "any"
[0xb6700d60] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0xb6700d60] skins2 interface: skin: subX  author: Martin Poehlmann

```

Maybe someone a suggestion how to do a complete reinstall of Qt4 and how make sure that plug-in gets installed?

---

### Post by mc4man on 2010-05-16
Not sure how you got yourself into this 'situation'

There should be no need to compile qt4 libs and seeing the default interface for vlc is qt4 installing vlc should of installed what was needed.

Maybe try 
```
sudo apt-get clean && sudo apt-get update
```

Then try re-installing libqtcore4 and libqtgui4 (or just remove both and start over (you'll lose a few apps and libs, no big deal - they can be re-installed

After try 
```
vlc -I qt4
```

---

### Post by kv300 on 2010-12-01
hving the same problem with vlc since i installed Autodesk Maya 2011... I have tried everything above but nothing works..... :/ Any ideas?

---

