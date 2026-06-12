---
title: "Drag &amp; Drop media from smb share?"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by scrop on 2006-11-02
For some reason, I can drag and drop media into totem or banshee or just double click on a file I've browsed to and it works just fine if its the local fs. 

Windows shares don't work at all. I can browse them just fine but I have to copy them to my disk locally before I can play them.

Why?

---

### Post by kidders on 2006-11-02
Hi there,

If movies are jumpy over your network, take a look at your buffering settings in smb.conf and your mount options for the fileshare, just to make sure they're reasonable. This is odd though, since the defaults are usually pretty okay.

---

### Post by scrop on 2006-11-02
Its not they are jumpy, its that it the movie can not be played from that location. Totem refuses to open it, but I can copy it and play it locally.

---

### Post by kidders on 2006-11-03
Are you using KDE?

---

### Post by Adamal on 2007-01-05
I have this problem using totem and gnome.

---

### Post by kidders on 2007-01-05
Hi there,

Are you sure you're not doing something weird? Linux is arranged so that, once a remote filesystem is mounted, it would be tough for an app like totem to find out that the files in it aren't actually on your own hard disk.

Say you do **mount -t smbfs //server/share /mnt/movies**. Other than things like partitions managers (whose job it is to know where things really are), I've never seen an application refuse to handle /mnt/movies/movie.avi, on the grounds that it's not a local filesystem.

This might seem silly, but I wonder if you could go, step by step, through what you're doing for us ... there must be something odd going on.

---

### Post by Adamal on 2007-01-05
The problem arises with you use the connect to server feature in nautilus.  It doesn't do a real mount.  It just says it does.  In fact if you right click you have the option to unmount.

If you mount manually using the mount command it works, but that is a pretty bad solution.  If I'm mounting the share in nautilus, it should mount the share but it doesn't seem to be doing that.  So when you click on the media file totem tries to play smb://path/filename which fails.

---

