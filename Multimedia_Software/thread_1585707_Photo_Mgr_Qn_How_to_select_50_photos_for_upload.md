---
title: "Photo Mgr Qn: How to select 50 photos for upload?"
date: 2010-09-30
forum: Multimedia Software
---

### Post by ian2112 on 2010-09-30
Hey Folks,

I'm looking for an easy way to solve the following problem.  I have a bazillion photos of my 1yr old daughter and a coupon to get 50 photos printed for free from Costco (online upload over the web).  The photos are spread across a number (20?) of different subdirectories.

I'd really, really like to avoid going through them taking note of the file names, and then having to go back and select and upload them one by one.

I'd like to find a solution along these lines: I could tag (in FSpot? Other) and then copy the tagged photos to a separate directory.  I poked around FSpot, and lots of plugins to upload to thinks like flikr etc... but that's not going to cut it.

Any advice?  I'm all ears!!!

Thanks,
Ian

---

### Post by nothingspecial on 2010-10-01
Hi, I think feh might be able to solve your problem

Assuming your the 20 directories are under a single directory, for example ~/Photos

```
feh -rzF -D 3 ~/Photos
```

You may or may not want all those options, I`ll break it down. This command will create a slideshow of all the photos in that directory.

-r is recursive, you`ll need that one to go through all the subdirectories

-z makes it random, you may or may not wan`t that

-F makes it fullscreen

-D 3 means the delay (the amount of time each photo is displayed ) is 3 seconds, change it to what you like.

You can skip to the next picture or go back using the arrow keys.

This is the important part. Create a folder for the photos you want to upload say ~/Desktop/Costco

Go there ```
cd ~/Desktop/Costco
``` and run the feh command from there.

Now as you go through the photos, each time you see one you like press the S key

That will save a copy of that photo to the directory you ran the command from, in your case ~/Desktop/Costco, so eventually you will have the 50 photos in that directory. It doesn`t move them, it makes a copy so the photos will still be in their original place.

This is what I do if we`ve come back from a holiday or whatever. I hook it up to the Tv and me the wife and kids watch the slide show. Every time someone shouts "Yes" or "That one!" I just hit the S.

Type man feh to see all the options.0

---

### Post by ian2112 on 2010-10-01
Thanks for advice - I'll give that a whirl.  And, I can always use another opportunity to use the command line.

Thanks,
Ian

---

### Post by jdmpike on 2010-11-24
feh is pretty cool - thanks for the tip.

I would like to see a Costco exporter in f-spot. I have spent a little time this morning looking at the Exporters for other services. I am not sure I have what it takes, but I might take a stab at trying to develop a plugin to push photos to costcophotocenter.com for easy printing.

Does anyone out there know of an f-spot extension that already does this? Does anyone want to help develop it?

Happy holidays,

jdmpike

---

