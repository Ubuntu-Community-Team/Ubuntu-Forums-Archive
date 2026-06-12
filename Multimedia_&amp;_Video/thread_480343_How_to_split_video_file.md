---
title: "How to split video file?"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by Ubivetz on 2007-06-21
Hi All!

I have large video (about 8 Gb size) packed with Windows Media codec (and this file has wmv extension) and I need to split in into 2 or more parts. How can I do it?

---

### Post by blackened on 2007-06-21
On the command line
```
man split
```

---

### Post by philc on 2008-01-30
> **nicb1977 said:**
> Try to use VideoCharge (Google, it)

From your website, System Requirements:

    *   Windows ME, Windows NT 4.0, Windows 2000, Windows XP, Windows Vista
    * 64MB RAM (128MB recommended)
    * 30MB of free hard disk space
    * 800x600 screen resolution
    * DirectX 8.1 or higher
    * Installed codecs for media formats you are going to work with 

Why would your product be of interest on an Ubuntu forum?

---

### Post by philc on 2008-01-30
> **Ubivetz said:**
> 
I have large video (about 8 Gb size) packed with Windows Media codec (and this file has wmv extension) and I need to split in into 2 or more parts. How can I do it?

If you are comfortable with using the command line, FFmpeg will do this for you.

Your command might look something like this:

```
ffmpeg -i input.mpg -ss 00:00:10 -t 00:00:30 out1.mpg
```

-ss is the start point in hh:mm:ss from the beginning of your video file

-t is the length of time in hh:mm:ss of your new segment.

So, in the above example, you're starting 10 seconds in from the beginning of the original file and ending 30 seconds later.

If you want to create multiple parts in one pass then the following should work:

```
ffmpeg -i input.mpg -ss 00:00:10 -t 00:00:30 out1.mpg -ss 00:00:35 -t 00:00:30 out2.mpg
```

In this example, the first segment is the same as the first example, but you're also creating a second file starting at 35 seconds in and being 30 seconds long.

If you would rather use a GUI tool for this, there are a number of options too. Search for ConvertIT or Fuoco Tools on this forum. Look into WinFF, ThinLiquidFilm and Avidemux.

If you want to use a more traditional non-linear editor, then I would recommend [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage") for this job. It's easy to add a clip to the time line, split the segment you need, then render to your new format. If you'd like to know more about Open Movie Editor, I recently wrote a [review of the software]("http://stream0.org/2008/01/open-movie-editor-surprisingly.html").

---

### Post by ahaslam on 2008-01-30
^ good advise ;)

---

