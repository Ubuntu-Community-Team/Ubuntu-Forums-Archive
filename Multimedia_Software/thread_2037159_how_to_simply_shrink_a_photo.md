---
title: "how to simply shrink a photo"
date: 2012-08-03
forum: Multimedia Software
---

### Post by karrank% on 2012-08-03
got some jpg photos that are too big for my phone, want to shrink the files to transfer, is there a simple way to do that? (gimp is not working/too complicated for me to comprehend) 

Fspot doesn't seem to have an option for this.

Thanks for looking.

---

### Post by The Cog on 2012-08-03
imagemagick is probably the package you want. Then something like:
```
convert -resize 100x100 picture.jpg
```

---

### Post by papibe on 2012-08-03
Hi karrank%.

If you don't mind using the terminal, it is very easy:
```
convert  original.jpg -resize 640x480  new_shrink.jpg
```
Regards.

---

### Post by hakermania on 2012-08-03
Ah, Gimp isn't so complicated as for the resize option:
Just open the image, click on the resize:
[IMG]http://i.imgur.com/8YawR.png[/IMG]
Do the resize and notice the values (X,Y):
[IMG]http://i.imgur.com/JttjN.png[/IMG]
After the resize, give Ctrl+N to create a new image and give it the last values. Then Ctrl+C the resized image and Ctrl+V to the newly created image. Data! Save the image and you're done.

Alternative, if you still don't like it:
```

sudo apt-get install imagemagick
convert input.png -resize 100x100 output.png

```

---

### Post by karrank% on 2012-08-03
Thanks, you folks are the greatest!

Installed fotoxx while I was looking around and did a one-button resize which seemed to work--

Will look into imagemagick soon.

---

### Post by papibe on 2012-08-03
:D

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

### Post by oldfred on 2012-08-03
I downloaded two different image resizer into Nautilus using synaptic. But I do not remember which is which and I prefer one.

nautilus-image-manipulator.
It is highly inspired by Nautilus Image Converter:
    [http://www.bitron.ch/software/nautilus-image-converter.php](http://www.bitron.ch/software/nautilus-image-converter.php)

nautilus-image-converter 
This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.

---

### Post by karrank% on 2012-08-12
papibe, thanks for reminding me, several other fora (unrelated to this) I frequent don't have this option.

---

### Post by mike acker on 2012-08-13
SHOTWELL gives an option to RESIZE when you save as. has cropping tool, nice basic stuff

what we need is IRFANVIEW for Linux

---

### Post by bcarlowise on 2012-08-14
> **mike acker said:**
> SHOTWELL gives an option to RESIZE when you save as. has cropping tool, nice basic stuff

what we need is IRFANVIEW for Linux

I use irFanview in Ubuntu....just install wine/winetricks and then use winetricks to install atmlib, mfc42, msxml4, vcrun2005 & vcrun6. Without one or more of those windows add-ons, irfanview will not install.

---

### Post by Cheesemill on 2012-08-14
XnView, which was always my favourite image editor for Windows now has a Linux version called XnView MP (Multi-Platform).
[http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033](http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033)

Before this was released I used [Pinta]("apt://pinta") for all of my basic editing tasks.

---

