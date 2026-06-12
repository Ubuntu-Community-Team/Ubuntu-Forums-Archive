---
title: "Editing video metadata"
date: 2009-06-21
forum: Multimedia Software
---

### Post by mirzmaster on 2009-06-21
Hi,

How can one edit the metadata in a video file?  Checking Nautilus' properties for a .avi file does not reveal the ability to edit the file's metadata.

---

### Post by elvinatom on 2009-08-01
I gotta bump this, because I wonder about the same thing.  I just encoded a mkv video in avidemux and when I play the video it says "avidemux" in the title.  Or as an alternative, does anyone know how to set the title in avidemux?

---

### Post by Kprojekt on 2009-09-30
bump

---

### Post by mirzmaster on 2009-09-30
Thanks for bumping, guys.  This is still an open question for me.

---

### Post by cor2y on 2009-09-30
Depending on your media container (avi, mp4,mpeg etc) you will need different tools.
For example mkvtoolnix allows you to add metadata to files you put into the mkv container and as far as i know this is the only app that has a gui frontend for use that does this.
For the others like avi,mp4,mpg wmv1 wmv2  output you can use mencoder or ffmpeg
Ffmpeg (Works with mp4,avi,mpeg,wmv1,wmv2,mkv output)
```
 ffmpeg -i file.avi -vcodec copy -acodec copy -metadata title="Dancing Bear" -metadata comment="Title Created Using FFmpeg metadata tag" outputfile.avi
```for mencoder (only works  AVI output)
```
 mencoder -ovc copy -oac copy file,avi -info name="Dancing Bear" -info comment="File Title Created with Mencoder Info tag "  -o outputfile.avi
```There's also ogmtools as well with which you can metadata to files put in the ogm container using ogmmerge, unlike mkvtoolsnix there is no gui 
```
ogmmerge --title "Dancing  Bear" --comment "File Title Created Using OgmMerge" file.avi  -o outputfile.ogm
```Finally for wmv1/wmv2/wmv3/asf files there is the closed binary of asfbin you can use the linux binary (cmdline only) or the windows based gui version that works with wine [http://www.radioactivepages.com/index.php?section=software&docid=asfbin](http://www.radioactivepages.com/index.php?section=software&docid=asfbin)

---

### Post by mirzmaster on 2009-10-04
cor2y:  Thanks so much.  Your post was very helpful and exactly what I was looking for.  It's just too bad that there isn't a way to edit the metadata of the file container without going through an encoding operation (even though it's a simple copy).

---

### Post by cor2y on 2009-10-05
Glad i could help but to be fair i dont think there are even are windows tools that allow this without the use of copying the codec and creating a new file first.
Even asfbin has to create a new output file if you didnt specify the metadata info etc during the original encode. :D

---

### Post by xpd259 on 2012-01-24
I have a video I made with handbrake 
and I'm trying to add a year metadata tag but it doesn't show
is this a bug with nautilus on gnome3 or a just me 
:confused:
Thanks

**** T

---

### Post by overdrank on 2012-01-24
Please start a new thread with your issues. Back to sleep thread.
Thread closed.

---

