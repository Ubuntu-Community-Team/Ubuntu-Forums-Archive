---
title: "ripping an ebook from flash"
date: 2012-01-13
forum: Multimedia Software
---

### Post by betterbutterman on 2012-01-13
lately iv been trying to rip an ebook from a my collage so as to keep it for offline homework time. iv found the files locations -
website.com/ebook/swf/ebookname/0001.swf
where 0001.swf is the ebook pages in swf format.
each swf is one page
i also found while snooping around a text file with every page number
i to xviii
1 to 752and some other a1-a4 aa1-aablah blah
is there a way i can download all of these at once? manually saving each file into a folder seems barbaric.
any help would be greatly appreciated

---

### Post by ageofsteam on 2012-05-09
The Firefox addon DownThemAll supports arguments to download numbered files.  For instance, adding 
```

http://www.fakesitehere.com/fakegallery/funnycatphotos[0001:9001].jpg

```could download **OVER 9,000 :lolflag:**funny cat photos (if they existed.) **[1]**

[SIZE=1]**[1]** I'm sorry for that example, but not sorry enough to change it.[/SIZE]

---

### Post by shantiq on 2012-05-10
i would have thought [**jd downloader**]("https://launchpad.net/~jd-team/+archive/jdownloader")

---

### Post by flemur13013 on 2012-05-10
$ wget website.com/ebook/swf/ebookname/0001.swf

You'll get a file named 0001.swf in whatever directory you're in.

"each swf is one page"

That's a rip!  But with wget you can make a simple script to DL all the pages.

---

### Post by ageofsteam on 2012-05-14
> **flemur13013 said:**
> $ wget website.com/ebook/swf/ebookname/0001.swf

You'll get a file named 0001.swf in whatever directory you're in.

"each swf is one page"

That's a rip!  But with wget you can make a simple script to DL all the pages.

True!   I can't believe I forgot about wget. >_>;  DTA is better for huge files, but with book pages that wouldn't be an issue...

What he said.  Use wget.

---

