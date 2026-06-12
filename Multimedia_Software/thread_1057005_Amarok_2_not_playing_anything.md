---
title: "Amarok 2 not playing anything"
date: 2009-02-01
forum: Multimedia Software
---

### Post by ravee on 2009-02-01
I installed Amarok 2 on fresh install of ubuntu 8.10..it worked.. but after installing KDE 4.1, Amarok 2 is not playing anything.. its loading main window but throwing following error when I'm trying to play a mp3 file

```

amarok(6050) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics()
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(6050) Plasma::Applet::save: saving to "1"
amarok(6050) Context::ContextView::setContainment: "" Line:  599
amarok(6050) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(6050) Plasma::Applet::save: saving to "2"
amarok(6050) Plasma::Applet::save: saving to "3"
amarok(6050) Plasma::Applet::save: saving to "4"
amarok(6050) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6050) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir(QString)
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(6050) MagnatuneConfig::load: load
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x460000c
QPixmap: Invalid pixmap parameters
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x1a6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    155 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x46003db
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x46003dc
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003db
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003db
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x46003dc
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003de
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003dd
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x46003db
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x46003dc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x46003db
QPixmap: Invalid pixmap parameters
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x1a6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    155 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x46003ef
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x46003f0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003ef
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003ef
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x46003f0
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003f2
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003f1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x46003ef
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x46003f0
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x46003ef
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x1a6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    155 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x46003f6
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x46003f7
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003f6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003f6
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x46003f7
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003f9
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003f8
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x46003f6
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x46003f7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x46003f6
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x1a6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    155 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x46003fd
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x46003fe
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003fd
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x46003fd
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x46003fe
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x4600400
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x46003ff
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x46003fd
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x46003fe
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x46003fd
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x1a6
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    155 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x4600404
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x4600405
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x4600404
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x4600404
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x4600405
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x4600407
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x4600406
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x4600404
X Error: RenderBadPicture (invalid Picture parameter) 179
  Extension:    155 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x4600405


```

I tried one of the solution found for the same problem:
i.e deleting all my personal config files (.kde/share/apps/amarok and .kde/share/config/amarok*) but still It's not working :(

Please help me out..

Thanks in advance :)

---

### Post by darcio53 on 2009-02-11
Hi, I had the same problem, solved for me with:

sudo apt-get install libxine1-ffmpeg

Bye.

---

### Post by rsmseys on 2009-06-05
Thanks! This helped me solve the same issue.

---

### Post by cruzer45 on 2009-06-09
> **darcio53 said:**
> Hi, I had the same problem, solved for me with:

sudo apt-get install libxine1-ffmpeg

Bye.

Thanks that solved my issue.

---

