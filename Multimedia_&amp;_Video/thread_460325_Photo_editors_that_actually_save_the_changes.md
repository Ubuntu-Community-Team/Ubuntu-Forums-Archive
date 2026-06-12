---
title: "Photo editors that actually save the changes?"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by PartisanEntity on 2007-05-31
I used Picasa to rotate an image, however Picasa does not seem to actually rotate the image because when I use Nautilus to navigate to the image the thumbnail shows it as un-rotated and if I open the image using Gimp or Image Viewer it is un-rotated.

It is as if Picasa simply remembers how you would like to view each image but it doesn't save the changes?

I have many images that I would like to rotate and to actually save the rotation edit, I tried F-Spot but when I open the images in Gimp they are also un-rotated.

Is there any image editor that actually really does edit the image and save the changes so that all other applications will see the change?

For example in windows I used to use ACDSee to edit many images and the changes were saved.

---

### Post by Toadmund on 2007-05-31
GIMP works for me.
Well, GIMP can rotate, and keeps it like that if you save it that way.

---

### Post by PartisanEntity on 2007-05-31
Yes Gimp works of course, I also realised that gThumb does it too. But what about selecting more than one image to edit, I don't know if Gimp does batch editing.

---

### Post by stani on 2007-06-01
I've started to work on a new graphic program especially designed for photo batching with a graphical user interface (GUI).  The first version will be fairly simple, no preview yet and only a few plugins (scale, rotate, save, invert, ...). I originally develop it for Ubuntu, but I might port it to Windows and Mac in the future. Progress is going fine, so beta testers will be welcome. If someone is interested in beta-testing my program at a later stage, please send me a private message with your email.
Stani

Everyone with knowledge of PIL (Python Image Library) can easily write plugins for it. There is no need for GUI programming, as my program will take care of it. So anyone who wants to write a plugin (as simple as rotate, invert, contrast, ...) please contact me as well.
--
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by PartisanEntity on 2007-06-02
> **stani said:**
> I've started to work on a new graphic program especially designed for photo batching with a graphical user interface (GUI).  The first version will be fairly simple, no preview yet and only a few plugins (scale, rotate, save, invert, ...). I originally develop it for Ubuntu, but I might port it to Windows and Mac in the future. Progress is going fine, so beta testers will be welcome. If someone is interested in beta-testing my program at a later stage, please send me a private message with your email.
Stani

Everyone with knowledge of PIL (Python Image Library) can easily write plugins for it. There is no need for GUI programming, as my program will take care of it. So anyone who wants to write a plugin (as simple as rotate, invert, contrast, ...) please contact me as well.
--
[http://pythonide.stani.be](http://pythonide.stani.be)

Sounds interesting, thanks for posting, I will check it out.

---

### Post by stani on 2007-06-02
The only way to check it out at the moment is by contacting me by private message or email as it is nowhere released yet.

---

### Post by PartisanEntity on 2007-06-02
> **stani said:**
> The only way to check it out at the moment is by contacting me by private message or email as it is nowhere released yet.

I have sent you a PM stani

---

### Post by carusoswi on 2007-06-02
> **PartisanEntity said:**
> I used Picasa to rotate an image, however Picasa does not seem to actually rotate the image because when I use Nautilus to navigate to the image the thumbnail shows it as un-rotated and if I open the image using Gimp or Image Viewer it is un-rotated.

It is as if Picasa simply remembers how you would like to view each image but it doesn't save the changes?

I have many images that I would like to rotate and to actually save the rotation edit, I tried F-Spot but when I open the images in Gimp they are also un-rotated.

Is there any image editor that actually really does edit the image and save the changes so that all other applications will see the change?

For example in windows I used to use ACDSee to edit many images and the changes were saved.

I haven't used Picasa for a while, but, if I remember correctly, you have to "export" the image after altering it if you want to write changes to disc.  I remember thinking to myself that Picasa was an interesting program, but could not figure out why some of the commands and procedures seemed to be named and carried out in a manner that most would not find intuitive.  Saving files is one example.

I find gmail to be equally annoying in that manner.  I rarely use the gmail interface directly, preferring to use my Mozilla to access and download messages instead.  But, on occasions when I am accessing from a remote computer and have to use the interface, I find it annoying that task selection is sort of all over the place and not where an experienced (or perhaps old fashioned, whatever) computer user would expect to find it.  I see no value in having to search (or learn) where the reply button is, or the attachments button.  Put that stuff together in one place (top, bottom or either side) on the screen so you know where to look for everything - leave creative and catchy design for some other application.

ok, end of rant.

Caruso

---

### Post by mahiyar on 2007-06-03
Well its all because picasa does not touch (by design) your original photos. There is a save option in windows (right click save) which then moves your original pictures to another folder marked original, but that option is not there in Linux. Instead you can do this >>file>save copy or >>file>export image.

---

### Post by westli on 2007-06-03
You can run many processes in batch mode with ImageMagick.  You have to do some research and you will learn about the command line while doing so, but it can be a timesaver if you have a lot of images to manipulate.

---

### Post by stani on 2007-06-06
The very first alpha version of my photo batch processor is available for testing:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

