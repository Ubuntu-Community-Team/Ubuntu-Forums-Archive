---
title: "Same image for 5 minutes using ffmpeg ?"
date: 2009-09-12
forum: Multimedia Software
---

### Post by ubuntizer on 2009-09-12
Hello.
I have been trying my hands on ffmpeg recently.

I have a .jpg file and i would like a video showing the jpg file for 5 minutes.

The following code just gives the image for 1second, how can i get a video with the image shown for 5minutes ?

```
ffmpeg -r 1 -b 1800 -i image.jpg output.mp4
```Any help would be really appreciated. 8-[

Thanks

---

### Post by ubuntizer on 2009-09-12
Just found the solution to the problem myself after some more google game :P
Here's the code.

```
ffmpeg -loop_input -vframes 300 -r 1 -b 1800 -i image.jpg output.mp4
```

Thanks Anyhow.

---

