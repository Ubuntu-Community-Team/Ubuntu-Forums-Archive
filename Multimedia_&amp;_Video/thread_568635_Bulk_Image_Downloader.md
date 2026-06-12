---
title: "Bulk Image Downloader"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by steevols on 2007-10-06
Does anyone know of a decent bulk image downloding tool for Linux? There are extremely useful in my 3D work for downloading large amounts of textures from forums, etc. I found one called "Bulk Image Downloader" in Windows, but it doesn't work in Wine.

---

### Post by quux on 2007-10-06
Maybe the Firefox extension downthemall ([http://www.downthemall.net/]("http://www.downthemall.net/")) suits your needs.

---

### Post by Zootropo on 2007-10-06
With DownThemAll you can download all the files in from a page or you can filter the ones you want using regular expressions. You also have checkboxes to download all the images, compressed files or video files without having to write a regular expression.

Cool tool :)

---

### Post by steevols on 2007-10-06
I've tried DTA before, but it doesn't work in many common scenarios.

If, for example, you went to the Oct Desktop Thread, and used it to download the pictures, it would work on the ones that were "attached" to the posts. All the images that were uploaded to, say, ImageVenue would not be downloaded.

---

### Post by SPr on 2007-10-06
Hi,

I don't know how the forum you use stores the textures but could wget work?
from man wget:
> ·   You want to download all the GIFs from a directory on an HTTP
           server.  You tried wget [http://www.server.com/dir/*.gif](http://www.server.com/dir/*.gif), but that
           didn&#8217;t work because HTTP retrieval does not support globbing.  In
           that case, use:

                   wget -r -l1 --no-parent -A.gif [http://www.server.com/dir/](http://www.server.com/dir/)

           More verbose, but the effect is the same.  -r -l1 means to retrieve
           recursively, with maximum depth of 1.  --no-parent means that ref&#8208;
           erences to the parent directory are ignored, and -A.gif means to
           download only the GIF files.  -A "*.gif" would have worked too.


---

### Post by marty922 on 2008-01-07
> **steevols said:**
> Does anyone know of a decent bulk image downloding tool for Linux? There are extremely useful in my 3D work for downloading large amounts of textures from forums, etc. I found one called "Bulk Image Downloader" in Windows, but it doesn't work in Wine.

Did you have any luck with this?

---

