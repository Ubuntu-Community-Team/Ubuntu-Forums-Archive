---
title: "App to transfer photos from camera"
date: 2011-02-05
forum: Multimedia Software
---

### Post by LonelyAspie on 2011-02-05
On Windows. when you plug in a memory card/SD Card or camera, a ting would pop up and ask you if you want to export them to wherever. The best thing about it, is that you can put in a title for the photos, and it will rename all the selected photos to whatever title to put in like example

dsc028.jpg
dsc029.jpg
dsc030.jpg to

Walking On The Beach 1.jpg
Walking On The Beach 2.jpg
Walking On The Beach 3.jpg etc.

These are just examples. I've tried a few apps like gThump, the default one that comes with Ubuntu and another one and they don't seem to d that. So I copy them off the card manually and rename them myself.

Is there an app that'll do this for me? I would really appreciate it.

---

### Post by xc3RnbFO8P on 2011-02-05
I use [**Irfanview**]("http://www.irfanview.com/") ,you need to install **Wine** first (Ubuntu Software Center)


[[img]http://ompldr.org/tN2F6OA[/img]](http://ompldr.org/vN2F6OA)

---

### Post by meles on 2011-02-16
There are many applications in Ubuntu that will download pictures from a memory card or digital camera. 
In my opinion, digiKam does the best job of importing images, since it's doing it very similarly to the digital camera applications (Canon, in my case). 
You do this from the menu "Import", with one of the three options on top (Cameras, USB Storage Devices or Card Readers). It will download the images in folders, by the dates the pictures were taken. Also, it will remember the already downloaded images, so the next time you download images, you just hit "Select New Items" and it will download only the last images.

As for batch renaming picture files, you can use KRename. It has many options for renaming files, also for what you need. 

Both digiKam and KRename are in the repositories. You find them in the Ubuntu Software Center

---

### Post by ac_d600 on 2011-02-16
Try "Rapid File Downloader" a very nice program.

[http://www.damonlynch.net/rapid/](http://www.damonlynch.net/rapid/)

---

### Post by starrygordon on 2011-02-23
In reference to this general problem, I would like to do the following:

1.  Transfer the images from the camera to a directory of my choosing
(and not a set of date-named directories a la iPhoto);

2.  Rename the images as I please (I have a formula which will identify
the camera, the date, and the image, and which avoids name collisions;

3.  Delete the images from the camera.

I would like to avoid GUI interaction during the transfer procedure.
I can look at and play with the pictures later.

I could do this easily with programmatic access to the files.

If I take the memory card out of the camera and stick it in my
Asus EeePC (also running Ubuntu) the card appears under /media/
as a hierarchy of directories and files, and I can easily do this.
However, it would be more convenient sometimes to transfer the
files over the camera's USB cable directly to my large computer.
However, when I insert the cable and turn the camera on, although
the system notices and a box asking me if I want to run F-Spot pops
up, I can't find the memory card or the pictures in the file hierarchy
and consequently can't do what I want.  F-Spot, shotwell, and gphoto2
all do more than I want and things I don't want.  There is probably a
simple, dumb solution here but I haven't come across it yet.

---

### Post by inobe on 2011-02-23
digikam

[http://www.digikam.org/drupal/about?q=about/features](http://www.digikam.org/drupal/about?q=about/features)

when i plug in my camera, i am prompted with several choices, one of which is 'open with digikam'

---

### Post by starrygordon on 2011-02-23
Thanks for the reply.  I did not choose to go with digiKam, but mention of
it did get me to look at their web site, which caused me to revisit gphoto2
successfully -- it will do what I want.

Now, if I could only configure my Eee to work with Skype, or vice versa....

---

### Post by inobe on 2011-02-24
starting a new thread would be a good idea.


> Now, if I could only configure my Eee to work with Skype, or vice versa.... 

---

