---
title: "f-spot very slow"
date: 2008-06-15
forum: Multimedia Software
---

### Post by frogitts on 2008-06-15
Since Ubuntu doesn't yet have a satisfactory photo suite, I'm using digikam to upload my photos to get the directory structure I want, then importing the photos into f-spot so that I can upload them onto picasaweb and facebook (since the picasaweb plugin for digikam doesn't work). However, I recently, though I can't remember why, removed almost all of the imported photos I had in f-spot. Why I did that isn't important, but now I'm trying to import all of my photos back into f-spot.

Importing goes very slow - it took a couple of hours to get about 2,500 of my 7,500 photos in (1-4 seconds per photo, when I was watching). Halfway through I got sick of it hogging my computer because I needed to do work, so I did a force quit. I opened it up again later to find that those 2,500 or so photos actually had been imported. However, now I can't scroll in f-spot without the program turning grey for a little and then taking about a minute to load all of the thumbnails in the new view. This, needless to say, makes the program unusable.

To debug, I ran f-spot through the terminal to see what sort of messages I'd get. I got three errors at the beginning about not being able to write text to some other variable or something like that. Then it was constantly saying "syncing metadata to file..." with the output of that operation. I looked, and "write metadata to file" was checked in my preferences. I unchecked that, exited, and restarted f-spot through the command line. No change. Then I removed all of the photos and restarted f-spot in the command line. Here are the errors I'm getting:

At the start:
```
Syncing metadata to file...
Error syncing metadata to file
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Jobs.SyncMetadataJob.WriteMetadataToImage (FSpot.Photo photo) [0x00000] 
  at FSpot.Jobs.SyncMetadataJob.Execute () [0x00000] 

(f-spot:27783): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

```

About 2-3 times per second:
```
Syncing metadata to file...
Error syncing metadata to file
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Jobs.SyncMetadataJob.WriteMetadataToImage (FSpot.Photo photo) [0x00000] 
  at FSpot.Jobs.SyncMetadataJob.Execute () [0x00000] 

```

The second error I'm getting without even touching the program - that is, it's not a result of user interaction. Anyone have any idea where these errors could be coming from? Especially considering that "write metadata to file" is not selected?

---

### Post by frogitts on 2008-06-15
Well, I thought a reinstallation of f-spot would do the trick. Of course, I was wrong. Absolutely nothing changed - and I mean, nothing. Even though my configuration files were supposedly deleted (I marked it for complete removal), my preferences, extensions, tags, custom tags, and imported photos were all still there. It was as if I had never uninstalled it. Definitely creepy.

Anyone know how to reinstall f-spot?

---

### Post by catchmeifyoutry on 2008-06-15
Your photo library is stored in ~/.gnome2/f-spot/photos.db, so if you delete the ~/.gnome2/f-spot directory manually, it should all be empty, me thinks. Did you try manual removal of your f-spot settings files already?

---

### Post by frogitts on 2008-06-16
I didn't get a chance to try your advice, sorry.

I restarted my computer and things magically fixed themselves. Not like I hadn't restarted before (I'm pretty sure I had, Ubuntu seems to need it a lot).

Anyway, I guess the moral of the story is that if f-spot slows down a lot, restart your computer a few times, and maybe reinstall it and then restart.

---

