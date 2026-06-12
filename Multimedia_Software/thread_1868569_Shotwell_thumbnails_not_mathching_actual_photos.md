---
title: "Shotwell thumbnails not mathching actual photos"
date: 2011-10-24
forum: Multimedia Software
---

### Post by Lars Noodén on 2011-10-24
I have a lot of images in Shotwell where the thumbnail image does not match the actual photo it links to.  Is there a way to force Shotwell to rebuild all its thumbnails?

---

### Post by eric-yorba on 2011-10-24
There is not a way to re-thumbnail on demand (though we have an open ticket for that.)

What kind of issues are you seeing with the thumbnails?  Did you make any changes to the ~/.shotwell folder?

---

### Post by Lars Noodén on 2011-10-25
The problem seen with some of the thumbnails was that they were showing a somewhat distorted view of the wrong picture.  A clumsy work-around was to delete the entire .shotwell directory and re-import all the images.

---

### Post by eric-yorba on 2011-10-25
What do you mean by "distorted"?  Also, when the wrong picture was shown, was it just random or was there some pattern to it?

---

### Post by celafon on 2012-06-06
> **eric-yorba said:**
> There is not a way to re-thumbnail on demand (though we have an open ticket for that.)

What kind of issues are you seeing with the thumbnails?  Did you make any changes to the ~/.shotwell folder?

Hi

Sorry for hijacking the thread but I have actually backed up only the DB not a .shotwell folder and now after restoring it everything is OK but  grey are the thumbnails... Is there a way to recreate them? I am on 12.04

THanks
Bart

---

### Post by eric-yorba on 2012-06-06
> **celafon said:**
> Sorry for hijacking the thread but I have actually backed up only the DB not a .shotwell folder and now after restoring it everything is OK but  grey are the thumbnails... Is there a way to recreate them? I am on 12.04
Wow, old thread!  But yes, you're in luck; it turns out there IS a way to re-create thumbnails, but it's a bit of a hack.  Just do the following:

1. Disable metadata writing in the prefs (if not already disabled)
2. In the Shotwell library window, select all the photos
3. Hit the "rotate" button
4. Edit->Undo

This may take a few minutes if you have a lot of photos, but it should force Shotwell to rebuilt your entire thumbnail cache.

---

### Post by celafon on 2012-06-06
Quick reply! Considering in my place its 1am :) Guess you're in the US.

There's one problem with this. How do I deselect movie clips? I think they're causing the rotate option to be disabled (greyed out) once everything gets selected. Is there a way to select only photos?

Thanks!
Bart

OK. Found it!:
Hitting the search option while whole collection is selected allows choosing only picture which worked. Now the rotate option is available. Thank you!

A quick question: As the metadata is not stored with the files, I understand that pictures are not touched, only shotwell's data is, right?

---

### Post by eric-yorba on 2012-06-06
Yup, we're located in San Francisco.

For future reference, if you activate the search filter bar (F3) you can click the "Photos" button and Shotwell will show only photos.  I should have mentioned that.

And you're correct, Shotwell does not modify your original files in any way if you have metadata writing off.  If you have it enabled, it will write tags and titles to the photo's EXIF, it's a format we can write to (i.e. not RAW or video files.)

---

### Post by celafon on 2012-06-07
No luck. I've also checked this on a single picture. But rotating (left/right/flipping) wont change the gray thumbnail. I guess something has changed in there since last time this hack was OK.

I will just recreate the db.

---

### Post by bitinerant on 2012-12-02
I found a good work-around (see below). :)

I am using Shotwell 0.12.3 and having the same problem as Lars.  Lars wrote:

[INDENT]The problem seen with some of the thumbnails was that they  were showing a somewhat distorted view of the wrong picture. A clumsy work-around was to delete the entire .shotwell directory and re-import all the images.[/INDENT]

In my case, "distorted" means wrong aspect ratio.  In short, it shows the thumbnail of the wrong photo, and the thumbnail is squished in one direction.  This is only for a few photos, but it is troubling.  Deleting the database is not an option because it would mean looseing hundreds of hours of metadata (crop, rotate, etc.) 

I tried the rotate work-around described above, and also deleting the thumbnails, but neither worked.  However, **THIS DID WORK:  'Enhance' and then undo.**

Rebuilding missing thumbnails would be a nice feature.

---

### Post by eric-yorba on 2012-12-02
> **bitinerant said:**
> Rebuilding missing thumbnails would be a nice feature.

Such a good feature that we added it in Shotwell 0.13!

---

### Post by bitinerant on 2012-12-02
> Such a good feature that we added it in Shotwell 0.13!

Good to know!  Thanks.

---

### Post by diff111 on 2012-12-18
> **eric-yorba said:**
> Such a good feature that we added it in Shotwell 0.13!

Where is it? I can't find it. I'm using Shotwell 0.13.1.

---

### Post by eric-yorba on 2012-12-18
> **diff111 said:**
> Where is it? I can't find it. I'm using Shotwell 0.13.1.

As soon as you start Shotwell it will automatically detect missing thumbnails and regenerate them.  (If you have a lot of photos, this can take a while.)

If I recall there's a bug where the progress bar doesn't show activity during the thumbnail regen, so unfortunately there's no visible sign that this is happening, aside from thumbnails appearing.

---

### Post by diff111 on 2012-12-19
> **eric-yorba said:**
> As soon as you start Shotwell it will automatically detect missing thumbnails and regenerate them.  (If you have a lot of photos, this can take a while.)

If I recall there's a bug where the progress bar doesn't show activity during the thumbnail regen, so unfortunately there's no visible sign that this is happening, aside from thumbnails appearing.

OK, thank you for your answer. I tested it. On my machine, the thumbnails for images are indeed reconstructed. But nothing is done for video files.

---

### Post by eric-yorba on 2012-12-19
Looks like we have a ticket for this now, diff111.  (Not sure if you're the one who filed it or not.)  For future reference it's here:
[http://redmine.yorba.org/issues/6152](http://redmine.yorba.org/issues/6152)

---

### Post by Lars Noodén on 2012-12-19
Thanks.  I didn't file that one, but it's good to know that it's being addressed.

---

### Post by diff111 on 2012-12-20
> **eric-yorba said:**
> Looks like we have a ticket for this now, diff111.  (Not sure if you're the one who filed it or not.)  For future reference it's here:
[http://redmine.yorba.org/issues/6152](http://redmine.yorba.org/issues/6152)

Yes, it was me who filed it. Thank you for your hard work at making such a fine piece of software.

---

