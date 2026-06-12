---
title: "From AVI TO DVD"
date: 2008-07-01
forum: Multimedia Software
---

### Post by rotary12 on 2008-07-01
Hi all, Ive been looking for program to convert AVI to DVD, did find Avidemux,but is complicated and dont know if it works,looking for something like ConvertoDVD

---

### Post by marklid on 2008-07-01
Install Devede, job done !

---

### Post by aeiah on 2008-07-01
i use a python script i made, along with nautilus actions (same sorta method as the imdb thing that's linked in my profile). you'll have to edit the paths to things, as i doubt you have a hard drive called giantpeach ;)

```
#! /usr/bin/python

import sys, os, optparse, os.path

print "========================================"
print "about to create a dvd..."
print "========================================"

from optparse import OptionParser
parser = OptionParser()
parser.add_option("-i", "--input", action="store", type="string", dest="video")
(options, args) = parser.parse_args()

os.system("mkdir /tmp/iso")
os.system("ffmpeg -i " + `options.video` + " -target pal-dvd /tmp/iso/1.mpg")
os.system("dvdauthor -o /tmp/dvdparts/DVD/ -t /tmp/iso/1.mpg")
os.system("dvdauthor -o /tmp/dvdparts/DVD/ -T")
os.system("mkisofs -dvd-video -v -o /tmp/iso/DVD.iso /tmp/dvdparts/DVD")
os.system("rm -r /tmp/dvdparts/DVD/")
os.system("rm /tmp/iso/1.mpg")
myPath = options.video
(dirName, fileName) = os.path.split(myPath)
(fileBaseName, fileExtension)=os.path.splitext(fileName)
os.system("mv /tmp/iso/DVD.iso /media/giantpeach/film" + `fileBaseName` +".iso")
raw_input('Hit enter to remove intermediary files')
print "removing files and folders DVD, 1.mpg that were used during processing"
os.system("rm -r /tmp/dvdparts/DVD/")
os.system("rm /tmp/iso/1.mpg")

```

with this i just right-click on a .avi file and i can select 'convert to dvd' from the menu (once i add it with nautilus-actions)

there's also tovid or gui programs like devede and mandvd if you want to create menus or are converting episodes to dvd.

---

