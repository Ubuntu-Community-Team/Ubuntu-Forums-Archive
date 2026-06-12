---
title: "[SOLVED] F-Spot: Sharing Photos and Photo Database Between Multiple Users and Machine"
date: 2008-09-24
forum: Multimedia Software
---

### Post by stefanadelbert on 2008-09-24
I've been trying to setup multi-machine access to F-Spot Photos and database on my home network. I've run into a problem where pictures imported from one machine aren't being displayed in F-Spot on another machine because the path to the picture location is stored literally (as an absolute path) in the database.

Here is my current setup in some more detail:

I have a desktop (Mythbuntu 8.04, Gnome) acting as a Media Centre and fileserver. My photographs and the F-Spot database are on that fileserver in a directory shared via Samba.

I have a laptop (Ubuntu 8.04) that I would like to use to browse, modify and import photos using F-Spot, but using the photos and F-Spot database on the fileserver. I have managed successfully to import photos via F-Spot on the laptop into F-Spot on the server. After the import the photos are in the correct location on the fileserver (the shared directory) with the correct user and access permission. The photos are browsable and viewable from the fileserver. However, the photos imported from the laptop cannot actually be opened in F-Spot on the server even though F-Spot knows that they exist.

I have the same problem when using F-Spot on the laptop to browse photos that were originally imported using F-Spot on the fileserver. If I view metadata (View | Metadata Browser) for the problem photos I get an error message claiming that the file does not exist and giving a path.

It's not really surprising that the file can't be found because the file location path that is being stored in the database is the absolute path to the file relative to the machine that imported the file.

This means that if my F-Spot on my laptop refers to photo directory /home/stefan/photos, which is in turn a symlink to /mnt/photos which is where the Samba shared directory is mounted, then any photos imported from the laptop will have path /home/stefan/photos/* as far as F-Spot is concerned.

From the fileserver perspective, these files are actually being stored in /media/multimedia/Photographs/*, but F-Spot uses the path stored in the database (/home/stefan/photos/*) and can't find the photo at that location/

I've included a screenshot from my laptop showing a thumbnail for one photo that I successfully imported onto the fileserver from the laptop via F-Spot. The other photos show no thumbnails as they were originally imported from the fileserver. Also shown is the Metadata Browser for one of the photos imported from the fileserver.

Please let me know if you have achieved a similar setup and how you got it working. Any ideas greatly appreciated.

Many thanks
Stefan

---

### Post by vanadium on 2008-09-24
This would probably work if you make sure that the path to your pictures is the same on the local machine as it is on the server. This is easily accomplished in linux, either with symbolic links or even by mounting the network files in a suitable location.

On the server, your pictures are under /media/multimedia/Photographs/

You could create a local /media/multimedia/Photographs/ which actually links to /mnt/photos, or directly mount the pictures in /media/multimedia/Photographs. In all of these ways, the local copy will use and store the same path as that what the server currently uses.

---

### Post by stefanadelbert on 2008-09-27
Thanks, Vanadium. This was a very easy fix! Basically, as long as each F-Spot installation uses the same path to access the Photos, all is good. Easily acheived with symlinks.

I'm not sure how the database would handle with two or more users making changes at the same time, but that shouldn't be a problem with my setup.

Stef

---

### Post by vanadium on 2008-09-27
It is the power of the operating system that allows you to lift limitations in application software. Try this with Windows!
f-spot uses sqlite as its database. Indeed, it is probably a risk to use the same database at the same time with two independent copies of fspot. For a true multi-user approach to work, fspot would need to use a database server such as mysql. Perhaps one day fspot developpers will include support for such a setup. The bibliographic reference software Bibus is an example where you have the option for both systems.

---

