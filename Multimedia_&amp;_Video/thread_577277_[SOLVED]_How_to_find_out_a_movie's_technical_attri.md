---
title: "[SOLVED] How to find out a movie's technical attributes?"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-10-16
I've got a movie file, "mov.mpg", stored in my hard drive. I'd like to find out some of the technical attributes of the movie, such as the natural screen dimensions, the frame rate and the total number of frames. How can i accomplish this task, preferably using the command line only?

---

### Post by yabbies on 2007-10-16
exiftool

```
sudo apt-get install libimage-exiftool-perl
```

here's the man[URL="http://www.sno.phy.queensu.ca/~phil/exiftool/exiftool_pod.html"]
http://www.sno.phy.queensu.ca/~phil/exiftool/exiftool_pod.html[/URL]

just by browsing through looks llike command is
```

cd "whatever directory the movie is in"
```
```
exiftool "mov.mpg"
```

---

### Post by berliita on 2007-10-17
Thanks a lot, yabbies. :)
"qtinfo" is the name of another command-line application that's suitable for this purpose. But in my experience, it can't always handle all types of files.

---

