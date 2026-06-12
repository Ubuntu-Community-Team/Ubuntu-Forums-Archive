---
title: "Eye of Gnome (eog) shows irritating warning with tif files"
date: 2017-12-31
forum: Multimedia Software
---

### Post by harry332 on 2017-12-31
The eog shows each time I open a tiff file (tagged image file format) this "warning" or "information" message:

"This image contains multiple pages. Image Viewer displays only the first page. Do you want to open the image with the Document Viewer to see all pages."

The reason to this is that Nikon creates a tiff file which contains two images, the main image is the full image itself and the second is a thumbnail if it.
There are no pages here, and this is not a document, it is an image file.
So the warning file is erraneous.

This is actually intentional act and not a bug. But it doesn't make the issue go away.
I cannot simply make this ugly blue information bar silent, not to appear again.

I want to be able to show the images full screen. The eog does this okay, but the warning bar appears each time and I have to shut it down each time.
Does anyone know a better application to show tiff images full screen.
Windows does this just fine, without any warnings.

---

### Post by coffeecat on 2017-12-31
@harry332, you posted this in the Ubuntu Development sub-forum which is for development versions only, but you do not state which release version you are using. If by chance you are using 18.04, this occurs in 16.04 as well, and probably all current versions of Ubuntu. So....

*Thread moved to **Multimedia Software**.*

Yes, that is correct. Strapline for Multimedia Software sub-forum:

> The place for your multimedia software questions: everything about using software for audio, video and image editing, display, or viewing and listening.

And point of information - not just Nikon. I get this with tif's created from a 35mm scanner.

---

### Post by harry332 on 2018-01-02
Coffeecat,

Actually I did not say this is specific only for Nikon.
The reason EOG behaves like this is if a tiff contains multiple images, then EOG shows this warning.
If tiff contains only one image, the warning is of course not shown.

And yes you are right about the Eye of Gnome version. This is the way it has been working for a long time.

---

### Post by Yellow Pasque on 2018-01-02
Gnome devs don't like user options. Maybe if you install dconf-editor and look for eog's settings there, you will find something. Don't bet on it though.

---

### Post by harry332 on 2018-01-05
No, nothing in dconf-editor that can change this odd behavior.
Eog is the only app that does this. Shotwell doesn't, Evince doesn't ...
What is the image viewer in KDE?

---

