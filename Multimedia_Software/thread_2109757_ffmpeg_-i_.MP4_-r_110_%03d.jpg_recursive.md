---
title: "ffmpeg -i *.MP4 -r 1/10 %03d.jpg recursive?"
date: 2013-01-28
forum: Multimedia Software
---

### Post by sohlinux on 2013-01-28
How can I run the following command recursively through all sub folders in a folder?

ffmpeg -i *.MP4 -r 1/10 %03d.jpg


thanks

---

### Post by matt_symes on 2013-01-28
Hi
 
Try something like this
 
```
find /path/to/folder -name "*.MP4" -exec ffmpeg -i "*.MP4" -r 1/10 %03d.jpg \;
```
 
Kind regards

---

### Post by sohlinux on 2013-01-28
> **matt_symes said:**
> Hi
 
Try something like this
 
```
find /path/to/folder -name "*.MP4" -exec ffmpeg -i "*.MP4" -r 1/10 %03d.jpg \;
```
 
Kind regards

thanks but that shows
*.MP4: No such file or directory

---

### Post by matt_symes on 2013-01-28
Hi
 
Sorry. My mistake.
 
Try this.
 
```
 
find /path/to/folder -name "*.MP4" -exec ffmpeg -i {} -r 1/10 %03d.jpg \;

```
 
Kind regards

---

### Post by andrew.46 on 2013-01-28
Perhaps *-iname* might catch both .MP4 and .mp4....

---

### Post by sohlinux on 2013-01-28
> **matt_symes said:**
> Hi
 
Sorry. My mistake.
 
Try this.
 
```
 
find /path/to/folder -name "*.MP4" -exec ffmpeg -i {} -r 1/10 %03d.jpg \;

```
 
Kind regards


thanks but the jpg files are all being written to the same folder, how can I make it write the screen caps to the sub folders folder1 folder2 etc? 

thanks

thanks

---

### Post by sisco311 on 2013-01-28
> **andrew.46 said:**
> Perhaps *-iname* might catch both .MP4 and .mp4....

+1 for the -iname test.

> **sohlinux said:**
> thanks but the jpg files are all being written to the same folder, how can I make it write the screen caps to the sub folders folder1 folder2 etc? 

thanks

thanks

Instead of -exec use the -execdir command.

Oh, and please check out: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by sohlinux on 2013-01-28
> **sisco311 said:**
> +1 for the -iname test.



Instead of -exec use the -execdir command.

Oh, and please check out: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

that works , thanks!

---

### Post by sohlinux on 2013-01-28
> **andrew.46 said:**
> Perhaps *-iname* might catch both .MP4 and .mp4....

iname didn't process the lowercase extensions, it would be interesting to do so because sometime some videos have lowercase extensions.

thanks

---

### Post by evilsoup on 2013-01-28
Perhaps try using "*.{mp4,MP4}" rather than just "*.MP4".

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> Perhaps try using "*.{mp4,MP4}" rather than just "*.MP4".

thanks but that doesn't appear to do anything, it doesn't process any files nor does it give any error.

---

### Post by evilsoup on 2013-01-29
Just tested, yeah turns out find doesn't support the same globbing as bash does.

As Andrew suggested, -iname "*.mp4" should work on all *.mp4 and *.MP4 files.

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> Just tested, yeah turns out find doesn't support the same globbing as bash does.

As Andrew suggested, -iname "*.mp4" should work on all *.mp4 and *.MP4 files.

your right, lower case appears to process the uppercase extensions too

---

