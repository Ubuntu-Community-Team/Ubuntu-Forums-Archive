---
title: "sorting photos on exif"
date: 2011-08-30
forum: Multimedia Software
---

### Post by Witch Lady on 2011-08-30
Hi,

The problem is: Me & my 2 friends were making photos on hours-log-event. Now, we want to put it chronologically, but as you can imagine, it was uploaded on different times on our computers. 

Now, how do I put the photos in folder sorted by actual time of photo taken (which is in exif)?

---

### Post by Witch Lady on 2011-11-04
question still appplicable.

---

### Post by Steeperton on 2011-11-04
pyrenamer will rename your files based on EXIF data. Maybe renaming them with the time stamp will work?

---

### Post by Witch Lady on 2011-11-04
Such a renaming is only a half-mean. In this case it could have worked (made something else). But now, I still have photos from various cameras, which I don't want to rename. Sorting by exif is the best solution. 

So, is that possible?

---

### Post by m42tyger on 2012-02-01
I'm looking into this myself at the moment. I found the below, for mp3s, which might be modifiable for photos.

[http://ubuntuforums.org/showthread.php?t=878683&highlight=browse+exif+data](http://ubuntuforums.org/showthread.php?t=878683&highlight=browse+exif+data)

Will let the thread know if I am able to do anything.

---

### Post by m42tyger on 2012-02-01
The link I posted above does address image exif data, but I couldn't get the deb installer uploaded in the thread to work ("deb is for amd64 architecture" error, I'm on x86).

I followed the rabbit and found this blog where that gives some terminal commands. It works!

[https://techsupporttv.wordpress.com/2010/11/17/add-mp3-wav-and-exif-columns-to-your-nautilus-view/](https://techsupporttv.wordpress.com/2010/11/17/add-mp3-wav-and-exif-columns-to-your-nautilus-view/)

```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install nautilus-columns

```

Once installed, it should automatically restart Nautilus but in case it doesn’t, manually restart Nautilus using the following command:

```

nautilus -q

```

---

### Post by dandaman96 on 2012-04-04
I've spent most of the afternoon looking for the same solution.  When I follow the last suggestion, it tells me that the nautilus-columns package is not available.  I'm running 11.10.  I guess the search continues.

---

