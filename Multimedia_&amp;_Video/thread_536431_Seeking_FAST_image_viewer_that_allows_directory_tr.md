---
title: "Seeking FAST image viewer that allows directory tree browsing"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by cinematography on 2007-08-27
I work as a photographer and I take over 1,000 pictures a week. I need a viewer that'll let me look through these pictures as quickly as possible using the directory trees I create.

I've tried gthumb, gwenview, f-stop, picasa, gqview, gtksee, and digikam.

gthumb and gwenview both load large images fairly slow. I've tried lowering the view quality on both of these programs, but it still takes about 2 to 3 seconds for each picture to load. I know this may not sound like a lot, but when you have to go through thousands of pictures, this rate can become extremely tedious.

f-stop and picasa (my current favorite) are both fast but they won't let me broswe folders. I have to import the folders first. f-stop, like digikam, waste space by making a copy of all my pictures during import, and picasa kills the order I put my pictures in by sorting everything by date.

My main questions:
* Is there a way to do directory tree browsing with Digikam or Picasa?
* Could I add something to Digikam to make it view .psd files?
* Are there any other image viewers I could try?

Any help with this would be greatly appreciated.

---

### Post by Haegin on 2007-08-27
You could try the command line tool feh. It is very powerful once you get to use it and seems to be able to load images quickly though I lack any massive pictures.

If you set the default program to open an image with to "/usr/bin/feh" after installing the feh package then double clicking the image will open it in feh. This won't limit the image to the size of the screen so if the image is too big you will only get part of it. To fix this you can add the fullscreen option by adding " -F" to the command. This will cause photos larger than the screen to fit to the screen.

You can also use feh from the command line to scroll through whole directories of images.

Other useful options are:
-r : recursive = travel down into subdirectories. e.g. "feh -r ~/Images" which lets you navigate all images in the ~/Images folder and any folders below that in slideshow mode (use the arrow keys to navigate through)
-d : draw the filename at the top right of each image
-t : thumbnail mode = shows a set of clickable thumbnails which when clicked show the full size image.

You could use nautilus scripts to let you right click on a directory and open it in feh with appropriate options if you want to or you can create individual scripts as slideshows if you end up showing lots of different groups of people the same set of snaps with one command instead of ages on Open Office Impress.

For more information see the feh manpage included in the feh package and [online]("http://pwet.fr/man/linux/commandes/feh") or check the [feh website]("http://linuxbrit.co.uk/feh/")

---

### Post by Haegin on 2007-08-27
I haven't a clue about speed for the following but I found some more image viewers for you to try:

[http://gimmage.berlios.de/index.html](http://gimmage.berlios.de/index.html)

[http://laas.altervista.org/cooka/ckaindex.php](http://laas.altervista.org/cooka/ckaindex.php)

Both of those projects have debs available for Ubuntu on their respective websites.

Finally there is a whole list of image viewers for Gnome here:
[http://www.gnomefiles.org/subcategory.php?sub_cat_id=35](http://www.gnomefiles.org/subcategory.php?sub_cat_id=35)

---

### Post by cinematography on 2007-08-27
Thank you for the reply.

Feh is pretty decent. Its no ACDSee, but it loads the images much faster than the other image viewers I've tried. What makes Feh load the images so quickly? Is it some kind of image viewing engine or something?

---

### Post by K.Mandla on 2007-08-27
+1 for feh, it's about as fast as they come. You can use it from within Midnight Commander, and that would be exceptionally fast.

I usually use Xfe and Mirage; Xfe will do thumbnailing, and I can trigger Mirage on double-click if I want a larger version. You can also open a whole folder at a time with Mirage, but it doesn't handle directory trees like you describe; it's really only previous-next navigation.

---

### Post by Haegin on 2007-08-27
> **cinematography said:**
> Thank you for the reply.

Feh is pretty decent. Its no ACDSee, but it loads the images much faster than the other image viewers I've tried. What makes Feh load the images so quickly? Is it some kind of image viewing engine or something?

Try [GTKSee]("http://gtksee.berlios.de/") if you want. That claims to be similar at least to ACDsee (not that I am familiar with either).

[IMLib2]("http://docs.enlightenment.org/api/imlib2/html/") is the library feh uses to access images.

---

### Post by -SpaZ on 2007-08-27
[Eye of Gnome]("http://www.gnome.org/projects/eog/") is pretty good.

---

### Post by cinematography on 2007-08-27
Thanks a lot for the replies and suggestions. 
:guitar:

I'm going test as many of these programs as I can and post my review in this thread later tonight.

---

### Post by cinematography on 2007-08-27
Forced image importing and auto sorting may be nice features for the novice (people who are easily confused by the concept of a directory tree), but for everyone else directory tree browsing is typically the preferred method for looking through a large image collection.

At any given time I usually have about 10 model galleries on my hard drive, containing between 200 - 400 pictures each. Because of deadlines, I must sort these pictures, stamp them with my name, create a web gallery, and have the gallery sent out within 2 - 3 days.

To work efficiently, I need a very versatile image viewer with some image editing and batch processing capabilities; rotate, resize, rename, convert, brightness, contrast, gamma, watermarking, web gallery creator. If I must, I can always use another program for watermarking and making web galleries.

Before I decided I wanted NOTHING else to do with Microsoft Windows, and that I would ONLY use Linux and/or a Mac from now on, I used a program called ACDSee.

I've tried many of the image viewing programs for Linux; Digikam, Feh, Gimmage, GQView, gThumb, GTKSee, Gwenview, Kuickshow, KView, Mirage, Picasa, Showimage, and XNView. Of the programs I tried, I found 4 favorites. 

**Kuickshow**, like Feh, is incredibly fast, but it lacks features. **gThumb** has great features, but it is one of the slowest viewers I tried. **DigiKam** is fast with nice features, but it uses the annoying "folder import" method, and lacks some of the features and neatness of gThumb. And **XNView** has the most features, and can view more image formats than any of the others (including .psd), but its a little too slow for large galleries.

If I had to rank them: 
1) XNView
2) Digikam
3) gThumb
4) Kuickshow (only for speed)

If I could find a way to make XNView view images as fast as Kuickshow, I would be a very happy camper. :) Maybe I could write a program that makes a 90% or 80% compressed copy of my galleries, and these galleries could be used for quick reference, and the changes made to these reference images would be made to the real / fullsize images. I'm not much of a programmer though. :( I only know Python and some C++. But its an idea.

Computer Specs -
OS: Xubuntu 7.04
Processor: 3ghz Intel Celeron D
RAM: 512mb
Video: 126mb ATI

---

### Post by cinematography on 2007-09-27
**Update:** With [KIPI]("http://extragear.kde.org/apps/kipi/") plugins, Digikam is an even better program for image galleries. The plugins add a lot of nice batch processing features. I still wish I could just browse folders with Digikam, but it'll do for now.

---

### Post by nhooey on 2007-10-02
Picasa is alright, and pretty fast. It just has a few problems, which is odd coming from Google.

The slideshow feature is stupid, and restricted to only showing images in the same directory.

The timeline also has pixelitus on my machine, and during the slideshow the photos have pixelitus until you mouseover the bottom of the screen and load the overlay. (You can unload the overlay again by moving the mouse away, and the pixelitus will be gone for the rest of that slideshow).

It also has stupid keyboard shortcuts, and no fullscreen button. There's some obscure fullscreen shortcut using ctrl+alt while mouseovering your photo of choice, but this is pretty dumb.

I'm surprised Google made so many mistakes in such a good image viewer.

---

### Post by MCMcButtah on 2007-10-02
> **cinematography said:**
> **Update:** With [KIPI]("http://extragear.kde.org/apps/kipi/") plugins, Digikam is an even better program for image galleries. The plugins add a lot of nice batch processing features. I still wish I could just browse folders with Digikam, but it'll do for now.

I am kind of confused by this because I organize and sort my pictures in a directory style and view it this way with digikam. Granted it does index them and you can't browse to the files directly, but I don't see the distinction. They are listed and displayed the same way in konqueror as they are in digikam. Let me clarify...here is an example of some of the directories in my /media/seagate500/canonpics pictures folder.

2006-05-23 North Lake Escarpment Hike
2007-01-01 New Years Party
2007-09-01 Moe. Down

When I check them out in digikam this is how they appear as well. Are all your pictures not in the same place? You can add multiple albums in digikam though no? I have about 50,000 pics across hundreds of dirs and it manages it well.

I used to be all about ACDSee, because it was a really fast way to zip through jpegs. But when I took my photography to a more professional level (i.e shooting raw only) ACDSee just didn't cut it anymore because of its lack of raw support and features. I started using adobe bridge for everything but it was pretty slow and painful to use. When I switched to linux digikam was an awesome surprise. It let me zip through my raw files the way I used to go through my jpegs using acdsee and it is nice to be able to do quick edits on them. The newest version of adobe bridge that just came out (ships only with photoshop cs3) is a huge improvement fyi and raw images now load as fast as digikam. I use bridge now running under windows XP in vmware and ya know...its actually pretty fast. I havn't needed to boot into windows for photo editing in forever thanks to that setup.

---

