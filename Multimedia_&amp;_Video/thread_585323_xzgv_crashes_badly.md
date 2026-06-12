---
title: "xzgv crashes badly"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by egalua on 2007-10-21
Hi all,

I successfully installed gutsy (and I also added kubuntu-desktop after the installation).
At the end, I installed the viewer xzgv from the universe repository: I like it and I used succesfully in the last ten years on many distributions, including dapper and feisty.

Now, on gutsy it starts regularly but as soon as I try to update the thumbnails inside a directory, or as soon as I enter a directory with thumbnails already created, it crashes badly.

It gives, on the terminal, a gtk error: I can't remember it because it is on my desktop at work: if needed, tomorrow I can forward the error.

For the moment, my question is: is there anybody else using xzgv on gutsy out there? Does it work ok? Can you please try it? (it is a matter of seconds installing it and giving it a try...)

Thank you a lot

Fabio

---

### Post by PurposeOfReason on 2007-10-31
I just gave it a shot today. It worked at first, I changed something, and it broke. I reinstalled but I still get (see below) on some folders.

```

Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 1413 error_code 8 request_code 148 minor_code 3

```

Actually, that's only my wallpaper folder. Might have to do with image types if so.

---

### Post by egalua on 2007-11-07
I get exactly the same error.

The problem is that I get it as soon as I try to generate the thumbnails of the images, regardless of the image type.
If the thumbnails are already there, then xzgv crashes as soon as I enter the directory.

Fabio

---

