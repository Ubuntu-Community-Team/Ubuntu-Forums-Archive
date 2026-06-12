---
title: "ImageMagick"
date: 2009-12-28
forum: Multimedia Software
---

### Post by pajoohesh on 2009-12-28
Hi all,

I have a small problem with the mogrify tool in Image Magick. I have read the mogrify and convert documentation but no clue. Another thing is that I want to avoid scripting in Perl or etc.

I want to resize a bunch of pictures and renaming them.
The first part is pretty much OK:
```
mogrify -resize 800x600 *.jpg
```

Now I want to append 800x600 to the file name by using %wx%h, but I have no idea. Something like this:
```
mogrify -format %b_%wx%h.jpg ?
```

Or probably both of the commands can be fit in to one?

Any idea?

Regards,

---

### Post by kaibob on 2009-12-29
I don't believe the mogrify command will do what you want. It's my understanding that the -format option is primarily used with the identify command to extract image and file characteristics.

My inclination would be to write a simple shell script utilizing the convert command, but you appear to have ruled that out. Perhaps you can use the mogrify command to resize then use the rename command to add 800x600 to the file names. For example,

```
rename -v 's/.jpg/800x600.jpg/' *
```

---

### Post by pajoohesh on 2009-12-29
Thanks kaibob.

---

