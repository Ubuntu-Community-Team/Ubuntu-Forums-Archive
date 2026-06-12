---
title: "Windows Gimp and UFraw help?"
date: 2009-09-20
forum: Multimedia Software
---

### Post by billdotson on 2009-09-20
My father uses a Nikon D50 camera and I am trying to set up GIMP to use UFraw so he can use the GIMP tools to edit the .NEF files. Currently when I open an .NEF file it can open it from GIMP's file>open but it just opens the image in UFRaw's standalone window/editor.

He is using Vista and hasn't tried giving Linux a chance, sorry..

---

### Post by billdotson on 2009-09-21
help..?

---

### Post by bapoumba on 2009-09-21
Moved to Multimedia.

---

### Post by hydrotemplar on 2009-09-21
try this:
[http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/)

---

### Post by mcduck on 2009-09-21
> **billdotson said:**
> My father uses a Nikon D50 camera and I am trying to set up GIMP to use UFraw so he can use the GIMP tools to edit the .NEF files. Currently when I open an .NEF file it can open it from GIMP's file>open but it just opens the image in UFRaw's standalone window/editor.

He is using Vista and hasn't tried giving Linux a chance, sorry..

That's how it works, the UFRaw plugin doesn't make Gimp capable of handling RAW files, it only allows you to do the RAW editing and then move the file to Gimp itself for further edits.

So the file still has to be converted to normal 8-bits/color channel before Gimp can handle it, the only difference between UFRaw plugin and standalone UFRaw is that the plugin can be started through Gimp and will automatically move the files to Gimp after you are ready editing the RAW image.

---

