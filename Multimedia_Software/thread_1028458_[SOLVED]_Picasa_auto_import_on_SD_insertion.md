---
title: "[SOLVED] Picasa auto import on SD insertion"
date: 2009-01-02
forum: Multimedia Software
---

### Post by celem on 2009-01-02
I use Ubuntu 8.20. I removed F-Spot and loaded Picasa3. The following steps enabled Picasa3 to be auto started when an SD card of photos is inserted, and Picasa then auto-imports the photos. I haven't tried it with a camera via a USB cable simply because I just don't use my camera in that way.

```
mv ~/.local/share/applications/picasa.desktop picasa-import.desktop
```

```
# I did the next step but it may not be necessary
sudo cp ~/.local/share/applications/picasa.desktop /usr/share/applications
```

```
gedit ~/.local/share/applications/mimeapps.list

I added the following line:
x-content/image-dcf=picasa-import.desktop

```

Opened nautilus and went to Edit > Preferences, go to the "Media" tab, and change the "Photos" item to Picasa image viewer.

Gnome now uses Picasa to import photos

---

### Post by snowguy on 2009-01-31
I'm using linux mint 6 based on ubuntu 8.10. I realize this is a different setup but in case anyone else has this issue and a similar setup to mine, fwiw, I couldn't get this solution to work because there is no file at the location specified in the first command and I couldn't figure out how to translate what was being said into something applicable.

---

### Post by celem on 2009-01-31
You may have to first execute Picassa for this file to be created.

---

### Post by jonj on 2009-05-17
There is a script provided by Picasa 3 to set this up. It may be similar for earlier versions, I don't know. Run:

```
sudo /opt/google/picasa/3.0/bin/gnomehalintegration.sh
```

---

### Post by scubasteve657 on 2010-08-29
Seems like maybe you just have to set the media to autoplay to picasa.  Not i am using ubuntu 10.04.  Go to Edit->Preferences, Media tab, as described above, and set the program for photos for the picasa executable, which should be this:

> /opt/google/picasa/3.0/bin/picasa

This line appeared automatically on my mimeapps.list file:

> x-content/image-dcf=userapp-picasa-7ZEYHV.desktop;

So it seems to me you just have to direct nautilus to the picasa executable and everything works fine.

---

