---
title: "Photo slideshow software"
date: 2009-03-20
forum: Multimedia Software
---

### Post by abandonedthe_mulletator on 2009-03-20
I have been trying for some time to get a decent photo slideshow program to run on linux.  I don't need anything fancy I just want to make a slideshow of my photos to share with friends and family that is visually attractive.

There are some like dvd-slideshow with its various frontends.  I've heard a lot about Manslide and SMILE but they only work under KDE and I use gnome.  The available programs for gnome are difficult to install and use.  There are a huge amount of these kind of programs for Mac and Windows that are incredibly easy to use and produce excellent effects.  I had to suck up my Linux pride and use a Windows computer to get the results I want.  If there is a decent easy photo slideshow program for gnome where the hell is it?

---

### Post by cotcot on 2009-03-21
You can use smile under Gnome as well. (the installation will require quite some kde stuff to be installed but that does not mean to you need to leave gnome).
Here is how I installed it. 
> INSTALLING SMILE - located at [http://smile.tuxfamily.org/](http://smile.tuxfamily.org/) I selected 0.6.4 for American Friends. NOW 0.6.6. 
[FYI: "DOWNLOAD" in French is "Téléchargement" If you wish,read the 'Smile' site in English by using Google-Translate.]

Unzip the file from the site into the directory/folder where you want to put it, for example “smile”.

Go to the directory where you just decompressed it; example: 

cd /home/g/smile



Compile SMILE with qt4 using these two commands:
/usr/bin/qmake-qt4 smile.pro 
make

---

