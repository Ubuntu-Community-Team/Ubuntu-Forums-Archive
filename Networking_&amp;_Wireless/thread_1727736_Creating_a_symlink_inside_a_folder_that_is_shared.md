---
title: "Creating a symlink inside a folder that is shared"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by mogators on 2011-04-12
I just added a 2GB hard drive to free up some space on my Ubuntu Media server.  My old 1 GB drive was setup like this:  mounted as /media/data1; shared 3 folders named data, downloads, and media.  Inside my media folder I have subfolders for music, movies, and pictures.  
I mounted the new 2 GB hard drive as /media/data2 and created a folder in it called movies.  I then renamed the /media/data1/media/movies folder to /media/data1/media/movies-old.  I then created a symlink in /media/data1/media/movies -> /media/data2/movies.

When browsing the network from my Win7 machine, I cannot access the movies folder, I get an access is denied.  I am the owner of all the files and have permissions set wide open.  Is it possible to do what I'm attempting to do?

---

