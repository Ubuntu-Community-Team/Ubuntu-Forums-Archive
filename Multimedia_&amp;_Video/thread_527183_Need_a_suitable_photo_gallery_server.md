---
title: "Need a suitable photo gallery server"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by jdogzilla on 2007-08-16
Hello all, 

I am looking for a server application which I can use to share my personal photos with family.   I'm looking for something that works like ampache ... 1) allows creation of users, and 2) allows me to maintain my photos in whatever directory I want on my server,  and 3) allows me to just point to the folder containing the photos and indexes it accordingly.  The challenge here is that it must index by the folder name and not by the name of the photos.  Or it may not need to index at all. 

Other servers that I have tried, like gallery, require that I add my photos to the repository or MySQL database, and I don't want to have to store the same set of photos in multiple locations.  

Anybody have any suggestions?  

Thanks

---

### Post by newlinux on 2007-09-04
> **jdogzilla said:**
> Hello all, 

I am looking for a server application which I can use to share my personal photos with family.   I'm looking for something that works like ampache ... 1) allows creation of users, and 2) allows me to maintain my photos in whatever directory I want on my server,  and 3) allows me to just point to the folder containing the photos and indexes it accordingly.  The challenge here is that it must index by the folder name and not by the name of the photos.  Or it may not need to index at all. 

Other servers that I have tried, like gallery, require that I add my photos to the repository or MySQL database, and I don't want to have to store the same set of photos in multiple locations.  

Anybody have any suggestions?  

Thanks

Bump... I'm looking for something similar.

---

### Post by robglinka on 2007-09-13
I found this thread while looking at newlinux's mythtv advice and discovered that I could actually return some advice!!!

I don't understand why gallery doesn't do what you are looking for, you can keep the files wherever you want, you can make users, secure directories, and make albums.

[http://gallery.menalto.com/]("http://gallery.menalto.com/")

I use gallery2. It is very easy to set up (assuming you already have an LAMP server running), just drop the install into the /var/www directory.

I use this in addition to my mythweb setup, and they work perfectly for my needs. I have my mythweb directory secured, and the gallery directory in the /var/www root open to the public.

Rob

---

