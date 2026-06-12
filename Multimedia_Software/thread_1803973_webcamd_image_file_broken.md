---
title: "webcamd image file broken"
date: 2011-07-14
forum: Multimedia Software
---

### Post by kraylus on 2011-07-14
for kicks i decided i'd give webcamd a shot. after setting it up, i've managed to get it to take a snapshot ever 30 seconds and upload an image to my site.

downside is that the image it uploads says it contains errors. you can see for yourself [here]("http://www.brazensanity.com/webcam.jpg"). however, in the ~/.webcamd/ folder, there's an image called pre-webcam.jpg that works just fine. (the file in that same dir called webcam.jpg has the same error as the uploaded image, so it's safe to assume the image doesnt get corrupted on the way to my website).

my question is, why does webcam.jpg not work when the pre-webcam.jpg does?

short of figuring this issue out and getting webcamd to upload a working image, could someone direct me to an easy way to write a simple script i could cron so i could just tell it to upload pre-webcam.jpg and rename it to webcam.jpg and not even let webcamd handle ftp operations? i wouldn't even know a way to ftp stuff via commandline or where to being looking. i tried googling but wasnt very successful.

thanks for the help!

ryan

---

### Post by SoFl W on 2012-01-21
I know this is an older topic but I am working on this problem as well.  It seems to be the "put_date = " feature.  If you turn it off everything works fine.  When it is turned on, the image becomes corrupt. 
I would like the image time stamped but I am looking how to fix it.

**Edit:**
I ended up switching to "fswebcam" for my capturing program, very easy to set up, you can title and date stamp the image as well as the filename.  Has several options.
I use ncftp's ncfttpput from the command line to upload the image to the server.  
I then created a bash script to call fswebcam, wait five seconds for the program to finish writing the file, and then call ncfttpput to upload.  I call this script from crontab.  Works like a charm, however charms work.

---

