---
title: "Compiz and kwin not working with composition, metacity works"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rang501 on 2011-03-10
I had some trouble getting composition to work with xorg 1.10rc2 and nvidia 270.29. Everything works when I don't use any effects. When I enable composition then everything seems to be freezed but it's not, because I can move my mouse. Weird thing is that I can drag and resize windows but I don't see any change. 
I installed latest nvidia drivers (270.30) and xorg server (1.10) from xorg-edgers today, it didn't help. Same redrawing/repainting issue.
When I use metacity, composition works. I disabled all kwin-s plugin, same.
Any help?

**UPDATE: unchecking "Enable direct rendering" in systemsettings helped, even with default plugins loaded.**

xsession-errors does not contain anything really serious. 
```
OpenGL vendor string:                   NVIDIA Corporation
OpenGL renderer string:                 GeForce Go 7300/PCI/SSE2
OpenGL version string:                  2.1.2 NVIDIA 270.30
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
Driver:                                 NVIDIA
Driver version:                         270.30
GPU class:                              NV40/G70
OpenGL version:                         2.1.2
GLSL version:                           1.20
X server version:                       1.10
Linux kernel version:                   2.6.38
Direct rendering:                       yes
Requires strict binding:                no
GLSL shaders:                           limited
Texture NPOT support:                   yes
kwin(4292): ""fsrestore1" - conversion of "0,0,0,0" to QRect failed" 
QDBusObjectPath: invalid path ""
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
Object::connect: No such signal KWindowSystem::windowChanged(WId,unsigned long*)
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -2) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGridLayoutEngine::addItem: Cell (1, 1) already taken
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(4309)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
```

```
ControllerWindow::resizeEvent QSize(1280, 97) 
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
klauncher(4273)/kio (KLauncher): SlavePool: No communication with slave. 

QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::end: Painter not active, aborted
```


```

X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x1e17831
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x1e1bc70
QMetaObject::invokeMethod: No such method BusyWidget::toolTipAboutToShow()
QMetaObject::invokeMethod: No such method BusyWidget::toolTipHidden()
OpenGL vendor string:                   NVIDIA Corporation
OpenGL renderer string:                 GeForce Go 7300/PCI/SSE2
OpenGL version string:                  2.1.2 NVIDIA 270.30
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
Driver:                                 NVIDIA
Driver version:                         270.30
GPU class:                              NV40/G70
OpenGL version:                         2.1.2
GLSL version:                           1.20
X server version:                       1.10
Linux kernel version:                   2.6.38
Direct rendering:                       yes
Requires strict binding:                no
GLSL shaders:                           limited
Texture NPOT support:                   yes
plasma-desktop(4309)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!

```

---

### Post by walmis on 2011-04-13
I'm having the same problem on my laptop with geforce go 7300. On my desktop PC with 9800GT everything works fine, it seems there's a problem with 7300 series cards.

---

