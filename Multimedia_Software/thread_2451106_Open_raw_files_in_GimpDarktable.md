---
title: "Open raw files in Gimp/Darktable"
date: 2020-09-27
forum: Multimedia Software
---

### Post by LK_gandalf_ on 2020-09-27
Hi all, I just did a fresh install of ubuntu 20.04, installed Gimp (2.10) from software center, and Darktable (latest version 3.2.1 in software center, which is a snap). The raw files are .nef as I have a Nikon camera.

If I try to open the file with gimp, Gimp loads but I then get two error messages:
- gimp-file-load error openng file /tmp/gimp/2.10/gimp-temp-49461.tif no such file or directory
- plug-in Raw Nikon could not open the image

It doesn't seem that when I open the image from Gimp it gest first opened in darktable, as it should be.

Thanks in advance for any help

---

### Post by ajgreeny on 2020-09-27
Is your gimp installed as the snap version?
Run command 
**snap list**
to see if gimp is listed.
Snaps can limit the use of files, depending on where those files are stored in the file system.  I do not use snaps so can not give you more detail, but if you do have the snap version you can also install the deb version with command 
**sudo apt install gimp**

---

### Post by LK_gandalf_ on 2020-09-27
yes it appears in the snap list:

darktable                3.2.1snap1                  59    latest/stable    kyrofa        -
gimp                     2.10.20                     297   latest/stable    snapcrafters  -

I uninstalled the software center version and installed from terminal as you suggested. Now when I open the raw file "open with gimp" it opens in darktable first and I see the image (which is a step forward!), but when I then close Darktable (and at this point it is supposed to open in gimp), I still get the same two errors as above.

---

### Post by SeijiSensei on 2020-09-27
I'd go look in the directory where the temp file is supposed to reside.
```
cd /tmp/gimp/2.10/
```
Does the directory exist? Do you see anything in it like gimp-temp-49461.tif?

Are you running out of space in the root partition? Run "df" to find out.

---

### Post by LK_gandalf_ on 2020-10-18
Hi, indeed I see no files in the tmp folder. I have space on the disk ;)

---

### Post by SeijiSensei on 2020-10-18
It might be a function of using a snap.  I'd remove the snap version of GIMP and install the regular version.  See if that helps.

---

